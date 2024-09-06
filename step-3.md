# Setting Up Linux For Website Development 

After finishing installing the necessary pack~/.asdf/shims/rubyages and depenancies from the post install script, this guide will teach you how to setup a minimal development enviroement with Fedora Linux.


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

Next, on th~/.asdf/shims/rubye left-hand side, click SSH and GPG keys. Then, click the green button in the top right corner that says New SSH Key. Name your key something that is descriptive enough for you to remember what device this SSH key came from, for example linux-ubuntu. Leave this window open while you do the next steps.

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

## Getting Started with asdf

**Setp 1 - Installing dependencies**
asdf primarily requires git & curl. Here is a non-exhaustive list of commands to run for your package manager (some might automatically install these tools in later steps).
```
sudo dnf install -y  curl
```

**Setp 2 - Downloading asdf Offical download**
```
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.14.1
```
**Setp 3 - Installing asdf**

There are many different combinations of Shells, OSs & Installation methods all of which affect the configuration here. Expand the selection below that best matches your system.

Bash & Git

Add the following to ~/.bashrc:
```
. "$HOME/.asdf/asdf.sh"
```
Completions must be configured by adding the following to your .bashrc:
```
. "$HOME/.asdf/completions/asdf.bash"
```

Restart your shell so that PATH changes take effect. Opening a new terminal tab will usually do it.

**Setp 4 - Installing a plugin for each tool/runtime you wish to manage**

Each plugin has dependencies so we need to check the plugin repo where they should be listed. For asdf-nodejs they are:

**Setup 4.1 - Nodejs**

A Now we have a plugin for Node.js we can install a version of the tool.We can see which versions are available with asdf list all nodejs or a subset of versions with asdf list all nodejs 14. We will just install the latest available version:
````
Plugin `asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git`
````
Now we have a plugin for Node.js we can install a version of the tool.
````
asdf install nodejs latest
````
Global defaults are managed in $HOME/.tool-versions. Set a global version with:
````
asdf global nodejs latest
````

**Setup 4.2 - Ruby**
Install plugins for fedora rub: 
````
sudo dnf install git zlib-devel make gcc openssl-devel readline-devel libyaml-devel sqlite-devel libxml2-devel libxslt-devel libcurl-devel libffi-devel
````
A Now we have the dependencies for Ruby we can install a version of the tool. We can see which versions are available with asdf list all nodejs or a subset of versions with asdf list all Ruby versions. We will just install the latest available version:
````
asdf plugin add ruby https://github.com/asdf-vm/asdf-ruby.git````
````
Now we have a plugin for Node.js we can install a version of the tool.
````
asdf install ruby latest
````
Global defaults are managed in $HOME/.tool-versions. Set a global version with:
````
asdf global ruby latest
````
ensure your system is running node js and ruby from asdf install 
````
$ which node
# output - ~/.asdf/shims/node
$ which ruby
# output - ~/.asdf/shims/ruby
````

## Visual Studio Code on Linux 

**Step 1 - Installing Visual Studio Code Package on Linux From Microsoft**

Head over the visual studo code website https://code.visualstudio.com/ RHEL, Fedora, and CentOS based distributions. The script below ships the stable 64-bit VS Code in a yum or dnf repository, the following script will install the key and repository:
```
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null
```
Then update the package cache and install the package using dnf (Fedora 22 and above):
```
sudo dnf check-update
sudo dnf install code # or code-insiders
```

