# Review-Git

### I. Git getting started

#### I.1. Git version

```git
$git --version
```

#### I.2. Config global Git

```git
$git config --global user.name "username"
$git config --global user.email "email"
$git config --global user.password "password"
```

#### I.3. Git status

```git
$git status
```

#### I.4. Git help

```git
$git command -help
```

### II. Git command

#### II.1. Initialize Git on the local machine

```git
$git init
```

#### II.2. Git staging environment

```git
$git add file  	#add file in current directory to the local repository
$git add --add	#add all files in current directory to the local repository
```

#### II.3. Git commit

```git
$git commit -m "message" #commit files from stage state to commit state
$git commit -a - m "message" #commit files directly without stage state (prefer)
```

#### II.4. Git branch

```git
$git branch new-branch	#create a new branch
$git checkout previous-branch #switch the current workspace to previous branch
```

#### II.5. Git branch merge

Ex: merge source code from the current branch (current-branch) to the master

```git
$git checkout master			#switch to the master branch
$git merge current-branch 		#merge current-branch to the master
$git branch -d current-branch 	#delete current-branch
```



### III. Github

#### III.1. Github getting started

