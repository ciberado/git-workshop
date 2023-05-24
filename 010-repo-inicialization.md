## Alice: repo initialization

* Alice is going to create his own workspace:

```bash
mkdir -p alice/book
cd alice/book
```

* After doing it, she starts writing the story

```bash
cat << EOF > chapter-01.md
## Tim and the waves

Being a young boy, Tim had always been fascinated with the ocean. He would spend hours at the beach, watching the waves crash against the shore, imagining all the creatures that lived beneath the surface. One day, he decided to go for a swim, but before he knew it, he was caught in a strong current and dragged out to sea.

As the waves tossed him around, Tim struggled to stay afloat. Just when he thought he couldn't hold on any longer, a strong hand grabbed his wrist and pulled him to safety. It was a kind stranger who had noticed him struggling from the shore.

From that day forward, Tim's love for the ocean only grew stronger. But he never forgot the lesson he had learned - that sometimes, even the strongest of us need help from others to make it through the rough waters of life.
EOF

ls
```

* Alice wants to enhance the description of the protagonist, but she is afraid of not being satisfied with the result. Because of that, she decides to work on a copy of the original content:

```bash
cp chapter-01.md  chapter-01v2.md
ed chapter-01v2.md << EOF
2i

Tim is a lean and athletic young man with short brown hair and piercing blue eyes. He has a strong jawline and a sun-kissed complexion from spending so much time at the beach. His body is toned and muscular from his active lifestyle, and he exudes a sense of energy and enthusiasm for life.
.
w
q
EOF

ls
cat chapter-01v2.md
```

* She quickly realizes that this tactic isn't practical at all. Luckily, Alice main job is developing software, so she is well versed on `git` and knows how to apply the tool to her other profession. First, she removes the copy:

```bash
rm chapter-01v2.md
```

* And she initializes the `git` database with

```bash
git config --global init.defaultBranch main
git init
ls -a
ls .git
```

* After that, Alice configures the database with her identity

```bash
git config user.name Alice
git config user.email alice@example.com
git config --list

cat .git/config
```
