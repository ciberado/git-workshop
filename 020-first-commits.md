## Alice: first commits

* Time to add the current version of the chapter

```bash
git status
git add chapter-01.md
git commit -m "Initial draft of the first chapter"
```

* She wants to check that everything is being tracked as expected:

```bash
git log
cat .git/HEAD
cat .git/refs/heads/main     # Whole sha-1 HEAD
git rev-parse --short HEAD   # Short sha-1 of the current HEAD
```

**Checkpoint snap01**

* Now she can safely apply the new paragraph to the text

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
git diff chapter-01.md
```

* Looks good, so Alice puts the changes in the `git` database

```bash
git add chapter-01.md
git commit -m "Added description of Tim"
git status
git log
```

* After taking a break and having her breakfast, our writer wants to refresh how was the first version of the story

```bash
git rev-list --all     # list revisions
git rev-parse HEAD     # get the current sha-1
git rev-parse HEAD~1   # get the previous sha-1
PREV_REVISION=$(git rev-parse HEAD~1)
echo The previous revision was $PREV_REVISION
git show $PREV_REVISION:chapter-01.md
git show HEAD~1:chapter-01.md
```