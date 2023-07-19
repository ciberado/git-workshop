# Bob: cloning repositories

Bob collaborates with Alice in writing the book. Both of them use the same old PC, as they find easier to focus in a very constrained environment. 

## Lab

* Bob is wise enough to know he should not mess with the work of Alice, so he creates his own directory

```bash
cd
mkdir bob
cd bob
```

* Alice has explained Bob how to use `git`, so he knows how to get a copy of the database

```bash
git clone ../alice/book
ls
```

* Bob moves to the retrieved copy of the repository, and investigates how Alice has
developed the story until now:

```bash
cd book
ls
git log --oneline
```

* As the copy of the book has been created using the `clone` command, 
the repository keeps a reference to its original address

```bash
git remote
```

<details>
<summary>
Bob wants to check the actual address of the original repo, so he
runs the next command

```
git remote get-███ origin
```
</summary>

---
#### Solution

```
git remote get-url origin
```
---
</details>

* The `clone` command doesn't copy the local configuration of the repo:

```bash
cat .git/config
```

* Bob updates the configuration of his repo with his name and email

```bash
git config user.name Bob
git config user.email bob@example.com
```

