# Bob: recovering from errors with the reference log

Bob has many nice traits, but he is not the most focused person in the world. Luckily for him,
it is very difficult to *really* mess up things while using git.

## Lab

* Bob comes back to the computer to keep working on the novel.

```bash
cd
cd bob/book
git branch
```

* He realizes that he is not on his *wip* branch, so he changes to it

```bash
git checkout wip-chapter-02
git status
```

* He has a very nice idea about how to continue with the story, and wants to write it down
before it vanishes from his mind

```bash
cat << EOF > chapter-04.md
Tim couldn't keep the curiosity at bay any longer. The dreams of the menacing mermaids haunting him each night had become unbearable. He found himself standing outside the lighthouse, his heart pounding with anticipation. It was time to seek answers from the man who seemed to hold the key to the mysteries of the sea.

Summoning his courage, Tim voiced his concerns. "John, these dreams... they feel so real. Like there's something beneath the waves, trying to reach out to me. Have you ever encountered such experiences?"

John's eyes seemed to hold a hint of mystery as he spoke. "Tim, the sea has its own language, a way of whispering secrets to those who dare to listen. Long ago, I too felt a connection, a call from the depths that echoed in my soul. It led me to encounters, encounters with beings that exist in the realm between dreams and reality."

As Tim absorbed John's cryptic explanation, a mix of apprehension and curiosity swirled within him. The dreams had become an invitation, a portal into a realm where truth and fantasy intertwined. Determined to uncover the hidden messages and the enigma that surrounded him, Tim vowed to embrace the call of the sea and venture forth into a world of wonders, where his own connection with the ocean awaited.
EOF
```

* Bob is so proud! He immediately commits the new chapter

```bash
git add chapter-04.md
git commit -m "New chapter, with Tim learning about his dreams"
```

* Great. Now he takes a look at the evolution of the book... and he notices that something is wrong

```bash
ls
```

* Wait... where is `chapter-03.md`? Oh, of course, it is on the `main` branch. Bob changes to it

```bash
git checkout main
```

* Let's see...

```bash
cat chapter-03.md
```

* Perfect. Also, the name of the integration branch was referring to chapter two,
so to avoid further confusions, Bob decides to delete the old branch

```bash
git branch -D wip-chapter-02
```

* Wait a second... umh... just after pressing the `enter` key, Bob realizes he has
done a mistake: the fourth chapter was in the deleted branch!

```bash
ls
```

* A quick `log` command doesn't show any trace of the lost chapter!

```bash
git log --oneline
```

* Desperate, he calls Alice. And she encourage him to use a more sophisticated version
of the `log` command that will include the references that have been generated recently,
even if they are not part of the branch history anymore

```bash
git log -g --oneline
```

* Oh, ok, ok. It's there. So lets take the SHA-1 of the lost commit

```bash
SHA=$(git log -g --oneline  \
  | grep "Tim learning" \
  | awk  '{print $1}')
echo The lost commit is $SHA.
```

<details>
<summary>
Now Bob can move `HEAD`to that commit in a new branch

```bash
git ███████ -b wip-resurrection $SHA
```
</summary>

---
#### Solution

```bash
git checkout -b wip-resurrection $SHA
```
---
</details>

* Ufff, here it is:

```bash
ls
cat chapter-04.md
git log --oneline
```

* Without losing more time, Bob merges it on main

```bash
git checkout main
git merge wip-resurrection -m "Integrated chapter 4"
```

* Bob has learnt his lesson, and will use `git branch -d` instead of `git branch -D` for now on,
as the lowercase version refuses to delete anything that hasn't been merged

```bash
git branch -d wip-resurrection
```

* Finally, he sends the update to the central server

```bash
git push origin main
```

* Bob understands he needs to take some fresh air before continuing, so he exits his directory

```bash
cd ../..
```