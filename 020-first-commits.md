# Alice: first commits

## Concepts and commands

- [x] Working zone
- [x] Index/staging area
- [x] `status`
- [x] `add`
- [x] Changeset
- [x] Revision
- [x] SHA-1
- [x] `commit`
- [x] `log`
- [x] HEAD, HEAD~, HEAD~~, HEAD~2
- [x] Show specific revisions of a file
- [x] Get the changesets applied between two revisions of a file

## Lab

* Our author wants to take a look at the current state of her repo:

```bash
git status
```

* Time to add the current version of the chapter to the git *index* (aka *staging* zone):

```bash
git add chapter-01.md
```

* The output of the `add` command was not very verbose, so Alice looks again at the state of the repo

```bash
git status
```

* Now that everything seems on its place, she will put the current text of the chapter in the repository by creating her first *commit*:

```bash
git commit -m "Initial draft of the first chapter"
```

* She wants to check that everything is being tracked as expected. To do it, she starts by using the `log` command:

```bash
git log
```

* How does the repo knows what is the current position in the chain of revisions? We can explore the structure created on disk by the `commit`:

```bash
cat .git/HEAD
cat .git/refs/heads/main     # Whole sha-1 HEAD
```

<details>
<summary>
Actually, there are several ways to store this information. What would
be the best way to programmatically retrieve the SHA-1 of the current
revision?

```bash
git rev-p████ HEAD
```
</summary>

#### Solution

```bash
git rev-parse HEAD
```

</details>

* Now Alice can safely apply the new paragraph to the text, without any fear
to lose the content of the previous version:

```bash
git status

ed chapter-01.md << EOF
2i

Tim is a lean and athletic young man with short brown hair and piercing blue eyes. He has a strong jawline and a sun-kissed complexion from spending so much time at the beach. His body is toned and muscular from his active lifestyle, and he exudes a sense of energy and enthusiasm for life.
.
w
q
EOF
```

* Good. Let's see what are the `unstaged` changes

```bash
git status
```

* The author is interested to check what are the differences (the *changesets*) between the current *working area* and the *commited revision*.

```
git diff chapter-01.md
```

* Looks good, so Alice puts the new changes in the `git` database

```bash
git add chapter-01.md
git commit -m "Added description of Tim"
git status
```

* Alice is happy to be able to travel through the history of all the
applied changes by using the `log` command:

```bash
git log
```

* After taking a break and having her breakfast, our writer wants to refresh how was the first version of the story. She starts by listing all the available revisions:

```bash
git rev-list --all
```

* Alice knows how to get the SHA-1 the current revision:

```bash
git rev-parse HEAD
```

* And also, the SHA-1 of the previous revision, corresponding in this
case to the original `commit`

```bash
git rev-parse HEAD~
```

* Being a developer, Alice cannot resist the temptation of playing with the revision SHA-1s to retrieve a particular version of the file:


```bash
PREV_REVISION=$(git rev-parse HEAD~)
echo The previous revision was $PREV_REVISION
git show $PREV_REVISION:chapter-01.md
```

* Although, in the end, she knows it is easier to just use the symbolic reference name:


```bash
git show HEAD~:chapter-01.md
```

<details>

<summary>
Umh... ok... and how can Alice see the differences between the current version of the chapter and the originally commited one (two revisions ago)? 


```bash
git d███ HEAD~ chapter-01.md
```
</summary>

#### Solution

```bash
git diff HEAD~ chapter-01.md
```

</details>

## Questions

* What does it mean that a set of files are *untracked*?
* Which command would allow you to access the version of `chapter-01.md` stored **two** revisions ago? And five?
