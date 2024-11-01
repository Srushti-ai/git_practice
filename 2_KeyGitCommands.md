## All Git commands begin with `git`, followed by the specific instruction

1. **git init**
    - To start version-controlling a project, you need to initialize a Git repository.
    - **Create a folder** for your project, or navigate to an existing project folder.
    - Open the terminal in that folder and run the following command. This command initializes a new Git repository, which will start
        tracking changes in that folder.
        ``` git init ```

2. . **git add**
    - In order for Git to start tracking a file, the file needs to be added to the staging area.
    - We can add a file to the staging area with the following command - 
        ``` git add <filename> ```
    - Check the status of the project in Git. In the output, notice that Git indicates the changes to be committed with **new file: <filename>** in green text. Here Git tells us that the file was added to the staging area.
    - You can add multiple files to the staging area in a single commit - 
    ``` git add <filename_1> <filename_2> ```
    - If you know you want to add every file in the working directory to the staging area, instead of adding each file individually, you can use a shortcut :-
    ``` git add . ```
    - The `.` means **all files**. Adding files to the staging area with `.` is faster than specifying each file individually, but its easy to accidentally add files you dont want there. Make sure you always know what you are adding.
    
3. **git diff**
    - When we make changes to a file that is tracked, we can check the difference between the working directory and the staging area with the following command
        ``` git diff <filename> ```
    - Notice the output
        - Content in the staging area is indicated in white
        - Changes to the file are marked with a **+** and are indicated in green.

4. **git commit**
    - A commit is the last step in our Git workflow.
    - A commit permenantly stores changes from the staging area inside the repository.
    - The option **-m** is followed by a message.
    - Standard Conventions for Commit Messages:
        - Must be in quotation marks
        - Written in the present tense
        - Should be brief (50 characters or less) when using **-m**
    ``` git commit -m "Complete first commit" ```

5. **git log**
    - Often with Git, you will need to refer back to an earlier version of a project.
    - Commits are stored chronologically in the repository and can be viewed with the following command - 
        ``` git log ```
    - The output will be as follows - 
        - A 40 character code, called a SHA, that uniquely identifies the commit. This appears in orange text.
        - The commit author
        - The date and time of the commit
        - The commit message
    - The following command shows the list of commits in one line format
    ``` git log --oneline ```
    - The following command displays a list of commits where the number of occurrences of the keyword changes within atleast one file via addition, deletion, or modification.
    ``` git log -S "keyword" ```
    - `--graph` displays a visual representation of how the branches and commits were created in order to help you make sense of your repository history. When used alone, the description can be very lengthy, so you can combine the command with `--oneline` in order to shorten the description. 
    ``` git log --oneline --graph ```

6. **git status**
    - The following command shows Untracked files and file changes staged for commit
    ``` git status ```

7. **head commit**
    - In Git, the commit you are currently on is know as the HEAD commit.
    - In many cases, the most recently made commit is the HEAD commit.
    - To see the HEAD commit, enter the following command - 
        ``` git show HEAD ```
    - The output of this command will display everything the `git log` command displays for the HEAD commit, plus all the file changes that were committed.
    - Notice that in the output, the most recent changes are in green text.

8. **git checkout**
    - The following command will restore the file in your working directory to look exactly as it did when you last made a commit.
        ``` git checkout HEAD <filename> ```
    - This is handy when you want to revert the local changes that you made to a file; instead of manually changing it to how it was originally.
    - There is a commonly used shortcut for this command and does the exact same thing as the above command.
        ``` git checkout -- <filename> ```

9. **git reset I**
    - Use the following command to "unstage" a file from the staging area - 
        ``` git reset HEAD <filename> ```
    - This command resets the file in the staging area to be the same as the HEAD commit.
    - It does not discard file changes from the working directory, it just removes them from the staging area.
    - This is handy when you add a modified file to the staging area, but later decide to not include it in the commit just yet with some other changes ready to be committed.

10. **git reset II**
    - Use the following command to reset HEAD to any of the previous commits.
        ``` git reset <commit_SHA>```
    - This command works by using the first 7 characters of the SHA of a previous commit. For example, if the SHA of the previous commit is 5d692065cf51a2f50ea8e7b19b5a7ae512f633ba, use - 
        ``` git reset 5d69206```
    - HEAD is now set to that previous commit. The commits that came after the one you reset to are gone.
    - Using the SHA of the most recent commit will not result in any resetting.
    - You can use the dates from `git log` to determine the order in which the commits were published.

11. **git stash**
    - While working on a file, you find a small bug in a separate file from a previous commit that needs to be fixed before you continue.
    - Running the command below will store your work temporarily for later use in a hidden directory.
        ``` git stash ```
    - At this point, you can switch branches and do work elsewhere.
    - Once the bug is fixed, you want to retrieve the code you were working on previously, you can **pop** the work that was stored in stash.
        ``` git stash pop ```
    - From here, you can continue your work and commit it when ready.

12. **git commit amend**
    - Git's **amend** flag is extremely useful when updating a commit. It allows you to correct mistakes and edit commits easily instead of creating a completely new one.
    - You could create your changes, stage them with `git add` and then type the following command to update your previous commit.
        ``` git commit --amend ```
    - Its important to note that although it seems like `--amend` is simply updating the commit, what Git actually does is replace the whole previous commit. For this reason, when you execute this command, your terminal editor asks you to update your **commit message**.
    - However, if you want to keep the same commit message, you can simply add the flag `--no-edit`
        ``` git commit --amend --no-edit ```

13. **Git Alias**
    - If you have a set of commands that you use regularly and want to save some time from typing them, you can easily setup an alias for each command using Git config.
    - Examples
        - ``` git config --global alias.co "checkout" ```
        - ``` git config --global alias.br "branch" ```
    - Once the aliases are configured, next time you want to checkout to another branch, you could type the following command
        ``` git co example_branch``` instead of
        ``` git checkout example_branch ```

14. **Git Branch**
    - Use the following command to check what branch you are on
        ``` git branch ```

15. **Deleting a branch**
    - The following command is used to delete the branch named "new-feature".
        ``` git branch -d new-feature ```
    - It's good practice to delete a branch after it has been merged into the main branch.

16. **Publish a repository to GitHub**
    - If you have created a repository locally, you can publish it to GitHub by running the following commands
        - Step 1 : Add a remote repository
            ``` git remote add origin https://github.com/Srushti-ai/git_practice.git ```
        - Step 2 : Push the repository to GitHub
            ``` git push -u origin main```
        - Provide the URL of your Git repository
        - The `-u` flag sets the upstream, so future `git push` commands know where to push by default

17. **Push committed changes to GitHub**
    - After you make commits locally, you can push them to GitHub using the followig command
        ``` git push ```
    - This will push your commits to the remote repository on the branch you are currently on.
    - If it's your first push to this branch, use
        ``` git push -u origin <branch-name> ```

18. **Create a Branch**
    - To create and switch to a new branch
        ``` git checkout -b new-branch-name ```
    - To push this new branch to GitHub
        ``` git push -u origin new-branch-name ```
        