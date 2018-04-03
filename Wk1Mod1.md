# CLIs, `git`, GitHub, and "Hello, World"
## Welcome to the first class!

### Housekeeping

To get things started, we need to download a few things for our __development environment__. These include the following:

1. An OS-specific package management system
2. A bash-friendly command-line interface
3. Version control systems
4. A text editor
5. Helpful editor plugins
6. Slack!

The process for each of these things should depend a bit on your operating system, but should help us work together in a consistent environment for the rest of the course.

You'll also need a few online accounts to get started. These should _all be tied to the same email address_! These external accounts include:

1. Slack
2. GitHub
3. Netlify

We'll set them up together as we work through tonight's materials.

### Building a Dev Environment

Whenever we work on a project, we want to make sure that we are using a consistent set of tools. But installing those tools in a way that is consistent is a tough problem! To help out with installing the pieces of our development environment, we rely on package managers to help us maintain a consistent set of __environment dependencies__.

> ENVIRONMENT DEPENDENCIES are programs that we depend on to help us create software in our development environment

Because each operating system is so different, we'll need to install a different command-line package manager for each OS (more on the "command-line" in a minute). They are:

#### Linux
  + all Ubuntu-flavored distributions ship with `apt`, which will work perfectly out-of-the-box!
  + Arch Linux comes with `pacman`, and it's a good idea to add [`yaourt`](https://www.ostechnix.com/install-yaourt-arch-linux/) as well.
  + RPM-based distributions should use `yum`

#### macOS
  + [Homebrew](https://brew.sh/) is the package manager of choice for macOS
  + to install, open up the `Terminal` application from Finder
  + copy this command : `curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install`
  + paste it into your terminal after the `$` like in the example below:

 __Johns-Macbook-Pro:~ John$__ _curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install_

  + ...then just follow the prompts to install!

#### Windows
  + [Chocolatey](https://chocolatey.org/install) is the package manager of choice for Windows.
  + To install, open the PowerShell application as an administrator, you do this by right clicking PowerShell and selecting  __Run as administrator__:<br><img src="https://www.isumsoft.com/it/wp-content/uploads/2016/04/run-powershell-as-admin.jpg" width="400" height="400" alt="PowerShell admin image" />
  + then copy the following command below and paste it into PowerShell to install Chocolatey:

  `Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))`

__Just a heads up, the command above is only one command, so please copy the entire thing. Thanks!__

### Interfacing with Computers

The operating system is the program (a series of instructions) that runs when you turn on your computer. It handles inputs (keyboard, mouse, camera, network connections) and outputs (monitor, speakers, network connections), manages shared access to computing resources and memory, and reads and writes data to the file system on behalf of any number of simultaneously running applications (web browser, code editor, text document, music player, etc). We interact with the computer through the operating system, usually by TYPING, TOUCHING, or CLICKING.

Computers can receive user input through either a command line interface (__CLI__) or a graphical user interface (__GUI__). In a command line interface (A.K.A. "Console", "Terminal", or "Shell"), the user types commands using the keyboard to tell the computer to take an action. The computer will display the results of the operation by writing text to the screen.

![Command-Line GIF](http://reactorprep.herokuapp.com/assets/images/cli.gif)

__GOAL FOR THE COURSE__: All navigation should be done using **words** instead of **pictures**.

> "When I was a child, I used a computer by looking at the pictures. When I grew up, I learned to read and write."
> -William Shotts, Jr.
> Linux Command.org

There are lots of applications that are built to be a command-line interface. Many of them are specific to different operating systems. The most commonly-used CLIs are based on the Unix shell, and there are a number of options available for each operating system.

#### Linux (all distributions)
  + Built-in Desktop Environment Terminals (Konsole, GNOME shell, etc.)
  + Termite, Terminator, Tilda, etc.

  __to install__:

  If you're using Linux, you already have a unix-style terminal installed! Any will do for this course, but you may use your distribution's package manager to install another if you're so inclined.
 
#### macOS
  + iTerm2

  __to install__: _(copy and paste the command below into your terminal)_

  `brew cask install iterm2`

#### Windows
  + Linux Subsystem for Windows terminal
  + PowerShell
  + git bash

  __to install__:

  If at all possible (on an updated Windows 10 machine) install the [Linux Subsystem on Windows](https://msdn.microsoft.com/en-us/commandline/wsl/install-win10). This gives you access to most of the functionality of a Linux system called Ubuntu, which includes a wonderful terminal emulator and package manager.

  However, this can be time-consuming to install, so we will get started tonight with the Git Bash terminal that's packaged with `git`, our version control system. We'll download that with the following code in PowerShell to get us started: _(copy and paste the command below into PowerShell)_ 

  `choco install git -params '"/GitAndUnixToolsOnPath"'`


> __NOTE__: From here on out, we'll use the terms `terminal`, `command-line`, and `CLI` interchangeably

---

#### EXERCISE 1

We will start out by using the CLI to navigate through the file system on our personal computers. The key is to think of the directory structure as a 'tree' with 'branches', rather than a bunch of 1s and 0s stored in memory. The OS abstracts all of that memory management away, so you and I can work directly with the human-facing interface we call a file structure.

1. Open up your terminal of choice and type in `pwd`. What do you see?
2. Make a note of that folder's location, then repeat the process with your CLI
   1. print your starting location: `pwd`
   2. list the file structure: `ls`
   3. change directories: `cd`
   4. move up a directory: `cd ..`
   5. move to your `$HOME` directory: `cd ~`
3. In your `$HOME` directory (`~`), create a folder called `Code` for all of your future coding projects. You can do that with the `mkdir` command (e.g. `mkdir ~/Code`)
4. Inside of `Code`, create a `SavvyCoders` directory for all of your Savvy-related work! You can do that with the `mkdir` command (e.g. `mkdir ~/Code/SavvyCoders`).

---

### More Environment Tools

Beyond a package manager and CLI, we need a few more tools to help us work more efficiently.

#### Git
As developers, we can't manage file saving (_a.k.a._ version control) the same way as everyone else. We need a command-line program called `git` to help us out! You can install `git` through your operating systems's package manager, e.g.: (Copy and paste the command below into your CLI according to your OS)

  + __Linux__: `sudo apt install git` __or__ `sudo pacman -S git`
  + __macOS__: `brew install git`
  + __Windows__: `choco install git -params '"/GitAndUnixToolsOnPath"'` (this should already be installed)


#### Atom
The text editor that we'll be using for this course is called [Atom](https://atom.io). It's a modular editor built for web development, maintained by GitHub, and contributed to by a large Open Source community. (Copy and paste the command below into your CLI according to your OS)

  + __Linux__: `sudo apt install atom` __or__ `sudo pacman -S atom`
  + __macOS__: `brew cask install atom`
  + __Windows__: `choco install atom`

Once you've installed Atom, you should be able to open it from the Start Menu (or Finder). Then, follow these steps to install a few helpful packages/extensions to Atom!

1. Open up the Settings in Atom (File > Settings or `ctrl + comma`) <br><img src="https://flight-manual.atom.io/getting-started/images/settings.png" width="500" height="400" alt="Atom settings" />
2. Go to '+ Install' and install the following packages:
   1. [atom-live-server](https://atom.io/packages/atom-live-server)
   2. [emmet](https://atom.io/packages/emmet)
   3. [file-icons](https://atom.io/packages/file-icons)
   4. [javascript-snippets](https://atom.io/packages/javascript-snippets)
   5. [linter-eslint](https://atom.io/packages/linter-eslint)
3. If you're on macOS, install shell commands (Atom > Install Shell Commands) <br><img src="https://cdn-images-1.medium.com/max/1200/1*1s3vPJrUXPgozK5cJc0UFw.png" width="500" height="400" alt="Atom install shell commands" />
4. Restart Atom
---

#### EXERCISE 2
1. Navigate to your `SavvyCoders` directory using your CLI
2. You can open specific directories in Atom using the `atom` command from your command line! Once you have navigated to the `SavvyCoders` directory, you can open its folder using the command `atom .`
3. Also in your CLI, use the command `touch haiku.txt` to create a new text file named `haiku.txt` inside of `SavvyCoders` directory.
4. Write a short haiku using Atom! (And don't forget the __5-7-5__ syllable structure):

  ```
  Haikus are easy,
  But endings are difficult.
  Refrigerator.
  ```

---

### Markdown

Formatted text is nice, but clicking buttons will never scale. We need to be able to programmatically describe how we want our text processed.

Markdown is a markup language. Markup languages mix in special sequences of coded characters to specify the intended layout and style of their text.

Copy this Markdown code into your Atom code editor and search for 'markdown preview' to have it parsed and rendered:

```markdown
# This is a header
## This is an even smaller header
### Even smaller...
###### Quite small

Here is some normal text. A paragraph, even!

*This text is in italics.*

**This text is in bold.**

***This text is in both.***

~~This text is rendered with strikethrough.~~

Sometimes you want to embed some \*stylized text\*
right into **your paragraph.** Pretty cool, right!

**Below you see different options for making an unordered list (bullet points):**
* Item
* Item
* Another item

or

+ Item
+ Item
+ One more item

or

- Item
- Item
- One last item

**Below you see a way to create an ordered list**

1. Item one
2. Item two
3. Item three

**Below you see a way to create an ordered list with a sub-list**

1. Item one
2. Item two
3. Item three
    1. Sub-item
    2. Sub-item
4. Item four

**Below you see a way to create a horizontal rule**
---

**Below you see a way to create a link to a web page** 
[I'm a link to a web page!](http://www.google.com)

**Below you see a way to add an image from a web page**
![alt text](https://i.imgur.com/81qyN1y.jpg)

**Below you see a way to add an image from your local directory**
![local photo](assets/profile.png)
```

#### EXERCISE 3

1. Now it's time to format haiku.txt with Markdown! Let's move `haiku.txt` to a new file called `haiku.md` with the `mv` command: `mv haiku.txt haiku.md`
2. Create a title for your haiku and format it as a header with `#`
3. Italicize the first two lines with `* *`
4. Italicize and bold the last line with `*** ***`
5. Create a horizontal rule after the haiku using `---`
6. Create a list of authors as an unordered list using `+ `
7. Find a relevant photo online and insert it using the syntax `![ ]( )` (see the Markdown above for full syntax)

---

### Developer Accounts

There are a number of different online services that help us be productive. Here are three that we'll use for this class:

#### Slack
All of our communication will go through the class-specific Slack channel! Please sign up for an account (if you haven't already) and download the slack client for your OS through your package manager.

#### GitHub
[GitHub](https://github.com) profiles are like a combination of LinkedIn and Facebook for developers, as well as a place to back up and store code. We'll learn more about how git and GitHub work later, but for now, it's important to create an account. When you've created an account, post a link to Slack, and follow the profiles of your classmates and instructors!

#### Netlify
Once you have a GitHub account, you can sign up for [Netlify](https://www.netlify.com/). We'll use Netlify for [Continuous Delivery](https://en.wikipedia.org/wiki/Continuous_delivery)

---

### Portfolio Project

Over the course of this class, you are going to build a Portfolio Page to practice your skills, introduce yourself to others, and demo all of the exercises and challenges that you complete in the next 4 weeks. To get started on this project, do the following:

1. Make a new directory called `FirstnameLastname` (with YOUR first and last name, of course) inside the `SavvyCoders` directory. (HINT: `mkdir FirstnameLastname`).
2. Navigate into your Portfolio Project directory (HINT: `cd FirstnameLastname`) and create a new Markdown document called `README.md`.
3. Open `FirstnameLastname` in Atom (HINT: `atom .`) and start editing `README.md`.
4. In `README.md`, mock out a quick introduction for those stumbling upon your future Portfolio Project. Be sure to include:
   1. a picture of yourself
   2. a heading
   3. a greeting paragraph
   4. a list of quick facts about you
   5. a list of links to your social media profiles like:
      + GitHub
      + LinkedIn
      + Facebook
      + Twitter

---

### Version Control with `git`
To help us maintain, back up, and share our codebases, we're going to use `git` (the command-line tool) and GitHub (the online repository). These tools are fundamental parts of the web developer's workflow, and you'll be using them *every day* for the rest of your programming career!

`git` works a bit like a Time Machine, in the sense that you'll be able to revert to any saved state within a directory. So if you mangle your site's directory structure, you can always use `git` to revert back to simpler times. The important things to understand about `git` specifically:
1. This is a CLI utility, so get ready for lots of text. All of our important files when programming will be text, so its only natural that we'd be navigating between save states (called 'commits') using text as well.
2. Arbitrarily or automatically saving code is NOT a feature of `git`, and it shouldn't be. You only want to save meaningful chunks of code (e.g. a feature), not broken pieces here and there. Otherwise, there's no way to revert back to a useful save-state!
3. Because of point \#2, 'saving' your progress with `git` is handled a bit differently. *You* are in charge of 'staging' your commits, and 'committing' changes only when *you* are ready.

![the git commit workflow](https://git-scm.com/images/about/index1@2x.png)

#### EXERCISE 4

Let's get our feet wet with `git` by configuring our user identity.

1. In any command prompt, type the following (using your name and email, of course):
```shell
$ git config --global user.name "Firstname Lastname"
$ git config --global user.email "your.email@example.com"
```
2. You can check all of your configuration settings by typing
```shell
$ git config --list
```

That wasn't so bad, right?


#### EXERCISE 5

`git` works by creating a folder within the 'working directory' (the directory that you would like to track/save over time). The first step to saving any project, then, is to navigate to this 'working directory' and create that `git` folder (named `.git`). Let's set up your portfolio project as a `git` repository to track over time.
1. First, navigate to your `~/Code/SavvyCoders/FirstnameLastname` directory.
2. Next, while still the `FirstnameLastname` directory, type the following:
```shell
$ git init
```
3. That *should* have created a `.git` folder, which is hidden by default. There are two ways to make sure that our `git init` command worked. Try these both out:
  + list all of the hidden folders (including `.git`) in `exercises`:
  ```shell
  $ ls -a
  ```
  You should see a folder called `.git` in the output.
  + try running a simple `git` command:
  ```shell
  $ git status
  ```
  If you get `FATAL: exercises is not a git repository`, something has gone wrong. If everything worked, you should see something like this:
  ```
  $ git status
  On branch master
  Initial commit
  Untracked files:
    (use "git add <file>..." to include in what will be committed)
          README.md
  nothing added to commit but untracked files present (use "git add" to track)
  ```
4. Once `git` is *initialized* (`init` = initialize), we should be able start saving snapshots of our work. Before committing our work, though, we have to *stage* our changes. You can do that with the following command:
```shell
$ git add .
```
That `.` at the end is very important! That's telling `git` to stage everything in the working directory at once. To make sure that everything worked, type in `git status` again. You should get output that looks something like this:
```shell
$ git status
On branch master
Initial commit
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
```
5. As nice as it is to get this far, we **still** haven't committed our changes yet. So we wouldn't be able to roll back to this point in the event of error, because `README.md` is still waiting to be fully committed. Let's do that with the following command:
```shell
$ git commit -m "First commit"
```
`git` forces us to create a *commit message* whenever a commit is made. This is a short snippet of text that helps you remember exactly what was changed in each commit. Normally committing and creating a commit are two different steps, but you can combine the two by adding the `-m` flag (for 'message'), followed by your custom commit message in quotation marks. If everything works as planned, you should see something like the following output:
```shell
$ git commit -m "First commit"
[master (root-commit) ee6ac27] First commit
 1 file changed, 3 insertions(+)
 create mode 100644 README.md
```
6. Now if you run `git log`, you'll see a list containing your entire `git` history (it should be pretty short at the moment). But we still only have _one copy_ of our codebase. To back up our work, let's use GitHub! The first step is to [create a new repository on online GitHub account](https://help.github.com/articles/create-a-repo/).
7. After you've created your new repository, you'll need to link that repo to your current project directory. You can do that with `git remote add origin https://github.com/YOURUSERNAME/YOUR-REPO-ADDRESS.git`. If you've done this correctly, you should see the word `origin` pop up in the command-line when you type `git remote`.
8. Now we need to **push** our local commit (called 'First commit', containing only the README.md file) to the remote repository. To do that, enter the following command:
```shell
$ git push origin master
```
9. If that worked, you should see your `README.md` file appear in your GitHub GUI after a page refresh. Now you have two copies of your `git` repository... nice work!

---

### Hello, World

For your very first website, we're going to complete a quick `Hello, World` using HTML (more on that next time!).

1. Set up your Netlify account to track your Portfolio Project's GitHub Repository! Once these two things are connected, you'll be able to push "live" to your very own website with a simple `git push origin master`.
2. Be sure to name your Netlify site whatever you'd like (instead of the randomly-generated name provided).
3. Now we're going to make a landing page for your new site!
  1. Create a landing page with the command `touch ~/Code/SavvyCoders/FirstnameLastname/index.html`
  2. In Atom, open up that new `index.html` file
  3. Type in `!`, then hit `TAB`
  4. You should now have some HTML boilerplate!
  5. Inside the `<body>` tags, type in `h1{Hello, world!}` and hit `TAB` to see your very first HTML text.
  6. Use `git` to `stage`, `commit`, and `push` your changes to GitHub
  7. Netlify should automatically update your landing page, where you should see `Hello, World!` in a big, bold font.

And now you have your very own website! Congratulations.
