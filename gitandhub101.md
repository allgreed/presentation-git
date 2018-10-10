# Git & hub 101
## by Olgierd &#34;Allgreed&#34; Kasprowicz



## I'm going to lie!
in order to:
- <input type="checkbox" checked> get
- <input type="checkbox" checked> shit
- <input type="checkbox" checked> done


## Git ain't Hub

<div style="display: grid; grid-template-columns: 1fr 1fr;">
<img src="https://proxy.duckduckgo.com/iu/?u=http%3A%2F%2Fwww.joewoodson.de%2Fassets%2Flogos%2Fgit.svg&f=1" style="margin: 0; box-shadow: none; border: 0; background: transparent; float:left;">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/Octicons-mark-github.svg/1024px-Octicons-mark-github.svg.png" style="margin: 0; box-shadow: none; border: 0; background: transparent; filter: opacity(30%);">
</div>


## Why git?
### Svn works fine, right?

<img src="/img/gitpopularity.png">


## Compatibility
<ul>
    <li class="fragment fade-up" data-index="1">C</li>
    <li class="fragment fade-up" data-index="2">Java (Enterprise edition)</li>
    <li class="fragment fade-up" data-index="3">Erlang, Elixir, LISP, Javascript, Smalltalk</li>
    <li class="fragment fade-up" data-index="4">[ insert your programming language here ]</li>
    <li class="fragment fade-up" data-index="5">Plaintext prose</li>
</ul>


## Gui iz 4 n00bz
<img src="img/gui-vs-cli.png" style="width: 50%">
- Learning: <s>GUI</s> CLI
- Work: whatever gets shit done



## 0/7 Installing & configuring git


### GNU/Linux
```bash
(sudo) [package_manager] install git (...)

# Ubuntu example
sudo apt install git -y
```

### Mac
```bash
git --version # should be preinstalled
```

### Windows
```bash
If you can't google it you won't make it
```
<br>
[Cheatsheet](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)


### Config (one time thing)

```bash
git config --global user.email [ insert email here ]
git config --global user.name [ insert name here ]
# must in your PATH / aka executable from command line
git config --global core.editor [ insert your favourite command here ]
```
<!-- .element style="width: 100%" -->

#### Example
```bash
git config --global user.email john@example.com
git config --global user.name John Smith 
git config --global core.editor atom
```
<!-- .element style="width: 100%" -->


## 1/7 My first & second commit
### We need a repo!
```bash
mkdir git-workshop # creare a folder for the workshop
cd git-workshop # get inside it
mkdir my-first-repo
cd my-first-repo
```
<!-- .element: class="fragment fade-up" -->
```bash
git init # sets up the git repository

touch rick.txt

[ editor command from config step ] rick.txt
```
<!-- .element: class="fragment fade-up" -->
```bash
# rick.txt
Rick is never gonna:
- give you up
```
<!-- .element: class="fragment fade-up" -->


### Thy first commit
```bash
git status
```
<!-- .element: class="fragment fade-up" -->

```bash
...

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        rick.txt

...
```
<!-- .element: class="fragment fade-up" -->

```
git add rick.txt # no output means OK
```
<!-- .element: class="fragment fade-up" -->

```bash
git commit # now your text editor should open
```
<!-- .element: class="fragment fade-up" -->


```

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master
#
# Initial commit
#
# Changes to be committed:
#	new file:   rick.txt
#
```
<!-- .element: style="width: 100%" -->

```
My first commit ever!
# Please enter the commit message for your changes. Lines starting
# ...
#
```
<!-- .element: style="width: 100%" class="fragment fade-up"-->
```
# 0. save the file
# 1. close the file
```
<!-- .element: style="width: 100%" class="fragment fade-up"-->
```
[master (root-commit) random digits] My first commit ever!
 1 file changed, 1 insertion(+)
 create mode 100644 rick.txt
```
<!-- .element: style="width: 100%" class="fragment fade-up"-->


### The change and the second commit

```bash
[ editor command from before ] rick.txt
```
<!-- .element: class="fragment fade-up" -->
```bash
# rick.txt
Rick is never gonna:
- give you up
- let you down
```
<!-- .element: class="fragment fade-up" -->

```bash
git status
```
<!-- .element: class="fragment fade-up" -->
```
...

modified:   rick.txt

...
```
<!-- .element: class="fragment fade-up" -->
```
git diff rick.txt
```
<!-- .element: class="fragment fade-up" -->


```bash
...
 Rick is never gonna:
 - give you up
+- let you down # the "+" sign and colour == addition
```

<!-- .element: style="width: 100%" -->
```bash
git add rick.txt
git commit
```
<!-- .element: style="width: 100%" class="fragment fade-up"-->

```bash
Extend Rick capabilities
# present, imperative

# the blank line above is important
Rick is no strager to love, he is thinking of
full commitment and this is how he feels.
You would not get this from any other guy. 
# Please enter the commit message for your changes. Lines starting
# ...
```
<!-- .element: style="width: 100%" class="fragment fade-up"-->
```
[master c1d8109] Extend Rick capabilities
 1 file changed, 1 insertion(+)
```
<!-- .element: style="width: 100%" class="fragment fade-up"-->

```
git log
git log --oneline
```
<!-- .element: style="width: 100%" class="fragment fade-up"-->


## 2/7 Create GitHub account


## 3/7 Share it with the world


## 4/7 Clone


## 5/7 Branch


## 6/7 Request to pull


## 7/7 <s>Knife</s> Fork!



<img src="/img/mission-acomplished.jpeg" style="width: 80%">


- [Back to main presentation](/#/2)

## Sources
<div style="font-size: 80%">
- [Google trends](https://trends.google.com/trends/explore?date=all&q=%2Fm%2F05vqwg,%2Fm%2F012ct9,%2Fm%2F08441_)
- [GUI vs CLI](https://lmddgtfy.net/?q=git%20why%20use%20cli%20instead%20of%20gui)
<div>

