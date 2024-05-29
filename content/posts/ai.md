+++
title = "Why AI won't replace engineers"
date = 2024-05-28T11:30:00Z
draft = false
tags = [ "AI", "Technology" ]
categories = [ "Random" ]
+++

In the context of the ongoing debate about the impact of AI on jobs, particularly in technology, I figured I'd share some of my thoughts on why AI isn’t going to be replacing engineering roles any time soon.

Of course it might seem prudent to defend the notion that engineers are essential - given I am one. Much in the same way I'm sure the "luddite" of old defended their necessity in the context of the industrial revolution. However despite this glaring conflict of interest, let me explain why.

The first point to address is we appear to be reaching a form of "peak AI", at least in the context of generative AI - which specifically affects engineering. Following a recent video from [Computerphile](https://www.youtube.com/watch?v=dDUC-LqVrPU), it features a [study](https://arxiv.org/abs/2404.04125) highlighting how AI models appear to be plateauing in performance even as the dataset grows.

![AI Performance](/ai-model.png)

Ultimately it boils down to the fact that companies are running out of the underlying data necessary to form the datasets for training these models. At a certain point it becomes infeasible to train a model for every specific scenario the AI may encounter, which means the generative AI has to bridge this gap between two data-points. While this may work for creative writing where there is no strict right or wrong - programming doesn't allow for such leniency.

To any given programming problem there are realistically only a small number of solutions, sort of like how there are only a few syntactically correct ways to write a loop in any particular language. This means the AI model is left with a very limited amount of data with which to train itself. The net result being, the more complex, contextualised and niche a problem becomes the worse the AI solution as it moves further and further from the data-points it has in its model.

Secondly, as current benchmarks on [SWE-Bench](https://www.swebench.com/) demonstrate, AI can barely handle more than 10% of real-world GitHub issues independently. As a replacement for engineers, this is all but useless in a real-world application.

Traditional thinking has been that if you simply increase the dataset eventually you will reach some form of "general intelligence" that can essentially generate the answer to any problem. However the data for the niche and contextual problems engineers solve simply do not exist and even if the code itself did, classifying that in a way that would allow it to be used by an LLM is an unrealistic undertaking.

This essentially leaves generative AI's ability to fully replace engineers almost dead in the water. Who would replace a fully capable engineer with an AI that can barely complete 10% of problems it encounters?

Much in the same way the development of the auto-pilot didn't replace the need for pilots. AI isn't a replacement for engineers. Even where AI can be used to augment engineers, it still requires the skill of the engineer to apply that AI effectively - prompting it and assessing the output are both skills in and of themselves. No doubt AI will be used more as part of engineering but finding where to leverage the benefits will simply become another skill of engineers.
