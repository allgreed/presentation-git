# Git: open-source, blockchain-based DVCS 
## by Olgierd &#34;Allgreed&#34; Kasprowicz


## 🤑
<!-- .slide: data-background-color="black" -->
<img style="margin: 0; box-shadow: none; border: 0; background: transparent" src="/img/just.png">
<hr>
## 💻
<img style="margin: 0; box-shadow: none; border: 0; background: transparent" src="/img/hs.png">


# <span style="color: #b58900">Disclaimer</span>
<!-- .slide: data-background-color="black" -->

### source: github.com/allgreed/presentation-git


<!-- .slide: data-background-color="black" -->
- The opinions expressed here represent my own and not those of my employer.
- Questions: during
- Shitstorm: after
- Feedback much appreciated 
- if Hackerspace: "Hackerspace is 4 things"


<!-- .slide: data-background-color="black" -->
## Expectations

- Ubern00b -> just a regular n00b
- Know git internals to understand better d2d operations
- Personalize a bit your git experiance
- Set sensible non-default-but-pretty-much-should-be configuration



## Cultural references


> ## "git gets easier once you get the basic idea that branches are homeomorphic endofunctors mapping submanifolds of a Hilbert space."


## Why? When?

- When you don't work alone
- When you don't want to work alone anymore
- Supports every language, every framework


### <s>GUI</s> CLI

[Follow up reading](https://lmddgtfy.net/?q=git%20why%20use%20cli%20instead%20of%20gui)

- While you're learning at least
- There are lots of GUIs, yet only one CLI



## Let's git to it! From scratch!

- <span class="fragment fade-up" data-fragment-index="1">Persistent map</span>
- <span class="fragment fade-up" data-fragment-index="2">Stupid content tracker</span>
- <span class="fragment fade-up" data-fragment-index="3">Revision control system</span>
- <span class="fragment fade-up" data-fragment-index="4">DVCS</span>



## Persistent map


### A map?

<img src="/img/pirate.jpg">


### Implementation

- Keys: SHA1 of the content<br>
- Values: the content

``` bash
git hash-object
```

``` bash
$ echo "elorap" | git hash-object --stdin
2511755d6bfe6afb0462cc8ba7b254e371b7e191
```


### Details

```
$ echo "elorap" | git hash-object --stdin
2511755d6bfe6afb0462cc8ba7b254e371b7e191
```

```
$ echo "elorap" | sha1sum -
8aec9bf5a852dbe30b3ebe9854be53feef471a5a  -
```

```
git_hash(content) = sha1("{type} {size_in_bytes}\0{content}")
```

```
echo -e "blob 7\0elorap" | sha1sum -
2511755d6bfe6afb0462cc8ba7b254e371b7e191  -
```


### Persistence

```
git init
```

```
echo "elorap" | git hash-object --stdin -w
2511755d6bfe6afb0462cc8ba7b254e371b7e191
```

```
.git/objects/25/11755d6bfe6afb0462cc8ba7b254e371b7e191
```

```
git cat-file
```

```
git cat-file -p 2511755d6bfe6afb0462cc8ba7b254e371b7e191
```

```
git cat-file -t 2511
```



## Stupid content tracker

```
git add -A
git commit
```


### What is a commit?

```
git cat-file -t `git log --oneline | cut -d' ' -f  1`
git cat-file -p `git log --oneline | cut -d' ' -f  1`
```


### Blockchain?

> A blockchain,[1][2][3] originally block chain,[4][5] is a growing list of records, called blocks, which are linked using cryptography.[1][6]~ [Wiki](https://en.wikipedia.org/wiki/Blockchain)


### What is a tree?

- Directory representation inside git
- Can be nested


### Optimization

- Two files with the same content


### Recap - type in git DB

- Blobs
- Trees
- Commits<br>

and

- <span style="text-decoration: underline">Annotated tags</span>



## Revision control system

- **Tag**: Constant pointer to a commit
- **Branch**: Mutable pointer to a commit

ref = [ branch | tag ]

- **HEAD**: Mutable pointer to [ commit | ref ]

Stored in `.git/refs/` and `.git/HEAD`


### Merge and conflicts

- **Merge**: integrating changes between branches
- **Merge conflict**: Is a condition where human intervention is required to do the above
- **Fast-forward merge**: Merging without a merge commit
- **Rebase**: integrate changes from 2 branches by "replaying" commits



## DVCS


### Network
- Connected via `remotes`
- Syncs unique objects, mostly immutable


### Equal clones
- All repos made equal (technically) - clones
- Repo has [eventually consistent] information about very remote
- Social aspect - distributed vs. decentralized


### Off-line
- Remote references are stored locally just like local branches
- `.git/refs/remotes/origin/HEAD`
- `packed-refs`



## Podziękował!
Fin części 0.


## Sources

- Paolo Perrotta - How Git Works? (Pluralsight)
- [Meme](https://twitter.com/agnoster/status/44636629423497217)
- [About git hashes](https://stackoverflow.com/questions/552659/how-to-assign-a-git-sha1s-to-a-file-without-git)
- [More about git hashes](https://stackoverflow.com/questions/7225313/how-does-git-compute-file-hashes)



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
