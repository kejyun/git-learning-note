# Hook

* DEPLOYDIR：部署的目錄
* GITDIR：Git 目錄
* BRNCH_NAME：分支名稱

```shell
#!/bin/bash
#
## store the arguments given to the script
read oldrev newrev refname

## Where to store the log information about the updates
LOGFILE=./post-receive.log
# 部署的目錄 The deployed directory (the running site)
DEPLOYDIR=/directory/to/deploy/to
# Git 目錄
GITDIR=/directory/above/hooks/repo_name.git
# 分支名稱
BRNCH_NAME=checkout_branch_name

blue='\033[1;34m'
no_color='\033[0m'

# %ae = Extract the user email from the last commit (author email)
USER_EMAIL=$(git log -1 --format=format:%ae HEAD)
# %an = Extract the username from the last commit (author name)
USER_NAME=$(git log -1 --format=format:%an HEAD)

## Record the fact that the push has been received
echo -e "Received Push Request at $( date +%Y-%m-%d:%H:%M:%S ) by $USER_NAME ($USER_EMAIL)" >> $LOGFILE
echo " - Old SHA: $oldrev New SHA: $newrev Branch Name: $refname" >> $LOGFILE

## Update the deployed copy
echo "Starting Deploy" >> $LOGFILE

echo " - Starting code deployment (to $DEPLOYDIR)"
# Move into the deploy directory
cd "$DEPLOYDIR";
# Then do a fresh checkout
git --git-dir="$GITDIR" --work-tree="$DEPLOYDIR" checkout -f $BRNCH_NAME;
# Then do a fresh update of all submodules.
git --git-dir="$GITDIR" --work-tree="$DEPLOYDIR" submodule update --init --recursive
# We're done in the deploy directory, so navigate back.
cd -
```

# Git 主機位置

```
ssh://{account}@{host_name}:{port}{git_folder}

ssh://kj@kejyun.com:22/home/kejyun/repo/kejyun.git
```