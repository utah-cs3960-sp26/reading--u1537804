### Q1: What bugs does scenario testing catch vs not catch?
I would expect it to catch integration bugs, end to end workflow failures, agent cheating, and some other realistic edge cases 
I would also expect it to not catch memory leaks or security vulnerabilities. Race conditions and Lo-level implementatino bugs arent really within this scope either. 
These type of tests seem to be good for agent generated code and LLM based systems. User facing features and projects with multi system workflows as well. 
Probably not so good for security critical code or performance critical code.

---

### Q2: Digital Twin Universe vs Mocks - same thing? Use both?

A traditional mock uses single functions/classes and hardcoded responses. They're also usually handwritten by developers, and it only covers what the developers have coded.
The digital twin universe mocks entire services like Jira, Octa, and Slack. There are full behavioral clones and replicates the whole service behavior. It's also an agent generated.
They do solve different problems. And I think that using both is smart. The mocks are good unit tests for individual functions and the digital twin universe for scenario tests/complete workflows.


DTU is basically "mocking at service level" instead of function level.
