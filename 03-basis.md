# Basis

## Files lifecycle

![Files lifecycle](./03-lifecycle.png)

### Working directory

Its the directory where your project is located within your computer, changes here will be invisible to the rest of the team.

### Staging area

Here are the files that contain changes with respect to the local repository, all files in this area will be later committed.

### Local repository

If a created, modified or removed file is in the staged area, it will be stored to the local repository once commited.

All files in the local repository will be compared with the remote one and then combined as appropiate.

### Remote repository

Here your project is stored and accessible to your team members. Changes can be identified and tracked and different strategies  can be implemented to adopt a correct version control system.

## Daily commands

### Add

`add` command is used to push files into the staging area, it recieves as its argument the directory or files to push:

```bash
git add . # Adds the current directory to staging
```

### Commit

`commit` is used for storing stagged files into the local database that represents our local repository. We can must add a commit message through our configured text editor or with the option `-m`.

```bash
git commit -m "some important info"
```

### Push

`push` is used to store our changes into the remote repository. Before pushing our changes we must first get the latest copy of the remote repository.

```bash
git push origin destination # Destination is by default your current branch!
```

### Pull

`pull` is used to synchronize our local copy with the remote repository contents, here is when `conflicts` will appear if not following a proper strategy.

```bash
git pull origin destination # Destination is by default your current branch!
```

## Emergency commands

### Delete local changes

If wanting to un-stagge your `uncommited` changes you can do it by using `stash` command.

```bash
git stash
```

This will reset our local copy to `HEAD`, the last version we pulled from / pushed to the remote repository. Changes will not be lost, they will be stored in your local database. You can find more information about the `stash` command [here](https://git-scm.com/docs/git-stash).

### Revert changes to commited files

If wanting to erase all changes on commited files, use `reset` command with the `--hard` option. Use with caution!

```bash
git reset --hard
```

Read more [here](https://git-scm.com/docs/git-reset)

### Remove untracked files

If wanting to remove files before stagging them with `add`, but not all of them, use `clean` with the option `-i`, this will open a prompt where you can work interactively.

```bash
git clean -i
```

More about `git-clean` [here](https://git-scm.com/docs/git-clean).

### Revert to an specific commit

If you have really messed things up you can revert the remote repository state to a previous commit using the `revert` command with the option `--no-commit` which lets git revert all the commits at once and specifying the `commit id` you want to become `HEAD`. Once again, use with caution.

```bash
git revert --no-commit commitId HEAD
```

Find more [here](https://git-scm.com/docs/git-revert).