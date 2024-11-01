# Install Git

1. Go to the website and download the installer for your OS 
    (https://git-scm.com/download/mac)

2. There will be many options. I picked **Homebrew** based on Chatgpt recommendation. Homebrew is a popular **package manager** for macOS. It makes it easy to install and manage software.

3. Run the following command in Terminal in order to install Homebrew. Also, follow any additional steps given in the installation instructions.

    ``` /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" ```
4. Run the following command to install Git.
    ``` brew install git ```

5. Alternately, Launch the **Terminal** application.
    - Type `git` and press enter.
    - If you dont already have Git installed, a dialog will appear saying that *The git command requires the command line developer tools. Would you like to install the tools now?*
    - Click **Install** and follow the instructions.

5. Verify installation using the following command. You should see the installed version of Git.
    ``` git --version ```  *git version 2.45.2*

# Setup Git

1. Setting your commit email address
    - You can use the `git config` command to change the email address you associate with your Git commits.
        ``` git config --global user.email "EMAIL" ```
    - You can use your GitHub provided no-reply email address or any email address.
    - Confirm that you have set the email address correctly in Git
        ``` git config --global user.email ```
    - Add the email address to your account on GitHub, so that your commits are attributed to you and appear in your contributions graph.
    - You can change the email address associated with your commits in a single repository. this will override your global Git configuration settings in this one repository, but will not affect any other repositories.
        - Change the current working directory to the local repository where you want to configure the email address that you associate with your Git commits.
        - ``` git config user.email "EMAIL" ```
        - To confirm that you have set the email address correctly in Git - ``` git config user.email ```
2. Username
    - Git uses a username to associate commits with an identity.
    - The Git username is not the same as your GitHub username.
    - You can change the name that is associated with your Git commits using the `git config` command.
    - The new name you set will be visible in any future commits you push to GitHub from the command line.
    - If you would like to keep your real name private, you ca use any text as your Git username.
    - Changing the name associated with your Git commits usiing `git config` will only affect future commits and will not change the name used for past commits.
    - Setting your Git username for *every* repository on your computer.
        ``` git config --global user.name "NAME" ```
    - Confirm that you have set the Git username correctly
        ``` git config --global user.name ```
    - Setting your Git username for a *single* repository
        - Change the current working directory to the local repository where you want to configure the name that is associated with your Git commits.
        - Set a Git username
            ``` git config user.name "NAME" ```
        - Confirm that you have set the Git username correctly
            ``` git config user.name ```
    - Create a Personal Access Token
        - To authenticate yourself in the terminal, you will need to generate a **Personal Access Token** on GitHub. Go to **Developer Settings**.
        - Navigate to the article [creating a personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic) and follow the instructions for creating a **classic token**.
        - Be sure to check the box that grants the token **repo** scope - this will allow you to write to the repository from the terminal on your machine.
        - Once you get the token, make sure to copy it, you will not be able to view the token again once you navigate away from the page.

# Create a Sample Git repository

1. Make a new directory to practice
    ``` mkdir git_practice ```
2. Make the new directory your working directory
    ``` cd git_practice ```
3. Turn the current, empty directory into a fresh Git repository
    ``` git init ```
4. Create a new README file with some sample text.
    ``` echo "Hello Git and GitHub" >> README.txt ```
5. Add the new file to the Git staging area
    ``` git add "README.txt" ```
6. Make your first commit with the new README file.
    ``` git commit -m "First commit" ```

# Few ways to check if a Git repository has been initialized properly

1. Check for the `.git` directory
    - Ater initializing a Git repository, Git creates a hidden .git directory inside your project folder. You can check for this directory
        to confirm the initialization.
    - This command lists all files, including hidden ones. If `.git` appears in the list, your Git repository has been initialized properly.
        ``` ls -a ```

2. Use git status
    - You can also check the repository's status using the following command
        ``` git status ```
    - This command inspects the contents of the working directory and staging area.
    - If the repository is properly initialized, it will display the current state of your working directory. You will see a message like      
        **On branch master**
        **No commits yet**
        **Untracked files** (These files appear in red)
    - Untracked means that Git sees these files, but has not started tracking changes yet.
    - If the repository is not initialized, you will see an error message like
        **fatal: not a git repository (or any of the parent directories): .git**

3. Check Git configuration
    - To see the Git configuration of the repository you can run
        ``` git config --list ```
    - This command will display configuration settings for the repository such as the remote URL, user info etc.