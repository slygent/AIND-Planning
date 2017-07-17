# Research review

## Three important historical developments in the field of AI planning and search

### 1. STRIPS

STRIPS (Fikes and Nilsson, 1971), the Stanford Research Insitute Problem solver, was an early automated planner. Apart from being a significant development in its own right in the nascent field of automated planning, its most lasting influence has been in its language, which is still the basis for most of the languages expressing automated planning problem instances used since then (Fikes and Nilsson, 1993). The research that STRIPS was developed for -- allowing a mobile robot to plan its actions to reach a goal -- also led to development of the famed A-star algorithm (Fikes and Nilsson, 1993).

### 2. WARPLAN

In the early 1970s, planners used _totally ordered_ action sequences, i.e. actions couldn't occur simultaneously in parallel. Instead subplans were formulated for each subgoal, and then these subplans must be _interleaved_ within a single sequence. One solution was _goal regression planning_, where steps in a totally ordered plan are instead reordered so that there would not be conflicts between subgoals. Amongst the first planners to use this technique was WARPLAN (Warren, 1974). WARPLAN is particularly notable for being written in the logic programming language Prolog, one of the first of its kind and currently the most popular (Colmerauer and Roussel, 1992). Logic programming languages are declarative, unlike most programming languages, and Prolog has been used many times for such AI tasks as expert systems and natural language processing.

### 3. SATPLAN

The SATPLAN algorithm was inspired by greedy local search algorithms for satisfiability problems (Kautz and Selman, 1992). Research on SATPLAN carries on to this day (Rintanen, 2012). Satisfiability -- more fully, the Boolean satisfiability problem -- is the problem of determining if a Boolean formula has an interpretation that satisfies it, in other words, whether it can be made to be equal to true. Satisfiability was the first problem that was proven to be NP-complete (Cook 1971), therefore all problems in complexity class NP are as difficult to solve as satisfiability, and so heuristic solutions to satisfiability continue to be researched, and many AI problems apart from planning benefit from this research, e.g. constraint solving.

### References

* Colmerauer and Roussel, 1992. "The birth of Prolog". In Bergin and Gibson (Eds.), History of programming languages II. New York: ACM: pp. 331-352.
* Cook, 1971. "The Complexity of Theorem-Proving Procedures". Proceedings of the 3rd Annual ACM Symposium on Theory of Computing: 151–158. doi:10.1145/800157.805047.
* Fikes and Nilsson, 1971. "STRIPS: A New Approach to the Application of Theorem Proving to Problem Solving". Artificial Intelligence. 2 (3–4): 189–208. doi:10.1016/0004-3702(71)90010-5
* Fikes and Nilsson, 1993. "STRIPS, a retrospective". Artificial Intelligence. 59 (1-2): 227-332. doi:10.1016/0004-3702(93)90190-M 
* Kautz and Selman, 1992. "Planning as Satisfiability". Proceedings of the 10th European conference on Artificial intelligence, pp. 359-363.
* Rintanen, 2012. "Engineering efficient planners with SAT". Proceedings of the 20th European Conference on Artificial Intelligence (ECAI 2012), IOS Press, 2012.
* Warren, 1974. "Warplan: A System for Generating Plans". Dept. of Computational Logic Memo 76, Edinburgh, June 1974.
