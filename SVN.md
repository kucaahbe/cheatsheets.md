### update

```
svn update
```

### status

```
svn status
# or
svn st
```

### diff

```
svn diff
```

### create tag

```
svn copy trunk tags/18.0.2
# then commit it:
svn commit
```

remove (also works for empty directories)

```
svn rm PATH
```

show all svn:ignore

```
svn propget -v -R svn:ignore
```

### Reset all local changes

```
svn revert . —depth=infinity
```