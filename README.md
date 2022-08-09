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
<br>
Flow
<br>

![image](https://user-images.githubusercontent.com/32736570/183742490-d5caa28f-2e7c-466c-addf-df735dc19e3d.png)


---
To verify that the local folder is connected to the GitHub's remote repository we can use the command :<br>
- git remote -v

git status

git commit -m "first commit"  --> option "-m" is used to add a comment

git log                       --> allows you to analyze the local history of our commits
git log --online              --> compact versione of "git log"
"q" to exit from the log


git commit: best practices
- 20/30 characters max, (50 max in some case)
- start with a lowercase letter
- separate commit for every feature/fix
- no punctuation marks at the end of commit
- imagine to write after the sentence "if applied, this commit will.."

git push

---
# PRO TIPS

git log

git log --grep="style"                  --> searching commit with a specific string
git log --invert-grep --grep="style"    --> searching commit without a specific string

Alias: insert alias in gitconfig (file in C/Programs/Git/etc)<bg>

![image](https://user-images.githubusercontent.com/32736570/183757187-4a855c91-bcfc-45ba-b08a-e60d7dd4ab80.png)

<bg>
in this example "git le" will make a "git log"

