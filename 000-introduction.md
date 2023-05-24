## Introduction

Alice and Bob are writers who are collaborating on a new book. They've decided to use Git as their tool for collaborative edition, and a very ancient computer with a [model M keyboard](https://en.wikipedia.org/wiki/Model_M_keyboard) attached to it.

![Model M keyboard](https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/IBM_Model_M.png/800px-IBM_Model_M.png)

To get started, they'll need to set up a Git repository for the book. This will allow them to track changes to the book over time, collaborate on the book together, and easily merge their changes into a single version of the book.

**Note**: this tutorial assumes you have access to both `git` and `ed` commands. If it is not true, feel free to install them:

```bash
sudo apt update
sudo apt install -y git ed
```

### About `ed`

[ed](https://www.cheat-sheets.org/project/tldr/command/ed/) is the original Unix editor. It is a sophisticated piece of software that will help us to manipulate text files in a precise way.

It can be used both programmatically and with an interactive shell, but mostly we will take advantage of its automation characteristics to update the content of the book.

For example, this script will insert a message in the line number two of the `example.txt` file, `w`rite the updated file on disk and `q`uit from `ed`:

```bash
ed example.txt << EOF
2i
This text will be inserted on line number two.
.
w
q
```

### Exercise

<details>
<summary>
(don't click on the left unless you want to unveil the answer to the exercise)

This exercise contains the solution hidden. We are going to use this format during the training: invest some time trying to solve the proposed problem, and ask for support to your trainer if you get lock. But, in case of desperation, you can always click on the little triangle on the left to get a tip or even the whole answer.

We are going to practice with the `ed` command. Start by creating a file:

```bash
cat << EOF > myfile.txt
aaaaaaaaaaa
bbbbbbbbbbb
ccccccccccc
ddddddddddd
EOF

cat myfile.txt
```

Now, use what you have learnt to insert a line of `0` (zeros) between all those `bbbbbbbbbbb` and `ccccccccccc`. Remember: `ed` is a line-based text editor.

*Hint*:

```bash
ed myfile.txt << EOF
█i
00000000000
.
█
█
EOF
```

</summary>

#### Solution:

```bash
ed myfile.txt << EOF
3i
00000000000
.
w
q
EOF

cat myfile.txt
```


</details>