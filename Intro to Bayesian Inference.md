# An Introduction to Bayesian Reasoning

> You're the Duty Watch Officer for the US Navy 3rd fleet.  You've just been advised that a nuclear attack submarine has gone missing off the Azores in the Atlantic Ocean with 99 crew onboard.  Your mission is to organise the search and rescue plan and direct the search efforts to the most likely location because the crew's oxygen will run out before you can search everywhere.  Divide the search area into a 5x5 grid.  Where should you search first?
>
> You assemble a team of experts who flesh out the most likely scenarios and help update your search focus:
> - The submarine hit an underwater mountain south of the Azures,
> - The submarine was hit by a deep draft surface vessel near the shipping channel,
> - A torpedo onboard malfunctioned and exploded,
>
> SONUS reports from the area show no signs of a pressure wave consistent with an explosion.  No vessels have reported collisions.  Should you update the the search focus?

---

What you've just done is use _Bayesian Reasoning_, a method of probabilistic reasoning for rationally updating subjective beliefs under conditions of uncertainty with new information as it comes to hand.  It's been used successfully in a diverse range of applications including criminal investigation to search and rescue to spam filtering and machine learning.

Bayes' theorem  `p(H|E) = p(E|H)p(H) / P(E)` was developed my the Rev Thomas Bayes.  A man so taken with his discovery that he was too embarrassed to publish it (it was published posthumously).  

In order to understand Bayes' theorem, we must first understand a bit about probability.

## Interpretations of Probability

- Word association
- Group definition
- Coin toss example
- Frequency
- Logical Space
- Propensity
- Belief
- Bayesian reasoning only makes sense with probability as subjective belief.  Why?

## Conditional Probabilities

Is the chance of a coin toss affected by today being a Wednesday rather than Sunday?  What about the chance of > 50 people being in the Great Court at 12pm?  We call this conditionalising.  When a conditional probability is the same as an unconditional one, we say that the probabilities are independent.

    p(H) = p(H|W)
    
When they differ, then the probability of the first is dependent or conditional on the second

    p(>50|W) > p(>50)
    
The idea behind Bayes' theorem is to update our conditional

## Deductive & Inductive Reasoning 

Deductive reason deals with certainty.  An argument is deductively valid iff its premises entail its conclusion.

    If A then B
    A
    Therefore B
    
Inductive reasoning but contrast involves uncertainty.

## Fallacies
