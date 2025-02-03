# Command Line Interface (CLI)

![Command Line](CLI.webp)

Image source: Dall-E by OpenAI

- [Command Line Interface (CLI)](#command-line-interface-cli)
  - [Learning Outcomes](#learning-outcomes)
  - [What is the Command Line?](#what-is-the-command-line)
    - [Windows](#windows)
    - [MacOS/Linux](#macoslinux)
  - [Node Project and Node Modules](#node-project-and-node-modules)
    - [Running Node Programs](#running-node-programs)
    - [Starting a Project](#starting-a-project)
    - [Installing and Removing Modules](#installing-and-removing-modules)
    - [Installing Project Dependencies](#installing-project-dependencies)
  - [Git Commands](#git-commands)

## Learning Outcomes

After completing this topic, you will be able to:

- Describe what the command line is;
- Use the command line to navigate directories;
- Use the command line for Node.js projects;
- Use the command line for basic Git operations.

## What is the Command Line?

The command line is a text-based user interface that allows users to interact with their computer by typing commands. It is part of the operating system and enables users to run programs, manage files and directories, execute scripts, and more.

In Node.js, we have already used the command line when running Node.js scripts from the terminal. For example:

```bash
node app.js
```

However, if we are in the wrong directory to run the command, we may need to navigate to the correct folder where the script resides. For this, we can use the following commands:

### Windows

- `cd foldername` - Moves from one directory to another;
- `cd ..` - Moves one level up in the directory structure;
- `dir` - Lists the contents of the directory;
- `mkdir foldername` - Creates a new directory;
- `del` - Deletes a file;
- `echo` - Writes text to the console;
- `type filename` - Displays the contents of a file;
- `cls` - Clears the console;
- `exit` - Closes the console;

### MacOS/Linux

- `pwd` - Displays the current directory;
- `ls` - Lists the contents of the directory;
- `cd foldername` - Moves from one directory to another;
- `cd ..` - Moves one level up in the directory structure;
- `mkdir foldername` - Creates a new directory;
- `rm filename` - Deletes a file;
- `mv filename newfilename` - Renames a file;
- `mv filename foldername` - Moves a file to another directory;
- `cp filename foldername` - Copies a file to another directory;
- `cat filename` - Displays the contents of a file;
- `touch filename` - Creates a new file;
- `clear` - Clears the console;
- `exit` - Closes the console;

## Node Project and Node Modules

To use third-party modules in Node.js, we will often need to use the command line and some commands to install and manage those modules.

> Note: The following commands assume that you've already created a directory for your Node.js project, and the commands are to be executed within that directory.

### Running Node Programs

To run Node.js programs, use the following command:

```bash
node app.js
```

### Starting a Project

To start a Node.js project, use the following command:

```bash
npm init
```

Alternatively, you can use the following command to create a Node.js project with default configuration files:

```bash
npm init -y
```

This command will create a `package.json` file in the root of the project directory, where project details such as the name, version, description, author, and project dependencies are listed.

### Installing and Removing Modules

Installing Node modules via the command line is very simple. Use the `npm` command followed by the `install` parameter and the module name. For example:

```bash
npm install express
```

To remove Node modules, use the `npm` command followed by the `uninstall` parameter and the module name. For example:

```bash
npm uninstall express
```

### Installing Project Dependencies

If we have a `package.json` file listing all project dependencies, we can install all dependencies with the following command:

```bash
npm install
```

## Git Commands

So far, we have used Git through a graphical user interface, and we can continue doing so. However, it's essential to know some Git commands to use Git from the command line when needed.

- `git clone <url>` - Clones a remote repository to your local machine;
- `git status` - Shows the changes made to files;
- `git add` - Stages files for commit;
- `git commit -m "Description of changes"` - Commits the staged changes with a description;
- `git push` - Pushes the committed changes to the remote repository;
- `git pull` - Pulls changes from the remote repository to your local machine;
- `git log` - Displays the commit history;
- `git branch` - Lists all branches and indicates the current branch;
- `git checkout -b newbranch` - Creates and switches to a new branch;
- `git merge branch` - Merges the specified branch into the current branch;
- `git reset` - Unstages the last commit but keeps the changes;
- `git reset --hard` - Removes the last commit and the changes;
- `git reset --hard <commit id>` - Resets all changes and commits to a specific commit;
- `git reset --hard origin/master` - Resets everything to match the state of the master branch on the remote repository;
