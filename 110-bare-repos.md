# Alice: centralized repository creation

Alice is going to create a repository intended to have only the data, without any working directory. This way, both Alice and Bob will be able to work against a common *integration branch*. 

## Concepts and commands

- [x] Bare repositories
- [x] `--bare`

## Lab

* First, Alice goes to the top directory to create the folder for the new repo. By convention, a
bare repos directory name ends with `.git`:

```bash
cd
mkdir central.git
```

* Jumping inside the newly created directory, our Writer is able to initialize it properly

```bash
cd central.git
git init --bare
```

* Here it is the interesting part: the new repository only contains the database, without
a working directory

```bash
ls
```

* Now Alice can go back to her own repo and configure a remote reference to the bare one

```bash
cd ../alice/book
git status
git remote add origin ../../central.git/
```

* As the *origin* repo doesn't have a working directory, there is no problem in
running a `push` command to execute a *remote merge* directly against the main branch

```bash
git push origin main
```

* Remote annotations usually are attached to versions of the repo that are significant
and should be share, so Alice also decides to push `v1` into the central repo

```bash
git push origin v1
```

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

