NPTEL NATURAL LANGUAGE PROCESSING – WEEK 4
Highly Detailed Subject-Focused Summary
(Only academic content included)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. HIDDEN MARKOV MODELS – DECODING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Week 4 starts with decoding in Hidden Markov Models (HMMs).

Goal:

Given:
Observed word sequence

W = w1, w2, w3 ... wn

Need to find:

Best hidden tag sequence

T = t1, t2, t3 ... tn

Example:
POS tagging

Words observed:
the light book

Need best tags:
Det Adj Noun etc.

This becomes a sequence optimization problem.

:contentReference[oaicite:0]{index=0}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
2. VITERBI ALGORITHM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Used to find most probable hidden state sequence efficiently.

Instead of checking all tag combinations,
Dynamic Programming is used.

Core idea:

At every position:
Store best probability of reaching each state.

Two tables used:

1. δj(t)

Best probability of any path ending in state j at time t.

2. ψj(t)

Best previous state leading to j at time t.

Recurrence:

δj(t+1)=maxi[δi(t) × aij × bj(wt+1)]

Where:

aij = transition probability
bj(word) = emission probability

Backpointer:

ψj(t+1)=argmaxi[δi(t) × aij × bj(wt+1)]

Final step:

Choose state with highest δ at last position,
then backtrack using ψ.

:contentReference[oaicite:1]{index=1}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
3. WHY VITERBI IS IMPORTANT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Without Viterbi:

If 5 tags each word and sentence length = 10

Total combinations:

5^10 = 9,765,625

With Viterbi:

Polynomial time solution.

Hence practical for POS tagging,
speech recognition,
bioinformatics.

:contentReference[oaicite:2]{index=2}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
4. PARAMETER LEARNING IN HMM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Two cases:

A. Labeled corpus available

Every word already tagged.

Then parameters estimated directly.

B. Only raw corpus available

No hidden states known.

Need unsupervised learning.

Use:

Baum-Welch Algorithm

:contentReference[oaicite:3]{index=3}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
5. SUPERVISED PARAMETER ESTIMATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

If tags known:

Transition probability:

P(tj|ti)= Count(ti→tj) / Count(ti)

Emission probability:

P(w|t)= Count(tag emits word) / Count(tag)

Simple maximum likelihood estimation.

:contentReference[oaicite:4]{index=4}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
6. BAUM-WELCH ALGORITHM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Used when hidden states unknown.

It is an EM Algorithm
(Expectation Maximization)

Parameters:

θ = (A, B, π)

Where:

A = transition matrix
aij = P(Xt=j | Xt-1=i)

B = emission matrix
bj(y)=P(observation y | state j)

π = initial state distribution

Goal:

Maximize probability of observed sequence.

:contentReference[oaicite:5]{index=5}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
7. BAUM-WELCH WORKING STEPS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Step 1:
Choose random initial parameters.

Step 2:
Estimate expected hidden paths.

Step 3:
Compute expected transitions/emissions.

Step 4:
Re-estimate A, B, π

Step 5:
Repeat until convergence.

Thus:

Guess → Improve → Repeat

:contentReference[oaicite:6]{index=6}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
8. FORWARD ALGORITHM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Forward variable:

αi(t)=P(y1...yt , Xt=i | θ)

Meaning:

Probability of seeing first t observations
and being in state i at time t.

Initialization:

αi(1)=πi bi(y1)

Recurrence:

αj(t+1)=bj(yt+1) Σi αi(t)aij

Used to compute sequence probability.

:contentReference[oaicite:7]{index=7}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
9. BACKWARD ALGORITHM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Backward variable:

βi(t)=P(yt+1...yT | Xt=i, θ)

Meaning:

Probability of remaining observations
given state i at time t.

Initialization:

βi(T)=1

Recurrence:

βi(t)=Σj βj(t+1)aijbj(yt+1)

:contentReference[oaicite:8]{index=8}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
10. STATE POSTERIOR PROBABILITIES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Probability of being in state i at time t:

γi(t)=P(Xt=i | Y,θ)

Using:

γi(t)= αi(t)βi(t) / normalization

Transition posterior:

ζij(t)=P(Xt=i, Xt+1=j | Y,θ)

These expected counts update parameters.

:contentReference[oaicite:9]{index=9}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
11. PARAMETER RE-ESTIMATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Initial state:

πi = γi(1)

Transition:

aij =
(sum over t of ζij(t))
/
(sum over t of γi(t))

Emission:

bi(vk)=
(expected times state i emits vk)
/
(expected times state i occurs)

:contentReference[oaicite:10]{index=10}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
12. LIMITATIONS OF MARKOV TAGGERS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Two main issues:

A. Unknown words

No emission probabilities.

Example:
new names, rare terms.

Solution:
Use morphology:
capital letters,
suffixes,
digits etc.

B. Limited Context

Example:

"is clearly marked" → participle

"he clearly marked" → past tense

Need richer context.

:contentReference[oaicite:11]{index=11}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
13. MAXIMUM ENTROPY MODELS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Alternative to HMM.

Discriminative model.

Directly estimate:

P(tag | context)

Instead of modeling joint sequence generation.

Uses many flexible features.

Examples:

- first word?
- previous tag?
- next word is “to”?
- word capitalized?
- suffix = ing?

:contentReference[oaicite:12]{index=12}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
14. MAXENT PROBABILITY FORMULA
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Conditional model:

p(y|x)= 1/Z(x) exp( Σ λi fi(x,y) )

Where:

fi(x,y) = feature function
λi = feature weight
Z(x) = normalization constant

Higher weighted active features
increase class probability.

:contentReference[oaicite:13]{index=13}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
15. FEATURE FUNCTIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Usually binary:

fi(x,y)=1 if condition true else 0

Examples:

1. word capitalized AND tag=NNP

2. suffix=ing AND tag=VBG

3. previous word = “the” AND tag=Adj

4. previous tag = Det AND current tag = Adj

:contentReference[oaicite:14]{index=14}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
16. TAGGING WITH MAXENT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Sentence:

w1...wn

Candidate tags:

t1...tn

Probability:

P(tags|words)= Π p(ti|xi)

Where xi includes:

- nearby words
- previous tags
- suffixes
- capitalization

Need search algorithm to find best sequence.

:contentReference[oaicite:15]{index=15}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
17. BEAM SEARCH
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Used because all sequences expensive.

Idea:

At each word position:

Keep only top k tag sequences.

Expand them next step.

Again keep top k.

Continue till sentence end.

Return highest probability sequence.

Advantage:

Fast approximate decoding.

:contentReference[oaicite:16]{index=16}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
18. MAXIMUM ENTROPY PRINCIPLE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Principle:

Among all probability distributions satisfying known constraints,
choose one with maximum entropy.

Meaning:

Use known facts only.
Assume nothing extra.

Entropy:

H(p)= - Σ p(x) log p(x)

Higher entropy = more uncertainty / more uniformity.

:contentReference[oaicite:17]{index=17}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
19. CONSTRAINTS IN MAXENT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Model expectation of features must match empirical data.

For each feature:

Ep[fi] = Edata[fi]

Then maximize entropy subject to these constraints.

Result gives exponential family model.

:contentReference[oaicite:18]{index=18}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
20. CONDITIONAL RANDOM FIELDS (CRF)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Introduced after MaxEnt limitations.

MaxEnt problem:

Per-state normalization causes:

Label Bias Problem

CRF solves this using globally normalized sequence model.

CRF is:

Conditionally trained
Undirected graphical model

Linear-chain CRF widely used for:

- POS tagging
- Named Entity Recognition
- Chunking
- Sequence labeling

:contentReference[oaicite:19]{index=19}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
21. LABEL BIAS PROBLEM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

States with fewer outgoing transitions may dominate.

Because each state locally normalizes probability mass.

Thus decisions become biased.

CRFs compare complete paths globally,
reducing this issue.

:contentReference[oaicite:20]{index=20}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
22. HMM vs MAXENT vs CRF
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

HMM:
Generative
Needs emission + transition probabilities

MaxEnt:
Discriminative
Flexible features
Local normalization

CRF:
Discriminative sequence model
Flexible features
Global normalization

:contentReference[oaicite:21]{index=21}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
23. CORE EXAM TOPICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Must Prepare:

- Viterbi Algorithm
- δ and ψ tables
- Forward algorithm
- Backward algorithm
- Baum-Welch
- γ and ζ
- HMM parameter estimation
- Maximum Entropy formula
- Feature functions
- Beam search
- Entropy principle
- Label bias
- CRF basics

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
24. VERY SHORT REVISION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Viterbi finds best hidden tag path.
Baum-Welch learns HMM parameters without labels.
Forward-backward computes expected counts.

Maximum Entropy predicts tags using features.
Beam search decodes efficiently.

CRF improves MaxEnt for sequences
and solves label bias.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
END OF SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━