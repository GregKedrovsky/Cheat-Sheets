# Git

**Reference Docs:** [Details](https://git-scm.com/docs) & [Visual](https://ndpsoftware.com/git-cheatsheet.html)

**Contents:**
- Concepts: [`GitHub`](#github), [`projects`](#git-projects), [`workflows`](#git-workflow), [`pages`](#pages), [`.gitignore`](#.gitignore)
- Configuration: [`username & email`](#git-username--email)
- Commands: [`common`](#common-commands), [`stash`](#stash), [`log`](#log), [`amend`](#amend-flag), [`alias`](#alias-commands), [`branching`](#branching), [`cloning`](#cloning)

## GitHub

https://docs.github.com/en

You can use GitHub to work on any file-based project, including coding projects, writing documentation, etc.
- It is simply a site and service provided to store and share code (file-based information).

Should be familiar with `clone`, `fetch`, `push`, `pull`, etc. 

**NOTE:** GitHub has changed the naming convention of the main branch from `master` to `main`.

## Git Projects

A Git project has three parts:
|Parts                | Description                                                               |
|---------------------|---------------------------------------------------------------------------|
|1. Working Directory | where files are created, edited, deleted, and organized                   |
|2. Staging Area      | where changes that are made to the working directory are listed           |
|3. Repository        | where Git permanently stores changes as different versions of the project |

## Git Workflow

### Individual Projects:
1. Edit files in the working directory
2. Add files to the staging area
3. Save changes to a Git repository

### Collaborative Projects, Single Repo:
1. Create a branch (copies the project for you to work on)
2. Commit changes (after coding whatever, commit and push to GitHub; goes to your branch)
3. Create a pull request (this is a discussion page for code changes between one branch and another)
4. Review pull request (collaborators look it over and comment on what should be changed and why)
5. Merge and delete branch (after a successful merge, delete your branch; keep things tidy)

### Collaborative Projects, Cloned:
1. Fetch and merge changes from the remote.
2. Create a branch to work on a new project feature
3. Develop the feature on your branch and commit your work
4. Fetch and merge from the remote again (in case new commits were made while you were working)
5. Push your branch up to the remote for review

Steps 1 and 4 are a safeguard against merge conflicts.

## Pages

GitHub pages require just a little bit of minor tweaking to get them to work. Also, it takes a few minutes for the page to get spun up and spit out (be patient).
- [GitHub Quickstart](https://docs.github.com/en/pages/quickstart)
- [W3Schools How-To](https://www.w3schools.com/git/git_github_pages.asp)
- [InMotion Hosting Pages How-To](https://www.inmotionhosting.com/support/website/git/host-site-github-pages/)
- [InMotion Hosting & Custom Domains](https://www.inmotionhosting.com/support/domain-names/how-to-use-a-custom-domain-with-github-pages/)

## .gitignore
The .gitignore file is a plain text file that tells Git to intentionally ignore changes in certain files.
- This avoids cluttering up your repo with .bak files, etc. when you issue a `git add .` command.
- Each line in .gitignore corresponds to a file, directory, or pattern you want to ignore when staging.
- Pattern matching is accepted [man page](https://git-scm.com/docs/gitignore)

## Git Username & Email

### Username

Git uses a username to associate commits with an identity. The Git username is NOT the same as your GitHub username. Changing your username does NOT change previous commits.

Set git username globally (for **every** repo on your machine)
```
git config --global user.name "Greg Kedrovsky"  # set a new username
git config --global user.name                   # confirm you set the name correctly
```

Set git username for a single repo only: 
```
cd /dir/for/local/repo                 # change to the local repo working directory
git config user.name "Greg Kedrovsky"  # set the name for this local repo only
git config user.name                   # confirm you set the name correctly
```

### Email

GitHub uses your commit email address to associate commits with your account on GitHub.com. 

Setting your commit email address in Git: 
```
git config --global user.email "gregkedro@gmail.com"  # set an email address
git config --global user.email                        # confirm the email address is set correctly
```

## Common Commands

Git commands to help keep track of changes made to a project:
```
git init                       # creates a new Git repository
git status                     # inspects the contents of the working directory and staging area
git add [filename | wildcard]  # adds files from the working directory to the staging area
git diff [filename]            # shows the difference between the working directory and the staging area
git commit -m "Present Tense"  # permanently stores file changes from the staging area in the repository
git log                        # shows a list of all previous commits on current branch checked out

git show HEAD                  # show the HEAD (usually the last/top) commit in the log
git checkout HEAD [filename]   # restore [filename] to last (HEAD) commit (undo last changes committed)
                               # basically it discards the changes in your working directory
git reset HEAD [filename | . ] # removes the filename from the staging area
 
git reset [commit_SHA]         # Restores project to the commit indicated by the first 7 chars of its SHA
```

## Stash

A place to "stash" your local work temporarily in order to update a previous commit and then after that retrieve your work you "stashed" away.

Commands:
```
git stash      # stores current work temporarily in a hidden local directory
git stash pop  # retrieves the code you were working on and "stashed" to do something else
```

## Log

Commands: 
```
git log                                     # view the commit history of the branch you currently have checked out.
git log --oneline                           # shows list of commits in one-line format
git log -S "keyword"                        # displays a list of commits that contain the keyword in the message
git log --oneline --graph --graph           # display repo history (branches & commits) visually
git log --graph --decorate --oneline --all  # fuller picture of commits and progress
```

## Amend Flag
 
Allows you to correct mistakes and edit commits easily instead of creating a completely new commit.

**Workflow:**
1. You makes changes and then do a standard commit
2. You find a couple simple mistakes and don't want to make an entire new commit
3. So, just fix your mistakes, then...
4. command:      

```
git commit --amend            # updates your previous commit (replaces the entire previous commit)
git commit --amend --no-edit  # keeps the same commit message (no prompt for a new one)
```

## Alias Commands

Aliases let you alias a lengthy git command you need frequently.

Examples: 
```
git config --global alias.co "checkout"
git config --global alias.br "branch"
git config --global alias.glop "log --pretty=format:"%h %s" --graph"
```

Once the aliases are configured, next time you want to check out to another branch you could type the command:
```
git co example_branch
```

Instead of:
```
git checkout example_branch
``` 

## Branching

```
git branch                  # list branch; the asterisk (*) shows you what branch you're on
git branch [branch_name]    # creates a new branch
git checkout [branch_name]  # switch to the new branch
git merge [branch_name]     # include the changes made to the new branch in the main branch
                            # execute from within the receiver branch
git branch -d [branch_name] # deletes a branch after you're finished with it
```

## Cloning

**NOTE:* When you clone a repo, the remote address is given the name `origin` (because it is the remote repository of origin for your clone).

```
git clone [remote_location] [clone_name]  # create your own replica of a repo
git remote -v                       # display a list of a project's remotes
git fetch                           # fetches new commits from the remote, but does not merge them
git merge origin/master             # merge your clone master branch with the origin/master branch you fetched
git push origin [your_branch_name]  # push (copy) your branch up to the remote/origin repo
                                    # creates a branch on the remote/origin for review & merging into main
```                                    

Specific example: a git repo can be cloned into any root directory of your choice:

```
git clone https://github.com/user/repo.git myDir  # repo.git will be cloned into the myDir directory
```

