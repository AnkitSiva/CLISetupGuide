# Who Wants to be a CLIllionaire?

## Introduction

Hello future Command Line Interface (CLI) navigator! Welcome to my (Ankit Siva) guide to being as productive as possible in the CLI! This set-up and orientation guide started off as a way for me to remember the order in which to install the tools, plugins and themes (will probably make a script for this soon) for new machines/servers I ssh into. Before you delve into the instructions, I strongly recommend you read this next section (the disclaimer) so that I don't hype you up _too_ much about what this guide does.

This guide includes specific instructions for MacOS and Debian based OSes (eg: Ubuntu). If you're using a different distro then you probably already know these things and don't need my help in setting it up (go you!).

I hope that this gets students in CS 2110 and other courses where they interact with Linux for the first time away from the GUI to understand how they can make their development experience much faster.
For CS 2110, I ssh-ed into the VM instance running and found I could code, test and debug much faster than people who used GUI based text editors within their VM instances.

## What this guide is (and what it isn't)
#### What it is

A quickstart in setting up and configuring command line tools so that you can succeed in migrating to the command line as quickly and painlessly as possible. This stems from a particularly painful couple of weeks I had to grind through at my summer research opportunity where my work was purely restricted to the command line. You will find that you will work much faster, but more importantly, look cooler while working with the command line.

This guide will also help you speed up your development in CS 2110/research projects/work where it is significantly more convenient to ssh into your development environment than being physically present with GUI.
I have added some hot tips on what ssh-ing is, how to do it, ways to copy files from one machine to another over a network (securely), and anything else I come up with while writing this guide.

I will try to reduce the number of separate webpages, github repos or other sources you'll have to visit. However...

#### What it isn't

* A scapegoat for not doing your work/your computer breaking. By using this guide, you accept all responsibility for anything that breaks as a result of commands written below, software vulnarabilities or bugs in the softwares that you download and any damages monetary or otherwise. This document has commands that works and has worked for me on MacOS Sierra, Ubuntu, and Raspbian. Just because I am doing my best to reduce the amount of reading that you have to do, doesn't mean that you shouldn't do any. I don't want any calls from professors/TAs/companies/anyone saying that a student has blamed this guide or me directly or indirectly for any fault of theirs.
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

3. You'll need a powerline font -- a special font that lets you see cool developer icons for filetypes, OSes and so on. I patched my own font using FontForge (which I won't get into in this guide) and set it as my default terminal font (this is under application preferences). However, if you feel okay with using pre-patched fonts, pick one that suits your aesthetic from [here](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts) and set it as your terminal font.

You're set!

#### For Debian flavours

```bash
sudo apt-get update && sudo apt-get dist-upgrade  
```

Most Debian distros come with powerline fonts already set up. If not, follow instruction 3 from the MacOS pre-requisite list above.

And you're set!

## Installing Vim

I am a through and through Vim user and have been ever since I started using the Terminal for my text editing needs. This guide will (making it obvious) involve using my current vim config file. If you haven't used vim and don't know how to use it, I strongly suggest running `vimtutor` to understand how to work with it. You can use this before or after my vim config as it doesn't change how plain it looks. Stick with it for a week and a half and make a hard switch. You'll get the hang of it. If I could, you can!

Only step 1 differs between MacOS and Debian:

#### MacOS

1. ```bash  
   brew install vim
   ```

#### Debian

1. ```bash
   sudo apt-get update && sudo apt-get install vim
   ```

#### Common

2. ```bash
   rm -r ~/.vim
   ```

3. ```bash
   git clone https://www.github.com/ankitsiva/vim .vim
   ```

4. ```bash
   vim ~/.vim/vimrc
   ```

5. When inside vim, type the following exactly (and then hit Enter):
   ```vimscript
   :PlugInstall
   ```

You should see a bunch of stuff updating and installing at this point. These are the plugins I use for Vim and it's now set up for you to use! Restart vim by first typing `:q` and then from terminal open vim by simply typing `vim`. You should see a knowledgeable Cow greeting you.


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

__Todo__
