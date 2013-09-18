# An Introduction to Bayesian Inference

Image the following scenario...

> You're the Duty Watch Officer for the US Navy 3rd fleet.  You've just been advised that the USS Scorpion, a nuclear attack submarine, has gone missing off the Azores in the Atlantic Ocean with 99 crew onboard.  Your mission is to organise the search and rescue plan and direct the search efforts to the most likely location because the crew, if they are still alive, will run out of oxygen before you can search everywhere.   Where should you search first?
>
> Luckily, you have access to a team of experts who flesh out the most likely scenarios and help update your search focus:
>
> - The submarine hit an underwater mountain south of the Azures,
> - The submarine was hit by a deep draft surface vessel near the shipping channel,
> - A torpedo onboard malfunctioned and exploded,
> - The communications system has malfunctioned.

Each of these scenarios represents a plausible theory of what happened, consistent with the evidence available.  But while each of these scenarios is plausible, some might be more plausible that others.  A method of evaluating how well each theory is supported by the evidence would be very useful indeed.

Thankfully, that method exists. It's called _Bayesian Inference_, and it's a method of probabilistic reasoning that allows us to rationally update our subjective beliefs under conditions of uncertainty, with new information as it comes to hand.  It's been used successfully in a diverse range of applications including criminal investigation to search and rescue to spam filtering and machine learning.  Think of it as common sense with mathematics on top.

Bayes' theorem,   

    p(H|E) = p(E|H)p(H) / P(E)
    
was developed by the Rev Thomas Bayes, a man so taken with his discovery that he never publish it.  He was actually embarrassed by what he saw as the absurdity of the conclusion and it only published posthumously. Largely ignored for two centuries, its popularity amongst statisticians, computer scientists, and medical researchers exploded in 1990's.

In order to understand Bayes' theorem however, we must first understand a bit about probability, and how it relates to other forms of reasoning.

## Deductive & Inductive Reasoning 

By now, you should all be well versed with the difference between deductive and inductive reasoning.

Deductive reason deals with certainty.  An argument is deductively valid iff its premises entail its conclusion.

> If A then B  
> A  
> Therefore B
    
Inductive reasoning by contrast involves uncertainty.  It's premises are never stated in absolute terms and so its conclusions can only be strong or weak rather than valid or invalid.

> All observed swans to date have been white  
> Therefore the next observed swan is very likely to be white

Bayesian reasoning allows us to formalise and accurately measure belief in both deductive and inductive reasoning.  It permits the strict logical relations of deductive logic under the conditions of uncertainty that are normally the realm of inductive logic.  But before we get into Bayesian inference, lets take a quick refresher on probability theory.

## Interpretations of Probability

When you think of the word probability, what other words do you associate with it?  Most likely, you would include terms like chance, likelihood, expectation, luck, belief, and random.  There is still strong disagreement within the philosophy of mathematics as to what exactly probability is, where it comes from, and if it is a singular or plurality of phenomena.  

Think about a coin toss for a moment.  When we talk about the probability of an flip landing on heads do we mean any or all of the following?

- my belief that the next flip will be heads is 50%
- my belief that coins in general land on heads 50% of the time
- the logical possibilities of heads or tails make heads 50% likely
- the coin has a physical or causal propensity to land on heads 50% of the time
- the probability of this next flip being heads is either 0% or 100%

Probability can be thought of as being 'out there' in the coin itself, or 'in our minds' as degree of belief.  It can apply to single case events, this specific coin flip, or to types of events, coin flips in general.  It can be a logical relation, or a causal one.

Bayesian inference only makes sense with subjective or logical probability.  This is because Bayes' Theorem is symmetrical while the physical-causal world is thought to be asymmetrical.  It tells us that for every `p(H|E)` there is a corresponding `p(E|H)`.  It makes perfect sense to infer that a window has been broken from seeing shattered glass on the floor.  It makes much less sense to infer that the window's breaking was caused by the broken glass.  

## Conditional Probabilities

Is the chance of a coin toss affected by today being a Wednesday rather than Sunday?  What about the chance of > 50 people being in the Great Court at 12pm?  We call this conditionalising.  When a conditional probability is the same as an unconditional one, we say that the probabilities are independent.

    p(H) = p(H|W)
    
When they differ, then the probability of the first is dependent or conditional on the second

    p(>50|W) > p(>50)

## A Simple Way to Think About Bayes
    
Bayesian reasoning allows us to formalise and accurately measure belief in both deductive and inductive premises.

    p(H|E) = p(E|H)p(H) / p(E)

What this says is that our belief in the hypothesis given the evidence at hand, is a function of the likelihood of the evidence given the hypotheses, the hypothesis, and the evidence.

Now if these symbols are scary or confusing in anyway, then think about it this way.  Bayes' Theorem tells us how to update our belief in something given new evidence and a significance function of that evidence. So

    p(H|E) = p(H) x p(E|H)/p(E)
    
...just means...
    
    New Belief = Old Belief x Significance Function
    
This way of thinking about Bayes tells us that our updated belief in some hypothesis, the _posterior_ or `p(H|E)`, is just our old belief, the _prior_ or `p(H)` adjusted for the new evidence and its significance, `p(E|H)/p(E)`. If the new evidence is common and/or expected, then its impact is minor. But if the new evidence is rare or unexpected, then the impact is more significant.  Lets look at the significance function in more detail.

`p(E|H)/p(E)` can either be greater than one, one, or less than one.  If it's greater than one, the our new belief will be stronger than our old belief.  If it's exactly one, then they will be the same, and if it's less than one, the new belief will be lower or weaker.  But how do we know which?

`p(E|H)` is the the probability of the evidence occurring, given the hypothesis is true.  It's also known as the true positive or sensitivity of a test.  For example, if a cancer test was 90% sensitive, then we'd expect the test to tell us we have cancer when we really do have cancer 90% of the time, and tell us we have cancer when we really don't have cancer 10% of the time.

`p(E)` is the unconditional probability of seeing the evidence.  It's often useful to conditionalise p(E) against H:

    p(E) = p(E|H)p(H) + p(E|-H)p(-H)

In the case of the cancer test, the probability of any positive result is the sum of the probability of a positive result if I have cancer times the chance I have cancer, and the probability of a positive result if I don't have cancer times the chance I don't have cancer.

So examining the significance function,

    p(E|H) / p(E|H)p(H) + p(E|-H)p(-H)

we see that there is a dynamic between the base-rate or prior belief `p(H)`, and the accuracy of our evidence, `p(E|H)` and `p(E|-H)`.  Accurate tests that deliver unexpected evidence should change our beliefs more than inaccurate tests delivering expected information.  But the lower the base-rate or prior belief, the less the change in belief should be.

An example should prove illuminating.

## An Example

Diagnoses

> 1% of the population has cancer.  A test for cancer is 95% sensitive (true positive) and 95% specific (true negative).  You take the cancer test and get a positive result (it says you have cancer). What is the probability you actually have cancer?

On hearing that they tested positive to a 95% accurate test, most people infer they have a 95% chance of having cancer.  Yet this is completely wrong.  We want to find `p(H|E)`, the probability we have cancer given the positive test result, and the simple way of thinking about Bayes can help us.

Before the test result, our belief that we had cancer should have been the same as the general population rate: 1%.  That's `p(H)`.  We need to update this based on the likelihood of the new evidence `p(E|H)/p(E)`.  `p(E|H)`, the chance the test is positive _if_ we have cancer is the sensitivity: 95%.  `P(E)` is just the chance of a true positive plus false positive.

So now we can calculate

    New Belief = Old Belief x Significance Function

    p(H|E) = p(H) x p(E|H) / p(E|H)p(H) + p(E|-H)p(-H)
    
    p(H|E) = .01 x .95 / (.95 x .01 + .05 x .99) 
    
    p(H|E) = .16667 or 16.7%
    
So while testing positive to the cancer test significantly increases your chance of having cancer, it only increases it from 1% to 17%

## Fallacies

A number of fallacies involve the failure to properly update conditional probabilities in the way Bayes' Theorem requires.

The Base Rate Fallacy is the description of many peoples tendency to ignore the base rate when updating beliefs.  From the cancer example, thinking that a positive test means you have a 95% chance of having cancer is an example of the base rate fallacy.

The Prosecutor's Fallacy describes the conflation of p(H|E) with p(E|H).  The first represents the probability of the accused's guilt given the evidence, whist the latter represents the probability of finding the evidence if they committed the crime.  As an example, an accurate DNA test should provide a very high chance of a match _if_ I committed the crime.  But a DNA match alone, provides very poor evidence that _I_ committed the crime because the DNA could match many people.

The Defence Attorney's Fallacy is the conflation of P(H|E) with p(E).  This was used to very good affect by OJ Simpson's defence team when they claimed the DNA test that linked him to the crime matched 1 in 400 people, and therefore it was not enough to convict OJ.  But this ignored the great deal of other evidence that increased the prior belief in OJ's guilt.

## Why Bayes is a big deal

1. It allows us to formalise our intuitions about inductive reasoning.
1. While many people might disagree on the probability of a theory, it is much easier to agree on what the theory should predict if correct.
2. The subjective probability account maps strongly to our intuitions and theories of learning.
4. It offer's scientific confirmation of a theory, rather than mere falsification.
