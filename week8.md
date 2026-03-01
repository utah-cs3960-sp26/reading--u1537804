A successful Git branching model responses:


#1 Git Flow has both main and develop because main is meant to always reflect stable and production code. 
Develop is where new features are combined and tested before they’re officially released. 

#2 A feature branch is used to build new functionality off develop branch, whereas a hotfix branch is created from main to quickly fix something broken in production.

#3 A release branch comes off develop when you’re getting ready to ship a version. This gives you space to polish/fix bugs and prepare the release without stopping new feature work.

#4 If you don’t plan to maintain older versions of your software, you likely don’t need separate release or hotfix branches.

#5 In a simpler project with continuous deployment and no version maintenance, you also may not need separate develop and main branches and could work from a single main branch.


Quickcheck Paper responses:

#1 The counterexample is something like xs = [2] and ys = [-2,1], where reverse (xs ++ ys) does not equal reverse xs ++ reverse ys, showing that reverse does not distribute over append in that order.

#2 Most ordered lists were very short because the precondition ordered xs filters out most random lists, and short lists (especially length 0 or 1) are far more likely to already be ordered.

#3 Conditional laws use ==> so QuickCheck only counts tests that satisfy the condition, meaning it may try up to 1000 generated inputs to find 100 valid test cases that meet the precondition.
