## Alice: centralized repository creation

* Alice is going to create a repository intended to have only the data, without any working directory. This way, both Alice and Bob will be able to work against a common *integration branch*. By convention, bare repos ends with `.git`:

```bash
mkdir central.git
cd central.git
git init --bare --shared
ls
```

* Our main writer will need to synchronize the content of both repositories, from his own content

```bash
cd ../alice/book
git status
git remote add origin ../../central.git/
git push origin main   # No problem, as it is a barebone repo
git push origin v1     # Annotated tags are usually pushed, too
```

### Alice: preparing new content

* Happy to see how everything is under control, she writes a new chapter and synchronizes everything

```bash
cat << EOF > chapter-03.md
Tim woke up with a start, his heart racing and his body drenched in sweat; it took him a few moments to realize that he had been dreaming about the mermaids again. He had been having the same dream for weeks now - the mermaids would appear out of nowhere, their beautiful faces twisted into a sinister snarl as they dragged him under the water.

He knew it was silly to be afraid of something that didn't exist, but he couldn't shake the feeling that there was some truth to his dreams. The sea was full of mysteries and he had heard stories of sailors who had encountered strange creatures on their voyages. Perhaps there was more to his dreams than just his imagination.

As he lay in bed, trying to calm his racing thoughts, Tim made a decision. He would set out to learn as much as he could about the sea and the creatures that dwelled within it. If there was any truth to his dreams, he wanted to be prepared. And he knew where to start his investigation.
EOF

ls
git add chapter-03.md
git commit -m "New chapter"
git push origin main
```

* Wow, Alice has done a tone of work. She now leaves her workspace

```bash
cd ../..
```

**Checkpoint snap09!**

### Bob: pulling

* Bob doesn't want to write today, but he is interested in reading what Alice has added to the story. First, he will check his own repository

```bash
cd bob/book
git status
git checkout main
```

* Now, he will update the configuration of the repository, setting his *origin* pointing to the centralized one

```
git remote
git remote get-url origin
git remote rename origin alice
git remote add origin ../../central/
git remote
```

* Not being completely sure of how to proceed, Bob wants to check the content of the central repo before merging it with its own

```bash
git fetch origin main    # Doesn't affect working tree
git diff FETCH_HEAD      # Diff against the fetched data
```

* Ok, doesn't seems dangerous: a new file will note trigger a conflict, so Bob merges the content of the remote branch

```bash
git pull origin main     # Or git merge FETCH_HEAD
git log --graph --decorate --online
```

* Another fantastic job, Bob thinks. And he leaves the workspace

```bash
cd ../..
```

**Checkpoint snap10!**