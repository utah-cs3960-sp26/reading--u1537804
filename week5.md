# Response to first reading
## In the blog post, tool definitions have a bunch of fields (4). Describe them briefly and then explain when each of those fields are used. 


1. **Name** - A string identifying the tool 
2. **Description** - Instructions telling the model what the tool does, when to use it, when NOT to use it, what it returns, etc
3. **InputSchema** - JSON schema describing what inputs the tool expects and in what format
4. **Function** - The actual executable function that takes the input and returns a result

## When is the description sent to the model?
The description is sent to the model during every `runInference()` call as part of the `anthropicTools` array in the API request. 

## When is the function run?
The function runs locally in the code when Claude responds with a `tool_use` content block. The `executeTool()` method looks up the 
tool by name and executes the function with the provided input.

## When is the input schema used?
The input schema is used twice. (1) It's sent to the model alongside the description so Claude knows what format to use when requesting 
the tool and (2) It's used locally when the code unmarshals the JSON input.

## Why all parts are necessary
These four fields work together as a complete contract between the code and the LLM:
- **Name** provides the identifier for routing
- **Description** teaches the model when and how to use the tool
- **InputSchema** ensures structured, reliable communication format
- **Function** actually executes the work

Without any one piece, the system breaks. together they create a loop. The description guides decision-making, schema structures the request, 
name routes it, and function executes it.


---

# Response to second article

# Three Ways to Improve My Editor Test Suite

## 1. Implementing Risk-Based Test Prioritization with Metrics Tracking

The article emphasizes categorizing tests by risk level and prioritizing based on business impact. At this point in the editor, my test suite was so bad.  
All tests were the same prioroity (no prioroity). I'll respond how I wouldve responded knowing what i know now too.  
I could tag tests with risk levels. Then I could do something like run high-risk tests on every commit, medium-risk on pull requests, and low-risk nightly. The 
article mentions tracking metrics to measure success.. It wouldve been cool to track which risk categories catch the most bugs and how often each tier fails. 

## 2. Adopting Test-Driven Development to Reduce Technical Debt


## 3. Establishing Continuous Test Suite Optimization Through Regular Review

