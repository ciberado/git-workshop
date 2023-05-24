## Alice: diff configuration

* She decides that a more fancy diff tool would provide better feedback, so she configures `delta`

```bash
wget -P /tmp https://github.com/dandavison/delta/releases/download/0.15.1/git-delta_0.15.1_amd64.deb
sudo dpkg -i /tmp/git-delta_0.15.1_amd64.deb
delta --version

git config core.pager delta
git config interactive.diffFilter "delta --color-only"
git config delta.navigate true
git config delta.light false  # or true!
git config delta.side-by-side true
git config delta.line-numbers true
git config merge.conflictstyle diff3
git config diff.colorMoved default

git show
```

* Alice thinks that maybe it would be more interesting to leave the description of Tim to the imaganation of the reader, so he goes back in time to the previous revision

```bash
cat .git/HEAD
cat .git/refs/heads/main
git checkout $PREV_REVISION
cat chapter-01.md
git log
cat .git/HEAD                  # Dettached!
cat .git/refs/heads/main       # main is in the future
```

* Nah, it was not a good idea: Tim  has to have a particular appearance for this story to work. So Alice reverses the timetravelling:

```bash
git switch -
git log
cat chapter-01.md
cat .git/HEAD
```