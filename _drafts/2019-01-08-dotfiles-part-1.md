---
layout: post
title: Dotfiles - introduction
gh-repo: cezarmathe/dotfiles
gh-badge: [star, follow]
tags: [dotfiles, linux, unix, configuration, tutorial]
comments: true
published: false
---

## What are dotfiles?

**Dotfiles** are files whose names start with a **dot**. 

## What are dotfiles used for?

**Dotfiles** are usually used as **configuration files** on Unix systems and are **hidden by default** in file managers like Finder, Dolphin, Thunar, Nautilus etc.

## Why would I care about my dotfiles?

As I said before, **dotfiles** are usually used as configuration files. Do you remember when you have to erase your OS and install it again? How much time did it take for you to make it feel like before? _An unpleasant amount of time, indeed_.

Well, first things first:

## What configurations do dotfiles store?

Assuming you're a git user, let's take the file `~/.gitconfig`.
Fire up your terminal and write:
```shell
$ cat .gitconfig
```
Just a quick reminder, don't paste the `$` in your terminal. The `$` sign actually means that you need user privileges(aka you don't use `sudo`). When you're going to see a `#` instead of a `$`, it means you need to use root privileges so you will have to use `sudo`.