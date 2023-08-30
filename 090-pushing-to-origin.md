# Bob: pushing to origin

## Lab

* Imbued with the creativity provided by a good cup of coffee, Bob writes his part of the book and commits the changes **on his own repository**

```bash
cat << EOF > chapter-02.md
Tim couldn't believe his luck. The stranger had saved his life, and he was filled with gratitude. "Thank you so much," he said, still panting from the ordeal. "I thought I was going to drown out there."

The lighthouse keeper smiled kindly at him. "You're welcome," he said. "But you should be more careful. The ocean can be dangerous, especially when there's a strong current like today."

Tim nodded, his heart still racing. He realized that he had underestimated the power of the ocean, and he felt humbled by the experience. From that moment on, he made a vow to always respect the sea and to never take its power for granted.

As they made their way back to the shore, the lighthouse keeper introduced himself as John, and they struck up a conversation. Tim learned that John had spent his life guiding ships safely through the treacherous waters of the coast. He was now enjoying his retirement in the nearby town, where he relished fishing and spending time with his grandchildren.

As they said their goodbyes, John turned to Tim with a twinkle in his eye. "Have you ever heard of the mermaids?" he asked, his voice filled with mystery.
EOF

ls
git add chapter-02.md
git status
git commit -m "Added chapter 2."
git log --oneline
```

* Satisfied with his masterpiece, he will try to synchronize his repository with the one owned by Alice. First,
he will check that everything is in place again

```bash
git status             # Branch ahead of origin/main
```

* Now he tries to update Alice's main branch with his own... but something goes wrong:

```bash
git push origin main  # Error
```

* Oh, ok: `git`has detected that Alice is also working in her copy of the main branch, and messing with it
could be result in a very confusing situation for her. So the operation has failed. Bobs understands the
situation, and to solve it creates a different branch:

```bash
git checkout -b wip-chapter-02
```

* Now he can safely push his content, as it will appear just as another branch in Alice's repo

```bash
git status
git push origin wip-chapter-02
```

* Everything looks fine, but let's just check it:

```bash
git log --oneline --decorate \
  | grep origin/wip-chapter-02 -C 9999
```

* All good, so he closes his workspace
  
```bash
cd ../../
```
