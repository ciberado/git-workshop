## Alice: tagging

* Our writer decides she has a good enough first chapter, so she proceeds to delete the vocabulary branch

```bash
git branch -d vocabulary-chapter-01
git branch
git log --graph --decorate --oneline # Commits don't belong to the deleted branch anymore
```

**Checkpoint snap04!**

* Finally, Alice marks this commit as the first version of the book with a tag

```bash
git tag v1
git log --oneline
ls .git/refs/tags
cat .git/refs/tags/v1
cat .git/refs/heads/main  # points to the same object that the tag
```

* Ouch: Alice realizes that she used a lightweight tag, but she would like to set a comment. So she deletes the tag an creates an annotated one

```bash
git tag -d v1
ls .git/refs/tags
git tag -a v1 -m "First chapter is ready to be reviewed!"
ls .git/refs/tags
cat .git/refs/heads/main
cat .git/refs/tags/v1      # the tag ref points to a tag object, so doesn't match the last commit
```

* Alice is very proud of her work, and closes the laptop to get some fresh air and inspiration

```bash
cd ../../
```

**Checkpoint snap05!**