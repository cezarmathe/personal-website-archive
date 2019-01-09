---
layout: post
title: How to manage your dotfiles like a boss
gh-repo: cezarmathe/dotfiles
gh-badge: [star, follow]
tags: [dotfiles, linux, unix, configuration, tutorial, stow]
comments: true
# published: false
---

First, a little bit of background. You set up a new computer and chances are you haven't backed up your dotfiles. What do you do now? You spend hours trying to replicate the workflow and configurations, because _someone_ didn't take the time to back up his dotfiles. But hey, at least you're trying now.

## Before we start

Go through your home directory, `~/.config` and other folders that might contain configurations. Also, make sure that you **DO NOT** include private information like ssh and gnupg keys!

Then, create a folder somewhere in your home directory, give it a proper name; this folder is going to be the git repository that keeps track of your dotfiles. Mine is `~/Maintenance/dotfiles`.

## Get stow

[Stow](https://www.gnu.org/software/stow/) is a tool for managing symbolic links and our second dotfile management tool, along git.

- Mac: `$ brew install stow`

- Ubuntu: `# apt get stow`
  
- Arch Linux: `# pacman -S stow`

## The actual management

Fire up your terminal of choice, `cd` to the folder that you just created and run `git init`, our dotfiles are going to be versioned with git.

Then, create a couple of folders for things that are related, for example, create a folder for bash-related dotfiles, one for vim-related dotfiles, one for zsh-related dotfiles etc. Then, move **the actual dotfiles** from their original location in your home directory into the dotfiles folder and into the correct category; for example, `~/.bashrc` would go for me to `~/Maintenance/dotfiles/.bashrc`. Also, make sure that files have their complete path relative to the home directory inside the dotfiles folder, for example `~/.config/a_config_file` will be moved to `~/Maintenance/dotfiles/a_category/a_config_file`.

Inside the dotfiles folder, run this command: `$ stow -t "${HOME}" bash` and look in your home directory. You will see a symlink for `.bashrc` and for any other file that you placed in the bash category folder.

Continue moving dotfiles and creating categories until you feel you're good to go, then run `$ git add -A`, `$ git commit -a -m "$(date)` and `$ git push <the_origin.git> master` and you're done!

## For your convenience

You might want to add these aliases in your `.bashrc`:

```shell
alias dotfiles="git --work-tree=/home/<your_user>/Maintenance/dotfiles/ --git-dir=/home/<your_user>/Maintenance/dotfiles/.git"
alias stow="stow -t ${HOME}"
```

Replace `Maintenance/dotfiles` with the path that you chose for your setup, but keep the `\` at the end of the path for the work tree.

## My dotfiles

If you'd like to see how my dotfiles are looking, visit [this](https://github.com/cezarmathe/dotfiles) repository.