# Git: open-source, blockchain-based DVCS 
## by Olgierd &#34;Allgreed&#34; Kasprowicz



# <span style="color: #b58900">Disclaimer</span>
<!-- .slide: data-background-color="black" -->


## 🤑
<!-- .slide: data-background-color="black" -->
<img style="margin: 0; box-shadow: none; border: 0; background: transparent" src="/img/just.png">
<hr>
## ⌨
<img style="margin: 0; box-shadow: none; border: 0; background: transparent" src="/img/hs.png">


<!-- .slide: data-background-color="black" -->
<img src="/img/qr-source.png" style="width: 27%; margin: 0">
### source: [github.com/allgreed/presentation-git](https://github.com/allgreed/presentation-git)
- The opinions expressed here represent my own and not those of my employer.
- Questions: during
- Shitstorm: after
- Feedback much appreciated 



## Y learn git?

- When you don't work alone
- When you don't want to work alone anymore


## Some of supported technologies
<img src="/img/supported-languages.jpg">


## Roadmap

- [Think like git](/think-like-git.html)


# Git: improved workflow
## by Olgierd &#34;Allgreed&#34; Kasprowicz



## So you know thoose commands:
- status
- add
- commit


### You don't:

- `git status -s`
- `git add -p`
- `git commit -v`



## Crafting good commits: -m option considered harmfull

- [Let's have some fun](https://whatthecommit.com/)


### ACID
- Atomic: commit make sense on it's own
- Coherent: one commit - one thing only 
- Incremental: commits do not depend on each other
- Documented: short summary - present tense, longer description - rationale, thoughts, etc., footer - Machine triggers, etc.)



## Podziękował!
Fin części 1.


## Resources:
- https://chris.beams.io/posts/git-commit/



# Git: tips-and-tricks 
## by Olgierd &#34;Allgreed&#34; Kasprowicz



## Shell


### Have handy info at hand

- Am I in git repo?
- What branch am I on?
- Is my repository dirty?
- ???


#### [Don't reinvent the wheel!](https://web.archive.org/web/20160704140739/http://ithaca.arpinum.org/2013/01/02/git-prompt.html)

- `__git_ps1`
- Requires `bash-completion` package installed and imported to your `.bashrc`
- Configurable, ex. `GIT_PS1_SHOWDIRTYSTATE=1`


- `bash-completion` package may be already installed and imported (at least it is on Ubuntu 16.04 and Debian Stretch)
- need to hook it up to your prompt, see my dotfiles for details (`allgreed/dotfiles/.bash_prompt`)


### Alias git itself (with autocompletion)

```
alias g="git"
[ -f /usr/share/bash-completion/completions/git ] \
    && . /usr/share/bash-completion/completions/git
__git_complete g __git_main
```



## Git aliases
```
[alias]
    s = status
    d = diff
    p = push
    a = add
    c = commit
    co = checkout
```


### "Smart" aliases
```
[alias]
    purge-branches = !git branch --merged >/tmp/merged-branches \ 
        && vi /tmp/merged-branches \
        && xargs git branch -d </tmp/merged-branches
```

- Can't use `_`!



## Integrations
```
[core]
    editor = vim
    pager = less
```

- can be also difftool, mergetool etc.



## Misc


## Global .gitignore
```
[core]
	excludesfile = /home/allgreed/.gitignore_global
```


## \r\n vs. \r vs. \n
```
[core]
	autocrlf = input
```

- true: CRLF -> LF (on checkout), LF -> CRLF (on push)
- input: CRLF -> LF (on checkout)
- false: nada


## Prune remote-deleted branches from local copy
```
[fetch]
	prune = true
```


## Advanced diff
```
[diff]
    renames = copies # rename and copy detection
    algorithm = patience # smaller diffs

[diff "bin"]
    textconv = hexdump -v -C # apply "filter" to binary diff
```



## Github


### Hub command line

#### Instalation

- [Download release](https://github.com/github/hub/releases)
- `tar -xvf RELEASE_FILE`
- `./UNTARED_FOLDER/install`<br><br>
or:<br>
<br>
- `brew install hub`


### Use SSH

- no need to type passwords
- no trouble when setting up 2FA
- much more secure solution

#### Tutorial resources from Github

- [Create a ssh key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)
- [Add it to Github](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)
- [Verify that it has been added correctly](https://help.github.com/articles/testing-your-ssh-connection/)
- `git config --global hub.protocol ssh` (SSH with Hub)



## Colors, so much colors!
```
[color "status"] # "status" can be also: diff, branch, ...
    added = green ul # underlined
    changed = blue
    untracked = red reverse # sets background to red
```



## Podziękował!
Fin.


## Sources

- Enrico Campidoglio - Advanced Git Tips and Tricks (Pluralsight)
- people's dotfiles
- my dotfiles
