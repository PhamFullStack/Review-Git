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

##### I.3.1. Initialize git on local machine

```git
$git init
```

##### I.3.2. Add a specific file to local repository and commit it

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

##### I.3.3. Create a new git branch

<img src="https://www.nobledesktop.com/image/gitresources/git-branches-merge.png" alt="Git Branches" style="zoom:50%;"/>

```git
$git branch new-branch
```

##### I.3.4. Switch from the current branch to main branch

```git
$git checkout main
```

##### I.3.5 Merge from the current branch to the main

```git
$git checkout main				#switch to the main branch
$git merge current-branch 		#merge current-branch to the main
$git branch -d current-branch 	#delete current-branch
```

##### I.3.6. Compare differences

```git
$git log --oneline	#view committing versions
$git diff commit-v1 commit-v2 #view differences between commit-v1 and commit-v2
$git diff branch1 branch2 #view differences between branch1 and branch2
```

##### I.3.7. Revert to previous states

- Create git versions 

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

- View git versions

```git
$git reflog
(HEAD -> master)
0c59891 HEAD@{1}: commit: 4th git commit: 4 files
4945db2 HEAD@{2}: commit: 3rd git commit: 3 files
defc4eb HEAD@{3}: commit: 2nd git commit: 2 files
2938ee3 HEAD@{4}: commit: 1st git commit: 1 file
```

OR

```git
$git log --oneline
f569e54 (HEAD -> main, origin/new-branch, new-branch) Merge to master
efbe4e1 Commit data to the new-branch
357d12b Test
0bcde83 Update Readme
8cb0875 Initial commit
```

Revert to latest version

```git
$git revert HEAD
```

Or revert to earlier commits

```git
$git revert HEAD~2	#going back 2 steps
```



### II. Github

#### II.2. Github Personal Access Token

##### II.2.1. Generating personal access token

https://stackoverflow.com/questions/68775869/support-for-password-authentication-was-removed-please-use-a-personal-access-to

> From your GitHub account, go to **Settings** => **Developer Settings** => **Personal Access Token** => **Generate New Token** (Give your password) => **Fillup the form** => click **Generate token** => **Copy the generated Token**, it will be something like `ghp_sFhFsSHhTzMDreGRLjmks4Tzuzgthdvfsrta`

##### II.2.2. Enter personal access token to Windows OS

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

##### II.2.3. Enter personal access token to Ubuntu

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

##### II.2.4. Enter personal access token to MacOS

Click on the Spotlight icon (magnifying glass) on the right side of the menu bar. Type **Keychain access** then press the Enter key to launch the app => In Keychain Access, search for `github.com` => Find the **internet password** entry for `github.com` => Edit or delete the entry accordingly => You are done

#### II.3. Github Security SSH

##### II.3.1. Generating an SSH key pair

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

##### II.3.2. Add SSH key pair to the SSH-Agent

```git
$eval `ssh-agent`
$ssh-add /home/michaelphamn/.ssh/id_rsa
Enter passphrase for /home/michaelphamn/.ssh/id_rsa: [Enter your keyphrase]
Identity added: /home/michaelphamn/.ssh/id_rsa (/home/michaelphamn/.ssh/id_rsa)
```

##### II.3.3. Copy the SSH public key and save to the Github setting

```git
$cat /home/michaelphamn/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDDCY81TwfQ4PRdpN8eonwmuF0uqMZuE0kFtWlZbhO4k4NqvCyebMq30pJ1HuPuP7PKc7AG9OPJeWHk+9vCnFyD2qzdPcyyvwvV+HqaMV0/2GHYvfdEvUatE09vs7JDq8CVR2E/iYcdb4UsVTkLjAn3L4AFd4Pq+tTnivE6WT51TyF2J6brVYP5SyucIud80DFVztMiN6B243RyTXZbdW4u59rZkbq0X8ihWc6RshFGa7aDdzeQcF5PIgahabSjh95icpN7FwzuP/EeOV+vxcZMMN+dx2dkvnpEfTUnIfof3sjyvAXgdXK+/MSrvSCz+NfOZiF7OY7107kvzLSReqI2ySyHLO4SnMZHSW2EvcMb8SNz9Jg9P2jdWS/Ry+NwApF7yUL52n5OH9otCUJY5yKh6pfMluEbL7QSiPFZhClanqmwyA7AF7LtdKJsnBWpZkUHFEd+3GoChCjEA3BsQvbqKp147wy0XqSkV8T3ldSvhwRyAO+bXo6i+ANJzUywdgIBRO9sY9HQH+8sdtdvlSFJYopl4DS5VnAxjA6eqPTGmPbTscIqECYkXXCiYykQAeYpjtmGMrzCqPRGGVdzhGvpwUfnf/EZJogoACVgaD0aprjRr98SfFmy+d9IiFqjJj/03UuODcUwcZEFGeYe4ruu9L6Nrh/4Shb1T10vW0pgHQ== michaelphamn@outlook.com
```

Copy the id_rsa.pub and save to the Github setting

##### II.3.4. Test SSH Connection to Github

```git
$ssh -T git@github.com
The authenticity of host 'github.com (192.30.255.112)' can't be established.
ECDSA key fingerprint is SHA256:p2QAMXNIC1TJYWeIOttrVc98/R1BUFWu3/LiyKgUfQM.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,192.30.255.112' (ECDSA) to the list of known hosts.
Hi PhamFullStack! You've successfully authenticated, but GitHub does not provide shell access.
```

##### II.3.5. Setup working directory

```git
$git clone git@github.com:PhamFullStack/git-testing.git
$cd git-testing
```

##### II.3.6. Push files to the working directory

```git
$touch alpha.html
$git add . && git commit -m "1st git commit: 1 file"
$git push
```

#### III.2. Git pull

##### III.2.a. Git fetch

#### II.2. Github security

