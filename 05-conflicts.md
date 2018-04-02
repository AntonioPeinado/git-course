# Conflicts

After a `pull` or `merge` command it is not rare to find `conflicts` in our code.
Most changes will be automatically merget but if, for example, you and another person edited the same file lines at the same time. This conflicts must be resolved with a new commit before you can `push` the changes to the `remote repository`.

![pizza](./05-conflicts.jpg)

## Detecting conflicts

For knowing which files have conflicts use `status` to see different information about the current state of your local repository:

```bash
git status
```

Most text editors offer support for fixing conflicts but it is usefull to know how to identify them:

* `<<<<<<< HEAD` marks the line where the conflict beggings.
* `=======` separates the `current` and `incoming` changes.
* `>>>>>>> branch_name` marks the end of the conflict.

## Resolving conflicts

1. Before going berserk and erasing all your teammates work please go ask them why they broke your code.
2. Decide which changes should take effect: yours (`current`), theirs (`incoming`), both or a mix of them.
3. Stage and commit yout changes:

    ```bash
    git add .
    git commit -m "fixed conflict"
    ```

## Removed files

If someone deleted a file you have edited, you have to decide whether to keep it or not in order to fix the conflict. Then proceed as above.