# Who Wants to be a CLIllionaire?

A guide by Ankit Siva

Contact me with the details from my [website](http://www.ankitsiva.xyz) or you could alternatively search the Georgia Tech directory.

## Introduction

Hello future Command Line Interface (CLI) navigator! Welcome to my (Ankit Siva) guide to being as productive as possible in the CLI! This set-up and orientation guide started off as a way for me to remember the order in which to install the tools, plugins and themes (will probably make a script for this soon) for new machines/servers I ssh into. Before you delve into the instructions, I strongly recommend you read this next section (the disclaimer) so that I don't hype you up _too_ much about what this guide does.

This guide includes specific instructions for MacOS and Debian based OSes (example: Ubuntu). If you're using a different distro then you probably already know these things and don't need my help in setting it up (go you!).

I hope that this gets students in CS 2110 and other courses where they interact with Linux for the first time away from the GUI to understand how they can make their development experience much faster.
For CS 2110, I ssh-ed into the VM instance running and found I could code, test and debug much faster than people who used GUI based text editors within their VM instances.

Embarrassing confession: I started using Vim because I have fleshy thumb-bases that set off the cursor in other text editors. I turned off mouse during insert mode in Vim, can't do this in non-modal text editors.

## What this guide is (and what it isn't)
#### What it is

A quick-start in setting up and configuring command line tools so that you can succeed in migrating to the command line as quickly and painlessly as possible. This stems from a particularly painful couple of weeks I had to grind through at my summer research opportunity where my work was purely restricted to the command line. You will find that you will work much faster, but more importantly, look cooler while working with the command line.

This guide will also help you speed up your development in CS 2110/research projects/work where it is significantly more convenient to ssh into your development environment than being physically present with GUI.
I have added some hot tips on what ssh-ing is, how to do it, ways to copy files from one machine to another over a network (securely), and anything else I come up with while writing this guide.

I will try to reduce the number of separate webpages, GitHub repos or other sources you'll have to visit. However...

#### What it isn't

* A scapegoat for not doing your work/your computer breaking. By using this guide, you accept all responsibility for anything that breaks as a result of commands written below, software vulnerabilities or bugs in the software that you download and any damages monetary or otherwise. This document has commands that works and has worked for me on MacOS Sierra, Ubuntu, and Raspbian. Just because I am doing my best to reduce the amount of reading that you have to do, doesn't mean that you shouldn't do any. I don't want any calls from professors/TAs/companies/anyone saying that a student has blamed this guide or me directly or indirectly for any fault of theirs.
* An in-depth guide that tells you all the commands that you should know in the command line, Vim, Zsh or Bash (more on these later) -- this is what man pages are for.
* A guide to using the Windows CLI, this can only be used for Unix-based CLIs (bash for Windows may work but [YMMV](https://lmgtfy.com/?q=YMMV) since I'm trying to get you over to Zsh).

Now that I've scared you adequately, let's get on to making you a CLIllionaire.

## Pre-requisites

Like any recipe worth cooking, this guide involves some prep-time.

#### For MacOS


1. You'll want to install homebrew:  
   ```bash
   /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```

2. Next, run:  
   ```bash
   brew update && brew upgrade 
   ```

3. You'll need a powerline font -- a special font that lets you see cool developer icons for file types, OSes and so on. I patched my own font using FontForge (which I won't get into in this guide) and set it as my default terminal font (this is under application preferences). However, if you feel okay with using pre-patched fonts, pick one that suits your aesthetic from [here](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts) and set it as your terminal font.

You're set!

#### For Debian flavours

```bash
sudo apt-get update && sudo apt-get dist-upgrade  
```

Most Debian distros come with powerline fonts already set up. If not, follow instruction 3 from the MacOS pre-requisite list above.

And you're set!

## Installing Vim

I am a through and through Vim user and have been ever since I started using the Terminal for my text editing needs. This guide will (making it obvious) involve using my current vim configuration file. If you haven't used vim and don't know how to use it, I strongly suggest running `vimtutor` to understand how to work with it. You can use this before or after my vim configuration as it doesn't change how plain it looks. Stick with it for a week and a half and make a hard switch. You'll get the hang of it. If I could, you can!

Only step 1 differs between MacOS and Debian:

#### MacOS

1. In terminal, run:
   ```bash
   brew install vim
   ```
   Move to the common steps.

#### Debian

1. In terminal, run:
   ```bash
   sudo apt-get update && sudo apt-get install vim
   ```
   Move to the common steps.

#### Common
Do these after you run one of the above
1. Remove the current config file
   ```bash
   rm -r ~/.vim
   ```

1. Clone my vimrc and auxiliary files
   ```bash
   git clone https://www.github.com/ankitsiva/vim .vim
   ```

1. Open my vimrc
   ```bash
   vim ~/.vim/vimrc
   ```

1. When inside vim, type the following exactly (and then hit Enter):
   ```vimscript
   :PlugInstall
   ```

You should see a bunch of stuff updating and installing at this point. These are the plugins I use for Vim and it's now set up for you to use! Restart vim by first typing `:q` and then from terminal open vim by simply typing `vim`. You should see a knowledgeable Cow greeting you.


__Note:__ If the vimrc runs too slow, then do the following steps:
1. From terminal:
   ```bash
   rm vimrc && mv light_vimrc.txt vimrc
   ```
2. Next, open `vimrc` in `Vim` with
   ```bash
   vim ~/.vim/vimrc
   ```
3. Finally, run `:PlugClean` and `:source ~/.vim/vimrc`

## Installing Zsh and OhMyZsh

Zshell (or Zsh) is a different shell to use when interacting with your computer through the CLI. Most machines use Bash by default but Zsh is more readily optimized for faster use, and configuration.

I use OhMyZsh as my plugin manager for Zsh -- it is the largest community for Zsh plugins and themes and the most widely supported.

#### MacOS
```bash
brew update && brew install zsh
sudo -s 'echo /usr/local/bin/zsh >> /etc/shells' && chsh -s /usr/local/bin/zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

#### Debian

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install zsh
chsh -s /bin/zsh user
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

#### Bullet-Train theme

Save [this link](https://raw.githubusercontent.com/caiogondim/bullet-train-oh-my-zsh-theme/master/bullet-train.zsh-theme) in the .oh-my-zsh/themes/ folder

#### Ankit's .zshrc

Save [this](https://gist.githubusercontent.com/AnkitSiva/568474f65ce83c377fe1002468f2ce11/raw/d9a6ac00230c6db37251f5070775d0f99e3b3197/.zshrc) in your ~/ (home directory) and edit the path of oh-my-zsh to what it is in your laptop. (Line 5 of the .zshrc)

## SSH

Now to a more command focussed section. The reasons I use SSH (Secure SHell) largely fall into one of the 3 following categories:
1. I don't want to use more of my own processing power to render GUI and I despise lag (VMs)
2. I don't have to be physically present to work on the computer (machines at my lab)
3. I don't want to hook up my Raspberry Pi to my monitor and keyboard + the above two reasons.

To ssh into a machine run:
```zsh
ssh <username>@<ip address of machine>
```

You will then be prompted to type in the username for the said machine.

Before I ssh into a machine, I first need to know what the ip address of said machine. One way is to ask someone who already knows it. Another would be to run `ifconfig` when you're physically present and the final case would be to check your router's logs or gatech's ethernet registration website.

`ifconfig` floods you with a ton of information, but all you need to note down is the inet address under the physical port through which you are connected to the internet with.

## SCP

This sub-section is to mainly deal with an annoyance I heard some friends air. CS 2110 TAs in Fall '17 uploaded all files related to a homework in a single .zip/.tar.gz file. Including the pdf. It's terrible to read a pdf file on a VM so many people would end up downloading the zipped resources twice. Instead, you can use the following command:

```zsh
scp <username1>@<ip of source host>:path/to/file/file_to_copy <username2>@<ip of destination host>:path/to/destination
```

Here's an example where I am copying the file `trial.pdf` from my VM to my main OS:
```zsh
scp ankit@128.95.54.78:/Users/ankit/HW4/trial.pdf ~/CS_2110/HW4/
```

## Vim
Here is a cheatsheet and basic explanation of Vim and commands:

* You use Vim in "modes". They are:
    1. Normal Mode (to navigate around the file)
    1. Insert Mode (to insert text)
    1. Visual Mode (to visually select code to copy/paste/cut/insert)
    1. Command Mode (to perform commands on the file like substitution/find/saving/editing)
* If you are unsure what mode you are in, pressing `<esc>` once will return you to normal mode, abandoning whatever command you were performing in the specfic mode you are in.
* There are many ways to enter the modes but here are the basic ones:
    1. `<esc>` to enter Normal
    1. `i` to enter Insert (places cursor before the character the cursor is on)
    1. `v` to enter Visual
    1. `:` to enter Command

Below, I have listed some of my most used commands, the shortcuts I have mapped them to. You can chain them easily to perform compound actions

#### Normal

|Action|Default Vim|My Shortcut
| :------ | :--------: | :------:
|Navigate file|`hjkl`|`hjkl`
|Open nerdTree|`<tab>`|`<tab>`
|Move to end of word|`e`|`e`
|Move to beginning of next word|`w`|`w`
|Move to beginning of last word|`b`|`b`
|Move to end of line|`$`|`$`
|Move to beginning of line|`0`|`0`
|Move to end of file|`G`|`G`
|Move to beginning of file|`gg`|`gg`
|Replace single character|`r`|`r`
|Replace multiple characters|`R`|`R`
|Change how many characters __*__|`c<navigator>`|`c<navigator>`
|Delete how many characters __*__|`d<navigator>`|`d<navigator>`
|Quit|`:q`|`:q`
|Save and quit|`:wq`|`''`
|Save|`:w`|`\\-`
|Show time|`:echo 'Current time is ' . strftime('%c')<CR>`|`<F2>`
|Start/end spellcheck|`:set spell!`|`,,`
|Find next instance of|`/<character sequence/regex>`|-
|Find previous instance of|`?<character sequence/regex>`|-
|Navigate to next instance|`n`|`n`
|Navgiate to previous instance (search backwards)|`N`|`N`
|Delete x lines|`d`x`d`|`d`x`d`
|Yank x lines|`y`x`y`|`y`x`y`
|Repeat last chain of commands|`.`|-


__*__ The characters to change means you can combine with `w`, `e`, `$`, etc from normal mode to change those many characters. It deletes those many characters and inserts cursor before them. This can similarly be done with `d` to delete x characters.

#### Insert

|Action|Default Vim|My Shortcut
| :------ | :--------: | :------:
|Insert text before cursor|'i'|'i'
|Insert text after cursor|'a'|'a'
|Insert text at end of line|'A'|'A'
|Insert line below and start editing|'o'|'o'
|Insert line above and start editing|'O'|'O'
|Exit to normal mode|'<esc>'|'jk/JK'

#### Command

|Action|Default Vim|My Shortcut
|:------|:--------:|:------:
|Find and replace|`:<start-line>,<end-line>s/<character_sequence/regex to find>/<character_sequence/regex to replace with>/[g/gc]`|-
