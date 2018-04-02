# Branches

## Creating a new branch

For creating a new branch use the following command

```bash
git branch branch_name
```

This will create a new branch in your `local repository` which will be a copy of your currently active branch, sharing its contents and history.

## Switching to another branch

For switching between branches use:

```bash
git checkout branch_name
```

This will switch your working directory contents to the ones of the checked out branch.

Note that if the branch exists only in the remote repository you need to `fetch` it so it becomes available in the local one:

```bash
git fetch && git checkout branch_name
```

## Pushing to the new branch

If wanting to make a new branch available in the `remote repository` configure the `upstream` when pushing:

```bash
git push --set-upstream origin branch_name
```

If the branch was available in the remote repository just use `push` as you normaly would.

## All in one

If you want to create and switch to the new branch at once you can use the `-b` option with the `checkout` command:

```bash
git checkout -b branch_name
```

## Deleting a local branch

Just use the `-d` option with the `branch` command:

```bash
git branch -d local_branch
```

## Deleting a remote branch

If you really need to delete a remote branch, you can use the `--delete` option in the `push` command:

```bash
git push origin --delete branch_to_delete
```

## Merging changes

When combining the changes of one branch into another (lets say we want to update branch `A` with the changes made on branch `B`) we first have to commit the changes on branch `B`:

```bash
git checkout B
git add .
git commit -m "ready to go"
```

Then switch to branch `A` and use the `merge` command specifying the branch you want to merge into the current one:

```bash
git checkout A
git merge -m "merge branch B" B
git push # No need to commit or add
```