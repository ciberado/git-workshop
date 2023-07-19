# Alice: merging and log format

Our preferred writer is back, and having read Bob's message she decides to merge his work. 

## Lab

* First, she jumps into her workspace

```bash
cd
cd alice/book
```

* And checks that everything is just like she left it:

```bash
git status
ls
```

* But Alice can confirm there is a new branch in her repo

```bash
git branch
```

* So this should be an easy one: Alice merges the changes from Bob into her main branch

```bash
git merge wip-chapter-02
```

* Ok, there it is the promised new chapter

```bash
ls
```

<details>
<summary>
Alice has her preferred way to take a quick look at the repo history, and this looks
like a good moment to put it in play. She uses the `pretty` option to set a particular
format for the log messages

```bash
git log \
  --pretty=██████:"%h%x09%Cgreen%an%Creset%x09%s (%ah) %Cred%d%Creset" \
  --graph
```
</summary>

---
#### Solution

```bash
git log \
  --pretty=format:"%h%x09%Cgreen%an%Creset%x09%s (%ah) %Cred%d%Creset" \
  --graph
```
---
</details>

* Alice doesn't want to get her repo polluted with many branches created by Bob, so she deletes the new one

```bash
git branch -d wip-chapter-02
git branch
```

* Well, time to drink some tea. Alice exits her repo


```bash
cd ../../
```

