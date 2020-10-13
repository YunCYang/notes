# Git

## Status and log and others
`git init` - initialize git, only need once at the start for every project
`git status` - see the current status for the files
`git log` - see the log for the commits
	`--oneline` - shows all the commits, each in one line, cleaner representation
	`--graph` - shows graph of the branches
`git show [unique hash for commit]` - shows the changes made in the commit

## Commit
Comments in commits are usually present tense, so it's more readble
Commit when hit a milestone

### Complicated message
`git commit` without -m will open an editor, allowing you to put in more message when it is needed
In the editor, put in a simple message at the first line, separate a line and then put the rest of the message. The first line will show normally on GitHub

## Reset
### Hard reset
`git reset --hard [unique hash for commit]`
Reset everything to the code looked at the moment of the provided commit, erases any changes

Be careful about hard resetting when you already pushed and shared on GitHub

### Soft reset
`git reset --soft [unique hash for commit]`
Reset to the commit, but any changes you made will still be reflected, only get rid of the commit

## Amend the commit
After `git add` the file, use `git commit --amend` to enter vim and amend the commit

## Branch
### Branch name
Put the type of work in the front, ex: "feature-report", "bug-53", "issue-[issue number on GitHub]", "fix-whatever"

### Merge
`git merge [branch name]`

create new branch -> work -> checkout to master branch -> git merge -> delete merged branch

### Conflict
`git diff [file name]` - see the branch difference of the file

## Alias
### Create alias
`git config --global alias.s status` -> creates an alias, or shortcut `s` for the command `git status`, instead of typing `git status`, you can just type `git s`

The aliases are stored in the gitconfig file

### Delete alaiis
`git config --global --unset alias.s`

### Even shorter alias
Can add alias to bashrc file to create shorter alias
ex. `alias ga="git add"`
	`alias gaa="git add .`

## Stash
`git stash` - temporary saves working directory
`git stash list` - shows save points, each with unique id
`git stash pop` or `git stash apply stash@{2}` - access the stored away work
	apply keeps the save point on the list, pop deletes it, stash@{2} or identifier is optional. Default is the most recent one
`git stash drop stash@{3}` - just delete the stashed object, identifier is optional

git stash can also apply to a different branch
`git stash [branch-name]`

## Origin
When pushing an existing repository to GitHub
`git remote add origin https:something.git` 
`git push -u origin master` - -u sets upstream

## Rebase
Similar to commit and merge, takes the unique commits from the current and place them on top of the target branch. Much cleaner commit history when rebasing. Still needs to do git merge on the target branch
(Go to the current branch you are working on) -> `git rebase [target branch name]` -> git merge

### Interactive rebasing
`git rebase -i [target branch name]` - useful to alter or combine commit history

## Reflog
`git reflog` - shows every event in git that took place, good when reverting back history