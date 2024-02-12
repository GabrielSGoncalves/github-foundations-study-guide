# Github Foundations Certification Study Guide
In this repository, we are going to review important Git and Github concepts and commands in order to prepare for the Github Foundations Certification exam. The content was extracted from [Linkedin Prepare for the GitHub Foundations Certification Course](https://www.linkedin.com/learning/paths/prepare-for-the-github-foundations-certification).

## Configuring your Git locally
First thing to do I to define your username and email.
```bash
git config --global user.name "YourUserName"
git config --global user.email "youremail@email.com"
```
Next, it's a convetion to use `main` as the name of your production repository branch, replacing the previous `master`.
```bash
git config --global init.defaultBranch main
```
## Initializing a Git Repository
To start a Git repository you simply use the `init` command.
```bash
git init
```
After this command you can find a `.git` folder inside your reopository with all the tracking files used by Git.

## Staging files and pushing changes
Whenever you create, change or delete a file you can track it by commiting it to your branch history.
```bash
git add --all
git add --A
git add .
```
By adding the file(s) you can then write a checkout message for it.
```bash
git commit -m "Adding README file to repo"
```
Finally, whenever you wan't to push the files to a remote repository like Github you can define it with the following command.
```bash
git remote add origin https://github.com/YourUserName/your_repo_name
git push -u origin main
```
Make sure you create your Github repository before trying to push the changes to it.

## Understanding Git environments
One important command to use to have a better understanding of the status of your Git repository ```git log```. This gives the view of your current branch, it's relation to remote repository and commits recorded.<br>
Another command is `git status`, which describe the status of the files in your current working branch.
Another powerful command is `restore`. It can restore the state of tracked files to previous states. For example, `git restore --staged .` would unstage all files that were added to staging, and `git restore .` would remove all the changes made to tracked files.
