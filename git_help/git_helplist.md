___

### useful sources
1. [cheat_sheets](https://training.github.com/)
2. [visual_cheat_sheet](https://ndpsoftware.com/git-cheatsheet.html#loc=index;)
3. [git_pro_book](https://git-scm.com/book/en/v2)

___
### --config. Basic settings 

```bash
git config --list
```
- the list of local git setup 

```bash
git config --global user.name "user_name"
git config --global user.email "user_email"
git config --global user.password "user_password"
# ---
git config user.name "new_name"
```
- changes a git user.name to `user_name` FOR ALL local repos
- changes a git user.email to `user_email` FOR ALL local repos
- changes a git user.password to `user_password` FOR ALL repos
- changes a git user.name to `new_name` for current local repo
- other ways
  [how to change my git username](https://stackoverflow.com/questions/22844806/how-to-change-my-git-username-in-terminal)

___

### --init repo

```bash
git init
```
- creates a `.git` file in current folder

```bash
git init [repo_name]
```
- creates a `repo_name` folder and a `.git` file within = init. a local repo `repo_name`

___

### --(how to connect NEW local repo with NEW remote repo)

- create a remote repo on github `repo_url`
- init a local repo
- makes some(mb. 1) local commits
- connect
```bash
git remote add origin [repo_url]
git branch -M master
git push -u origin master
```
- if you dont login in your github account on this machine, use this instead `repo_url`  `http://github_user_name:github_user_password@github.com/github_user_name/repo_name.git`
- example:
  http://cameronmcnz:T55tutorial@github.com/cameronmcnz/my-github-repo.git

___

### --create a `.gitignore` file

1. [bitbucket_tutorial](https://www.atlassian.com/git/tutorials/saving-changes/gitignore)

<p align="center">
this commands for `.gitignore` file and NOT FOR TERMINAL:
</p>

```txt
# comment
<file_name>.<file_ext>
```
- to ignore file_name.file_ext file

```txt
*.<file_ext>
```
- to ignore all files with `<file_ext>` extension

```txt
/<dir_name>
```
- to ignore directory `dir_name` 

___

### --add file to start them track

```bash
git add [file_name]
```
- snapshots the `file_name` file in preparation for versioning

```bash
git add .
``` 
- snapshots ALL file in current directory in preparation for versioning

```bash
git commit -m "[message]" 
```
- records file snapshots permanently in version history

___

### --branches

```bash
git branch
```
- list of all existing branches

```bash
git branch [branch_name]
```
- creates a new `branch_name` branch

```bash
git switch -c [branch_name]
```
- switches to chosen `branch_name` branch AND updates the working directory  

```bash
git branch -m [branch_name]
```
- renames master branch to `<branch_name>`

```bash
git branch -d [branch_name]
```
- deletes a `branch_name` branch
