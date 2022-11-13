# Git

## Contents
1. ![What is Git and how does it work?](https://github.com/S010MON/git-workshop/edit/main/README.md#1-what-is-git-and-how-does-it-work)
2. ![How can you use Git as an individual on your projects?](https://github.com/S010MON/git-workshop/edit/main/README.md#2-how-can-you-use-git-as-an-individual-on-your-projects)
3. ![Basic Git commands in the terminal](https://github.com/S010MON/git-workshop/edit/main/README.md#3-basic-git-commands-in-the-terminal)
4. Connecting to GitHub in the terminal
5. Using IntelliJ IDEA with Github.
6. How can you use git in group projects?

## 1. What is Git and how does it work?
Git is a Version Control System (VCS) that is used to modify software to try out changes without losing the original working version.  Git works using a graph implementation:

Here we have some software that we have built until point A.
```
A *
```

Normally we would develop this until a point B, changing the code at each stage until B might not be recognisable as the same code:
```
A *
  |
  |
  |
B *
```

Now if we realise that B doesn't work, we can `ctr-z` our way back, but if we made three changes, and only the first was bad, then we have lost all of our progress.  Git allows us to **CHECKOUT** a branch (a new copy of the code) so that we can work on that, while keeping the original saved.

```
A *
  | \
  |  |
  |  |
  *  * B
```

Once we are done with development and testing, we can **MERGE** the two branches together:
```
A *
  | \
  |  |
  |  |
  | /
  * B
```

## 2. How can you use Git as an individual on your projects?
For individual work, this can be very useful, whenever you make significant changes, commit (i.e. save) your work and you will create snapshots in time that will give you points where you can return to without having to remember all the changes you made.  We can add messages to each commit that helps us understand code changes easily:

```
A * : Initialse project
  | 
B * : Add feature 1
  |
C * : Add feature 2
  |
D * : Fix bug in feature 1
```

Additionally, if you're doing something extremely experimental, that might not work, you can make a branch to test out on, and if it fails, just abandon it!

```
A * : Initialse project
  | \
  |   \
  |    | 
  |  B * : Add feature 1
  |    |
  |  C * : Add feature 2
  |    |
  |  D * : Didn't work ... fuck it!
```

## 3. Basic Git commands in the terminal
Git was built by Linus Torvalds (of linux fame) and is available on the terminal of all major operating systems.  Many IDEs have support inbuilt, and there are desktop Git editors that you can use.  However they all use the underlying terminal implementation.  It is very useful to first learn how to work with the Git terminal, because it is far more powerful than most editors, and if a language (like MATLAB) doesn't support Git natively, you can just use it in the terminal.

There are 4 main commands you should learn:
*note: for these examples I'm showing what it would look like for a linux terminal (`user:~$` which I have shortend to `$` you may have something else for windows such as `C:\Users\name>` so please don't include the $ in your commands!*

#### init
Any folder can become a git folder with `init`.  You simply need to navigate to the folder in the terminal and run:
```bash
$ git init
```

#### status
Now that you have a git folder, you can check on the staus of the folder using `status`.  This will show you what changes are being tracked, and what is being ignored by git:
```bash
$ git staus
```
The ouput should look like this:
![](https://github.com/S010MON/git-workshop/blob/main/images/status-untracked.png)

#### add
If we have changed a file we need to track its changes to confirm that they are to be tracked by Git.
```bash
$ git add [file_name]
```
The image below shows that the file we saw earlier is now tracked and shows up in green:
![](https://github.com/S010MON/git-workshop/blob/main/images/status-tracked.png)

Why don't we track all the files?  We if we compiled our Java code into a `.class` file, we don't want to record that.  It's a binary and not soruce code, so we can just recompile everything when we change the source anyway.  So make sure you select the right files to track when you have something like the below:
![](https://github.com/S010MON/git-workshop/blob/main/images/status-class-files.png)

#### commit
To save our changes we use the `commit` command to save the state of the system at the current point.  You must add a message to all commits and you can do this using the `-m` tag.  IF you forget you will get a text editor pop-up that will ask you to add a message.  
```bash
$ git commit -m [MY_MESSAGE_FOR_THIS_COMMIT]
```
To use the `-m` tag, add a message in quotes like this:
![](https://github.com/S010MON/git-workshop/blob/main/images/commit.png)
