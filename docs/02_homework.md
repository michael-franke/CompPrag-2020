---
title: "Homework 2"
hide: true
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

<link rel="stylesheet" href="https://s3-us-west-2.amazonaws.com/cdn.webppl.org/webppl-editor-1.0.9.css">
<link rel="stylesheet" href="https://s3-us-west-2.amazonaws.com/cdn.webppl.org/webppl-viz-0.7.11.css">
<link rel="stylesheet" href="https://yui.yahooapis.com/pure/0.6.0/pure-min.css">
<script src="https://code.jquery.com/jquery-2.1.4.min.js"></script>
<script src="https://s3-us-west-2.amazonaws.com/cdn.webppl.org/webppl-editor-1.0.9.js"></script>
<script src="https://s3-us-west-2.amazonaws.com/cdn.webppl.org/webppl-viz-0.7.11.js"></script>
<script src="https://s3-us-west-2.amazonaws.com/cdn.webppl.org/webppl-v0.9.7.js" defer async></script>

Solutions are due on Friday, April 5 2019, midnight. Please send your solutions as a zipped archive. Please name the archive `lastName_HW2.zip` and send it to [Britta Grusdt](mailto:bgrusdt@gmail.com). The archive should contain exactly one plain text file or a markdown file (.txt or .md) with your answers and explanations to all questions. Please keep all your answers short and to the point. Also include your name and student number in the text file. Additionally the archive should contain WebPPL code files (.wppl), one for each exercise that requires code. Name your code files appropriately; e.g., the code file for the 34th part of exercise 27 should be `ex27_part34.wppl`. Submissions that conform to these style requirements receive a bonus point. 

#### Exercise 1: Rewriting the vanilla RSA modelhttps://doi.org/10.1038/s41562-018-0467-4

The speaker rule in the vanilla RSA model is defined in terms of a literal listener like so:

$$P_{LL}(s \mid u) = \frac{\delta_{s \in [\![u]\!]} P(s)}{\sum_{s'} \delta_{s' \in [\![u]\!]} P(s')}$$

$$P_S(u \mid s) \propto \exp(\alpha (\log P_{LL}(s \mid u) - C(u))) $$

Show that, if $$P(s) = P(s')$$ for all $$s,s'$$, the speaker rule can alternatively be written as:

$$P_S(u \mid s) \propto \left [ \delta_{s \in [\![u]\!] } \  \  | [\![u]\!] |^{-1}  \right]^\alpha \ exp(-\alpha C(u)) $$

(You can type your solution (e.g., using LaTeX) or write by hand and attach a picture or scan.)


#### Exercise 2: Vagueness

Use the code from the last model in the first section of [Chapter V of the BDAPPL Webbook](http://www.problang.org/chapters/05-vagueness.html). This model uses the empirically measured priors over prices for various items to calculate the listener's interpretation of *expensive*. We would like to explore the behavior of this model under different values of its parameters. 

##### Part A: convenience function for predictions

To do so conveniently, extend the code by wrapping the relevant part of the given code in a convenience function called `predictions`. The arguments to a function call of `predictions` should be:

1. the item (as a string)
2. the speaker optimality parameter $$\alpha$$
3. the cost of the utterance *expensive*

For example, a function call to get the predictions for the item `"watch"` with `alpha = 1` and utterance cost `2` for expensive would be `predictions("watch", 1, 2)`.

The output of the `predictions` function should be two plots, the same ones that are shown by the model code as it is in the chapter:

1. listener's posterior marginalized over prices 
2. listener's posterior marginalized over thresholds

Additionally, make sure that calls like `print("the listener's posterior over XXX prices:")` is properly changed so that the correct item name is included. Finally, also include the expected value of each marginal posterior distribution using the built-in function `expectation`.

Call your convenience function several times for $$\alpha = 2$$ with different values for $$c$$. What is the functional relationship between $$c$$ and the expected value of prices? Give your answer in at most five simple sentences. (E.g., the higher $$c$$, the ... )

##### Part B: the interpretation of the null message

Build on your code from the previous part, to now give the predictions for the interpretation of the null utterance `""`. Look at the functional relationship for $$c$$ on the expectation of the threshold value. Try to explain your observations in at most three simple sentences.

##### Part C: utterance priors

Make the utterance prior a function of $$\alpha$$, like described in [Appendix Chapter 3](http://www.problang.org/chapters/app-03-costs.html). (NB: there are two equivalent ways of doing this; one involves making $$\alpha$$ a parameter to the utterance prior; the other involves using a flat utterance prior and putting the costs elsewhere.) Which version of the model do you think is *conceptually* more plausible, the one with $$\alpha$$-dependent utterance priors or the one that is currently in the chapter (without $$\alpha$$ dependence) and why do you think so? Give your answer in at most two concise sentences.

#### Exercise 3: 

Extend the modeling in the final code box in the new (hidden!) [chapter on lexical uncertainty](http://www.problang.org/chapters/08-lexical-uncertainty_hidden.html) to cover the case where three individuals are salient: Anne, Bob and Carol. (To so this you need to add possible worlds, extend the set of utterances, and knowledge states, and update the semantic meaning function and refinements.) The complete set of relevant utterances $$U$$ is isomorphic to the set of all belief states, in the sense that if `[A, AB, AC]` is a belief state, we will include the utterances "Anne or Anne and Bob or Anne and Carol". (This means that there are 127 utterances; you can write all of these (and their semantics) by hand; but you should also seriously consider writing more efficient code.) Which utterances are most interesting to test (i.e., which utterances would a normal RSA model (without lexical uncertainty or local enrichment choice) have problems with)? Do you find the predictions plausible (for at least some parameter values)? Answer in at most ten short sentences. 
