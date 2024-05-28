+++
title = 'Why AI won't replace engineers'
date = 2024-05-29T11:30:00Z
draft = false
tags = [ "AI", "Technology" ]
categories = [ "Random" ]
+++

In the context of the ongoing debate about the impact of AI on jobs, particularly in technology, I figured I'd share some of my thoughts on why AI isn’t going to be replacing engineering roles any time soon.

Of course it might seem prudent to defend the notion that engineers are essential - given I am one. Much in the same way I'm sure the "luddite" of old defended their necessity in the context of the industrial revolution. However despite this glaring conflict of interest, let me explain why.

The first point to address is we appear to be reaching a form of "peak AI". Following a recent video from [Computerphile](https://www.youtube.com/watch?v=dDUC-LqVrPU), it features a [study](https://arxiv.org/abs/2404.04125) highlighting how AI models appear to be plateauing in performance even as the dataset grows.

![AI Performance](static/ai-model.png)

Ultimately it boils down to the fact that companies are running out of the underlying data necessary to form the datasets for training these models. At a certain point it becomes infeasible to train a model for every specific scenario the AI may encounter, which means the AI has to bridge this gap in its knowledge between two data-points. While this may work for creative writing where there is no strict right or wrong - programming doesn't allow for such leniency.

To any given programming problem there are realistically only a small number of solutions, sort of like how there are only a few syntactically correct ways to write a loop in any particular language. This means the AI model is left with a very limited amount of data with which to train itself. The net result being, the more complex, contextualised and niche a problem becomes the worse the AI solution as it moves further and further from the data points it has in its model.

Furthermore, as current benchmarks on [SWE-Bench](https://www.swebench.com/) demonstrate, AI can barely handle more than 10% of real-world GitHub issues independently. As a replacement for engineers, this is all but useless in a real-world application. Combine this with a current generation of AI that is plateauing in performance and you can begin to understand why AI offers no material threat to engineering roles.

Much in the same way the development of the auto-pilot didn't replace the need for pilots. AI isn't a replacement for engineers. Even where AI can be used to augment engineers, it still requires the skill of the engineer to apply that AI effectively - prompting it and assessing the output are both skills in and of themself.
