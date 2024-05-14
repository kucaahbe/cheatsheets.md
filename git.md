---
tag: tools
---

mark files needs to be merge-resolved:

```
git checkout --conflict=merge file
```

grep with excluding specific pattern or files:
```sh-session
# search for "belongs_to" but filter out "optional"
git grep -e belongs_to --and --not -e optional -- app

# list only filenames and use extended regexp:
git grep -l -E -e belongs_to --and --not -e 'optional:\s*true' -- app

# find (within found files) only files with rails validations:
git grep -l -E -e belongs_to --and --not -e 'optional:\s*true' -- app | xargs grep -l validates

# exclude specific files (*.js)
git grep term -- ':!*.js'
```

ignore locally changed file:

```
git update-index --assume-unchanged file
```

undo this action:

```
git update-index --no-assume-unchanged [<file> ...]
```


rebase on top of end-of-line **normalized** branch:

```
git rebase -i develop -s recursive -Xrenormalize
```

copy of the repository in another folder:

```
git worktree
```

auto-set origin and remote branch name:

```
git config remote.pushDefault origin
```

rebase against initial commit

```
git rebase -i --root
```

 [extract subfolder as separate repository](https://help.github.com/articles/splitting-a-subfolder-out-into-a-new-repository/)

```
git filter-branch [-d /tmp] --prune-empty --subdirectory-filter FOLDER-NAME -- BRANCH-NAME
# example with commit message filter:
git filter-branch --prune-empty --subdirectory-filter config/ec2/provision.ansible --msg-filter 'while read cmtline; do echo ${cmtline#provision:}; done' -- --all
```
remove remote-only branch (e.g. `remote/origin/branch-name`)

```
# use git branch -r for remote-only branches listing
git branch -d -r branch1 branch2
```

search commit messages:

```
git log --grep
```

search in diffs:

```
git log -Sgovnocode-as-string
git log -Ggovnocode-as-regex
```