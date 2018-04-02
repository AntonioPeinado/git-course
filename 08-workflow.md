# Workflow

Once you are familiarized with Git, it is time to choose or elaborate a workflow that best suits your team needs, here goes a proposal:

## Branches

### Feature branches

When working in a software project, the first thing that should be done is to identify `which task` should be completed after a set deadline.

After those task are identified they can be assigned to or taken by different team members, to minimize conflicts it is important to do so with care and avoid that multiple members are working simultaneously on the same pieces of code.

For that you can use `feature branches`. A feature brach will represent a specific task, and ideally only one developer will be working on it. For example, if the task is implementing a menu, we would create a feature branch menu, called `feature/menu`. Note that the name is just a convention,
you could have called it `f-menu`, the important thing here is that you and your team share an strategy for naming the branches.

The developer will be making changes and commiting them to the feature branch and once it is done and tested by the developer in charge of that task, that branch will be merged into `develop`, ideally with a pull request approved by the team.

If using pull requests, you can and should open them when creating the branch, so the reviewers can see the changes progresively and not at once at the end of the feature.

Note that this branch should be updated from `develop` frequently to avoid future conflicts.

### Develop

This branch contains the project codebase and the code that is being done in the current delivery periods but is not ready for production yet, therefore it is `unstable`.

Here all features should be integrated and it must be verified that they work in conjunction with both, the old and the new code. If they don't, a new feature should be created to fix the bugs.

Once all features are finished and merged, changes should be pushed to a `release candidate`.

### Release candidate

Release candidate branches are used to describe a set of features that are going to be delivered soon. You can have as many `release candidate` branches as you need, differenciating them adding a `version or sprint` number to the name. For example `R.C. 1.0.0` or `R.C. Sprint 23`.

Here a `Quality assurance` team, (which can be the same development one) must berify that the software that is going to be delivered complies with the `acceptance tests` and the `functional and non-functional requisites` that were specified for the delivery.

Once verified that the release is correct with respect to its specification, it can go into production by mergin it into `master`.

In order to be able to come back to a previous release in case of disaster, it is important to keep this branches in the remote repository for a not too short period of time.

### Master

`Master` branch contains the code that is running in `production`, therefore this branch must be `stable`.

Write acces should be restricted and merges should be done using pull requests only when it has been verified that the new code works correctly.

### Hotfix

`Hotfixes` arise when we have to respond immediately to make a change on a `production` version.

We can create a branch from master, effectuate the change and then merge it back. A naming convention could be `hf/nothing works`.

## Version numbers

The famous three numbers that usually identify software versions are not arbitrary, instead follow a simple set of rules called `Semantic Version`, you can find more about `SemVer` [here](https://semver.org/)

Given a version number of the form `MAJOR.MINOR.PATCH`:

* MAJOR: version where incompatible changes are made.
* MINOR: version where changes are backwards-compatible.
* PATCH: version where backwards-compatible bug fixes are made.

## Commits

In order to maintain good information about the history of a repository,being able to quickly detect and identify changes, and to minimize conflicts among other reasons, it is imporant that commits follow this two rules:

* Commits should be `small` and `frequent`.
* The message describing them must be `informative` and `short`.

## Pull request

Some good points to take into account and not make your reviewers work harder are:

* Open them as soon as you start with your new task.
* Commit often.
* Read the comments and discuss about them with an opened mind.
* Ideally, all team members should be reviewing everything.
* Pull request are a tool for learning, not critizicing.