## Bob: cloning repositories

* Bob collaborates with Alice in writing the book. Both of them use the same old PC, as they find easier to focus in a very constrained environment. But Bob is wise enough to know he should not mess with the work of Alice, so he creates his own directory

```bash
mkdir bob
cd bob
```

* Alice has explained Bob how to use `git`, so he knows how to get a copy of the database

```bash
git clone ../alice/book
ls
cd book
ls
git log --oneline
```

* As the copy of the book has been created using the `clone` command, the repository keeps a reference to its origin

```bash
git remote
git remote get-url origin
```

* Bob updates the configuration of his repo

```bash
git config user.name Bob
git config user.email bob@example.com
```

**Checkpoint snap06!**
