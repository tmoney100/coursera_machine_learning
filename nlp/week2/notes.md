# Week 2 - Naive Bayes

P(A) = how frequently events occur
P(A) = P(Positive) = positive_number / total_tweets
P(A) = 14 / 20

pos_tweets = 0.65
neg_tweets = 0.35
total_tweets = 1.00

P(B) = P(happy) = numb_tweets_with_happy / total_tweets
P(B) = 4 / 20 = 0.2


Probability of the intersection(AND upside down U - union): 
P(A) & P(B) / total
3 of 4 contain happy and positive
1 of 4 contain happy and negative
4 tweets contain happy

3/20 = 0.15
1/20 = 0.05

![Alt text](<Screenshot 2023-09-30 at 2.22.36 PM.png>)

## Bayes Rule (conditional probability)
guess outcome given X, where X confines the scope

given that a tweet contains "happy" what's the liklihood of positive?
P(A | B) = P(Positive | "happy") - we know the tweet is happy, what's the liklihood it's positive?
P(+ | happy) = 3 / 4 = 0.75
P(- | happy) = 1 / 4 = 0.25
4 words contain happy

P(B | A) = P("happy" | Positive) = 3 / 13 = 0.231

Probability of B, knowing that A scopes the context.
Looking at the number of events A, what's the likelihood of B.

P(A | B) = P(A union B) / P(B)
P(Pos | 'happy') = P(Pos union 'happy') / P('happy')


## Bayes rule:

P(A | B) = P(B | A) * P(A) / P(B)

intersection = and = upside down U = A & B

Did you consider the amount of farmers and librarians?

Prior = P(A)
Likelihood = P(B | A)
Posterior = P(A | B)

P(H) = P () prob of hypothesis
P(E) = P () prob of exp being true

## Naive Bayes
Quick, simple way to get an initial assessment of thedata

naieve bayes inference condition =  prob(w_1 | pos) / prob(w_1 | neg)


# Laplacian Smoothing
- Avoiding zero
add 1 & # unique words to avoid zero

P(w_i | class ) = freq(w_1, class) / N_class
P(w_i | class ) = (freq(w_1, class) + 1) / (N_class + V)

# Log Likelihood
logorithm of the probability

prior = P(pos) / P(neg)
likelihood = sum(P(w_1 | pos) / P(w_1 | neg))
  - range from 0 to inf
log(likelihood) 
  - range from -inf to inf

log(prior) + log(likelihood) = log(prior * likelihood)


### ratio of probability

positive = inifinity = 
neutral  = 1         =
negative = 0         = 

reduces the risck of numerical underflow (too little of values for the computer )

lambda(w) = log(P(w_1 | pos) / P(w_1 | neg))
the lambda dictionary (log likelihood) can be summed to 
I 0.05 | 0.05 | log(1) => 0 = neutral
sad 0.01 | 0.09 | log(0.11111) => -2.2 => negative

# 5 steps to train naive bayes
1. collect and annotate data - (test/train, pos/neg, labled)
2. preprocess: lowercase, remove punct/urls/etc, remove stop words, stemming, tokenize
3. compute word count: how many times does word_x appear in pos/neg; gives P(w_x | class); conditional probability table
  - happi    pos: 2, neg: 1
  - corpus_# N_class 
4. get lambda score for each word: log of ratio of conditional probabilty
5. log_prior

process_tweet
feq(w, class)
P(w | pos), P(w | neg)
lambda(w) = log(pos_likelihood / neg_likelihood)
log_prior = log(P(pos) / P(neg))





