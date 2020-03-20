# Git Commit Hook Demo

## What
This project is an example of a git commit-msg hook.

If Git sees file `.git/hooks/commit-msg` in its repository tree,
Git will execute it, passing an argument path to file 
`.git/COMMIT_EDITMSG`. That file contains the commit
message. 

## Trivial `commit-msg` Hook:
 
Create  `.git/hooks/commit-msg` in this project. Give it the
following contents according to your operating system:

### Mac OS

The sed command acts uniquely in Mac OS.

```shell script
#!/usr/bin/env bash

OLD_MSG=$(cat $1)
NEW_MSG="Commit message: $OLD_MSG"

sed -i '' -e  "s/.*/$NEW_MSG/g" $1
```

### Linux or Windows

```shell script
#!/usr/bin/env bash

OLD_MSG=$(cat $1)
NEW_MSG="Commit message: $OLD_MSG"

sed -i  "s/.*/$NEW_MSG/g" $1
```



## Try It

1. open a terminal/command window on this project
1. edit the contents of a victim file, such as `file.txt`
1. commit it ...
  
```shell script
git add file.txt
git commit -m "I'm committed"
```

Note the console:

```text
[master 0f97fc6] Commit message: I'm committed
 1 file changed, 1 insertion(+)
```

Check the Git log:

```shell script
git log

commit 0f97fc6ad7654162faaf21a2993d8e32e14ac0d1 (HEAD -> master)
Author: mauget <mauget@gmail.com>
Date:   Fri Mar 20 11:19:08 2020 -0400

    Commit message: I'm committed

commit dc941c0d1d6150eda0955f13d50
```

## Notes

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


