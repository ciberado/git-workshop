
cd
cd alice/book
git status

git checkout -b feat-meta

cat << EOF > about-authors.md
## Biography

Alice is a software developer with a deep love for writing and literature. When she's not immersed in coding, you can find her sailing the open waters, drawing inspiration from the vastness of the ocean for her imaginative stories that explore the fusion of technology and humanity.

Bob is a skilled developer and aspiring author, blending his programming prowess with imaginative storytelling. He finds solace in both coding and sailing, where the rhythmic waves inspire his fiction, delving into the intricate connections between technology, the human psyche, and the vast mysteries of the ocean.
EOF

ls

git add about-authors.md
git commit -m "Created first draft of the authors biography."


sed -i "s/Chapter one/Chapter 1/" chapter-01.md 
sed -i "s/Chapter two/Chapter 2/" chapter-02.md 
sed -i "s/Chapter three/Chapter 3/" chapter-03.md 
sed -i "s/Chapter four/Chapter 4/" chapter-04.md 

git add chapter*.md
git commit -m "Updated titles to figures"

cat << EOF > summary.md
## Summary

Tim's story follows a young person who has always been captivated by the ocean. During a fateful encounter while swimming, Tim is saved from a dangerous current by a mysterious lighthouse keeper named John. As they connect, Tim discovers John's own enigmatic experiences with the sea's secrets, leading him to question the meaning behind his haunting nightmares of malevolent mermaids. Drawn by a sense of wonder and curiosity, Tim sets out on a journey to understand the mysteries of the ocean and the potential connection he shares with it. The story explores the mystical allure of the sea, unraveling the depths of imagination and reality.
EOF

git add summary.md
git commit -m "First draft of the summary"




git switch main

ls

cat << EOF >> chapter-05.md
## Chapter 5

In the depths of the shimmering sea, a young mermaid found herself plagued by haunting dreams of a young person. In her slumber, vivid visions of him swimming above the waves filled her mind. She marveled at his interaction with the ocean, wondering why he seemed so drawn to its vast expanse.

As she swam through the ocean's depths, her dreams of the young person became a guiding light, urging her toward a future that held both wonder and uncertainty. She embraced the journey, ready to discover the true meaning behind their shared dreams.
EOF

git add chapter-05.md
git commit -m "Introduction of the mermaid protagonist"

cat chapter*.md | grep Chapter


git branch

git log feat-meta --oneline

git show ":/figures" -- chapter-01.md

git cherry-pick ":/figures"

git status
git log --oneline --graph

cat chapter*.md | grep Chapter
