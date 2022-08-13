# Git Fundamentals

This is a summary of the commands covered in the **Git Fundamentals** course by Fabio Biondi & Giorgio Boa.<br>
Link: https://fabiobiondi.teachable.com/p/github-fundamentals


1. [Git-GitHub Fundamentals](#git-github-fundamentals)
2. [PRO TIPS](#pro-tips)
3. [Remote Repository](#remote-repository)
4. [Branch](#branch)
5. [Rebase](#rebase)
6. [Tag-Release](#tag-release)
7. [Pull-Request](#pull-request)
8. [Git-Stash](#git-stash)
9. [Bonus](#bonus)

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
  
|command|description|
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
  
|command|description|
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
|command|description|
|---|---|
|```git push origin new_branch```|orgin is the alias of remote repo|

### Delete remote and local branch
|command|description|
|---|---|
|```git branch -d branchname```|delete local branch|
|```git push origin --delete branchname```|delete remote branch|

# REBASE

What is the rebase command? It is used to rewrite the history(commit) of our project.

|command|description|
|---|---|
|```git rebase -i [HEAD~n][HASH]```|take the last n commit or the commit with that hash, then we have many options (type ```a``` to go to ***insert mode***)|
|```reward```|replacing ```pick``` with option ```r```, then with ```:wq``` (to save) we can edit the commit message. Then ```:wq``` yet.|
|```squash```|replacing ```pick``` with option ```s```, then with ```:wq``` (to save) we can merge more commit and edit the commit message. Then ```:wq``` yet.|
|```fixup```|replacing ```pick``` with option ```s```, then with ```:wq``` (to save) we can merge more commit like squash but CAN'T edit the commit message. Then ```:wq``` yet.|
|```drop```|replacing ```pick``` with option ```d```, then with ```:wq``` (to save) we can drop the specific commit selected. Then ```:wq``` yet.|
|```edit```|replacing ```pick``` with option ```e```, then with ```:wq``` (to save) we can edit files. Then with  ```git add .```. Once time we finished, type ```git --amend [-m "optional commit"][--no-edit]```. Finally ```git rebase --continue```|
|```git rebase -i [--root][HEAD~n][HASH] --exec "node index.js" ```|to execute and print results of file "index.js" from root, before type ```:wq```|

### MERGE VS REBASE
Suppose we have a **"main" branch**, and one **"feature" branch**, and we are in main branch :
  
- with merge (```git merge feature```), the changes will be integrated subsequently with another commit;
<br><br>***MERGE MAIN INTO FEATURE***<br>
![image](https://user-images.githubusercontent.com/32736570/184239993-cde9bfee-6414-4035-8ba7-1938acd1ee1c.png)

- with rebase, (```git rebase feature```), takes our commit of the feature branch and put them in head of main branch;
<br>

![image](https://user-images.githubusercontent.com/32736570/184240665-be4a7f79-1812-4d97-876e-df143b80e708.png)

# TAG-RELEASE
  
The command **TAG** let us to create a simil branch but it's in read only, it is used when people wants to release new version.
  
|command|description|
|---|---|
|```git tag```|to see how many tags we have in history|
|```git checkout v.1.0```|switched to tag "v.1.0"|
|```git tag -a v.1.0```|let to create a tag with name "v.1.0", after confirm, cmd will ask us a description, finally ```:wq``` to exit|
|```git tag -a -f v.1.0```|create a tag with force option|
|```git -d v.1.0```|delete tag|
|```git tag v.1.0 [HASH]```|associate tag to old commit (hash from ```git log --oneline```)|
|```git push origin v.1.0```|sync local tag with remote tag|

### Create a release
  The concept of "tag" belongs to git, while "release" to remote, in this case to GitHub
  1) ***Draft a new release*** in **Code** section of your GitHub repository, to create a new release
  2) Choose a created tag, or create it, the same for branches
  3) Write the tag name
  4) Optional description and attachments 
  5) Publish or Save draft
  
  # PULL-REQUEST
  
  It's a request that we make inside a project (that could my public/private project or project of another author).
  So, we can include code inside our project or we can propose a change inside a repository of an other author on GitHub.
  
  With the command ```fork```let us to clone a project of an other author and associate it with us.
  So, we create the same project in our repository to be able to modify it later and make the pull request.
  
  ### Open a pull-request on GitHub:
  - go to the repo that you want to edit
  - now edit, create new file or something that you want to do
  - make the ```commit``` with the click on "Commit" or "Commit new file"
  - in the main page of repository now we have a button called "Compare & pull request", click that
  - in the new page we can have all the options for the pull request
  - once time that it's ready, click on "Create pull request" or "Create draft pull request" (for draft) 
  
  ### Close a pull-request on GitHub:
  - go to the page with open pull requests
  - click on "Close pull request"
  - it's possible to reopen the request with the button "Reopen pull request"
  
  # GIT STASH
  
  |command|description|
  |---|---|
  |```git stash save my_stash```|This command allows you to "put aside for later" the changes made to our code, without committing them, so that it is possible, therefore, to go back to the last local "commit" and, if necessary, modify branches if necessary.|
  |```git stash -u```|the untracked files too|
  |```git stash list```|to see the list of stash|
  |```git stash show```|to see the content of last stash|
  |```git stash show stash_name```|to see the content of "stash_name", taked by ```git stash list```|
  |```git stash pop```|allow us to apply the first change of the list we have put aside|
  |```git stash pop stash_name```|allow us to apply the specific change we have put aside|
  |```git stash apply stash_name```|make the same of pop but it doesn't delete the stash|
  |```git stash drop [stash_name]```|delete the last/specific stash|
  |```git stash clear```|delete all stashs|
  |```git stash save stash_name -u``` ```git stash branch branch_name stash_name```|create a stash, then take a stash and copy in a (new) branch|
  
  # BONUS
  |command|description|
  |---|---|
  |```git diff my_new_branch```|verify diff to my branch(the branch you are in) and the other branch(my_new_branch)|
  |```git diff```|pending changes in the current branch|
  |```git diff > file_diff```|extract off ```git diff``` in a file|
  |```git diff [HASH][HASH]```|diff between the 2 commits |
  |```git bisect start```, ```git bisect bad HEAD```, ```git bisect good [hash]``` |find bugs and regressions|
  |```git bisect HEAD [hash]|the same uf commands above, but in one command (the first parameter is the bad commmit, the second is the last good commit)|
  |```git bisect log```|log of bisect|
  |```git bisect bad```|we are saying that the current commit is bad|
  |```git bisect good```| we are saying that the current commit is good|
  |```git bisect reset```|I go back to the initial situation|
  
  ### Deploy static website (HTML, CSS, JS) on GitHub Pages
  
  1) Go on your repository on GitHub, "Settings", "Pages"
  2) On "Source" options, select the branch that you would you like to deploy, and click on "Save"
  
  Your static website is online.
  
