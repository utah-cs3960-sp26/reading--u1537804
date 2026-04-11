# Week 13 readings
Describe what you believe are the necessary conditions for autoresearch to work, 
and also describe what situations we would expect autoresearch to not work well for. 
What is it about a problem that makes it suitable or unsuitable for autoresearch. 
Karpathy's writeup contains a positive example -- we can probably expect autoresearch to work well for the problem that he describes. 
As a negative example, if we asked an LLM to autoresearch "world peace" we should not expect it to make very good headway towards a practical solution. 
Go ahead and generalize these situations, tell us where this will work and where it won't.


## When it works
Autoresearch works when you have a clear and computable metric (like validation loss), fast iteration cycles, and a 
well-scoped search space. Small changes need to be measurable. The LLM needs sufficient domain knowledge from its t
raining data to generate plausible hypotheses, and the problem must allow incremental progress.

## When I think it fails
Autoresearch fails for problems with ambiguous objectives (world peace, AI safety). slow feedback loops or requirements for novel conceptual breakthroughs.
I think it's gonna fail with anything that requires lots of feedback over an extended period of time. Like trying to optimize a social media site for engagement.
Or trying to measure a code base for maintainability. These things are really hard to iterate through quickly. While measuring engagement might be a specific and calculable measurement,
it's not a quick feedback loop.

