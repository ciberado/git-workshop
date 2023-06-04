# Bob finds the author of a typo

Here we will see how Bob is able to trace who introduced a bug in the novel, in the
form of a spelling error.

## Concepts and command

- [x] `blame`

## Lab: Alice

* Alice worked for a lot hours today, and although she is exhausted, she also wants to
review the state of the book. So she goes to her repo and gets the updates

```bash
cd
cd alice/book
git pull origin master
```

* The new chapter written by Bob looks very promising! But Alice notices a problem: John is not
living in the *lighthouse* anymore. So she will help his mate correcting it... but she will
inadvertently also introduce another type of error in the sentence:

```bash
sed -i "s/the lighthouse/the olt man's home/" chapter-04.md
cat chapter-04.md
```

* Job done, `add`, `commit` and `push`... but she is so tired that the commit message
is no specially inspired

```bash
git add chapter-04.md
git commit -m "Minor change"
git push origin main
```

* And, finally, she leaves her working area

```bash
cd ../..
```

## Lab: Bob

* After the weekend, Bob comes back to the old computer continue the development of his
chapter

```bash
cd
cd bob/book
git pull origin main
```

* When he starts editing the text of chapter four, he realizes there is something odd...
a typo in a sentence he doesn't remember to have introduced

```bash
cat chapter-04.md | grep "the olt man's home" -C 999
```

* Well... maybe he made a change in the text and doesn't remember it. Or not. He
needs to know, so he asks `git` about who wrote each line of the book:

```bash
git blame chapter-04.md \
  | grep -e Alice -e Bob
```

* Ok, mystery solved: so it was a change made by Alice. Bob agrees with the
modification, so he just needs to update the wrong word

```bash
sed -i "s/the olt/the old/" chapter-04.md
cat chapter-04.md | grep "the old man's home" -C 9999
```

* And store it in the common repo

```bash
git add chapter-04.md
git commit -m "Fixed typo"
git push origin main
```

* Bob exists his working directory

```bash
cd ../..
```