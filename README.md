# Git Fundamentals

This is a summary of the commands covered in the **Git Fundamentals** course by Fabio Biondi & Giorgio Boa.


1. [Git-GitHub Fundamentals](#git-github-fundamentals)
2. [PRO TIPS](#pro-tips)
3. [Remote Repository](#remote-repository)

# Git-GitHub Fundamentals

After registration on GitHub, create a repository.
Then, we can create and commit files directly on GitHub if necessary.

Setting up <br><br>
Open cmd and type:
- git config --global user.name yourusername;
- git config --global user.email youremail;

Login and clone <br><br>
From August 2021 GitHub has the ability to authenticate via password for all operations carried out, for example from Command Line or Desktop Applications.<br>Two solutions are now available: 1) Token-based authentication 2) the use of SSH Token Based Authentication <br>The simplest option (and recommended by Github) for the new authentication process is to use a "personal access token" (PAT) via HTTPS.<br><br>
Documentation: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

# PRO TIPS

To verify that the local folder is connected to the GitHub's remote repository we can use the command :<br>
- git remote -v
