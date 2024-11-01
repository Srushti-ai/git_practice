# Creating a GitHub Account

1. To use GitHub, you will need a GitHub account - (https://github.com/)
2. Set commit email address
    - If you would like to ensure that you dont accidentally publish your email address, simply check the options below in your [Email Settings](https://github.com/settings/emails) 
        - Keep my email address private
        - Block command line pushes that expose my email
    - If you havent enabled email address privacy, you can choose which verified email address to author changes with when you edit, delete or create files or merge a pull request on GitHub.
    - If you enabled email address privacy, then the commit author email address cannot be changed and will be a no-reply email address by default.
    - no-reply email address - **ID+USERNAME@users.noreply.github.com**

# Connect your local Git repository to GitHub

1. Finally, we will create a repository on GitHub and then link it to a local repository on your computer.
2. This allows you to backup your work constantly and safely.
3. Make sure your current working directory is your new Git repository. Navigate there if not.
4. Check the status of which files and folders are new or have been edited. There should be no files modified.
    ``` git status ```
5. Create a new repository on GitHub. On the new repository page, give your repository a name. Its not necessary, but it would be convenient to name it the same as the directory git_practice.
6. After creating a repository, GitHub displays the repository page. At the top of the page, make sure **HTTPS** is selected.
7. Run below GitHub commands from the GitHub page. These commands will add a remote repository, and then push your local repository to the remote repository.
    ``` git remote add origin https://github.com/Srushti-ai/git_practice.git ```
    ``` git branch -M main ```
    ``` git push -u origin main ```
8. Enter below details when prompted
    - username - Your GitHub username
    - password - Your personal access token
9. Once your command line interface reports that the push is complete, refresh the page on GitHub to see repository.
10. GitHub automatically displays the contents of a file named README.txt if it exists in the repository. The README file is the perfect place to write a description of your project.