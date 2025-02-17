## February 20th

### Git, Github, HTML Basics

#### Github, Terminal, Class Files

- Now, that we are set up, let's setup your class repository.

- Open Terminal on Mac, or the Command Line on Windows:

  - List the current files and folders in your current directory:

  OSX:

  ```
  ls
  ```

  Windows:

  ```
  dir
  ```

  **note - all of these commands are executed by the enter key. So if you see a series of commands in a row, assume you hit enter after each individual command**

  The terminal should list out the file system at the root of your computer. We can move in and out of folders using `cd` which stands for change directory. cd is always followed by the folder or route you wish to move to. For example. When I open terminal, and type `ls` I can see a Desktop and a Documents directory along with many others. If i wish to navigate to my Desktop and type:

  ```
  cd Desktop
  ```

  and then `ls` on Mac or `dir` on Windows the command line will print out the current files and folders on my desktop.

  If we need to jump back out of a folder using the command line, we can type

  ```
  cd ../
  ```

  Now if we list the contents of our current directory, we will see we have moved back into the parent folder. Lets take a moment to practice moving around our computers file system using `cd` and reading out contents using `ls` or `dir`.

  On your desktop create a folder for this course (You are welcome to do all of this to your Documents folder instead).

  While signed in to Github. Go to your account page and click the `Repositories` tab.

- Click New
- Name it something unique but descriptive (or you can name it GITHUBUSERNAME.github.io to set up your server)
- Feel free to edit the READEME.md with a longer description
  - Click the Clone/Download Button in the upper right (just like we did for the class files)
- In terminal, navigate to the folder we made earlier for you class files. :

```
cd WebDevStuff
```

**IMPORTANT**- note that we are in the Class Files folder you made!

We are going to clone you HW directory into the `WebDevStuff` folder. You will take notes, make edits and push your HW assignments to YOUR HW REPO.

You have created a repo on GitHub for your HW. Navigate to it, grab to the clone url from the `Clone or Download` button. Make sure you are in your WebDevClassFiles folder, then type:

```
git clone [your clone url copy paste here]
```

**Pro Tip: You can type cd + [Space] and then drag and drop any folder into your terminal window and it will automatically populate with that directory's location.**

### Adding and Editing Files, Pushing and Committing Changes.

Every week, you will be committing files and folders to your HW repo, and pushing them to your online GitHub repo for me to review. This is how you will submit your HW code.



- Lets open your repo in VS Code and create a new subfolder called `Hello World`
- Next, create a file named README.md in the Hello_World folder
- Open the file, type anything you like (Keep in mind this will be published on GitHub in a few minutes. So keep it professional.) And save the file.

- Back in terminal, navigate to your HW repo folder.

- Use `ls` or `dir` to make sure you are in the correct folder.

In terminal

```
git status
```

You should now see a list of files and folders that git is not keeping track of yet. In our case is would be Hello_World/ and the README.md within. To add the current state of this file and folder we use `git add` + `file or folder name`.

```
git add Hello_World
git add Hello_World/README.md
```

or if we want to add any and everything new or updated to git :

```
git add *
```

Now we commit with a message:

```
git commit -m "Initial Commit, In class exercise"
```

Finally, we need to `push` our local repos changes to our GitHub repository.

```gi
git push
```

Take a look at your online repo. It should match your local computers if you used ` git add` `git commit` and `git push` correctly.

_Helpful Resources_

- [Command Line Cheat Sheet Windows](http://simplyadvanced.net/blog/cheat-sheet-for-windows-command-prompt/)
- [Terminal Cheat Sheet Mac](https://github.com/0nn0/terminal-mac-cheatsheet)
- I will be teaching on a MAC, for the terminal/command line equivaltents see this [handy article](http://skimfeed.com/blog/windows-command-prompt-ls-equivalent-dir/).


### Bonus: 
#### What if we want to add an exisiting project from our local computer to a GitHub Repository?

- follow the instructions above to create a new online repository on GitHub.

- in terminal/command line execute the following commands:

```
cd [your local folder here]
git init
git add .
git commit -m "initial commit"
git remote add origin https://github.com/USERNAME/REPONAME.git
git branch -M main
git push -u origin main

```

_a tutorial on how to do this is generated when you create an online repo on Github_

You can also [follow the tutorial here](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/)