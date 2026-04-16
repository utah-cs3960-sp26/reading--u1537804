# Week 4 Reading responses:

Explain what three parameters the authors found matter for LLM performance, and what parameters they found 
don't matter. Also explain what they mean by "overfitting" or "bottlenecking".

The 3 parameters that mattered were:

N (number of model parameters excluding embeddings), D (the size of the dataset in tokens)
and C (the amount of compute used for training). 

They found that performance depends very little on architectural hyperparameters:

- Network depth vs. width
- Number of attention heads
- Dimension of feed-forward layers
- Other architectural details

Overfitting/Bottlenecking occurs when they increase a scale factor while holding another one fixed. Performance 
enters "a regime of diminishing returns." Essentially bottlenecking the performance. 

