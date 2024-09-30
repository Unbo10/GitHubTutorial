<h1>Git and GitHub Tutorial</h1>

In this document you'll find a tutorial on how to use Git and GitHub.

<h2>Why bother on learning them?</h2>

As a programmer, developer or code enthusiast, at some point, you have changed or will have to change your code and suddenly it doesn't work. You try multiple fixes that should solve the issue you're having, yet nothing works. You're stuck...

Then you remember `Ctrl + Z` or `Cmd + Z` exists, and you try to go back to that one version of your code that was working perfectly fine. However, to your disappointment, it unly undoes so far, and you cannot reach the desired version...

But wait, there is a light at the end of the tunnel: your team members may have saved the correct version of the code you're looking for. You ask them, and they do have it!!! Nonetheless they are using Git and GitHub, that stuff you never bothered to learn for whatever reason.

If you find yourself in this situation or you want to learn how to improve your life, keep reading.

<h2>What is Git?</h2>

Git is a version control system. It keeps track of how a directory evolves in something called a repository (or repo for short), which stores the versions of the directory, metadata and other stuff. In other words, it's like if you had another directory filled with copies of the directory you want to keep track of.

But wait, there is more. There are two distinctive features of Git that make it so appealing:

> - On one hand, it doesn't just copy entire directories every time it records a new version of the directory. Instead, it only saves the changes or deltas made to each file in every version.
> - On the other hand, it has something called branches, which allow you to work on multiple things separetely. 

Let's dive in a bit more on what exactly are branches.

<h3>Branches: Git's cherry</h3>

Suppose you're working on a project whose structure looks like this:

amazing_project/
├── app.py
├── database.db
└── README.md

So far, you've been working on the `app.py` and `README.md` files and they work just fine. However, you now want to play around with the `database.db` file, but you're afraid of breaking it. What do you do?

Well, my friend, you create a branch. A branch is a separate and parallel version of your repo, sort of like a copy of it within itself. In it, you can try new things and experiment without worrying about breaking the main version of your repo. Now, here is the thing: if the version on the branch works, you can merge it back to the main version. If it doesn't, you can just delete the branch and nothing will be affected.

Put in other words, if your directory was your room, each branch would be an exact copy of it that you can modify as you please; you could make it look like fire or set it on fire (don't try this at home), it doesn't matter because your room will remain the same. However, if you do like the changes you made, you can make your room look like the copy you made.

Quite powerful, isn't it? But what if you could share your project with others and work on it together? After all, multiple minds are better than one. Just imagine sharing your room with anyone you want and making it look as you please. That's where GitHub comes in.

<h2>What is GitHub?</h2>

We already saw what Git is, but what is a hub?

> A hub is a place where multiple things come together. It allows multiple things to connect and interact with each other.

Using that and what we know about Git, we can infer that GitHub is a place where multiple Git repositories come together. However, repos do not interact with each other, but the owners, maintainers and contributors of them do.

Overall, it is a website where you can store your repos and share them with others. In addition, it has other software tools that make it easier to publish projects, collaborate with others and manage your work.

<h2>How to use Git and GitHub?</h2>

Now that you know what Git and GitHub are, let's see how to use them.

<h3>Installing Git</h3>

Git isn't installed by default on most operating systems, so you'll have to install it yourself. You can download it from the [official website](https://git-scm.com/).

When you're think you're done, you can type in your therminal the command `git --version` to check if it was installed correctly. It should appear something like `git version 2.34.1`.

<h3>Setting up Git</h3>

Before you start using Git, you need to set up your identity. This is stored in the metadata of your repo, and it's used to identify who made the changes in each version.

To do so, you can use the following commands:

```bash
git config --global user.name "Your username"
git config --global user.email "youremail@something.something"
```

You **do not** need to use your real name or your personal email, just an email you have access to.

<h3>Creating a repository</h3>

Okay, finally we're getting to the fun part. To create a repository, you need to first be in the directory you want to keep track of. Afterwards, you should open a terminal in the directory and type the following command:

```bash
git init
```

The output of this command should be something like this:

```
Initialized empty Git repository in /Path/To/Your/Directory/.git/
```

This means a hidden directory called `/.git` has been created in your repository. This directory is where Git stores all the metadata and versions of your directory.

If you access it (using a command like `cd .git/`), its structure should look like this:

```
.git/
├── branches/
├── config
├── description
├── HEAD
├── hooks/
├── info/
├── objects/
└── refs/
```

You may also see `.` and `..` directories, which are used to navigate directories in Unix-like systems (so ignore them).

You can take a look at the contents in each of the files and directories, but for now, let it be as it is (this is honestly because I am not even sure what some of them do, although it seems something fun to explore).

<h3>Adding files to the repository</h3>

If you already had files in your repository, that's perfectly fine. In this repo, for example, I already had a `README.md` file created. However, if you don't have any, you can try for now to uderstand the basics by just adding a `README.md` file. You can do so by typing the command `touch README.md` in your terminal or by using your system's file explorer.

Now, before 

You may want to type "Hello, world!" or something in your `README.md` file, but just adding it should be enough for git to recognize an untracked file. Don't believe me? You can run the command `git status` in your terminal to see what files are being tracked and what aren't. You should see something like this:

```
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```

Note: If the `README.md` file doesn't appear colored, you can run the command `git --global color.ui auto` to enable colors in your terminal.

The message means you haven't asked Git to track the file yet. To do so, you can use the command `git add README.md`. This won't show any output, but if you run `git status` again, you should see something like this:

```
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
```

> Pro tip: If you want to stage the changes made in all the directories and files in your repository, you can use the command `git add -A`.

This means the file is now being tracked by Git, or, in other words, you have staged the changes to the file (creating it and modifying it if you had written something in it). In fact, you can set the alias `git stage` to `git add` by running the command `git config --global alias.stage add`, if you want to make more clear what you're doing (esentially, they mean the same).

Now, you may be wondering what's with the "On branch main" message. For now, don't worry about it, but just now the branch `main` won't be accessible until you make your first commit, which is what we are going to do next.

<h3>Committing changes</h3>

Committing changes means saving to the repo the changes staged. If you only stage your deltas or changes, Git won't make a new version of the directory until you commit them. To do this, you can use the command `git commit -m "Your message here"`. The `-m` flag is used to add a message to the commit, which is used to describe what changes were made in that version of the directory. You can add as many messages as you want, but usually two `-m` flags suffice to give a title of the changes and a brief description of them.

Note: if you're curious, you can modify the file and run the command `git status` to see what happens. You might notice the file is staged as both staged and not staged. This is because from the moment you staged the file to now, there has been a delta or change in the file that hasn't been staged yet. This means you could commit a previous version of a file unintentionally, so be careful (if that's the case, you can stage the file again).

For example, you can run the command `git commit -m "Add README.md" -m "Add a README.md file to the repository"` (to write it in imperative is the standard) to commit the changes made to the `README.md` file. The output should be something like this:

```











