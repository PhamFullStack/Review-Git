# Review-Git

### I. Git tutorial

#### I.1. Install git on ubuntu

```git
$sudo apt install git
```

#### I.2. Git basic

##### I.2.1. View git version

```git
$git --version
```

##### I.2.2. Set global git configuration

```git
$git config --global user.name "username"
$git config --global user.email "email"
$git config --global user.password "password"
```

##### I.2.3. View git status

```git
$git status
```

##### I.2.4. View git help

```git
$git command -help
```

##### I.2.5. View git log

```git
$git log
$git log branch	#view log of a branch
```

#### I.3. Git advanced

##### I.3.1. Git remote

> Git remote is used to refer to a remote repository or your central repository. It means you have a local repository and you want to add references to a remote repository for further tracking.

```git
$mkdir git-testing
$cd git-testing
$git init
$git remote add origin https://github.com/PhamFullStack/Git-testing.git
$touch HelloWorld.txt
$git add .
$git commit -m "Add HelloWorld.txt"
$git push --set-upstream origin master
```

##### I.3.2. Git clone

> Git clone is used to copy or clone a different repository.

```git
$git clone https://github.com/PhamFullStack/Review-Git-Testing.git
$cd Review-Git-Testing
$touch HelloWorld.txt
$git add .
$git commit -m "Add HelloWorld.txt"
$git push
```

##### I.3.3. Initialize git on local machine

```git
$git init
```

##### I.3.4. Add a specific file to local repository and commit it

![A representation of a series of commits in Git](https://opensource.com/sites/default/files/uploads/gitcommands1_local-environment.png)

```git
$git add filename 			#add filename to the local repository
$git commit -m "message" 	#commit filename from local repository to staging area
```

Or shorthand (prefer)

```git
$git commit -a - m "message" #commit files directly without **git add** 
```

<u>Note:</u> Add all files in current directory to the local repository

```git
$git add --add
```

##### I.3.5. Git pull 

I.3.5.1. Git Fetch is used to get all the change history of a tracked branch/repo

```git
$ git fetch
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 647 bytes | 58.00 KiB/s, done.
From https://github.com/PhamFullStack/Review-Git-Testing
   1190c7b..f0c21c0  main       -> origin/main
```

You can check with the following commands

```git
$git status
On branch main
Your branch is behind 'origin/main' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean
$git log origin/main
commit f0c21c0ca18219f493479d06468d86253ba6562f (origin/main)
Author: PhamFullStack <107211966+PhamFullStack@users.noreply.github.com>
Date:   Sat Jun 11 21:05:54 2022 -0700

    Update HelloWorld.txt

commit 1190c7bcb4fb2fc112ac2a390020c2ab904190d3 (HEAD -> main)
Author: PhamFullStack <michaelphamn@outlook.com>
Date:   Sat Jun 11 21:01:45 2022 -0700

    Add HelloWorld.txt
$git diff f0c21c0ca18219f493479d06468d86253ba6562f
diff --git a/HelloWorld.txt b/HelloWorld.txt
index e6f4275..e69de29 100644
--- a/HelloWorld.txt
+++ b/HelloWorld.txt
@@ -1 +0,0 @@
-Hello World
```

I.3.5.2. Git Merge is used to combine the current branch with a  specified branch

We  merge the origin/main with id f0c21c0ca18219f493479d06468d86253ba6562f

```git
$git merge f0c21c0ca18219f493479d06468d86253ba6562f
```

I.3.5.3. Git Pull is a combination of fetch and merge

```git 
$git pull
$git pull origin
```

##### I.3.6. Git push

```git
#git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Test.TXT

nothing added to commit but untracked files present (use "git add" to track)
#git push origin
```

##### I.3.7. Create a new git branch

<img src="https://www.nobledesktop.com/image/gitresources/git-branches-merge.png" alt="Git Branches" style="zoom:50%;"/>

```git
$git branch new-branch
```

##### I.3.8. Switch from the current branch to main branch

```git
$git checkout main
```

##### I.3.9. Merge from the current branch to the main

```git
$git checkout main				#switch to the main branch
$git merge current-branch 		#merge current-branch to the main
$git branch -d current-branch 	#delete current-branch
```

##### I.3.10. Compare differences

```git
$git log --oneline	#view committing versions
$git diff commit-v1 commit-v2 #view differences between commit-v1 and commit-v2
$git diff branch1 branch2 #view differences between branch1 and branch2
```

##### I.3.11. Reset to previous states

Let's say you had commits:

```git
$touch alpha.html
$git add . && git commit -m "1st git commit: 1 file"

$touch beta.html
$git add . && git commit -m "2nd git commit: 2 files"

$touch gamar.html
$git add . && git commit -m "3rd git commit: 3 files"

$touch delta.html
$git add . && git commit -m "4th git commit: 4 files"
```

View git versions

```git
$git reflog
399775a (HEAD -> main, origin/main) HEAD@{0}: commit: 4th git commit: 4 files
694ff64 HEAD@{1}: commit: 3rd git commit: 3 files
d62a8cd HEAD@{2}: commit: 2nd git commit: 2 files
1ee08d3 HEAD@{3}: commit (initial): 1st git commit: 1 file
```

OR

```git
$git log --oneline
399775a (HEAD -> main, origin/main) 4th git commit: 4 files
694ff64 3rd git commit: 3 files
d62a8cd 2nd git commit: 2 files
1ee08d3 1st git commit: 1 file
```

Reset to d62a8cd version but still be at state of origin/main

```git
$git reset --soft d62a8cd
```

Or Reset to d62a8cd version but still be at state of d62a8cd

```git
$git reset --hard d62a8cd
```

### II. Github

#### II.1. Github Personal Access Token

##### II.1.1. Generating personal access token

https://stackoverflow.com/questions/68775869/support-for-password-authentication-was-removed-please-use-a-personal-access-to

> From your GitHub account, go to **Settings** => **Developer Settings** => **Personal Access Token** => **Generate New Token** (Give your password) => **Fillup the form** => click **Generate token** => **Copy the generated Token**, it will be something like `ghp_sFhFsSHhTzMDreGRLjmks4Tzuzgthdvfsrta`

##### II.1.2. Enter personal access token to Windows OS

Go to **Credential Manager** from **Control Panel** => **Windows Credentials** => find `git:https://github.com` => **Edit** => On Password replace with with your **GitHub Personal Access Token** => You are Done

Then you need to configure the local GIT client with a username and email address,

```git
$git config --global user.name "PhamFullStack"
$git config --global user.email "michaelphamn@outlook.com"
$git config -l
```

Once GIT is configured, we can begin using it to access GitHub. Example:

```
$git clone https://github.com/PhamFullStack/Review-Git-Testing.git
$cd Review-Git-Testing
```

Push files to the working directory

```git
$touch alpha.html
$git add . && git commit -m "1st git commit: 1 file"
$git push
```

##### II.1.3. Enter personal access token to Ubuntu

For Linux, you need to configure the local GIT client with a username and email address,

```git
$git config --global user.name "PhamFullStack"
$git config --global user.email "michaelphamn@outlook.com"
$git config -l
```

Once GIT is configured, we can begin using it to access GitHub. Example:

```
$git clone https://github.com/PhamFullStack/Review-Git-Testing.git
$cd Review-Git-Testing
```

Push files to the working directory

```git
$touch alpha.html
$git add . && git commit -m "1st git commit: 1 file"
$git push
```

Now cache the given record in your computer to remembers the token:

```
$git config --global credential.helper cache
```

If needed, anytime you can delete the cache record by:

```
$ git config --global --unset credential.helper
$ git config --system --unset credential.helper
```

##### II.1.4. Enter personal access token to MacOS

Click on the Spotlight icon (magnifying glass) on the right side of the menu bar. Type **Keychain access** then press the Enter key to launch the app => In Keychain Access, search for `github.com` => Find the **internet password** entry for `github.com` => Edit or delete the entry accordingly => You are done

#### II.2. Github Security SSH

##### II.2.1. Generating an SSH key pair

```git
$ssh-keygen -t rsa -b 4096 -C "michaelphamn@outlook.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/michaelphamn/.ssh/id_rsa):
Created directory '/home/michaelphamn/.ssh'.
Enter passphrase (empty for no passphrase): [Enter your keyphrase]
Enter same passphrase again: [Enter your keyphrase]
Your identification has been saved in /home/michaelphamn/.ssh/id_rsa
Your public key has been saved in /home/michaelphamn/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:yT7WcrAEnvsvR2beTyUuQRhGgrltsFTy7xlzzqSGxuo michaelphamn@outlook.com
The key's randomart image is:
+---[RSA 4096]----+
|      .+o.+      |
|      =o o o     |
|     ..=. . .    |
|     .o+oo .     |
|      o.S + + . .|
|       = *+X o o |
|      . X=B.+ o  |
|       =.=o .o   |
|     .E .+.  ..  |
+----[SHA256]-----+
```

##### II.2.2. Add SSH key pair to the SSH-Agent

```git
$eval `ssh-agent`
$ssh-add /home/michaelphamn/.ssh/id_rsa
Enter passphrase for /home/michaelphamn/.ssh/id_rsa: [Enter your keyphrase]
Identity added: /home/michaelphamn/.ssh/id_rsa (/home/michaelphamn/.ssh/id_rsa)
```

##### II.2.3. Copy the SSH public key and save to the Github setting

```git
$cat /home/michaelphamn/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDDCY81TwfQ4PRdpN8eonwmuF0uqMZuE0kFtWlZbhO4k4NqvCyebMq30pJ1HuPuP7PKc7AG9OPJeWHk+9vCnFyD2qzdPcyyvwvV+HqaMV0/2GHYvfdEvUatE09vs7JDq8CVR2E/iYcdb4UsVTkLjAn3L4AFd4Pq+tTnivE6WT51TyF2J6brVYP5SyucIud80DFVztMiN6B243RyTXZbdW4u59rZkbq0X8ihWc6RshFGa7aDdzeQcF5PIgahabSjh95icpN7FwzuP/EeOV+vxcZMMN+dx2dkvnpEfTUnIfof3sjyvAXgdXK+/MSrvSCz+NfOZiF7OY7107kvzLSReqI2ySyHLO4SnMZHSW2EvcMb8SNz9Jg9P2jdWS/Ry+NwApF7yUL52n5OH9otCUJY5yKh6pfMluEbL7QSiPFZhClanqmwyA7AF7LtdKJsnBWpZkUHFEd+3GoChCjEA3BsQvbqKp147wy0XqSkV8T3ldSvhwRyAO+bXo6i+ANJzUywdgIBRO9sY9HQH+8sdtdvlSFJYopl4DS5VnAxjA6eqPTGmPbTscIqECYkXXCiYykQAeYpjtmGMrzCqPRGGVdzhGvpwUfnf/EZJogoACVgaD0aprjRr98SfFmy+d9IiFqjJj/03UuODcUwcZEFGeYe4ruu9L6Nrh/4Shb1T10vW0pgHQ== michaelphamn@outlook.com
```

Copy the id_rsa.pub and save to the Github setting

##### II.2.4. Test SSH Connection to Github

```git
$ssh -T git@github.com
The authenticity of host 'github.com (192.30.255.112)' can't be established.
ECDSA key fingerprint is SHA256:p2QAMXNIC1TJYWeIOttrVc98/R1BUFWu3/LiyKgUfQM.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,192.30.255.112' (ECDSA) to the list of known hosts.
Hi PhamFullStack! You've successfully authenticated, but GitHub does not provide shell access.
```

##### II.2.5. Setup working directory

```git
$git clone git@github.com:PhamFullStack/git-testing.git
$cd git-testing
```

##### II.2.6. Push files to the working directory

```git
$touch alpha.html
$git add . && git commit -m "1st git commit: 1 file"
$git push
```
