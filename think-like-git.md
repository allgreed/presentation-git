# Think like git
## by Olgierd &#34;Allgreed&#34; Kasprowicz



## Myths
<img src="/img/mythbusters.jpg">


## Git is magic
<img src="img/git-gets-easy.png" style="width: 200%">


## Gui iz 4 n00bz
<img src="img/gui-vs-cli.png" style="width: 50%">
- Learning: <s>GUI</s> CLI
- Work: whatever gets shit done

[Follow up reading](https://lmddgtfy.net/?q=git%20why%20use%20cli%20instead%20of%20gui)



## Let's git to it! From scratch!

- <span class="fragment fade-up" data-fragment-index="1">DVCS</span>
- <span class="fragment fade-up" data-fragment-index="2">Version control system</span><span class="fragment fade-up" style="color:#b58900" data-fragment-index="7"> + network = ↑</span>
- <span class="fragment fade-up" data-fragment-index="3">Stupid content tracker</span><span class="fragment fade-up" style="color:#b58900" data-fragment-index="6"> + branches & tags = ↑</span>
- <span class="fragment fade-up" data-fragment-index="4">Persistent map</span><span class="fragment fade-up" style="color:#b58900" data-fragment-index="5"> + trees & commits = ↑</span>



## Persistent map


### A map?

<img src="/img/pirate.jpg">


### Implementation

- Keys: SHA1 of the content<br>
- Values: the content

<br>

``` bash
$ echo "elorap" | git hash-object --stdin
```
<!-- .element: class="fragment fade-left" -->

```
2511755d6bfe6afb0462cc8ba7b254e371b7e191
```
<!-- .element: class="fragment fade-right" -->


### Details

<br>

``` bash
$ echo "elorap" | git hash-object --stdin
2511755d6bfe6afb0462cc8ba7b254e371b7e191
```

```bash
$ echo "elorap" | sha1sum -
```
<!-- .element: class="fragment fade-left" -->

```
8aec9bf5a852dbe30b3ebe9854be53feef471a5a  -
```
<!-- .element: class="fragment fade-right" -->

<br>
```
git_hash(content) = sha1("{type} {size_in_bytes}\0{content}")
```
<!-- .element: class="fragment fade-up" -->

```bash
echo -e "blob 7\0elorap" | sha1sum -
```
<!-- .element: class="fragment fade-left" -->

```
2511755d6bfe6afb0462cc8ba7b254e371b7e191  -
```
<!-- .element: class="fragment fade-right" -->


### Persistence

```
git init
```
<!-- .element: class="fragment fade-up" -->

#### Insert

```bash
echo "elorap" | git hash-object --stdin -w
```
<!-- .element: class="fragment fade-left" -->

```
2511755d6bfe6afb0462cc8ba7b254e371b7e191
```
<!-- .element: class="fragment fade-right" -->

#### Retrive

```
git cat-file -p 2511755d6bfe6afb0462cc8ba7b254e371b7e191
```
<!-- .element: class="fragment fade-left" -->

```
elorap
```
<!-- .element: class="fragment fade-right" -->


### Demo
```
mkdir -p /tmp/demos/persistent-map
cd $_
git init
echo "elorap" > whatever.txt
ranger .git

git hash-object whatever.txt -w
git cat-file -p 2511755d6bfe6afb0462cc8ba7b254e371b7e191
ranger .git
```


### Typeof "elorap" ?
```
git cat-file -t 2511755d6bfe6afb0462cc8ba7b254e371b7e191
```
<!-- .element: class="fragment fade-left" data-fragment-index="1"-->
## Blob
<!-- .element: class="fragment fade-right" data-fragment-index="3"-->
<img src="img/the_blob.jpg" style="width: 70%; margin: 0">
<!-- .element: class="fragment fade-right" data-fragment-index="2"-->



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
