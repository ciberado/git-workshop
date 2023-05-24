## Introduction

Alice and Bob are writers who are collaborating on a new book. They've decided to use Git as their tool for collaborative edition, and a very ancient computer with a [model M keyboard](https://en.wikipedia.org/wiki/Model_M_keyboard) attached to it.

![Model M keyboard](https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/IBM_Model_M.png/800px-IBM_Model_M.png)

To get started, they'll need to set up a Git repository for the book. This will allow them to track changes to the book over time, collaborate on the book together, and easily merge their changes into a single version of the book.

**Note**: this tutorial assumes you have access to both `git` and `ed` commands. If it is not true, feel free to install them:

```bash
sudo apt update
sudo apt install -y git ed
```