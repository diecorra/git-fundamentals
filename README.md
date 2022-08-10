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
- **git config --global user.name yourusername**;
- **git config --global user.email youremail**;

Login and clone <br><br>
From August 2021 GitHub has the ability to authenticate via password for all operations carried out, for example from Command Line or Desktop Applications.<br>Two solutions are now available: 1) Token-based authentication 2) the use of SSH Token Based Authentication <br>The simplest option (and recommended by Github) for the new authentication process is to use a "personal access token" (PAT) via HTTPS.<br><br>
Documentation: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token
<br>
Flow
<br>

![image](https://user-images.githubusercontent.com/32736570/183742490-d5caa28f-2e7c-466c-addf-df735dc19e3d.png)


---
To verify that the local folder is connected to the GitHub's remote repository we can use the command :<br>
- **git remote -v**

**git status**

**git commit -m "first commit"**  --> option "-m" is used to add a comment

**git log**                       --> allows you to analyze the local history of our commits
**git log --online**              --> compact versione of "git log"
"q" to exit from the log


**git commit: best practices**
- 20/30 characters max, (50 max in some case)
- start with a lowercase letter
- separate commit for every feature/fix
- no punctuation marks at the end of commit
- imagine to write after the sentence "if applied, this commit will.."

**git push**

---
# PRO TIPS

**git log**

**git log --grep="style"**                  --> searching commit with a specific string
**git log --invert-grep --grep="style"**    --> searching commit without a specific string

Alias: insert alias in gitconfig (file in C/Programs/Git/etc)<bg>
  in this example "git lg" will make a "git log"

![image](https://user-images.githubusercontent.com/32736570/183757187-4a855c91-bcfc-45ba-b08a-e60d7dd4ab80.png)
  
<bg><bg><bg><bg>
  
**git restore --staged .**                                              --> remove ALL changes (with ".", or instead a specific file) from STAGING AREA<br>
**git commit -am "comment"**                                            --> make add and commit in one command<br>
**git commit --amend -m "changing commit message"**                     --> change last commit message<br>
**git commit --amend -m "changing commit message and adding new file"** --> add change at the last commit (before is necessary "git add." )<br>
**git restore --staged <file>**                                         --> remove files from STAGING AREA<br>
**git reset HEAD <file>**                                               --> remove files from STAGING AREA<br>
**git diff origin/main HEAD**                                           --> watch differences from LOCAL COMMIT and REMOTE COMMIT<br>
  (origin=alias remote repo, main=remote branch HEAD=name of the commit)<br>
**git reset HEAD~1**                                                   --> remove n LOCAL COMMIT(reset default mixed option), files returned in WORKING AREA<br>
  (in this example: from HEAD, return 1 commit before)<br>
**git reset hash**                                                     --> remove to n LOCAL COMMIT with hash, taked with "git log --online"(reset default mixed option), files returned in WORKING AREA<br>
**git checkout HEAD -- .**                                             --> all files will revert to their original state, to the last commit<br>
**git reset --soft HEAD~1**                                            --> remove n LOCAL COMMIT, files returned in STAGING AREA<br>
**git reset --hard HEAD~1**                                            --> remove n LOCAL COMMIT, files will be deleted <br>
**git reflog**                                                         --> after a "git reset --hard ..", if you need to watch all actions on the project. Then, taked the hash, you can restore with "git reset --hard hash"<br>
**git revert #hash** (":wq" after the git command)                     --> undo remote repo to local repo<br>
**git reset --hard #hash/HEAD~n** + **git push --force**               --> delete last n LOCAL COMMIT and REMOTE COMMIT<br>
**git rm --cached (file/folder name) [-r]**                              --> delete files/folders from REMOTE REPO (option -r if folder with files internally)<br>
  
  ## git ignore
  
*.env         --> ignore all files with "env" extension<br>
node_modules  --> ignore folder with thah name<br>
