# Git Repository Basics

## Problem Statement
`Git` is a a widely-used version control system. It is a program used to track
changes in a set of files. While building a project on our local machine, we
may want to be able to keep a running log of our changes as well as store these
changes somewhere accessible, regardless of what may happen to the physical files
on our computer. This is where `git` can save the day! Sounds useful right? So,
how do we set this up?

## Objectives

1. Use `git` to enhance the way we work
2. State how to manage files in a directory with `git init`
3. Use `git status` to check the status of our repository
4. Recognize how to keep track of files with `git add`
5. Create a commit with `git commit` and apply a commit message

## Use `git` to Enhance the Way We Work

Now that we've established the usefulness of `git`, we want to start using it.
`Git` will allow us to keep track of all changes to our files. It operates
on a per-directory setup. We'll need to create a new directory and then change into
that directory. Go to our terminal and type the following:

**REMEMBER** Don't type the `$`, that's the universal symbol for a command prompt.
It's how technical documentation says "Here's a thing for the shell to interpret."

```
~ $ mkdir my-git-project
```

This command creates new directory. Then:

```
~ $ cd my-git-project
```

This command moves into the newly created directory.

## State How to Manage Files in a Directory With `git init`

Now that we're in the directory where we want `git` to watch for changes (adding,
removing, and editing files) let's set up this directory by _initializing_ it.
In our terminal type `git init`. It should look like the following:

```
my-git-project $ git init
Initialized empty Git repository in /Users/avi/my-git-project/.git/
```

After entering `git init`, the output in our terminal reads `Initialized empty Git repository in /our/path/here/my-git-project/.git/`. `Git` is letting we know that it created
a new repository within the hidden `.git` folder in `my-git-project`. This hidden
directory, `.git`, is what `git` uses to keep track of our log of changes. So, don't
go in there and start randomly deleting things!

## Use `git status` to Check the Status of Our Repository 

Now we have `git` watching this directory, let's see what `git` can tell us about
the directory with `git status`. Without any files added yet, we'll see:

```
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

Let's create a `README.md` that describes the project. Make our new file by
typing `touch README.md` from within the `my-git-project` directory. We won't
see any output after `touch`, but we will see a new file has been created if
we type `ls`, which gives a list of all the files in the directory.

```
my-git-project $ touch README.md
my-git-project $ ls
README.md
```

With at least 1 new project file we can enable `git` to start tracking changes.
Type `git status`. `Git` will show us what our current repository looks like
and what changes it sees.

```
my-git-project $ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	README.md

nothing added to commit but untracked files present (use `git add` to track)
```

As expected, `git` confirms that it's not watching or tracking anything in this
directory. Let's change that!

Whenever we want to check the status of our Git repository –– which
we do quite often –– type `git status`. 

## Recognize How to Keep Track of Files with `git add`

Currently the file in our repository is not being tracked by `git` just yet.
We have to tell `git` about all the files we want it to keep track
of and consider as part of our project. We can do this by adding the files
to our `git` repository with `git add <filename or path>`. To add our new
`README.md` to the repository and check the status, we would type:

```
my-git-project $ git add README.md
my-git-project $ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   README.md
```

We can now see that `git` is ready to keep track of `README.md` and recognizes
that the file is new to this repository. However, while we've informed `git` that
there is a new file, we still haven't informed `git` that this new file is
considered a change to our repository. We create changes in our repository
by making "snapshots" or "commits."

**To capture all changes in a directory –– the standard way to do it –– type `git add .`, where the `.` refers to the entire current directory.**

## Create a Commit With `git commit` and Apply a Commit Message

Git knows that the state of `README.md` is "to be recorded as part of this commit"
because our last use of `git status` listed `README.md` under `Changes to be committed:`.
That's why a _commit_ is composed of two steps: adding the files in the snapshot
(_commit_) and then doing the commit with your message.

To make our first commit, type: `git commit -m "Initial commit"`. This tells
`git` that our commit message, represented by the `-m` flag, is `"Initial commit"`.

```
my-git-project $ git commit -m "Initial commit"
[master (root-commit) e55477d] Initial commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
```

We can see that `git` has created a new version of our code, represented by the
_SHA_ `e55477d` (_SHA_s are the identification system that `git` uses to keep track
of versions). The commit changed 1 file. Now, if we type `git status` ask to
see the status of our project, with no other changes to any files, we'll see
that it is at a "clean state", and there is nothing to commit and no new changes.

```
my-git-project $ git status
On branch master
nothing to commit, working directory clean
```
If we make another change, for example, to README.md, we can add another commit 
with this new set of changes with `git commit -am`:

```
my-git-project $ git commit -am "Updated README.md"
[master (root-commit) e55477d] Updated README.md
 1 file changed, 4 insertions(+), 0 deletions(2)
```

**A faster way to capture all outstanding changes for files that are _already being tracked_ in a commit is to use
`git commit -am "Our commit message"`, where the `a` refers to adding 'all changes'
and `m` assigns a commit message of `"Our commit message"`.**

Commits are amazingly powerful in `git`. With a commit you can move your project
back to a past commit and throw away bad ideas. You can tell `git` to create a new
"parallel universe" based off of a past commit and you can start working in that
universe and decide later to keep that work or throw it away. We won't cover
these features in this lesson, but they exist, and are very useful.

## Conclusion

To make a new `git` repository out of a directory –– which we'll only have to
do once per project –– use `git init`. Be careful about making an entire directory,
like our home directory or our desktop, into a `git` repository accidentally. Make
sure you only type `git init` within the directory you want `git` to track. Whenever
you make a change to a file or create a new file, you can check the status of these
changes with with `git status`. When you're ready to keep track of changes, you can
add them individually with the `git add <filename or path>` command, or collectively
with the `git add .` command. Once your changes have been added, use `git commit -m`

If we've followed these instructions, our `my-git-project` directory is now a `git`
repository. We can retain the directory as a sandbox for Git experimentation, or
delete or ignore it.

<p class='util--hide'>View <a href='https://learn.co/lessons/git-basics-readme'>Git Repository Basics</a> on Learn.co and start learning to code for free.</p>
