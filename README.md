<p align="center">
  <img alt="Git Logo" title="Git Logo" src="logo.png" />
</p>

<br />
<br />

<h3 align="center">Notes taken during the Udacity <a href="https://classroom.udacity.com/courses/ud123" target="_blank">Version Control with Git</a> course</h3>

<br />

## :pushpin: Global Configs

Sets up Git with your name

```bash
$ git config --global user.name "Your-Full-Name"
```

Sets up Git with your email

```bash
$ git config --global user.email "your-email-address"
```

Makes sure that Git output is colored

```bash
$ git config --global color.ui auto
```

Displays the original state in a conflict

```bash
$ git config --global merge.conflictstyle diff3
```

Sets up Git with your default text editor

```bash
$ git config --global core.editor "your-editor's-config-went-here"
```

Lists all your configs

```bash
$ git config --list
```

VSCode Setup:

```bash
  $ git config --global core.editor "code --wait"
```

Sublime Text Setup

```bash
  $ git config --global core.editor "'C:/Program Files/Sublime Text 2/sublime_text.exe' -n -w"
```

Atom Editor Setup

```bash
  $ git config --global core.editor "atom --wait"
```

- Note: if closing a file that Git opened doesn't complete the given command, then you need to close the entire editor

## :pushpin: Git uses Less (terminal pager program)

- to scroll **down**, press

  - `j` or `↓` to move _down_ one line at a time
  - `d` to move by half page screen
  - `f` to move by a whole page screen

- to scroll **up**, press

  - `k` or `↑` to move _up_ one line at a time
  - `u` to move by half page screen
  - `b` to move by a whole page screen

- press `q` to **quit** out of the log (returns to the regular command prompt)

## :pushpin: The .gitignore file

- Add this file to your project in the same directory that the hidden .git directory is located

- List the names of files that you want Git to ignore (not track) and it will ignore them

- [Globbing](https://git-scm.com/docs/gitignore) lets you use special characters to match patterns/characters

---

## :pushpin: git init

Create brand new repository on your computer

## :pushpin: git clone

Copy existing repositories from somewhere else to your local computer

```bash
$ git clone "url" "new-dir-name"

$ git clone "path-to-repository-to-clone" "new-dir-name"
```

## :pushpin: git status

- Check the status of a repository

- Always run this command when returning to a project after a period of time

## :pushpin: git log

Displays information about the existing commits. By _default_, displays:

- the SHA
- the author
- the date
- and the message

```bash
$ git log --oneline
```

- lists one commit per line
- shows the first 7 characteres of the commit's SHA
- shows the commit's message

```bash
$ git log --stat
```

- displays the file(s) that have been modified
- displays the number of lines that have been added/removed
- displays a summary line with the total number of modified files and lines that have been added/removed

```bash
$ git log --patch
```

- displays the files that have been modified
- displays the location of the lines that have been added/removed
- displays the actual changes that have been made

```bash
$ git log -p --stat
```

- combines both of them (-p is the same of --patch)

```bash
$ git log -p -w
```

- ignores whitespace changes

```bash
$ git log -p "reference-to-commit"
```

- starts at the specified commit, no need to scroll through the entire log

```bash
$ git log --oneline --graph --all
```

- shows the branching of all the branches in the repository

## :pushpin: git show

Displays information about the given commit. By _default_:

- the commit
- the author
- the date
- the commit message
- the patch information

```bash
$ git show "reference-to-commit"
```

- by default it is the same as the `$ git log -p` command

```bash
$ git show "reference-to-commit" --stat -p -w
```

- it can be combined with other tags

## :pushpin: git add

Add files from the working directory to the staging index

```bash
$ git add "file1" "file2" ...
```

- add a file to the staging index

```bash
$ git rm --cached "file"
```

- unstage a file to the working directory

```bash
$ git add .
```

- add all files and directories (including all nested files and directories)

## :pushpin: git commit

Take files from the staging index and save them in the repository

```bash
$ git commit
```

- edit the commit message and body on the default text editor

```bash
$ git commit -m "message"
```

- pass the message directly on the command line

- Try to complete the phrase "This commit will {...}" and then, use the {...} as a commit message

- Avoid using the word "and", your commit message is probably doing too many changes. Break the changes into separate commits

- **What**, not why, how or where

- The first line of a commit message is the message itself. Leave a blank line and then type the body or explanation including details (e.g. URL links)

## :pushpin: git diff

Displays the difference between two versions of a file (its output is the same of `$ git log -p`). By _default_:

- the files that have been modified
- the location of the lines that have been added/removed
- the actual changes that have been made

## :pushpin: git tag

Add tags to specific commits

```bash
$ git tag -a v1.0
```

- create an annotated tag to the most recent commit

```bash
$ git tag -a v1.0 "reference-to-commit"
```

- create an annotated tag to the given commit

```bash
$ git tag -d "tag-name"
```

- delete the given tag, it is the same as --delete

- _it is recommended to always use annotated tags_ to include extra information such as the person who made the tag, the date the tag was made and a message for the tag

- git log shows the tag associated to the commit at the end of the first line

## :pushpin: git branch

Allows multiple lines of development. It can be used to:

- list all branch names in the repository
- create new branches
- delete branches

```bash
$ git branch "branch-name"
```

- create a new branch with the given name

```bash
$ git branch "branch-name" "start-point or SHA"
```

- create a new branch that points to the specified commit (e.g. fix a bug created in a old commit)

```bash
$ git branch -d "branch-name"
```

- delete the specified branch (after adding commits to this branch, Git won't let you delete it before merging, _even_ if switch to the master branch)

- To force deletion, you need to use the `-D` flag

## :pushpin: git checkout

Switch between different branches and tags.

```bash
$ git checkout "branch-name"
```

- switch to the specified branch

- _`git log` shows the "HEAD" indicator pointing to the current branch, any commits made right now will be added to the current branch_

```bash
$ git checkout -b "branch-name" "start-point or SHA"
```

- the `-b` tag allow us to create and switch to a new branch at the same time and in the specified location

```bash
$ git checkout "file-name"
```

- it can be used to discard changes in the working directory

## :pushpin: git merge

Combines changes on different branches

```bash
$ git merge "name-of-branch-to-merge-in"
```

```bash
$ git reset --hard HEAD^ [if you merge on the wrong branch]
```

- When a merge happens, Git will:

  - look at the branches that it's going to merge
  - look back along the branch's history to find a single commit -that both branches have in their commit history
  - combine the lines of code that were changed on the separate branches together
  - make a commit to record the merge
  - HEAD is pointing to the current branch, and it will move foward after the new commit

- When we merge, we're merging some other branch into the current (checked-out) branch

- Fast-forward merge: the branch being merged in must be ahead of the checked out branch. The checked out branch's pointer will just be moved forward to point to the same commit as the other branch.

- Regular type of merge: two divergent branches are combined and a merge commit is created

## :pushpin: merge conflicts

A merge conflict will happen when the **_exact_** same line(s) are changed in separate branches

- E.g.: you are merging the branch heading-update and master. The HEAD points to master, and a merge conflict occur. Then, you need to choose what you are going to delete and keep, a window in your _default text editor_ will open.

  `<<<<<< HEAD`

  Current branch content

  `|||||||||`

  Merged common ancestors

  `========`

  Other branch content

  `>>>>>> heading-update`

- After the conflict is resolved, you just need to add the conflicting files to the staging index and commit them like a regular merging.

- Remember to delete the merge conflict indicators `<<>> ||`.

- If you forgot to delete them, Git will commit the file anyway, it's up to you to decide :)

Resume:

- locate and remove all lines with merge conflict indicators
- determine what to keep
- save the file(s)
- stage the file(s)
- make a commit

## :pushpin: git commit --amend

Alter the most-recent commit

```bash
$ git commit --amend
```

- If there aren't any uncommitted changes in the repository, this command will let you provide a new commit message in your default text editor.

Alternatively, it will let you include files (or changes to files) you might've forgotten to include:

- edit the file(s)
- save the file(s)
- stage the file(s)
- and run git commit --amend

```bash
$ git commit --amend -m "message"
```

- pass the new message directly on the command line

## :pushpin: relative commit references

Ancestry References:

- `^` - indicates the parent commit
- `~` - indicates the _first_ parent commit

E.g.:

- The parent commit – the following indicate the parent commit of the current commit

  - HEAD^
  - HEAD~
  - HEAD~1

- The grandparent commit – the following indicate the grandparent commit of the current commit

  - HEAD^^
  - HEAD~2

- The great-grandparent commit – the following indicate the great-grandparent commit of the current commit
  - HEAD^^^
  - HEAD~3

With a merge commit, the `^` reference is used to indicate the first parent of the commit (the branch you were on when you ran git merge) while `^2` indicates the second parent (the branch that was merged in)

E.g.:

-HEAD is pointing to the top commit in branch master.

-HEAD~4^2 points down _**4 commits**_ + _**one commit in second parent**_ = _**5 commits**_ (the last commit isn't in the master branch, it is in the second branch)

## :pushpin: git revert

Reverses given commit

```bash
$ git revert "reference-to-commit"
```

- Git takes the changes that were made in a commit and does the exact opposite of them. Then, creates a new commit to record the change

## :pushpin: git reset

- Note: before doing any resetting, create a backup branch on the most-recent commit so that you can get back to the commits if you make a mistake

Erases, stages previously committed changes, or unstages previously committed changes according to the flag that's used:

- --mixed (it is the _**default tag**_, moves HEAD and branch to the referenced commit and all commits midway to the _working directory_)
- --soft (moves HEAD and branch to the referenced commit and all commits midway to the _staging index_)
- --hard (moves HEAD and branch to the referenced commit and all commits midway to the _**trash**_)

```bash
$ git reset "reference-to-commit"
```

```bash
$ git reset --mixed "reference-to-commit"
```

```bash
$ git reset --soft "reference-to-commit"
```

```bash
$ git reset --hard "reference-to-commit"
```

- Reverting _**creates a new commit**_ that reverts or undos a previous commit. Resetting, on the other hand, _**erases**_ commits

- This is one of the few commands that lets you erase commits from the repository. If a commit is no longer in the repository, then its content is _**gone**_

- Git does keep track of everything for about 30 days before it completely erases anything. To access this content, you'll need to use the `git reflog` command

It can also be used to:

- move the HEAD and current branch pointer to the referenced commit
- move committed changes to the staging index
- unstage committed changes (same as `git rm --cached`)

If you created the `backup` branch prior to resetting anything, then you can easily get back to having the `master` branch point to the same commit as the `backup` branch. You'll just need to:

1. remove the uncommitted changes from the working directory
2. merge backup into master (which will cause a Fast-forward merge and move master up to the same point as backup)

```bash
$ git checkout -- "file-name"

$ git merge backup
```
