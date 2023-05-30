# Alice: merging without conflicts

Alice knows that branches must be integrated often to avoid problems, 
so she will *merge* the vocabulary branch with the main one.

## Concepts and commands

- [x] Branch merging

## Lab

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

* As time passes and we keep adding commits to the history, it is more 
and more convenient to simplify the output of the log

```bash
git log --oneline
```

<details>
<summary>
* And once we start to merging different branches, it is always nice to be able
to see the different timelines of our project visually:

```bash
git log --oneline --gr███
```
</summary>

---
#### Solution

```bash
git log --oneline --graph
```

---
</details>



