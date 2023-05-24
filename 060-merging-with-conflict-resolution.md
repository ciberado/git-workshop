## Alice: merging with conflict resolution

* Alice will keep working hard in increasing the tension of the story

```bash
git status    # on main
sed -i 's/afloat/afloat, fighting the waves/' chapter-01.md
git diff chapter-01.md
git add chapter-01.md
git commit -m "Enhanced paragraph"
```

* At the same time, she also keeps pushing for a richer use of language

```bash
git checkout vocabulary-chapter-01
cat chapter-01.md  | grep strug
sed -i  's/struggling/floundering/' chapter-01.md
git diff chapter-01.md
git add chapter-01.md
git commit -m "Replaced struggling"
```

**Checkpoint snap03!**

* Time to *merge* both branches again, but in this case we have a more complex situation

```bash
git status
git branch
git checkout main
git diff vocabulary-chapter-01
git merge vocabulary-chapter-01 -m "Merged vocabulary" # Conflict!!
git status
git diff --name-only --diff-filter=U --relative        # List conflicting files
cat chapter-01.md
git diff
```

* No problem: Alice manually merges both changes and submits the new *commit*

```
L0=$(grep -n "<<<<<<<" chapter-01.md | cut -f1 -d:)
LF=$(grep -n ">>>>>>>" chapter-01.md | cut -f1 -d:)

echo Replacing from $L0 to $LF.

ed chapter-01.md << EOF
${L0},${LF}d
7i
As the waves tossed him around, Tim struggled to stay afloat, fighting the waves. Just when he thought he couldn't hold on any longer, a strong hand grabbed his wrist and pulled him to safety. It was the lighthouse keeper who had noticed him floundering from the shore.
.
w
q
EOF

cat chapter-01.md
```

* She double checks everything is as intended to be, and commits the new version:

```bash
git status
git add chapter-01.md
git commit -m "Solved conflict, merged keeper and floundering."
git log --graph --decorate --oneline
```