---
title: "Homework 1"
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

Solutions are due on Wednesday, March 20 2019, before class (9am). Please send your solutions as a zipped archive. Please name the archive `lastName_HW1.zip` and send it to [Britta Grusdt](mailto:bgrusdt@gmail.com). The archive should contain exactly one plain text file or a markdown file (.txt or .md) with your answers and explanations to all questions. Please keep all your answers short and to the point. Also include your name and student number in the text file. Additionally the archive should contain WebPPL code files (.wppl), one for each exercise that requires code. Name your code files appropriately; e.g., the code file for the 34th part of exercise 27 should be `ex27_part34.wppl`. Submissions that conform to these style requirements receive a bonus point. 

General advice: develop all your code on [webppl.org](webppl.org)!

#### Exercise 1: 2-Box problem

Implement Bayesian reasoning for the 2-box problem in WebPPL in parallel to [the code for the 3-card problem](https://michael-franke.github.io/probLang/chapters/app-01-probability.html).

Jones has two boxes. One contains two gold coins, the other one gold and one silver coin. Jones selects a random box and picks a random coin from it. He shows you a gold coin. What is the probability that the other coin in the box from which Jones presented the gold coin to you is also gold?

#### Exercise 2: Plot samples from a (truncated) normal distribution

1. Plot 10,000 samples from a standard normal distribution. Use `Gaussian(...)` or `gaussian(...)` (whichever you find more appealing), together with `repeat(...)` and `viz(...). ` (You can find more information about the normal distribution in WebPPL in the [documentation](http://docs.webppl.org/en/master/distributions.html).)
2. Produce a similar plot for a truncated standard normal distribution where only positive values are allowed. This is equivalent to a Bayesian update of a standard normal prior with the observation (or true information) that the realized value was positive. Do this in a manner similar to the above with `repeat(...)` and `viz(...). `. (Hint: you might want to use a recursive call to a sampling function: if the sampled value is positive, keep it; otherwise sample again.) 
3. Now do the same as in the previous exercise but use `Infer(...)` and one of `condition(...)`, `factor(...)` or `observe(...)`.

#### Exercise 3: Null utterance in Scalar Implicature model

The final model of scalar implicature reasoning presented in [Chapter II of problang.org](http://www.problang.org/chapters/02-pragmatics.html) includes a 'null utterance'. Answer the following questions about the 'null utterance' in this model.

1. Looking at the utterance prior, is the null utterance any different from the other utterances? If so, how?
2. Take the `speaker` function defined in the last code block and find values for its arguments such that the result is a distribution which puts all probability mass on the null utterance. (Another way of saying this: find a situation in which the speaker would use only the null utterance.)
3. Interpret the parameter values you chose in the previous part. What kind of an epistemic situation is the speaker in?
4. Comment on whether it is reasonable for the model to have the speaker choose the 'null utterance' for this case.

#### Exercise 4: Hyperbole

Look at the final version of the hyperbole model in [Chapter III of problang.org](http://www.problang.org/chapters/03-nonliteral.html).

1. Change the pragmatic listener function so that it returns `prize` and `qud`. (Hint: this is  like in the final model of scalar implicature reasoning, where we also returned several values for the pragmatic listener's interpretation.) Include, as the answer to this exercise, the whole function `pragmaticListener` with whatever changes you made to it (but no other parts of the code, since nothing else should change).
2. Change nothing else about the code and look at the picture that you get from the final call of `viz(listenerPosterior)`. Interpret this picture! Concretely, suppose that you show this to a friend who is not familiar with RSA, WebPPL or the model at hand. Explain to that friend the model's predictions, as shown in the graph.
3. Comment on whether you find these predictions intuitive.
