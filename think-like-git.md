# Think like git
## by Olgierd &#34;Allgreed&#34; Kasprowicz


<img src="img/git-gets-easy.png" style="width: 200%">


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
