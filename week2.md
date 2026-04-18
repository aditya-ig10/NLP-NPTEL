NPTEL NATURAL LANGUAGE PROCESSING – WEEK 2
Highly Detailed Subject-Focused Summary
(Only academic content included)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. SPELLING CORRECTION IN NLP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Spelling correction is the process of detecting and correcting wrongly
typed words in text.

Examples:
- behaf → behalf
- acress → actress
- recieve → receive

Importance:
- Search engines
- Text editors
- OCR correction
- Chat applications
- Speech-to-text cleanup

Two main tasks:

1. Error Detection
   Identify whether a word is wrong.

2. Error Correction
   Replace it with the most probable correct word.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
2. TYPES OF SPELLING ERRORS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

━━━━━━━━━
A. Non-Word Errors
━━━━━━━━━

The typed word does not exist in dictionary.

Examples:
- behaf
- recieve
- acress

Detection:
If word not found in dictionary → likely error

━━━━━━━━━
B. Real-Word Errors
━━━━━━━━━

Typed word exists, but wrong in context.

Examples:
- three → there
- piece → peace
- too → two

Harder than non-word errors because spelling is valid.

Need context understanding.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
3. EDIT DISTANCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Edit Distance measures similarity between two strings.

Definition:
Minimum number of operations needed to convert one word into another.

Allowed operations:

1. Insertion
   Add a character

   cat → cart

2. Deletion
   Remove a character

   cart → cat

3. Substitution
   Replace one character

   cat → cut

Used for:
- Spell checking
- DNA sequence matching
- Search correction
- OCR correction

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
4. MINIMUM EDIT DISTANCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Minimum Edit Distance = lowest possible total edits required.

Example:

intention → execution

Different edit paths possible.
Choose one with minimum cost.

If each operation cost = 1
This is standard Levenshtein distance.

If substitution cost = 2
Distance changes.

Hence result depends on cost model.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
5. LEVENSHTEIN DISTANCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

A common edit distance where:

Insertion = 1
Deletion = 1
Substitution = 1

Used widely because simple and efficient.

Example:

kitten → sitting

k → s (substitution)
e → i (substitution)
+ g (insertion)

Distance = 3

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
6. EDIT DISTANCE AS SEARCH PROBLEM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Transform source word into target word using sequence of edits.

Components:

Initial State:
Original word

Goal State:
Target word

Operators:
- Insert
- Delete
- Substitute

Path Cost:
Total edit cost

Goal:
Find minimum-cost path.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
7. DYNAMIC PROGRAMMING FOR EDIT DISTANCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Brute force checking all edit sequences is expensive.

Dynamic Programming solves efficiently using subproblems.

Let:

X = source string length n
Y = target string length m

Define:

D(i,j)

= minimum edit distance between:

first i chars of X
and
first j chars of Y

Final answer:

D(n,m)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
8. DP TABLE INITIALIZATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Base cases:

D(i,0) = i

Meaning:
Convert first i letters to empty string using deletions.

D(0,j) = j

Meaning:
Convert empty string to first j letters using insertions.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
9. DP RECURRENCE RELATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

For each cell D(i,j):

Take minimum of:

1. Delete:
D(i-1,j) + 1

2. Insert:
D(i,j-1) + 1

3. Match/Substitute:

If X[i] = Y[j]:
D(i-1,j-1)

Else:
D(i-1,j-1) + cost

Thus:

D(i,j) = min(all three options)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
10. TIME AND SPACE COMPLEXITY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

If source length = n
target length = m

Time Complexity:
O(nm)

Space Complexity:
O(nm)

Efficient for moderate strings.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
11. BACKTRACE / ALIGNMENT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Sometimes distance alone is insufficient.

Need to know exact changes made.

Store direction while filling table:

←  insertion
↑  deletion
↖  match/substitution

Then trace backward from final cell.

This gives alignment.

Example:

I N T E * N T I O N
* E X E C U T I O N

Shows inserted/deleted/replaced characters.

Used in:
- Bioinformatics
- OCR
- Translation alignment

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
12. WEIGHTED EDIT DISTANCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Not all mistakes are equally likely.

Example:
Typing q instead of w is common
Typing q instead of p less common

So assign custom costs.

Insertion cost:
ins(c)

Deletion cost:
del(c)

Substitution cost:
sub(a,b)

This improves real-world spelling correction.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
13. CONFUSION MATRIX
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

A confusion matrix stores common typing mistakes.

Example:

e typed instead of r
m typed instead of n

Used to estimate probable user errors.

More frequent mistakes receive lower penalty.

Useful in:
- Keyboard typo correction
- OCR repair
- Mobile autocorrect

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
14. KEYBOARD-BASED ERRORS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Letters near each other on keyboard are mistyped often.

Examples:

s instead of a
r instead of e
n instead of m

Weighted edit distance handles this better.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
15. TRANSPOSITION / METATHESIS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Two adjacent letters swap positions.

Example:

teh → the
form → from

This is common human typing error.

Standard Levenshtein does not directly model it.

Need Damerau-Levenshtein Distance.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
16. DAMERAU–LEVENSHTEIN DISTANCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Adds one extra operation:

4th Operation:
Transpose adjacent letters

Allowed edits:

1. Insertion
2. Deletion
3. Substitution
4. Transposition

Useful for common typing mistakes.

Example:

acress → actress
teh → the

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
17. FINDING BEST DICTIONARY MATCH
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Given wrong word, find closest correct word.

Naive Method:

Compare input word with every dictionary word.

Choose smallest edit distance.

Problem:
Slow for huge dictionaries.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
18. USING TRIE FOR FASTER SEARCH
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Trie = prefix tree storing dictionary words.

Advantages:
- Efficient lookup
- Shared prefixes
- Faster candidate generation

Used in spell checkers and autocomplete.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
19. GENERATING ALL POSSIBLE EDIT WORDS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Another approach:

Generate all words within edit distance ≤ 1 or 2
Then check dictionary.

Includes:

- delete one char
- insert char
- substitute char
- transpose letters

Problem:
Huge number of candidates.

Example:
Length 9 word with alphabet size 36
Can generate 100k+ candidates.

Very expensive.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
20. SYMMETRIC DELETE SPELLING CORRECTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Efficient modern technique.

Method:

Offline:
Generate delete variants of dictionary words.

Online:
Generate delete variants of input word.

Then match quickly.

Benefits:
- Much fewer candidates
- Fast lookup

Example:
Word length 9 with edit distance ≤2
Only ~45 delete variants.

Used in high-speed spell systems.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
21. CANDIDATE GENERATION OBSERVATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Statistics:

- Around 80% errors within edit distance 1
- Almost all errors within edit distance 2

Therefore systems usually search small edit distances first.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
22. NOISY CHANNEL MODEL
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

One of most important spelling correction models.

Observed word = x (possibly wrong)
Correct word = w

Need:

Choose w maximizing:

P(w | x)

Using Bayes Rule:

P(w|x) ∝ P(x|w) × P(w)

Where:

P(w)
= probability correct word occurs naturally
(Language Model)

P(x|w)
= probability correct word became error
(Error Model)

Choose candidate with maximum score.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
23. LANGUAGE MODEL IN SPELLING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

P(w) gives commonness of word.

Examples:

the > zebra
house > hause

Frequent words preferred unless strong evidence otherwise.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
24. ERROR MODEL IN SPELLING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

P(x|w) measures likelihood of typo.

Examples:

teh from the = common typo

there from three = possible typo

Based on:
- confusion matrix
- keyboard proximity
- edit operations

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
25. REAL WORD ERROR CORRECTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

For valid but wrong words:

Example:
I went too school.

Need context.

Candidate set includes:

- too
- to
- two

Then use language model/context model.

Best sentence probability wins.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
26. PHONETIC SIMILARITY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Sometimes wrong words sound similar.

Examples:
- piece / peace
- sea / see
- knight / night

Generate candidates using pronunciation similarity.

Useful in:
- Speech systems
- Homophone correction

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
27. CORE WEEK 2 IDEAS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. Spell correction is key NLP preprocessing task.
2. Edit distance measures word similarity.
3. Dynamic programming computes efficiently.
4. Weighted costs improve realism.
5. Transposition handles common typos.
6. Trie and delete methods improve speed.
7. Noisy Channel combines word frequency + typo probability.
8. Context needed for real-word errors.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
28. EXAM IMPORTANT TERMS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- Spelling Correction
- Non-word Error
- Real-word Error
- Edit Distance
- Minimum Edit Distance
- Levenshtein Distance
- Weighted Edit Distance
- Dynamic Programming
- Backtrace
- Alignment
- Trie
- Confusion Matrix
- Transposition
- Damerau-Levenshtein
- Candidate Generation
- Symmetric Delete
- Noisy Channel Model
- P(w)
- P(x|w)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
END OF SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━