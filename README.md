# Github Foundations Certification Study Guide
In this repository, we are going to review important Git and Github concepts and commands in order to prepare for the Github Foundations Certification exam. The content was extracted from [Linkedin Prepare for the GitHub Foundations Certification Course](https://www.linkedin.com/learning/paths/prepare-for-the-github-foundations-certification).

## Using GitHub Codespaces to explore this repository
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/GabrielSGoncalves/github_foundations_study_guide)

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
One important command to use to have a better understanding of the status of your Git repository `git log`. For a simpler view, use `git log --oneline`. This gives the view of your current branch, it's relation to remote repository and commits recorded.<br>
Another command is `git status`, which describe the status of the files in your current working branch.
Another powerful command is `restore`. It can restore the state of tracked files to previous states. For example, `git restore --staged .` would unstage all files that were added to staging, and `git restore .` would remove all the changes made to tracked files. In case you deleted a tracked file, if you run `restore` command, it would appear back in your repository folder.

## Ignoring files
Software projects usually need settings files that are not supposed to be versioned, as it may carry sensitive data. To prevent Git to track these types of files you can create `.gitignore` file inside your repository.

## Deleting and renaming files
Whenever you delete a tracked file from your Git repository, it's marked for deletion, an you need to add and commit it, in order to formalize the deletion. You can also use the `git rm <file>` to delete and stage a file in one step. <br>
In case of renaming, you can use `git mv <file>` in order to avoid having to track a deletion and creation of files.

## Differences
Another interesting command for checking the differences made on your track files is `git diff`, as it displays changes made to each line on altered files. You can also check a specific commit from your `git log --oneline` and copy the id to inspect the changes made to that specific commit with `git diff 9723453` (for commit id 9723453).

## Changing history
### Amend
There a few ways for your to make changes to your Git history. The first one is amend, which offers you the possibility to modify the last commit made. Instead of creating a new commit, you simply use `git commit --amend`, to replace the last one. 

### Reset
If you want to reset changes made to a specific point in time you can use `git reset <commit id>`. The reset command actually moves the `HEAD` to a specific past commit. If you specify the `git reset --hard <commit id>` parameter it will delete all the changes made between the original `HEAD` commit and the past commit id, while if you don't specify the files will keep the changes, but it won't be staged.

### Rebase
Rebase allows you to take the changes from one branch and apply it to another branch. You have a few ways to use rebase, like the interactive, which opens your default text editor in order for you to organize your current branch history.
```bash
git rebase -i --root
```

## Branching
Branching allows you to create alternative versions of your Git project in order to develope and test new features. To have check the available branches from your repository you can use `git branch`. Whenever you want to create a new branch, keeping the history of the current branch you can use `git switch -c <NEW BRANCH NAME>` (or older command `git checkout -b <NEW BRANCH NAME>`).

## Merge
After making changes to your new branch, you can merge it to the `main` branch. First, you need to commit the changes made to the new branch, and switch back to the `main` branch.
```bash
git switch main
```
And then, use `merge` to bring the changes made to the new branch to `main`.
```bash
git merge <NEW BRANCH NAME>
```

## Deleting branches
It's a good practice to delete branches that were already merged into production (to `main` branch). 
```bash
git branch --delete <NEW BRANCH NAME>
git branch --d <NEW BRANCH NAME>
git branch --D <NEW BRANCH NAME>
```

## Git Flow
Git Flow is the process described above of:
1. Creating a new feature branch from main branch
2. Make changes to the new feature branch
3. Merge the changes from feature to main branch
4. Delete feature branch
Most companies follow these steps, adding a few variations.

## Merging conflicts
Merging conflicts are probably one of the most trickier activities when using Git, as you have to decided between which changes to keep, and which to discard. Whenever you perform a `merge` and the branches are display code differences, Git will display arrows (`<<<<<<<<<<`, `==========` and `>>>>>>>>>>`) around the code block that is in conflict and you have to decide what to keep.

## Stash and clean
With `git stash` you store current changes from working branch, without staging and commiting it. To list the stashed changes you can use `git stash list`, and if you want to bring the stashed changes to working branch without removing it from stash list use `git stash apply`. Or `git stash pop` to do it while removing changes from stash list.<br>
One way to get rid of untracked files and folder is by using `git clean`. If you want to perform a dry run to validate what would remove, you should use `git clean -n`. And if you want to perform the cleaning `git clean -df` (`-d` for removing folders and `-f` for forcing clean).

# Working with GitHub
Previously we have used Git commands to manage our local repository. With GitHub (and other Git Cloud platforms like Bitbucket and Gitlab) you can sinchronize your local tracked repository with a cloud storage. <br>
After creating a GitHub account you can create new repositories and start pushing and pulling information from it. <br>

## Pushing to GitHub
The first thing you need to do to link your local repository to a GitHub repository is use the `git remote add` with the url from the desired GitHub repository. The convention is to use `origin` to reference GitHub repository url.
```bash
git remote add origin  https://github.com/<YOUR GITHUB USERNAME>/<YOUR REPOSITORY NAME>
```
Next, you can push the local changes to the remote GitHub repository by using `--set-upstream` or `-u` to the command.
```bash
git push -u origin main
```
Where `origin` is the name you define for your remote repository and `main` the name of the local branch you want to push.
You can also sinchronize all your local branches with GitHub with the command `git push --all`.

## Important GitHub repo files
There are some essential files that should be present in every GitHub repository, specially if it's a open source project.
- README : The markdown file that behaves like your project landing page
- LICENSE : If it's a open source project, this is an essential file that describe how your software is licensed
- CODE_OF_CONDUCT : Describe how contributors should behave within the project
- SECURITY : Describes how to report security problems
- CONTRIBUTING : Describes how contributors should contribute to the project
- SUPPORT : Describes how users should ask support about the project
- CODEOWNERS : Describes who's responsible for code in the project

## Pull requests
Pull requests are the process of submitting changes to the main repository branch through the creation of a new branches. Instead of pushing the changes directly to the main branch, when you are working in a colaborative project, every change must pass the scrutiny of the pull request and code review in order to stablish a quality control for colaboration. It's an essential part of the Git Flow framework.

## Syncing GitHub
### Clone
Cloning is how you copy a GitHub repository to your local environment. This usually the first step when you start colaborating witha already created project.
```bash
git clone <GitHub repository URL>
```

### Fetch
`fetch` brings the changes made to the remote GitHub repository to the local, without changing your current branch.
```bash
git fetch
```

### Pull
Finally, `pull` will perform a fetch and merge for your working local branch with the remote branch.
```bash
git pull
```

## Best practices for managing issues on GitHub
1. Be descriptive with titles
    - Titles are the first thing seen when viewing issues
    - Keep titles short and simple
2. One issue per Issue
    - Provide all the information needed
    - The information targets one issue per issue
    - For complex issues, separate into multiple issues
3. Avoid duplication
    - Avoiding duplication is essential!
    - Search for similar issues prior to opening a new one
4. Communicating within issues
    - Poor communication:
        - "Wrong template applied, resolving"
        - "Issue already exists, closing duplicate"
    -  Good Communication:
        - "Incorrect template applied for specific type of issue, please refer to 'Unable to launch application' template to have issue reviewed properly"
        - Please refer to #103 for information on how to resolve issue"
5. Set up practical templates
    - Be detailed
    - Include prompts for information needed to proceed with review
    - Consider it in multiple perspectives

## Best practices with projects in GitHub
1. Use the Description and README
    - Avoid leaving a project description or README empty
    - README's support photos, videos and GIFs
2. Use different views and layouts
    - Project views can be based on certain criteria which can be changed to fit the scope of a project's goal
3. Communicate through mentions
    - Communicate with others on GitHub by using a mention via the @ symbol
4. Break down large issues
    - Complex issues can be broken into separate smaller issues
    - Enable team members to work in parallel and not overlap
5. Apply workflows
    - Automate tasks to spend less time on maitenance and more time on reaching goals
    - Utilize the built-in workflows when possible



# GitHub Codespaces
It's a fully managed cloud development environment that allows you to write code, collaborate, test and deploy your applications. It runs on a configurable virtual machine in the cloud.

## GitHub Codespaces vs GitHub.dev
- GitHub.dev allows developers to make quick edits to files in their project
- It does not offer advanced features like code collaboration, deployment, or development configuration machine features like Codespaces
- GitHub.dev editors are not persistent

## Defining your own Codespace Docker Container
You can define your own Codespace Docker container by creating a a JSON file with the environment settings on `.devcontainer/devcontainer.json`. You can create from your VSCode inside Codespaces selecting the options `View/Command Pallete/>Add dev container configuration files`.

