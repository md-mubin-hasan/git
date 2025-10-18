Git Commands

```
clone -> bring a repository from GIthub into my loacl machine
add -> track my files and changes in git
commit -> save my files in Git
push -> upload Git commits in remote repo, Github, GitBucket, 
pull -> download the changes in remote repo to my local machine, the opposite of push

git //shob commands chole asbe
git --version //kon version ta install kora ache seta dedkhabe
git config --global user.name "Mubin"    //--global use na korle ei user name ta sudhu ei working repository 
git config --global user.email "mubin.md.hasan@gmail.com"
git config user.name
git config user.email


git status //first e ei command diye check kora uchit folder er obostha
git init //ekta folder ke repository banaite hole ei command dite hoy 
git add . //working directory er shob files staging area te rakha hoy, this is also equivalent to git add --a
git commit -m "Message or Reason for commiting"
git log //check kora hoy ke ki changes korse

rm -rf foldername  //this command deletes all the contents inside foldername
git clone url newfoldername

pwd //this is a linux command, this basically outputs kon directory/folder e kaj kortesi
ls //this is also a linux command, this list outs the filenames present in that directory

folder er baire git status kaj korena
q press korle code jeta run hocche terminal e sheta bondho hoye jabe

touch filename //this creates an empty file with the filename

.gitignore file er vitore kono filename likhe rakhle seta git track korena plus jodi boli je .log er jekono file track korte na chaile simply *.log likhte hobe, 
jodi kono folder er content track korte na chai tahole foldername/ eita .gitignore e likhte hobe, so jekono jaygay foldername er folder thakle ignore korbe, 
jodi /foldername/ likhe .gitignore e add kori tahole sudhu pwd er outer foldername ta ignore korbe, kono secondfolder er vitorer firstfolder ta ignore korte 
chai tahole secondfolder/firstforlder
by default git blank folder ignore kore

git diff //ei command ta working directory er shathe staging area er shathe compare kore
git diff --staged //ei command current staging area er shathe previous commited area er shathe compare kore

git commit -a -m "Commti Message" //ei command ta staging area te jesob files ache and pwd er tracked files aceh sesob gulake directly commit kore dey, 
untracked files gula commit kore na

kono filename ke jodi manually change kora hoy tokon git status mone kore je filename ta delete kora hoise and new ekta renamed file add kora hoise eta mone kore, 
kintu abar staging area te transfer kora hoile git bujhte pare je rename kora hoise

rm filename  //ei command filename er file ta delete kore dey
git rm filename //ei command filename er file ta remove kore dey, plus pwd ke staging area te shift koray dey, however new file create kore jodi commit kora na 
thake tahole git rm filename command ta kaj korbena rm filename command use korte hoy, new file create kore jodi stage kora thake tahole git rm -f filename command 
ta use korte hoy
git rm  --cached filename //ei command ta filename ke staging area theke untracked files banay dey

git mv firstfilename secondfilename // ei command ta already commit kora/tracked kora firstfilename ke rename kore secondfilename banay dey then staging area te 
move koray dey 

kono filename ke track kora start korar por .gitignore file e filename ta add kore dewar por jodi filename tar moddhe changes kori tarpor jodi git status dekhi 
taholeo kintu git filename ta ignore korena, changes gula catch kore, filename tokon jodi asholei untrack korte chai tokon git rm --cached filename command 
diye untrack korte hobe taholei git ignore kora start korbe

rm -rf .git //ei command .git folder ta delete kore dey, khubi dangerous command

git log -p command ta use kori tahole joto gulo commit kora acheh sob gular changes gula dekhabe

git log -p -n where n is a positive integer, ei command last n ta commit er diff dekhabe
git log --stat  //ei command ta sobgula commit er summary dibe je koto gula insertions hoise, kotogula deletions hoise
git log --pretty=oneline  //shows all the commits in one line
git log --pretty=short //shows short summary of each commit
git log --pretty=full
git log --since=n.seconds /minutes/hours/days/weeks/months/years  ei command ta last n  seconds /minutes/hours/days/weeks/months/years er git log dekhabe
git log --pretty=format:"%H -- %ae"   more commands are available in Git - git-log Documentation (git-scm.com)

git commit --amend //ei command diye last commit er message plus onno change add korte parbo after oi change ta stage korar por, erpor vim editor open hobe, 
i press kore commit message edit korte parbo and esc button press kore :wq likhe vim editor close korte parbo

git restore --staged filename  //ei command staged area theke filename ta ke remove kore modified filename banay dey
git checkout -- filename //ei command working area er modified filename er current changes gula badh diye last commit er copy er shathe match koray dey, 
filename staged area te thakle abar kaj korena
git checkout -f  //ei command ta working area er shob modified file gula ke unchange kore dey, stage area te thakle kaj korbena

git remote
git remote add origin url  //instead of origin, we can give any name
git remote -v  //it shows kotha theke push or pull kora hobe
git push -u origin master   //ei command kaj korbena jodi SSH key add kora na thake //"origin": "origin" is the name of the remote repository.
When you clone a repository from a remote source, Git automatically creates a remote named "origin" that points to the original repository you cloned from.
In this context, "origin" specifies the remote repository where you want to push your local commits. "master": "master" is the name of the local branch you
want to push to the remote repository. The "master" branch is the default branch name in Git, but some repositories may use a different default branch name,
such as "main". You can replace "master" with the name of another local branch if you want to push a different branch.
git push origin branchname //branchname can also be master
git push -d origin branchname //remote repository te jei branchname er branch thakbe seta delete hoye jabe

To add SSH keys 
-Github account er settings e jaite hobe SSH key er section e to add new SSH key with a suitable title
-To generate a new SSH key and adding it to the ssh-agent, Generating a new SSH key and adding it to the ssh-agent - GitHub Docs
//add korar shomoy ekta code e lekha thake je clip, clip er bodole tail kora better
Checking for existing SSH keys - GitHub Docs , jodi exist kore tahole SSH generate korte hobena

git config --global alias.st status  //basically status command ta ke short kore st banano
git config --global alias.unstage 'restore --staged --' //one example of using alias
git config --global alias.last 'log -p -1'

git checkout -b branchname //new branch create kore with the name branchname
git checkout master/any branchname
git branch  //lists out all the branch names
git branch -v  //protita branch er commit hash and commit message show korbe

git merge branchname //the branchname should be the one which we want to merge with master branch

git branch --merged   //already merged branches gula dekhabe
git branch --no-merged //jei branches gula ekhono merged kora nai sesob dekhabe

deleting branches
git branch -d branchname //gives error if that branchname is not merged
git branch -D branchname  //will not give any error and delete that branchname

git pull --rebase origin master  //get the commits from remote repo (origin) and combine with the local repo branch ('master', usually 'main' branch thake locally)
//"origin" refers to the remote repository (you might name it differently when adding the remote repo) from which you want to pull the latest changes.
It specifies that you want to pull the changes from the remote repository named "origin" and rebase your local branch (master in this case, usually 'main'
branch thake locally) on top of the updated commit history from that remote repository.
 
Conflict resolution markers
Branching workflow
-Long running branches
-Topic branches

```

So you think you know git? - Scott Chacon
https://git-scm.com/book
gitbutler.com

How well do you know git?
- Porcelain (82)
44 main commands (add, commit, push, pull, ...)
11 manipulators (config, reflog, replace, ...)
17 interrogators (blame, fsck, rerere, ...)
10 interactors (send-email, p4, svn, ...)
- Plumbing (63)
19 manipulators (apply, commit-tree, update-ref, ...)
21 interrogators (cat-file, for-each-ref, ...)
5 syncing (fetch-pack, send-pack, ...)
18 internal (check-attr, sh-i18n, ...)
Total (145)

What has been changing?
- https://blog.gitbutler.com/

git workflow?

creating a git repo
1. make a new floder
2. git init   #init a repo
3. git remote add origin "ADDRESS"  # add a remote repo to you local repo
4. git remote -v

clone 

git clone “ADRESS(http/ssh)” # you can clone a remote repo from github 

add and commit
1. add: Stage your changes, i.e. tell git what you have changed
2. commit: turn your code into a git object and move to repository, i.e. record your changes each commit has a commit id in SHA-1. If git commit is executed, HEAD will point to this commit.
Commit without add, git will not record any changes
Add without commit, nothing will be uploaded when push
3. Upload your commit
# git push <remote> <branch>
git push origin master

Add new branch
	git branch <BRANCH>

Change branch
	git checkout <BRANCH>

Both with one command
	git checkout -b

If want to combine two branch:
	git merge <branch>

then it will automatically perform the merging.
	If it is unsuccessful, merge conflict occurs. You need to solve it and commit and you are not allowed to checkout or perform another merge.
	Even if it successfully merged, you need to check what has been changed(Can be checked by diff) as it is very unreliable.

git state?
branch workflow?
