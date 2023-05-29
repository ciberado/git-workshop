# Alice: merging without conflicts

## Concepts and commands

- [x] Branch merging

## Lab

Alice knows that branches must be integrated often to avoid problems, 
so she *merges* the vocabulary branch with the main one

* First, she checks that she is in the `main` branch

```bash
git branch
```

* Now, she checks the differences between both branches

```bash
git diff main vocabulary-chapter-01
```

![Screenshot of the differences between both branches](images/050-diff-main-vocabulary.png)

* There are some long lines, so maybe it would be better to get the difference without using `delta`.
To deactivate it, Alice just pipes the output of `git` to another command

```bash
git diff main vocabulary-chapter-01 | cat -  # diff without using delta
```

* This is the moment to create a new `commit` with the content of both versions merged

```bash
git merge vocabulary-chapter-01 -m "Merged vocabulary"
```

* Now the main branch contains all the words, plus the stranger's profession:

```bash
 cat chapter-01.md \
   | grep -e sand -e shore -e beach -e "lighthouse keeper" -C 9999 --color
```

* The log of the main branch will include the changes performed on the merged one:

```bash
git log
```

* Time passes, it is more and more convenient to simplify the output of the log:

```bash
git log --oneline
```

* And once we start to merging different branches, it is always nice to be able
to actually see the different timelines of our project visually:

```bash
git log --graph --decorate --oneline
```



