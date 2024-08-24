# [**Git & GitHub Crash Course For Beginners**](https://www.youtube.com/watch?v=SWYqp7iY_Tc)

Author: IxxI5

## Table of Contents

- [Step 1 - WHAT IS GIT?](#step-1---what-is-git)
- [Step 2 - CONCEPTS OF GIT](#step-2---concepts-of-git)
- [Step 3 - BASIC COMMANDS](#step-3---basic-commands)
- [Step 4 - INSTALLING GIT](#step-4---installing-git)

### [**Step 1 - WHAT IS GIT?**](#table-of-contents)

**Version Control System (VCS) for tracking changes in computer files**

&check; Distributed version control

&check; Coordinates work between multiple developers

&check; Who made what changes and when

&check; Revert back at any time

&check; Local & remote repos

### [**Step 2 - CONCEPTS OF GIT**](#table-of-contents)

&check; Keeps track of code history

&check; Takes "snapshots" of your files

&check; You decide when to take a snapshot by making a "commit"

&check; You can visit any snapshot at any time

&check; You can stage files before committing

### [**Step 3 - BASIC COMMANDS**](#table-of-contents)

```python
git init            """Initialize Local Git Repository"""
git add <file>      """Add File(s) To Index"""
git status          """Check Status Of Working Tree"""
git commit          """Commit Changes In Index"""
git push            """Push To Remote Repository"""
git pull            """Pull Latest From Remote Repository"""
git clone           """Clone Repository Into A New Directory"""
```

### [**Step 4 - INSTALLING GIT**](#table-of-contents)

&check; Linux (Debian)

```
$ sudo apt-get install git
```

&check; Linux (Fedora)

```
$ sudo yum install git
```

&check; Mac

```
http://git-scm.com/download/mac
```

&check; Windows

```
http://git-scm.com/download/win
```

**VS Code Command Prompt**

```python
git --version           """git version 2.41.0.windows.1"""
```

### [**Step 5 - EXERCISING WITH GIT**](#table-of-contents)

**VS Code Command Prompt or (Windows Command Propmpt)**

```python
mkdir myapp             """create the folder /../myapp"""

cd myapp                """go to myapp folder"""

type nul > index.html   """create the file /../myapp/index.html"""

type nul > app.js       """create the file /../myapp/app.js"""

"""
The system cannot find the file specified.

Note: Ignore the message (however the files have been created)
"""
```

Add the following content into /../myapp/index.html

```html
<html>
  <head>
    <title>My App</title>
  </head>
  <body>
    This is my app
  </body>
</html>
```

```python
git init                """initialize empty Git repository in ../myapp/.git/"""
```

Resulted Structure:

```
myapp (master or main)
│
├── .git
├── app.js
└── index.html
```

Configure the git:

```
git config --global user.name "John X"

git config --global user.email "johnx7778@gmail.com"
```

Add index.html to the created git repository:

```python
git add index.html      """add (stage) index.html in git repository"""
```

```python
git status
"""
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        app.js
"""
```

Unstage from git (not include it on next commit):

```python
git rm --cached index.html
"""
rm 'index.html'
"""
```

```python
git status
"""
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        app.js
        index.html

nothing added to commit but untracked files present (use "git add" to track)
"""
```

```python
git add .                  """add (stage) all files to git repository"""
```

```python
git status
"""
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   app.js
        new file:   index.html
"""
```

Add an ! (exclamation mark) at the end of the body in index.html:

```html
<!-- -->
<body>
  This is my app!
</body>
<!-- -->
```

```python
git status
"""
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   app.js
        new file:   index.html

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   index.html
"""
```

```python
git add .                  """add (stage) all files to git repository"""
```

```python
git status
"""
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   app.js
        new file:   index.html
"""
```

Commit all staged files (git add .) in git repository:

```python
git commit -m "Initial commit"
"""
[main (root-commit) 70d62a8] Initial commit
 2 files changed, 8 insertions(+)
 create mode 100644 app.js
 create mode 100644 index.html

 Note: The "-m" option allows you to write the message in-line with the "commit" command.
"""
```

```python
git status
"""
On branch main
nothing to commit, working tree clean
"""
```

Edit the app.js file by adding the follow:

```javascript
console.log("Hello");
```

```python
git status
"""
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   app.js

no changes added to commit (use "git add" and/or "git commit -a")
"""
```

```python
git add .                  """add (stage) all files to git repository"""
```

```python
git commit -m "Changed app.js"
"""
[main d8b081b] Changed app.js
 1 file changed, 1 insertion(+)
"""
```

Create the .gitignore file (to ignore files and folders from being staged):

```python
type null > .gitignore     """create the .gitignore file"""
"""
The system cannot find the file specified.

Note: Ignore the message (however the file has been created)
"""
```

Create the log.txt (that is usually ignore from being staged):

```python
type null > .gitignore     """create the log.txt file"""
"""
The system cannot find the file specified.

Note: Ignore the message (however the file has been created)
"""
```

Add the following text into log.txt:

```
error logs
```

Add the following into .gitignore:

```
log.txt
```

Then, execute:

```python
git add .                  """add (stage) all files to git repository"""

git status
"""
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   .gitignore

Note: log.txt was ignored (not staged)
"""
```

Create the dir1, dir2 directories and app1.js, app2.js files :

```python
mkdir dir1              """create the folder /../myapp/dir1"""

mkdir dir2              """create the folder /../myapp/dir2"""

cd dir1                 """go to dir1"""

type null > app1.js     """create the /myapp/dir1/app1.js file"""

cd..                    """go back to myapp directory"""

cd dir2                 """go to dir2"""

type null > app1.js     """create the /myapp/dir2/app2.js file"""

cd..                    """go back to myapp directory"""
```

Add the following into both app1.js and app2.js:

```javascript
console.log("123");
```

Add the "/dir2" into .gitignore:

```
log.txt
/dir2
```

```python
git add .                  """add (stage) all files to git repository"""

git status
"""
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   .gitignore
        new file:   dir1/app1.js

Note: dir2 folder was also ignored (not staged)
"""
```

Create a new branch (login) to add some fake login functionality to your app :

```python
git branch login           """create the branch login"""

git status
"""
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   .gitignore
        new file:   dir1/app1.js

Note: It shows the status on main and not on login branch
"""

git commit -m "another change"
"""
[main 590b99f] another change
 2 files changed, 3 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 dir1/app1.js

Note: The files are committed to main branch
"""

git checkout login         """switch to login branch"""
"""
Switched to branch 'login
"""
```

Branches resulted structure:

```
myapp (main)
│
├── .git
├── dir1
├── dir2
├── app.js
├── index.html
└── log.txt

myapp (login)
│
├── .git
├── dir2
├── app.js
├── index.html
└── log.txt
```

Create the file login.html (add the text login into it) into login branch:

```python
type null > login.html     """create the /myapp/login.html file"""

"""
Note: We have switched to login branch
"""

dir
"""
29.06.2023  16:14    <DIR>          .
29.06.2023  16:14    <DIR>          ..
29.06.2023  15:06                23 app.js
29.06.2023  15:41    <DIR>          dir2
29.06.2023  14:51               107 index.html
29.06.2023  15:32                10 log.txt
29.06.2023  16:14                 0 login.html
               4 File(s)            140 bytes
               3 Dir(s)  927’496’712’192 bytes free
"""
```

Modify the index.html (login branch) as follow:

```html
<body>
  This is my app! Login Form
</body>
<!-- -->
```

Then:

```python
git add .                  """add (stage) all files to git repository"""

git commit -m "login form"
"""
[login dbc6f95] login form
 3 files changed, 3 insertions(+)
 create mode 100644 dir2/app2.js
 create mode 100644 log.txt
 create mode 100644 login.html
"""

git checkout main
"""
Switched to branch 'main'
"""
```

Branches resulted structure:

```python
myapp (main)
│
├── .git
├── dir1
├── .gitignore
├── app.js
├── index.html

myapp (login)
│
├── .git
├── dir2
├── app.js
├── index.html
└── log.txt
└── login.html

"""
Note: In main branch the index.html does not have the text "Login Form" as also the file login.html is not present (since it was created just for the login branch)
"""
```

Now to merge the login with the main branch, we have to be in main branch, first:

```python
git merge --no-ff -m "Added login feature" login
"""
Merge made by the 'ort' strategy.
 dir2/app2.js | 1 +
 log.txt      | 1 +
 login.html   | 1 +
 3 files changed, 3 insertions(+)
 create mode 100644 dir2/app2.js
 create mode 100644 log.txt
 create mode 100644 login.html
"""
```

**Github account**: Create a new remote repository in Github and then execute the following (while being in main branch):

```python
git remote add origin https://github.com/IxxI5/myappsample.git

git remote
"""
origin
"""

git push -u origin main
"""
Enumerating objects: 19, done.
Counting objects: 100% (19/19), done.
Delta compression using up to 4 threads
Compressing objects: 100% (11/11), done.
Writing objects: 100% (19/19), 1.44 KiB | 295.00 KiB/s, done.
Total 19 (delta 3), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (3/3), done.
To https://github.com/IxxI5/myappsample.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.

Note: myapp now has been pushed (uploaded) to remote github repository
"""
```

Create a README.md file:

```python
type null > README.md
```

Add the following text into README.md:

```
# My App

This is my app
```

Then:

```python
git add .                  """add (stage) all files to git repository"""

git commit -m "Added readme"
"""
[main 7b2f007] Added readme
 1 file changed, 3 insertions(+)
 create mode 100644 README.md
"""

git push                    """push the file to github remote repository"""
"""
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 290 bytes | 290.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/IxxI5/myappsample.git
   8c95426..7b2f007  main -> main
"""
```

In order to clone from the remote github repository to your local machine, create a folder somewhere (not in myapp) in your hard drive:

```python
Go to Public Documents

mkdir myapp2            """create myapp2 folder in Public Documents"""

cd myapp2               """go to myapp2 folder

git clone https://github.com/IxxI5/myappsample.git

Cloning into 'myappsample'...
remote: Enumerating objects: 22, done.
remote: Counting objects: 100% (22/22), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 22 (delta 4), reused 22 (delta 4), pack-reused 0
Receiving objects: 100% (22/22), done.
Resolving deltas: 100% (4/4), done.
"""
```

Update (with the latest changes) the cloned repository:

```python
cd myappsample

git pull
"""
Already up to date.
"""
```

## License

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)

Copyright (c) 2015 Chris Kibble

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.