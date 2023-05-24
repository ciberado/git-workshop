## Bob: pushing to origin

* And, imbued with the creativity provided by a good cup of coffee, Bob writes his part of the book and commits the changes **on his own repository**

```bash
cat << EOF > chapter-02.md
Tim couldn't believe his luck. The stranger had saved his life, and he was filled with gratitude. "Thank you so much," he said, still panting from the ordeal. "I thought I was going to drown out there."

The lighthouse keeper smiled kindly at him. "You're welcome," he said. "But you should be more careful. The ocean can be dangerous, especially when there's a strong current like today."

Tim nodded, his heart still racing. He realized that he had underestimated the power of the ocean, and he felt humbled by the experience. From that moment on, he made a vow to always respect the sea and to never take its power for granted.

As they made their way back to the shore, the lighthouse keeper introduced himself as John, and they struck up a conversation. Tim learned that John had spent his life guiding ships safely through the treacherous waters of the coast. He was now enjoying his retirement in the nearby town, where he relished fishing and spending time with his grandchildren.

As they said their goodbyes, John turned to Tim with a twinkle in his eye. "Have you ever heard of the mermaids?" he asked, his voice filled with mystery
EOF

ls
git add chapter-02.md
git commit -m "Added chapter 2."
git log --oneline
```

* Satisfied with his masterpiece, he tries to synchronize his repository with the one owned by Alice

```bash
git status             # Branch ahead of origin/main
git push origin main   # Error! This action would mess with Alice's content
```

* Oh, ok: looks like `git` refuses to mess up with the current working copy of Alice's repository. So Bob creates a new branch and runs the `push` command again

```bash
git checkout -b wip-chapter-02
git status
git push origin wip-chapter-02
```

* Finally, he closes his workspace

```bash
cd ../../
```

**Checkpoint snap07!**

## Alice: merging (from the branch created by Bob's push)

* Our preferred writer is back, and having read Bob's message she decides to merge his work

```bash
cd alice/book
git status
ls
git branch
git merge wip-chapter-02
ls
git log --graph --oneline
```

* Alice don't want to get her repo populated by many branches created by Bob, so she deletes the new one

```bash
git branch -d wip-chapter-02
git branch
```

* She decides it will be easier if their respective repositories don't interact directly between each other, so she leaves her workspace to create a solution to this problem

```bash
cd ../../
```

**Checkpoint snap08!**