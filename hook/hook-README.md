# Hook

* DEPLOYDIR：部署的目錄
* GITDIR：Git 目錄

```shell
#!/bin/bash
#
## store the arguments given to the script
read oldrev newrev refname

## Where to store the log information about the updates
LOGFILE=./post-receive.log
# The deployed directory (the running site)
DEPLOYDIR=/directory/to/deploy/to
GITDIR=/directory/above/hooks/repo_name.git
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
git --git-dir="$GITDIR" --work-tree="$DEPLOYDIR" checkout -f;
# Then do a fresh update of all submodules.
git --git-dir="$GITDIR" --work-tree="$DEPLOYDIR" submodule update --init --recursive
# We're done in the deploy directory, so navigate back.
cd -
```