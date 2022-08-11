# Git Fundamentals

This is a summary of the commands covered in the **Git Fundamentals** course by Fabio Biondi & Giorgio Boa.


1. [Git-GitHub Fundamentals](#git-github-fundamentals)
2. [PRO TIPS](#pro-tips)
3. [Remote Repository](#remote-repository)
4. [Branch](#branch)
5. [Rebase](#rebase)

## GIT-GITHUB FUNDAMENTALS

After registration on GitHub, create a repository.
Then, we can create and commit files directly on GitHub if necessary.

Setting up <br><br>
Open cmd and type:
- ```git config --global user.name yourusername```
- ```git config --global user.email youremail```

Login and clone <br><br>
From August 2021 GitHub has the ability to authenticate via password for all operations carried out, for example from Command Line or Desktop Applications.<br>Two solutions are now available: 1) Token-based authentication 2) the use of SSH Token Based Authentication <br>The simplest option (and recommended by Github) for the new authentication process is to use a "personal access token" (PAT) via HTTPS.<br><br>
Documentation: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token
<br>
Flow
<br>

![image](https://user-images.githubusercontent.com/32736570/183742490-d5caa28f-2e7c-466c-addf-df735dc19e3d.png)


---
To verify that the local folder is connected to the GitHub's remote repository we can use the command :<br>
- ```git remote -v```
```git status```
```git commit -m "first commit"```  --> option "-m" is used to add a comment

**git commit: best practices**
- 20/30 characters max, (50 max in some case)
- start with a lowercase letter
- separate commit for every feature/fix
- no punctuation marks at the end of commit
- imagine to write after the sentence "if applied, this commit will.."

---
# PRO TIPS

|COMMAND|DESCRIPTION|
|---|---|
|```git log```| allows you to analyze the local history of our commits|
|```git log --online```|compact versione of "git log" ("q" to exit from the log)|
|```git log --online --all```|compact versione of "git log" ("q" to exit from the log) with commit of all branches|
|```git log --grep="style"```|searching commit with a specific string| 
|```git log --invert-grep --grep="style```|searching commit without a specific string|
<br><br>
Alias on Windows: insert alias in gitconfig (file in C/Programs/Git/etc)<bg>
  in this example "git lg" will make a "git log"

![image](https://user-images.githubusercontent.com/32736570/183757187-4a855c91-bcfc-45ba-b08a-e60d7dd4ab80.png)
  
<bg><bg><bg><bg>

|COMMAND|DESCRIPTION|
|---|---|
|```git restore --staged .```|remove ALL changes (with ".", or instead a specific file) from STAGING AREA|
|```git commit -am "comment"```|make add and commit in one command|
|```git commit --amend -m "changing commit message"```|change last commit message|
|```git commit --amend -m "changing commit message and adding new file"```|add change at the last commit (before is necessary "git add." )|
|```git commit --no-edit```|commit without messagge or default message|
|```git restore --staged <file>```|remove files from STAGING AREA|
|```git reset HEAD <file>```|remove files from STAGING AREA
|```git diff origin/main HEAD```|watch differences from LOCAL COMMIT and REMOTE COMMIT (origin=alias remote repo, main=remote branch HEAD=name of the commit)|
|```git reset HEAD~1```|remove n LOCAL COMMIT(reset default mixed option), files returned in WORKING AREA(in this example: from HEAD, return 1 commit before)|
|```git reset hash```|remove to n LOCAL COMMIT with hash, taked with "git log --online"(reset default mixed option), files returned in WORKING AREA|
|```git checkout HEAD -- .```|all files will revert to their original state, to the last commit|
|```git reset --soft [HEAD~n][HASH]```|remove n LOCAL COMMIT, files returned in STAGING AREA|
|```git reset --hard [HEAD~n][HASH]```|remove n LOCAL COMMIT, files will be deleted|
|```git reflog```|after a "git reset --hard ..", if you need to watch all actions on the project. Then, taked the hash, you can restore with "git reset --hard hash"|
|```git revert [HEAD~n][HASH]``` (":wq" after the git command)|undo remote repo to local repo|
|```git reset --hard [HEAD~n][HASH]``` + ```git push --force```|delete last n LOCAL COMMIT and REMOTE COMMIT|
|```git rm --cached (file/folder name) [-r]```|delete files/folders from REMOTE REPO (option -r if folder with files internally)|
  
  ## git ignore

|   |   |
|---|---|
|*.env|ignore all files with "env" extension|
|node_modules|ignore folder with thah name|<br>

  
# REMOTE REPOSITORY
  
|   |   |
|---|---|
|```git branch```|return the branch of the your repo|
|```git push -u origin master```|first push to allineate local repo with remote repo|
|```git push```||
|```git pull```||
  
# BRANCH
  
  in Git, a branch rapresents a temporary line. It is already created once the project is initialized. During new developments, it's possible to create new branches for new feaures.<br><br>
  ![image](https://user-images.githubusercontent.com/32736570/183938635-2d233c73-15b2-42e2-9d02-5a4da849d9a7.png)
  ![image](https://user-images.githubusercontent.com/32736570/183939072-ba45a7d0-f7eb-4a91-9063-704674c269b4.png)
<br>
<br>
  
|   |   |
|---|---|
|```git branch```|return the branch of the your repo|
|```git branch branchname```|create new branch|
|```git branch -M main```|rename branche name with "main"|
|```git checkout branchname```|switched to branch "branchname"|
|```git branch -d branchname```|delete branch "branchname"|
|```git checkout -d branchname```|create and switched to branch "branchname"|
|```git merge branchname```|merge with "branchname"|

### Conflicts with remote repositories on different files
Suppose we have committed on a branch "detached" from main, which we will call "new_branches" :
after the branch change (returning to "main") we will make ```git merge``` <br>
Now, another person commits to ANOTHER file on the main branch of the remote repository - the ```git push``` command will not work.
So we have to do a ```git pull``` to download the latest changes, and now we could make the ```git push```.

### Branch diagram with "lg" alias
In the file ***gitconfig***, put in the section "alias":
lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --branches<br>
With this command we can see the branch diagram.

### Conflicts with remote repositories on same files
Suppose we have committed on a branch "detached" from main, which we will call "new_branches" :
after the branch change (returning to "main") we will make ```git merge``` <br>
Now, another person commits to the SAME file on the main branch of the remote repository - the ```git push``` command will not work.
So we have to do a ```git pull``` to download the latest changes, but now the IDE that we're using will ask what changes we want to take.
Once time that we have choose, now we could make the ```git push```.

### Create remote branch
|   |   |
|---|---|
|```git push origin new_branch```|orgin is the alias of remote repo|

### Delete remote and local branch
|   |   |
|---|---|
|```git branch -d branchname```|delete local branch|
|```git push origin --delete branchname```|delete remote branch|

# REBASE

What is the rebase command? It is used to rewrite the history(commit) of our project.

|   |   |
|---|---|
|```git rebase -i [HEAD~n][HASH]```|take the last n commit or the commit with that hash, then we have many options (type ```a``` to go to ***insert mode***)|
|```reward```|replacing ```pick``` with option ```r```, then with ```:wq``` (to save) we can edit the commit message. Then ```:wq``` yet.|
|```squash```|replacing ```pick``` with option ```s```, then with ```:wq``` (to save) we can merge more commit and edit the commit message. Then ```:wq``` yet.|
|```fixup```|replacing ```pick``` with option ```s```, then with ```:wq``` (to save) we can merge more commit like squash but CAN'T edit the commit message. Then ```:wq``` yet.|
|```drop```|replacing ```pick``` with option ```d```, then with ```:wq``` (to save) we can drop the specific commit selected. Then ```:wq``` yet.|
|```edit```|replacing ```pick``` with option ```e```, then with ```:wq``` (to save) we can edit files. Then with  ```git add .```. Once time we finished, type ```git --amend [-m "optional commit"][--no-edit]```. Finally ```git rebase --continue```|
|```git rebase -i [--root][HEAD~n][HASH] --exec "node index.js" ```|to execute and print results of file "index.js" from root, before type ```:wq```|

### MERGE VS REBASE
If we have a **"main" branch**, and one **"feature" branch** :
- with merge, the changes will be integrated (from the main) subsequently with another commit;
<br><br>***MERGE MAIN INTO FEATURE***<br>
![image](https://user-images.githubusercontent.com/32736570/184239993-cde9bfee-6414-4035-8ba7-1938acd1ee1c.png)

- with rebase, takes our commit of the feature branch and put them in head of main branch;
<br>

![image](https://user-images.githubusercontent.com/32736570/184240665-be4a7f79-1812-4d97-876e-df143b80e708.png)

#
