# Setting Up Linux For Website Development 

After finishing installing the necessary packages and depenancies from the post install script, this guide will teach you how to setup a minimal development enviroement with Fedora Linux.


## Creating a Development Folder
The purpose of this folder is to organize and store the code for all your projects related to software development. To get started, open your system terminal and create a folder named development inside your home directory.
```
# Navigate to your home directory and create the 'development' folder.
$ cd ~
$ mkdir development

```
## Configure Git and GitHub

**Step 2.1: Create a GitHub account**

Go to GitHub.com and create an account! During the account setup, it will ask you for an email address. This needs to be a real email, and will be used by default to identify your contributions. If you are privacy conscious, or just don’t want your email address to be publicly available, make sure you tick the following two boxes on the Email Settings page after you have signed in:

![https://cdn.statically.io/gh/TheOdinProject/curriculum/770be14190139683dbe9933ca5e9393c797c63f2/foundations/installations/setting_up_git/imgs/01.png](https://cdn.statically.io/gh/TheOdinProject/curriculum/770be14190139683dbe9933ca5e9393c797c63f2/foundations/installations/setting_up_git/imgs/01.png)

Having these two options enabled will prevent accidentally exposing your personal email address when working with Git and GitHub.

You may also notice an email address under the Keep my email addresses private option. This is your private GitHub email address. If you plan to use this, make note of it now as you will need it when setting up Git in the next step.

**Step 2.2: Setup Git**

For Git to work properly, we need to let it know who we are so that it can link a local Git user (you) to GitHub. When working on a team, this allows people to see what you have committed and who committed each line of code.

The commands below will configure Git. Be sure to enter your own information inside the quotes (but include the quotation marks)!

1. git config --global user.name "Your Name"
2. git config --global user.email "yourname@example.com"
3. git config --global init.defaultBranch main
4. git config --global color.ui auto
5. git config --global pull.rebase false
6. git config --global core.editor "nvim"

**Step 2.3: Create an SSH key**

An SSH key is a cryptographically secure identifier. It’s like a really long password used to identify your machine. GitHub uses SSH keys to allow you to upload to your repository without having to type in your username and password every time.

First, we need to see if you have an Ed25519 algorithm SSH key already installed. Type this into the terminal and check the output with the information below:
```
ls ~/.ssh/id_ed25519.pub
```
If a message appears in the console containing the text “No such file or directory”, then you do not yet have an Ed25519 SSH key, and you will need to create one. If no such message has appeared in the console output, you can proceed to step 2.4.

To create a new SSH key, run the following command inside your terminal.
```
ssh-keygen -t ed25519
```
- When it prompts you for a location to save the generated key, just push Enter.
- Next, it will ask you for a password; enter one if you wish, but it’s not required.

**Step 2.4: Link your SSH key with GitHub**
Now, you need to tell GitHub what your SSH key is so that you can push your code without typing in a password every time.

First, you’ll navigate to where GitHub receives our SSH key. Log into GitHub and click on your profile picture in the top right corner. Then, click on Settings in the drop-down menu.

Next, on the left-hand side, click SSH and GPG keys. Then, click the green button in the top right corner that says New SSH Key. Name your key something that is descriptive enough for you to remember what device this SSH key came from, for example linux-ubuntu. Leave this window open while you do the next steps.

Now you need to copy your public SSH key. To do this, we’re going to use a command called cat to read the file to the console. (Note that the .pub file extension is important in this case.)
```
cat ~/.ssh/id_ed25519.pub
```
Highlight and copy the entire output from the command. If you followed the instructions above, the output will likely begin with ssh-ed25519 and end with your username@hostname.

Now, go back to GitHub in your browser window and paste the key you copied into the key field. Keep the key type as Authentication Key and then, click Add SSH key. You’re done! You’ve successfully added your SSH key!

**Step 2.5 Testing your key**

Follow the GitHub directions for testing your SSH connection. Make sure the fingerprint output in the terminal matches one of the four GitHub’s public fingerprints. (Don’t forget to omit the $ when you copy and paste the code!).

You should see this response in your terminal: Hi username! You’ve successfully authenticated, but GitHub does not provide shell access. Don’t let GitHub’s lack of providing shell access trouble you. If you see this message, you’ve successfully added your SSH key and you can move on. If the output doesn’t correctly match up, then try going through these steps again or come to the Discord chat to ask for help.

> Resource https://www.theodinproject.com/lessons/foundations-setting-up-git
