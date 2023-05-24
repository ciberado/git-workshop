## Alice: basic branching

* Reading the chapter again, Alice understands she has to enhance the vocabulary of the chapter. But she also wants to keep developing the story, so she creates a *branch* to undertake that task:

```bash
git checkout -b vocabulary-chapter-01
git status
git branch
cat .git/HEAD
cat .git/refs/heads/main
cat .git/refs/heads/vocabulary-chapter-01  # right now, it is the same than main
```

* Alice will replace one of the appearence of the word *beach*

```bash
cat chapter-01.md | grep beach
sed -z -i 's/beach/soar/2' chapter-01.md
cat chapter-01.md | grep -e soar -e beach
git add chapter-01.md
git commit -m "Replacing repetitive words"
git log
```

**Checkpoint snap02**

* Probably she will also change other words, but right now she wants to modify an important point of the story. So she moves `HEAD` to the main branch

```bash
git checkout main
cat chapter-01.md
cat chapter-01.md | grep -e soar -e beach
git log
```

* The saviour of Tim has actually an interesting profession, much more evocative than a simple *kind stranger*

```bash
sed -i 's/a kind stranger/the likehouse keeper/' chapter-01.md
cat chapter-01.md
git add chapter-01.md
git commit -m "Introducing the lighthouse keeper"
git log
```
