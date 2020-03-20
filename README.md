# Git Commit Hook Demo

## What
This project is an example of a git commit-msg hook.

If Git sees file `.git/hooks/commit-msg` in its repository tree,
it will execute it, passing an argument based on the contents
of file `.git/COMMIT_EDITMSG`. That file contains your commit
message appended to a bracketed branch name ID. It acquires appended 
counts changes, insertions, and deletions.

## Trivial `commit-msg` Hook:
 
Create  `.git/hooks/commit-msg` in this project. Give it the
following contents:

```shell script
#!/usr/bin/env bash

echo "Commit message: " $(cat %1)
```

## Try It

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

    I'm committed
```

A smarter `commit-msg` could prepend a JIRA issue number to 
that commit message, or something equivalent for your Agile process.

### Using bash or sh
The `commit-msg` file must be marked executable. It must have the
usual UNIX shell shebang language indicator. Ours uses `bash`.
If the OS is Windows, Git will execute the file via the `gitbash`
shell. 

### Using a Python `commit-msg` on Windows n
If the script language were python, resident on a MS Windows, the 
script header would likely need to be `winpty`, passing python 
and `$1` arguments.

Search the web literature for more information about this 
Windows-meets-UNIX case.


