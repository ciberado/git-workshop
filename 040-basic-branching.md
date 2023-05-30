# Alice: Basic branching

Reading the chapter again, Alice understands she has to enhance the vocabulary of the descriptions. But she also wants to keep developing the story, separating both tasks.

## Concepts and commands

- [x] Branches

## Lab

<details>
<summary>
so she creates a *branch* to undertake that task.

```bash
git status
git branch                          # show branches
git b█████ vocabulary-chapter-01    # create new branch
git status
git branch                          # show branches
git c███████ vocabulary-chapter-01  # move HEAD to the new branch
git status
git branch                          # show branches
```
</summary>

---
#### Solution

```bash
git status
git branch
git branch vocabulary-chapter-01
git status
git branch
git checkout vocabulary-chapter-01
git status
git branch
```
---

</details>

* Our artist wants to check where *HEAD* is pointing to:

```bash
cat .git/HEAD
cat .git/refs/heads/vocabulary-chapter-01  # It contains the same value than main!
cat .git/refs/heads/main
```

* Alice will replace one of the appearance of the word *beach* with the much more beautiful *sand*

```bash
cat chapter-01.md | grep beach
sed -z -i 's/beach/sand/2' chapter-01.md
cat chapter-01.md | grep -e sand -e beach -e shore -e border
git add chapter-01.md
git commit -m "Replacing repetitive words"
git log
```

* Probably she will also change other words, but right now she wants to modify an important point of the story. So she moves `HEAD` to the main branch

```bash
git checkout main
cat chapter-01.md | grep -e sand -e beach # No sand, here
git log
```

* The saviour of Tim has actually an interesting profession, much more evocative than a simple *kind stranger*

```bash
sed -i 's/a kind stranger/the lighthouse keeper/' chapter-01.md
cat chapter-01.md
git add chapter-01.md
git commit -m "Introducing the lighthouse keeper"
git log
```


## Questions

* Why, just after creating the new branch, `main` and `vocabulary-chapter-01` had the same SHA-1 value?