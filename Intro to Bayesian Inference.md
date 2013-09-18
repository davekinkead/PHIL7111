# An Introduction to Bayesian Inference

Image the following scenario...

> You're the Duty Watch Officer for the US Navy 3rd fleet.  You've just been advised that a nuclear attack submarine has gone missing off the Azores in the Atlantic Ocean with 99 crew onboard.  Your mission is to organise the search and rescue plan and direct the search efforts to the most likely location because the crew's oxygen will run out before you can search everywhere.  Divide the search area into a 4x4 grid.  Where should you search first?
>
> You assemble a team of experts who flesh out the most likely scenarios and help update your search focus:
> - The submarine hit an underwater mountain south of the Azures,
> - The submarine was hit by a deep draft surface vessel near the shipping channel,
> - A torpedo onboard malfunctioned and exploded,
> - The communications system has malfunctioned.
>
> SONUS reports from the area indicate a noise consistent with a collision but not  an explosion.  Should you update the the search focus?
>
> Search near the mountains reveals nothing.  Should you update the search function?

What you've just done is use _Bayesian Inference_, a method of probabilistic reasoning for rationally updating subjective beliefs under conditions of uncertainty, with new information as it comes to hand.  It's been used successfully in a diverse range of applications including criminal investigation to search and rescue to spam filtering and machine learning.  Think of it as common sense with mathematics on top.

Bayes' theorem  `p(H|E) = p(E|H)p(H) / P(E)` was developed my the Rev Thomas Bayes.  A man so taken with his discovery that he never publish it.  He was embarrassed the conclusion and it only published posthumously. Largely ignored for two centuries, its popularity amongst statisticians, computer scientists, and medical researchers exploded in 1990's.

In order to understand Bayes' theorem however, we must first understand a bit about probability, and how it relates to other forms of reasoning.

## Deductive & Inductive Reasoning 

By now, you should all be well versed with the difference between deductive and inductive reasoning.

Deductive reason deals with certainty.  An argument is deductively valid iff its premises entail its conclusion.

    If A then B
    A
    Therefore B
    
Inductive reasoning by contrast involves uncertainty.  It's premises are never stated in absolute terms and so its conclusions can only be strong or weak, rather than valid or invalid.

    All observed swans to date have been white
    Therefore the next observed swan is very likely to be white

Bayesian reasoning allows us to formalise and accurately measure belief in both deductive and inductive premises.  It permits the strict logical relations of deductive logic under the conditions of uncertainty that are normally the realm of inductive logic.

## Interpretations of Probability

When you think of the word probability, what other words do you associate with it?  Most likely, you would include terms like chance, likelihood, expectation, luck, belief, and random.  There is still strong disagreement within the philosophy of mathematics as to what exactly probability is, where it comes from, and if it is a singular or plurality of phenomena.  Think a about a coin toss for a moment.  When we talk about the probability of an flip landing on heads do we mean any or all of the following?

- my belief that the next flip will be heads is 50%
- my belief that coins in general land on heads 50% of the time
- the logical possibilities of heads or tails make heads 50% likely
- the coin has a physical or causal propensity to land on heads 50% of the time
- the probability of this next flip being heads is either 0% or 100%

Probability can be thought of as being 'out there' in the coin itself, or 'in here' as degree of belief.  It can apply to single case events, this specific coin flip, or to types of events, coin flips in general.  It can be a logical relation, or a causal one.

Bayesian inference only makes sense with subjective or logical probability.  This is because Bayes' Theorem is symmetrical while the physical-causal world is thought to be asymmetrical.  It tells us that for every `p(H|E)` there is a corresponding `p(E|H)`.  It makes perfect sense to infer that a window has been broken from seeing shattered glass on the floor.  It makes much less sense to infer that the window's breaking was caused by the broken glass.  

## Conditional Probabilities

Is the chance of a coin toss affected by today being a Wednesday rather than Sunday?  What about the chance of > 50 people being in the Great Court at 12pm?  We call this conditionalising.  When a conditional probability is the same as an unconditional one, we say that the probabilities are independent.

    p(H) = p(H|W)
    
When they differ, then the probability of the first is dependent or conditional on the second

    p(>50|W) > p(>50)

## Two Ways of Thinking about Bayes
    
Bayesian reasoning allows us to formalise and accurately measure belief in both deductive and inductive premises.

    p(H|E) = p(E|H)p(H) / p(E)

What this says is that our belief in the hypothesis given the evidence at hand, is a function of the likelihood of the evidence given the hypotheses, the hypothesis, and the evidence.  There are two ways of thinking about this.  The first is temporally - Bayes' Theorem gives as a formal way of updating belief given new evidence.

    p(H|E) = p(H) x p(E|H)/p(E)

This way of thinking about Bayes tells us that our updated belief in some hypothesis, the _posterior_ or p(H|E), is just our old belief, the _prior_ or p(H) adjusted for the new evidence.  The adjustment for new evidence depends on how significant and likely that evidence was.  If the new evidence is common and/or expected, then its impact is minor. But if the new evidence is rare or unexpected, then the impact is more significant.  Consider this:

I hypothesise that the sun always rises at within 10-14hrs of it setting because this is what I have always observed.  My observation of the sun rising tomorrow does very little to change this because both p(E|H) and p(E) are very high.  But if it didn't, because say I had flown to a high latitude in winter, then p(E|H) becomes a very small indeed. My belief in p(H|E) will change significantly.

Another way of thinking about Bayes is in terms of conditional relations.

    p(H|E) = p(E|H) x p(H)/p(E)
    
This perspective tells us that the relation between the conditionals is a function of base rate and likelihood of initial belief.  The more fanciful the theory and the less specific the evidence, the less similar the conditional probabilities are.  Some examples will prove illustrative.

## Examples

Diagnoses

    1% of the population has cancer.  A test for cancer is 95% sensitive (true positive) and 95% specific (true negative).  Your test for cancer is positive. What is the probability you have cancer. 

On hearing that they tested positive to a 95% accurate test, most people infer they have a 95% chance of having cancer.  Yet this is completely wrong.  We want to find `p(H|E)` - the probability we have cancer given the positive test result, and the first perspective can help us.

Before the test result, our belief that we had cancer should have been the same as the general population rate: 1%.  That's `p(H)`.  We need to update this based on the likelihood of the new evidence `p(E|H)/p(E)`.  `p(E|H)`, the chance the test is positive _if_ we have cancer is the sensitivity: 95%.  `P(E)` is just the chance of a true positive plus false positive.

So now we can calculate

    p(H|E) = .01 x .95 / (.95 x .01 + .05 x .99) 
    
    p(H|E) = .16667
    
So while testing positive to the cancer test significantly increases your chance of having cancer, it only does so to 17%

Spam Filtering

    p(spam|words) = p(words|spam)p(spam) / p(words)

Search

## Fallacies

A number of fallacies involve the failure to properly update conditional probabilities as per Bayes' Theorem

- Base Rate Fallacy (ignoring base rates when estimating likelihoods)
- Prosecutor's Fallacy (conflating p(E|H) with p(H|E))

## Why Bayes is a big deal

1. It allows us to formalise our intuitions of inductive reasoning.
1. While many people might disagree on the probability of a theory, it is much easier to agree on what the theory should predict if correct.
2. The subjective probability account maps strongly to our intuitions and theories of learning.
