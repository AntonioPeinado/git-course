# Tips and tricks

## Ignoring files and folders

In order to ignore certain files and folders create a `.gitignore` file in your project root directory. Then write the name of the files and directories you don't want to include under version control.

```bash
node_modules
dist
.my-local-config-file
```

Note that all files and folders named that way will be ignored, not only the ones in the directory of the `.gitignore`.

For complex use cases refer [here](https://git-scm.com/docs/gitignore)

## Keeping empty folders

Empty folders are by default excluded from version control, if you need to preserve your folder structure you can add a `.gitkeep` file so the folder is pushed to the remote repository.

If by any change, you want to keep a folder but ignore its contents, you can do so by creating a '.gitignore' file inside it with the content:

```bash
*
*/
!.gitignore
```

`*` is used to ignore  all files in the folder. `*/` ignores all subdirectories and `!.gitignore` indicates to ignore the `.gitignore` file from exclusion.

## Git Hooks

Git hooks are a powerfull tool to intecrate tools or add custom behaviours to our git commands.

Every `git hook` is located under `./git/hooks` and is called in a way that indicates when it is going to be executed, so for example `pre-commit` will be executed before the `commit` command starts running.

Those files are programmed in `sh` but fear not Windows users, since `git bash` will be used to execute them.

Hooks cannot be configured from the repository, setting them up is responsability of each programmer in its local machine, but there are several build tools that solve this _problem_ such as [`husky`](https://www.npmjs.com/package/husky) for `NPM`.

### Linting modified files before commiting

One common use case is to use a linter to analyze our modified files before commiting them, in that way we can detect if the quality of our commit is going to be under our team standarts, and if so, abort the commit:

`pre-commit`

```bash
#!/bin/sh

# Get staged .js files, but only the ones added, coppied or modified
STAGED_FILES=($(git diff --cached --name-only --diff-filter=ACM | grep ".js\{0,1\}$"))

# Get ESLint executable
ESLINT="./node_modules/.bin/eslint"

# Define some colors for the messages
RED='\033[0;31m'
NC='\033[0m'

# Nothing to commit
if [[ "$STAGED_FILES" = "" ]]; then
 exit 0
fi

# Check for ESLint executable
if [[ ! -x "$ESLINT" ]]; then
 echo -e ${RED}"\tPlease install ESLint (npm install eslint)"${NC}
 exit 1
fi

# Pass ESLint on all staged files at once, save the exit code
$ESLINT "${STAGED_FILES[@]}" --fix
failed="$?"

# Re-add files since they may have been fixed and therefore modified again
git add "${STAGED_FILES[@]}"

# If ESLint failed abort the commit
if [[ $failed != 0 ]] ; then
 echo -e ${RED}"\t🚫 🚫 🚫  ESLint failed, git commit denied! Look output above and fix the errors."${NC}
 exit $failed
fi

```

The above script will be executed everytime you issue a `commit` but, if in a hurry, you can skip pre-commit checks with the `--no-verify` option:

```bash
git commit --no-verify
```