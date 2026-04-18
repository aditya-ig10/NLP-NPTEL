NPTEL NATURAL LANGUAGE PROCESSING – WEEK 3
Highly Detailed Subject-Focused Summary
(Only academic content included)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. LANGUAGE MODELLING: ADVANCED SMOOTHING MODELS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Week 3 begins with advanced smoothing methods used in n-gram language
models to solve sparse data problems.

Problem:
Many valid word combinations are unseen in training corpus.

Hence raw maximum likelihood probability becomes:

P = 0

This is harmful because unseen but valid phrases must still receive some
probability.

Solution:
Use smoothing techniques.

Major techniques covered:

1. Good-Turing Estimation
2. Absolute Discounting
3. Kneser-Ney Smoothing
4. Backoff Models
5. Interpolation Models

:contentReference[oaicite:0]{index=0}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
2. GOOD-TURING ESTIMATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Main idea:

Use frequencies of rare events to estimate unseen events.

If many words occur once, then unseen words likely exist.

Define:

Nc = number of n-grams appearing exactly c times

Example:

N1 = number seen once
N2 = number seen twice

Adjusted count:

c* = (c + 1)Nc+1 / Nc

Instead of using actual count c, use adjusted count c*.

Meaning:
Some probability mass from frequent seen events is transferred to unseen
or low-frequency events.

For unseen events:

Probability mass proportional to:

N1 / N

where N = total observed events.

Advantages:
- Better zero-frequency handling
- Strong for sparse corpora

Problems:
- For large counts values become unstable
- Needs smoothing of Nc values itself

:contentReference[oaicite:1]{index=1}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
3. SIMPLE GOOD-TURING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Improved version of Good-Turing.

Instead of raw Nc values, fit a smooth curve (power law).

Reason:
Frequency-of-frequency counts become noisy for large c.

Used in practical NLP systems.

:contentReference[oaicite:2]{index=2}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
4. ABSOLUTE DISCOUNTING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Instead of recomputing counts, subtract fixed discount d.

Formula:

P(wi|wi-1) =
(c(wi-1,wi) - d) / c(wi-1)
+ λ(wi-1)P(wi)

Meaning:

1. Seen bigram gets reduced count
2. Leftover probability mass distributed using unigram model

Usually:

d ≈ 0.75

Advantages:
- Simple
- Effective
- Basis for better methods

:contentReference[oaicite:3]{index=3}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
5. KNESER-NEY SMOOTHING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

One of the best smoothing methods.

Problem with unigram fallback:

Frequent words may not fit every context.

Example:

“I can’t see without my reading ___”

Candidates:

- glasses
- Francisco

“Francisco” may be frequent overall because of “San Francisco”
but poor continuation here.

So instead of unigram probability use:

Continuation Probability

Pcontinuation(w)

Measures:
How many different contexts word appears in.

Formula:

Pcontinuation(w) ∝
Number of unique previous words before w

Word appearing in many contexts gets higher probability.

Thus:

“glasses” > “Francisco” in many unseen contexts.

Final Kneser-Ney:

PKN(wi|wi-1) =
max(c-d,0)/c(history)
+ λ(history)Pcontinuation(w)

Why powerful:

- Uses context diversity
- Excellent for bigram/trigram models
- Standard benchmark method

:contentReference[oaicite:4]{index=4}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
6. WHY HIGHER N-GRAMS NEED HELP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

As N increases:

Advantages:
- More expressive context
- Better phrase modelling

Disadvantages:
- Severe sparsity
- Many unseen combinations

Example:

Unigram:
Easy estimates, weak context

Trigram:
Strong context, poor coverage

Hence combine models.

:contentReference[oaicite:5]{index=5}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
7. BACKOFF MODELS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Idea:

Use highest-order n-gram available.
If unavailable, back off to lower order.

Example:

Use trigram if seen.

Else:
Use bigram

Else:
Use unigram

Formula concept:

Pbo(wi|wi-2 wi-1)

If trigram count > 0:
use trigram estimate

Else:
λ × Pbo(wi|wi-1)

Recursive fallback continues.

Advantages:

- Efficient
- Uses specific context when known
- Falls back safely

:contentReference[oaicite:6]{index=6}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
8. LINEAR INTERPOLATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Instead of choosing one model, mix all models.

Formula:

P = λ1 P(trigram)
  + λ2 P(bigram)
  + λ3 P(unigram)

Where:

λ1 + λ2 + λ3 = 1

Benefits:

- Robust
- Uses all evidence simultaneously
- Better than hard switching

Lambda values chosen using held-out validation corpus.

:contentReference[oaicite:7]{index=7}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
9. COMPUTATIONAL MORPHOLOGY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Morphology studies internal structure of words.

Words are built from morphemes.

Morpheme:
Smallest meaning-bearing unit.

Examples:

dogs = dog + s

unladylike =
un + lady + like

Used in:

- stemming
- lemmatization
- machine translation
- parsing
- speech systems

:contentReference[oaicite:8]{index=8}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
10. TYPES OF MORPHEMES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

A. Free Morphemes

Can stand alone.

Examples:
dog, house, walk

B. Bound Morphemes

Cannot stand alone.

Examples:
-s, -ed, -ly

C. Content Morphemes

Carry lexical meaning.

Examples:
car, happy

D. Functional Morphemes

Carry grammar info.

Examples:
plural -s
tense endings

:contentReference[oaicite:9]{index=9}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
11. STEMS AND AFFIXES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Stem / Root:
Core meaning unit.

Affixes:
Added to stem.

Types:

1. Prefix
Before stem

un-happy

2. Suffix
After stem

talk-ing

3. Infix
Inside stem

4. Circumfix
Around stem

Used in many world languages.

:contentReference[oaicite:10]{index=10}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
12. ALLOMORPHS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Different surface forms of same morpheme.

Examples of negative prefix:

un-happy
in-correct
im-possible
ir-regular

Meaning same, form changes.

:contentReference[oaicite:11]{index=11}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
13. INFLECTIONAL vs DERIVATIONAL
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

A. Inflectional Morphology

Creates grammatical forms of same word.

bring
brings
bringing
brought

Changes:
tense, number, gender etc.

B. Derivational Morphology

Creates new words.

logic → logical
logical → illogical
logic → logician

Often changes part of speech.

:contentReference[oaicite:12]{index=12}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
14. MORPHOLOGICAL PROCESSES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. Concatenation

Add morphemes in sequence.

hope + less

2. Reduplication

Repeat full/partial word.

Used in many languages.

3. Suppletion

Irregular replacement.

go → went

4. Internal Change

sing → sang → sung
man → men

:contentReference[oaicite:13]{index=13}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
15. WORD FORMATION METHODS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. Compounding

rain + bow = rainbow

2. Acronyms

LASER

3. Blending

breakfast + lunch = brunch

4. Clipping

laboratory → lab

:contentReference[oaicite:14]{index=14}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
16. NLP TASKS USING MORPHOLOGY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. Lemmatization

saw → see / saw

2. Morphological Analysis

saw →
<see, verb past>
<saw, noun singular>

3. POS Tagging

Peter saw her

Here “saw” = verb

4. Morpheme Segmentation

de-nation-al-iz-ation

5. Generation

see + past = saw

:contentReference[oaicite:15]{index=15}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
17. APPLICATIONS OF MORPHOLOGY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- Text to Speech
- Search Engines
- Information Retrieval
- Machine Translation
- Grammar Correction
- Spell Checking

:contentReference[oaicite:16]{index=16}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
18. KNOWLEDGE REQUIRED FOR MORPH ANALYSIS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Need:

1. Lexicon / Dictionary
Known roots

2. Morphotactics

Rules of morpheme order

Example:
plural follows noun

3. Spelling Rules

get + er = getter
fox + s = foxes

:contentReference[oaicite:17]{index=17}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
19. WHY NOT STORE ALL WORDS IN DICTIONARY?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Because languages generate huge forms.

Examples from slides:

English:
317,477 forms from 90,196 entries

Sanskrit:
11 million forms from 170,000 entries

Hence rule-based systems needed.

:contentReference[oaicite:18]{index=18}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
20. FINITE STATE AUTOMATON (FSA)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Used for morphology processing.

Definition:

Directed graph with:

- States
- Edges labeled by symbols
- Start state
- Accept states

Recognizes regular languages.

Applications:

- Morphological parsing
- Word generation
- Spell checking
- Lexicon traversal

:contentReference[oaicite:19]{index=19}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
21. CORE EXAM POINTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Important topics:

- Good-Turing smoothing
- Nc counts
- Absolute Discounting
- Kneser-Ney smoothing
- Continuation probability
- Backoff
- Interpolation
- Morpheme
- Prefix/Suffix/Infix
- Inflection vs Derivation
- Lemmatization
- Morphological Analysis
- FSA

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
22. VERY SHORT REVISION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Language Models need smoothing because unseen n-grams exist.
Good-Turing uses rare counts.
Kneser-Ney uses continuation contexts.
Backoff falls to lower n-grams.
Interpolation mixes models.

Morphology studies word structure using morphemes.
Words formed through affixation, compounding, reduplication etc.
Finite-state machines efficiently process morphology.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
END OF SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━