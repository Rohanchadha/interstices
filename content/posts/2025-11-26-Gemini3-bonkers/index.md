---
date: '2025-11-26'
draft: false
title: 'Gemini 3 is bonkers'
tags: ["How I AI","Python"]
---
At work today, I was trying to come up with a **math function** to normalize some scores on a scale of 0-1.
I had some idea of how I wanted the normalization to work (maybe a log or sigmoid function) but didn't quite had the function nailed down.

So, I gave Gemini 3 an idea of what I am trying to do and I gave it rough **expectations from the normalization function** i.e
* Low Score (20) should map to 0.25
* Medium Scores (50) maps to 0.5
* High Scores (~150) maps to 0.8


And Gemini thinks for a while & just **one shots** the function & plots it :)
And to flex, it gives an additional alternate function, also meeting the expectations.


![plot](functionPlot.png)