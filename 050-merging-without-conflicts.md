## Alice: merging without conflicts

* Alice knows that branches must be integrated often to avoid problems, so she *merges* the vocabulary branch with the main one

```bash
git branch                                   # check current branch
git diff main vocabulary-chapter-01 | cat -  # diff without using delta
git diff main vocabulary-chapter-01          # diff with delta (it doesn't understand the different time of the commits)
git merge vocabulary-chapter-01 -m "Merged vocabulary" ## ORT strategy
cat chapter-01.md
git log --oneline
git log --graph --decorate --oneline
```