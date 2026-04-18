NPTEL NATURAL LANGUAGE PROCESSING – WEEK 1
Highly Detailed Subject-Focused Summary
(Only academic content included)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. INTRODUCTION TO NATURAL LANGUAGE PROCESSING (NLP)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Natural Language Processing (NLP) is a field of Artificial Intelligence,
Computer Science, and Linguistics focused on enabling computers to
understand, interpret, process, and generate human language.

Natural languages include:
- English
- Hindi
- French
- Tamil
- Arabic
etc.

Unlike programming languages, natural languages are flexible,
ambiguous, context-dependent, and constantly evolving.

Main Goals of NLP:

1. Scientific Goal:
   Study how human language works and how meaning is formed.

2. Engineering Goal:
   Build practical systems that automatically process language.

Examples:
- Translation systems
- Chatbots
- Search engines
- Voice assistants
- Summarizers

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
2. WHY NLP IS IMPORTANT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Text is the largest source of human knowledge.

Examples of textual data:
- News articles
- Books
- Emails
- Research papers
- Legal documents
- Websites
- Tweets
- Social media posts
- Product reviews

Most information in the world exists in text form. NLP helps
extract useful knowledge from that text automatically.

Need for NLP:
- Too much data for humans to read manually
- Multiple languages exist on the internet
- Need faster access to information
- Need automation in communication systems

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
3. MAJOR APPLICATIONS OF NLP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

A. Machine Translation
Convert one language into another.

Examples:
English → Hindi
English → French

Used in:
- Google Translate
- International communication
- Tourism
- Multilingual websites

B. Search Engines
Understand user query and return relevant results.

Features:
- Autocomplete
- Spell correction
- Intent understanding
- Ranking results

C. Chatbots and Conversational AI
Systems that interact in natural language.

Examples:
- Customer support bots
- AI assistants
- FAQ bots
- Domain-specific bots

D. Information Extraction
Extract structured data from unstructured text.

Example:
Sentence:
"Russell Lewis became President of New York Times."

Extract:
Person = Russell Lewis
Company = New York Times
Position = President

E. Sentiment Analysis
Determine emotional polarity of text.

Types:
- Positive
- Negative
- Neutral

Used in:
- Product reviews
- Social media monitoring
- Brand analysis

F. Text Summarization
Generate short summaries from long text.

Used in:
- News apps
- Research tools
- Reports

G. Spam Detection
Detect unwanted messages/emails.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
4. WHY NLP IS HARD
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Human language is difficult because words and sentences can have
multiple meanings depending on context.

━━━━━━━━━
A. Lexical Ambiguity
━━━━━━━━━

One word can have many meanings.

Examples:

1. Will Will will Will’s will?
   (Will = name, future auxiliary, desire)

2. Rose rose to put rose roes on her rows of roses.

Words can function differently depending on usage.

━━━━━━━━━
B. Structural Ambiguity
━━━━━━━━━

Same sentence can have multiple grammatical structures.

Example:
"The man saw the boy with the binoculars."

Meaning 1:
Man used binoculars.

Meaning 2:
Boy had binoculars.

━━━━━━━━━
C. Semantic Ambiguity
━━━━━━━━━

Meaning changes depending on interpretation.

Example:
"Flying planes can be dangerous."

Meaning:
- Piloting planes is dangerous
OR
- Planes that are flying are dangerous

━━━━━━━━━
D. Vagueness
━━━━━━━━━

Language often lacks exactness.

Examples:
- It is warm here.
- She must have.

Interpretation depends on context.

━━━━━━━━━
E. Parsing Explosion
━━━━━━━━━

As sentence length increases, number of possible parses grows rapidly.

Examples:
Short sentence = 2 parses
Longer sentence = many parses

This makes sentence understanding computationally difficult.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
5. NATURAL LANGUAGE VS PROGRAMMING LANGUAGE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Natural Language:
- Ambiguous
- Flexible
- Informal
- Context dependent

Programming Language:
- Strict syntax
- Unambiguous
- Deterministic
- Machine interpretable

Example:
Python code has one exact meaning.
English sentence may have multiple meanings.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
6. ADDITIONAL CHALLENGES IN NLP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

━━━━━━━━━
A. Non-Standard Text
━━━━━━━━━

Used in social media and messaging.

Examples:
- U = You
- gr8 = great
- soo happyyy

Creates preprocessing difficulty.

━━━━━━━━━
B. Segmentation Problems
━━━━━━━━━

Where to split words or phrases.

Example:
New York-New Haven Railroad

Possible tokenizations vary.

Important in:
- Chinese/Japanese text
- Hashtags
- Compound words

━━━━━━━━━
C. Idioms
━━━━━━━━━

Phrase meaning differs from literal meaning.

Examples:
- Ball in your court
- Dark horse
- Burn the midnight oil

Literal word meaning is useless here.

━━━━━━━━━
D. Neologisms
━━━━━━━━━

New words created over time.

Examples:
- Unfriend
- Retweet
- Google (verb)
- Photoshop (verb)

Models must adapt to new vocabulary.

━━━━━━━━━
E. Word Sense Shift
━━━━━━━━━

Existing words gain new meanings.

Example:
"That’s sick!"

May mean:
- Amazing
- Cool

Not illness.

━━━━━━━━━
F. Named Entity Ambiguity
━━━━━━━━━

Need to know whether phrase is title/person/place/etc.

Examples:
- Let It Be
- A Bug’s Life

Could be song/movie names.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
7. HOW NLP SOLVES THESE PROBLEMS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

NLP systems use:

1. Knowledge of language
   - Grammar
   - Syntax
   - Morphology
   - Semantics

2. World knowledge
   - Facts
   - Common sense
   - Context

3. Statistical methods
   Learn patterns from large text corpora.

4. Probabilistic Models

Examples:
P("maison" = house) is high

P("I saw a van") >
P("eyes awe of an")

Meaning most probable interpretation is selected.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
8. FUNCTION WORDS VS CONTENT WORDS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

━━━━━━━━━
Function Words
━━━━━━━━━

Words with grammatical role, little standalone meaning.

Examples:
- the
- a
- and
- of
- to
- in
- was

Used to connect sentence structure.

Closed class:
New function words rarely added.

━━━━━━━━━
Content Words
━━━━━━━━━

Carry meaning.

Examples:
- computer
- dog
- democracy
- teacher
- happiness

Open class:
New words frequently added.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
9. TYPE VS TOKEN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Token:
Every occurrence of word.

Sentence:
cat cat dog

Tokens = 3

Type:
Unique words only.

Types = {cat, dog} = 2

Important in corpus linguistics and NLP statistics.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
10. TYPE TOKEN RATIO (TTR)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Formula:

TTR = Number of Types / Number of Tokens

Used to measure vocabulary diversity.

Higher TTR:
More unique words used.

Lower TTR:
Many repeated words used.

Examples from slides:

Tom Sawyer:
- 71,370 tokens
- 8,018 types
- TTR = 0.112

Shakespeare:
- 884,647 tokens
- 29,066 types
- TTR = 0.032

TTR depends on text size, so not perfect alone.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
11. WORD FREQUENCY DISTRIBUTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Words are not evenly distributed.

Observations:

- Few words occur very frequently
- Many words occur rarely

Example:
Around 50% word types may appear only once.

Such words are called:

Hapax Legomena
= Words appearing exactly one time.

Important in:
- Vocabulary sparsity
- Language modeling

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
12. ZIPF’S LAW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

One of the most famous empirical laws in NLP.

If words are ranked by frequency:

Frequency ∝ 1 / Rank

Meaning:

1st most common word occurs most often.
2nd most common occurs around half as often.
3rd less frequent, etc.

Formula:

f × r = constant

Where:
f = frequency
r = rank

Implications:
- Small number of common words dominate text
- Long tail of rare words exists

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
13. OTHER ZIPF OBSERVATIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

A. Frequent words tend to have more meanings.

Examples:
set, run, get

B. Frequent words tend to be shorter.

Examples:
the, is, of, to

This supports efficient communication.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
14. IMPACT OF ZIPF’S LAW IN NLP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Advantages:
- Stopword removal reduces large token count.
- Common words easy to model.

Challenges:
- Rare words lack enough training data.
- Sparse vocabulary problem.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
15. OVERALL CORE IDEAS OF WEEK 1
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. NLP enables machines to process human language.
2. Text data is huge and valuable.
3. NLP powers translation, search, chatbots, sentiment analysis.
4. Language ambiguity is the biggest challenge.
5. Statistical and probabilistic methods are key.
6. Language follows measurable frequency patterns.
7. Zipf’s Law explains common vs rare words.
8. Corpus statistics are foundational for modern NLP.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
16. EXAM IMPORTANT TERMS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- NLP
- Ambiguity
- Lexical Ambiguity
- Structural Ambiguity
- Parsing
- Token
- Type
- TTR
- Function Words
- Content Words
- Hapax Legomena
- Zipf’s Law
- Sentiment Analysis
- Information Extraction
- Machine Translation

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
END OF SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━