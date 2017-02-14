---
layout: post
title: Writing Ansible Modules Part 1 - Preparing Your Environment
comments: true
categories: ansible, modules, configuration management, software development, automated testing, code coverage, agile, tdd, bdd
---
This is part 1 of a series of articles. For other parts, see
[the introductory article](/2017/02/writing-ansible-modules-with-tests.html).


## Prerequisites
You'll need a few things handy before you can continue:

- Git branching basics. [Learn Git Branching](http://learngitbranching.js.org)
  is a great resource!

- Ansible 2.2 features a tech preview of Python 3 support.
- Ansible 2.3+ will enforce all code to be version compatible for both Python 2 && 3.

- Pip

- The following Python libraries:
    - paramiko
    - PyYAML
    - Jinja2
    - httplib2
    - six
    - nose

  - Basic testing knowledge including mocking. If you're not too familiar with mocking, you can still follow along but I encourage you to read up on it after you're done here as it will help make your unit tests more robust.


## Prep Your Ansible Repo

If you haven't already done so, fork the [Ansible](https://github.com/ansible/ansible)
repo to a GitHub account or organization you have access to. Afterwards, clone your fork:

    $ git clone git@github.com:<your-github-account>/ansible.git

  Next, add the upstream Ansible repo as 'upstream'

    $ cd ansible
    $ git remote add upstream https://github.com/ansible/ansible

After this, you now should have two remotes with 'origin' pointing to your Github fork of the repo, and 'upstream' pointing to the upstream repo. You won't be able to push upstream but you can fetch from it and then create pull requests which is how it should be.

    $ git remote -v
    origin  git@github.com:<your-github-account>/ansible.git (fetch)
    origin  git@github.com:<your-github-account>/ansible.git (push)
    upstream        https://github.com/ansible/ansible (fetch)
    upstream        https://github.com/ansible/ansible (push)

I'm going to refer to your local clone as your  **ansible repo** from now on.


## Note: Add a Few Git Aliases to Your Toolkit!

You don't have to do this but if you want to follow along with my git commands, I'll be using these below so feel free to add them to your `~/.gitconfig` under the aliases section:

    [alias]
    fa = fetch --all
    t = log --graph --pretty=oneline --abbrev-commit --decorate --color
    ta = log --graph --pretty=oneline --abbrev-commit --decorate --color --all

With these, you'll gain the following `git` commands:

- `git fa` - Fetch (but don't merge) the latest from all remotes
- `git t` - See the history of the current branch laid out in a tree
- `git ta` - See the history of the entire repo laid out in a tree

## Prepare Your Environment For Local Development

While at the root dir of your **ansible repo**, run the following:

    $ source hacking/env-setup

This will prepare your current terminal session and prepend the current
ansible repo to your $PATH. Running `ansible --version` should get you
something similar to this:
    $ ansible --version
    ansible 2.3.0 (devel 09edc00008) last updated 2017/02/14 11:07:50 (GMT +200)
    config file =
    configured module search path = Default w/o overrides

Provided you didn't have any shims messing up your path, running `which ansible` should now show the `<path to your local ansible repo>/bin/ansible`.
If not, you probably have some crazy shim-y stuff going on. Fix that before proceeding.

If you want to make this permanent, add the following to your `~/.bash_profile` or `~/.bashrc`:

  source <path to ansible repo>/hacking/env-setup
