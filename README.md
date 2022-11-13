# Demo

Demo repo created for the [Git and GitHub for Beginners - Crash Course](https://youtu.be/RGOj5yH7evk) by [Gwendolyn Faraday](https://gist.github.com/gwenf).

Contents:
- [My Notes](#my-notes)
  - [Using the CLI](#using-the-CLI)
  - [Git Commands](#git-commands)
  - [Creating repositories locally](#Creating-repositories-locally)
  - [Workflows](#Workflows)
    - [GitHub Workflow](#GitHub-Workflow)
    - [Local Git Workflow](#Local-Git-Workflow)
  - [Git Branching](#Git-Branching)

## My Notes

Below are my notes from this tutorial.

### Using the CLI

CLI stands for "Command Line Interface". On a Apple machine, the default CLI is Terminal. This lets you access your directories (folders) and input Git commands directly without having to use a software application such as GitHub Desktop.

- `cd` = change directory
  - `..` will return your to the parent directory above your current directory. For example, let's say you're in `Documents/GitHub/portfolio` but you want to move to another directory in the `GitHub` directory. You can type `../to-do-list-app` into the CLI and it will move you to the directory `Documents/GitHub/to-do-list-app`. Without this you would need to type `cd` followed by the entire directory route (i.e., `cd Documents/GitHub/to-do-list-app`).
- `ls -al` will list all the files in the current directory

### Git Commands

- Tracking files: `git add .` will track all files in the repository whereas `git add index.html` tells git to **only** track that one file.
- Commit: `git commit -m` will tell git to save any changes to files in the directory **BUT** needs to be followed by a message (`-m`) in order to commit the files. The message could be one character and meaningless but it's best practice to have a message with the *what* and *why* of the changes your making.
  - all messages are contained within quotes `""`
  - a second `-m` can be added for the description (e.g., `git commit -m "Added index.html -m "description"`)
  - If a file has already been committed and then is changed later, you can use `git commit -am ""` as as shortcut for `git add` and `git commit`. This shortcut combines both statements and lets you add and commit at the same time. **NOTE:** This will not work for *newly* created files.
- Push: `git push` will push the files to a remote repository where the project is hosted. We follow the command with `origin` (the location of our git repo) and `main`(the branch we want to push to): `git push origin main`
  - **Shortcut**: You can set the *upstream* by typing `git push -u origin main` on your first push and in the future you can simply type `git push` when you want to push to your remote repo.
- Initializing a repository: `git init` will initialize the git repository in the current directory
- Remote: `git remote` will find remote repository and add theme locally
  - `git remote -v` will tell you what repositories are connected to your current directory
- Branching: `git branch` will list the current branches in the directory. The branch name with an asterisk `*` beside is the branch you're currently on. So `*master` means you're currently on the `master` branch.
  - `git checkout` will allow you to switch branches (e.g., `git checkout feature` will move you to the `feature` branch)
    - To create a new branch type `git checkout -b` followed by the name of your branch (e.g., `git checkout -b bugFix`). If you're working with other people, you want to make your branch name as descriptive as possible such as using `/` or `-` to include the ticket number or issue number. Best practice is to follow the convention of your team.
  - `git branch -d` followed by the branch name will delete the branch
- Merging: `git merge` will merge branches (i.e., `git merge BRANCH-NAME` will merge the `BRANCH-NAME` into the `main` or `master` branch)
  - `git diff` will compare two versions of the code and show you the lines that have changed.
  - Common practice: You can just use `git merge` to merge the branches, but it's more common to `push` the changes in the branch then make a `pull` request,
- A **pull request** (PR) is a request to have your code *pulled* into another branch.
  - Once the PR is accepted and merged into the main/master, generally you delete the branch where the changes were made. If more changes are needed afterward, you'll repeat the process (i.e., make a branch, commit changes, make a PR, merge)
- Undoing: `git reset` (or `git reset FILE-NAME`) will undo any stages
  - To undo a `commit` you can use `git reset HEAD~1` to undo the most recent commit and go back to the previous commit
  - To go back to a previous commit, you need to view the log, find the Git hash code for the commit, then use `git reset` followed by the Git hash code to go back to that specific commit
    - Adding `--hard` after `git reset` will remove all changes/commits
- Log: `git log` will display a log of all commit changes

#### Creating repositories locally

If you create a repository locally, here are the steps to link to a remote repository on GitHub:

1. Create an empty repository with the same name on GitHub.
2. Copy the SSH for the newly created repository.
3. In the CLI, type `git remote add origin git@github.com:USER/REPO-NAME.git` to connect the remote repo to your local repo
4. You can use `git remote -v` to see which remote repositories are connected
5. Now you can use other git commands (e.g., `push`) to keep your repositories in sync.

### Workflows

The basic workflow will change depending on if you're using the online GitHub interface or the CLI interface to run Git locally on your machine. Below are simple outlines detailing each workflow.

#### GitHub Workflow

Write code -> commit changes -> make a pull request (only if you don't have access right)

#### Local Git Workflow

Write code -> stage changes (`git add`) -> commit changes (`git commit`) -> push changes (`git push`) -> make a pull request (only if you don't have access rights)

### Git Branching

- Each individual branch has no one of knowing what commits were made on other branches
  - The changes you make (commit) are only seen on the branch they're committed to. For example, if you have the branches `main` and `feature` but only commit changes to the `feature` branch, they will not be seen on the `main` branch.
- Branching allows you to add new features, fix bugs, etc. in a "sandbox" area *without* "breaking" the code in your master branch
  - Once you have the new features (or changes) complete and ready, then you can merge them back into the main/master branch
  - This is really useful when you have multiple people working within the same repository at once
