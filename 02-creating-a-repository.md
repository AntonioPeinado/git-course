# Creating a repository

We can create a repository in two ways, starting from a project which is not in a repository or cloning an existing one.

## Starting from a project

First thing we have to do is creating an empty git repository and then openning the folder that contains our project inside a terminal:

```bash
cd path/to/my/awesome/project
```

Then crete an empty repository in that directory:

```bash
git init # Creates .git folder where your project config is stored
```

`Add` some files to version control tracking and `commit` them to the repository with a message:

```bash
git add . # Add current folder documents and subfolders to the stagging area
git commit -m "initial commit" # Send those files to the local repository
```

Now configure a `destination` for that project in your Git server:

```bash
git remote add origin git@me.awesome.repo # Link origin (alias to this project) to your Git repository
```

And `push` your changes to it:

```bash
git push origin master # Upload the files from your git repository to the master branch in your remote repository
```

## Starting from a repository

For getting a previously created git repository just `clone` it (note that it will create a folder named as the repository):

```bash
git clone git@my.awesome.repo
```

## Sources

* [Getting a git repository](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)
