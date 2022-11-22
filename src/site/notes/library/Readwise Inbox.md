---
{"dg-publish":true,"permalink":"/library/readwise-inbox/"}
---

[[Home\|Home]]

# Readwise Inbox
[Readwise](https://readwise.io/dashboard)

## Pending
- [[library/highlights/books/Free to Learn\|Free to Learn]]
- [[library/highlights/books/Quiet\|Quiet]]
- [[library/highlights/books/The Goal\|The Goal]]
- [[library/highlights/books/How to Stay Alive in the Woods\|How to Stay Alive in the Woods]]
- [[library/highlights/articles/Digital product launches and product growth\|Digital product launches and product growth]]
- [[library/highlights/articles/50% of Gen Z and Gen Alpha make in-game purchases\|50% of Gen Z and Gen Alpha make in-game purchases]]
- [[library/highlights/books/Introduction to Statistics\|Introduction to Statistics]]
- [[library/highlights/books/The Lean Six Sigma Pocket Toolbook\|The Lean Six Sigma Pocket Toolbook]]
- [[library/highlights/books/The Phoenix Project\|The Phoenix Project]]
- [[library/highlights/tweets/🪄Walt Disney’s Creative...\|🪄Walt Disney’s Creative...]]
- [[library/highlights/articles/What is the Theory of Constraints and why I should bother\|What is the Theory of Constraints and why I should bother]]
- [[library/highlights/tweets/I've Been Tinkering With...\|I've Been Tinkering With...]]
- [[library/highlights/tweets/At the Very Least, You S...\|At the Very Least, You S...]]
- [[library/highlights/articles/Spaced Repetition for Efficient Learning\|Spaced Repetition for Efficient Learning]]
- [[library/highlights/books/How to Think Like a Roman Emperor\|How to Think Like a Roman Emperor]]
- [[library/highlights/books/Working Backwards\|Working Backwards]]


## Misc
Original Querry
```SQL
TABLE file.inlinks AS Inlinks, file.outlinks AS Outlinks, file.tags AS Tags
FROM #pkm/process 
WHERE length(file.inlinks) > 0 OR length(file.outlinks) > 1 Or length(file.tags) > 2
SORT file.size ASC
```
 