# CHANGE BRANCH

To see what branches are available :

```
$ git branch -a
```

To change branches in Git, you can use the `git checkout` command. Here are the steps to change to a different branch:

1. Open your terminal or command prompt.
    
2. Navigate to the root directory of your Git repository using the `cd` command. For example:
    
    ```
    cd /path/to/your/repository
    ```
    
3. To switch to an existing branch, use the following command, replacing `<branch-name>` with the name of the branch you want to switch to:
    
    ```
    git checkout <branch-name>
    ```
    
    For example, if you want to switch to a branch called "feature-branch," you would run:
    
    ```
    git checkout feature-branch
    ```
    
4. Git will change your working directory to match the state of the branch you've checked out. Any files that were modified in the previous branch but not committed will be preserved in your working directory.
    

If you want to create a new branch and switch to it in one step, you can use the `-b` flag with `git checkout`. For example:

```
git checkout -b new-branch-name
```

This command will create a new branch called "new-branch-name" and immediately switch to it.

Remember to commit your changes before switching branches if you have any uncommitted changes in your working directory, as switching branches with uncommitted changes can lead to conflicts or data loss. You can use `git status` to check the status of your changes and `git commit` to commit them before switching branches.

# COMMIT

1. **Open Git Bash**:
    
    - Launch Git Bash application on your computer.
2. **Navigate to your repository**:
    
    - Use the `cd` (change directory) command to navigate to the folder containing your Git repository.
        
        ```bash
        cd path/to/your/repository
        
        ```
        
3. **Check the status of your repository**:
    
    - Run the following command to see which files have been modified or added.
        
        ```bash
        git status
        
        ```
        
4. **Stage your changes**:
    
    - Use the `git add` command to stage the changes you want to commit.
        
    - To stage all changes in the repository, use:
        
        ```bash
        git add .
        
        ```
        
    - To stage specific files, use:
        
        ```bash
        git add file1.txt file2.txt
        
        ```
        
5. **Commit your changes**:
    
    - Use the `git commit` command to commit your staged changes.
        
    - Be sure to include a meaningful commit message using the `m` flag.
        
        ```bash
        git commit -m "Your commit message here"
        
        ```
        
6. **Push your changes**:
    
    - Use the `git push` command to push your committed changes to the remote repository.
        
    - If you are pushing to the master branch, use:
        
        ```bash
        git push origin master
        ```
        
    - If you are pushing to a different branch, replace `master` with the name of your branch:
        
        ```bash
        git push origin your-branch-name
        ```
        

These steps will help you stage, commit, and push your changes to a remote repository using Git Bash. If you are working with a newly created branch, you may need to set the upstream branch with the `-u` option during the first push:

```bash
git push -u origin your-branch-name

```