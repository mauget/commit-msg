# Test Project for Testing Git Commit Hook

## What
This project is an example of a git commit-msg hook

## Lab

Touch this README.md file, then commit it, supplying your commit message.
  
```shell script
git add *
git commit -m "I'm committed"
```

Note the console message.

```text
Commit message: 
[master fce9496] I'm committed
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Check the Git log:

```shell script
git log

commit fce9496125bda9abbad8d74deca5da53f4f0d288 (HEAD -> master)
Author: mauget <mauget@gmail.com>
Date:   Thu Mar 19 19:51:27 2020 -0400

    Test 4
```

A smarter `commit-msg` could prepend a JIRA issue number,
or the equivalent, to that commit message.

## Source of Simple `commit-msg` Hook:

If Git sees file `.git/hooks/commit-msg` in its repository tree,
it will execute it, passing an argument based on the contents
of file `.git/COMMIT_EDITMSG`. This file contains your commit
message appended to a bracketed branch name ID. It has appended 
counts changes, insertions, and deletions. 

```shell script
#!/usr/bin/env bash
echo "Commit message: " $(cat %1)
```

### Using bash or sh
The `commit-msg` file must be marekd executable. It must have the
usual Unix shebang language indicator. Ours uses `bash`.
If using Windows, Git will execute the file from the `gitbash`
shell. 

### Windows
If the script language is python resident on a Windows OS, the 
will need to invoke `winpty` passing python and `$1` arguments.
Search for more information in this case.


