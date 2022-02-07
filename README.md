# Mav's dotfiles

* A repo for my dotfiles, forked from the repo of [paulirish/dotfiles](https://github.com/paulirish/dotfiles).
* If you're starting anew, consider forking [mathias](https://github.com/mathiasbynens/dotfiles/) or [alrra](https://github.com/alrra/dotfiles/). Or, [paulmillr](https://github.com/paulmillr/dotfiles) and [gf3](https://github.com/gf3/dotfiles) also.

## Setup

Here are steps to get these profiles into your Linux environment:

### Installing & Using

* [Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) this repo
* [Clone](https://docs.github.com/en/get-started/quickstart/fork-a-repo#cloning-your-forked-repository) that repo
* Review and run parts of [`setup-a-new-machine.sh`](./setup-a-new-machine.sh)
* Review and run [`symlink-setup.sh`](./symlink-setup.sh)
  * [git config](./.gitconfig) needs attention, read the notes
* Enjoy automatic profiles

#### Maintenance

* Commit/push back to the fork any changes you want
* You can also hypothetically cherry-pick commits from [paulirish/dotfiles](https://github.com/paulirish/dotfiles) and mathias and our fork ecosystem

#### Shell

This repo contains config for bash, zsh, and fish. As of March 2016, I'm using fish shell mostly, but fall back to bash once in a while. The bash and fish stuff are both well maintained; zsh, less so. If you're using fish you'll want to do a `git submodule update --init`.

## Paul's favs

### [`.aliases`](https://github.com/paulirish/dotfiles/blob/master/.aliases) and [`.functions`](https://github.com/paulirish/dotfiles/blob/master/.functions)

So many goodies.

### The "readline config" ([`.inputrc`](.inputrc))

Basically it makes typing into the prompt amazing.

* Tab like crazy for autocompletion that doesn't suck. Tab all the things. Srsly.
* No more <tab><tab> that says "Display all 1745 possibilities? (y or n)" YAY
* Type `cat <uparrow>` to see your previous `cat`s and use them
* Case insensitivity
* Tab all the livelong day

### Moving around in folders (`z`, `...`, `cdf`)

`z` helps you jump around to whatever folder. It uses actual real magic to determine where you should jump to. Separately, there's some `...` aliases to shorten `cd ../..` and `..`, `....` etc. Then, if you have a folder open in Finder, `cdf` will bring you to it.

```sh
z dotfiles
z blog
....      # drop back equivalent to cd ../../..
z public
cdf       # cd to whatever's up in Finder
```

`z` learns only once its installed so you'll have to cd around for a bit to get it taught.
Lastly, I use `open .` to open Finder from this path. (That's just available normally.)

## Overview of Files

#### Automatic Configuration

| Script | Purpose |
|---|---|
| [`.vimrc`](./.vimrc), [`.vim`](./.vim) | vim config, obv. |
| [`.inputrc`](./.inputrc) | behavior of the actual prompt line |

#### Shell Environment

* [`.aliases`](./.aliases)
* [`.bash_profile`](./.bash_profile)
* [`.bash_prompt`](./.bash_prompt)
* [`.bashrc`](./.bashrc)
* [`.exports`](./.exports)
* [`.functions`](./.functions)
* `.extra` &mdash; not included, [explained below](#extra-for-your-private-configuration)

#### Manual Run
 
| Script | Purpose |
|---|---|
| [`setup-a-new-machine.sh`](./setup-a-new-machine.sh) | Installs random apps I need |
| [`symlink-setup.sh`](./symlink-setup.shh) | Sets up symlinks for all dotfiles and vim config |
| [`.macos`](./.macos) | Run on a fresh mac os setup |
| [`brew.sh`](./brew.sh) and [`brew-cask.sh`](./brew-cask.sh) | Homebrew initialization |

#### git, bruh

* [`.git`](./.git)
* [`.gitattributes`](./.gitattributes)
* [`.gitconfig`](./.gitconfig)
* [`.gitignore`](./.gitignore)

### `.extra` for your private configuration

There will be items that don't belong committed to a git repo, because either 

1. they shouldn't be the same across your machines or
2. they shouldn't be in a git repo.

Kick it off like this:

```sh
touch ~/.extra && $EDITOR $_
```

I have some EXPORTS, my PATH construction, and a few aliases for ssh'ing into my servers in there.

I don't know how others manage their $PATH, but this is how I do mine:

```shell
# The top-most paths override here.
PATH=/opt/local/bin
PATH=$PATH:/opt/local/sbin
PATH=$PATH:/bin
PATH=$PATH:~/.rvm/bin
PATH=$PATH:~/code/git-friendly

# ...

export PATH
```

### Sensible OS X defaults

Mathias's repo is the canonical for this, but you should probably run his or mine after reviewing it.

```bash
./.macos
```

### `~/bin`

One-off binaries that aren't via an npm global or homebrew. [git open](https://github.com/paulirish/git-open), [wifi-password](https://github.com/rauchg/wifi-password), [coloredlogcat](https://developer.sinnerschrader-mobile.com/colored-logcat-reloaded/507/), [git-overwritten](https://github.com/mislav/dotfiles/blob/master/bin/git-overwritten), and `subl` for Sublime Text.

### Syntax highlighting for these files

If you edit this stuff, install [Dotfiles Syntax Highlighting](https://github.com/mattbanks/dotfiles-syntax-highlighting-st2) via [Package Control](http://wbond.net/sublime_packages/package_control)

### 2020 update

Rust folks have made waves in which we rudder our boats.

* As most know, `bat`  as a `cat` replacement (🦇 vs 😼)
* <https://github.com/dandavison/delta> may be better than the [diff-so-fancy project](https://github.com/so-fancy/diff-so-fancy)
* <https://github.com/ogham/exa> is better `ls` and gets all the trapd00r/LS_COLORS stuff, etc.
* <https://github.com/bigH/git-fuzzy> interactive git thing. This deprecates Paul's `git recent` script&hellip; and probably some other things.

 Also, I'd like to migrate to using homesick or <https://www.atlassian.com/git/tutorials/dotfiles>

 Also interested in <https://github.com/dandavison/open-in-editor>
