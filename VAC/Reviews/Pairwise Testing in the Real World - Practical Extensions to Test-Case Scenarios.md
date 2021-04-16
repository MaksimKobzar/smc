Date: 13:01 16-04-2021

# Pairwise Testing in the Real World: Practical Extensions to Test-Case Scenarios

### Reviewer: #Maksim 

### Tags: #2-WISE #PAIRWISE #SW #MSFT #PICT

### Rates - 28
- Usefulness - 8 на сколько идея может быть полезна в использовании
- Applicability - 5 на сколько идея применима
- Innovativeness - 7 на сколько идея нова
- Availability - 8 на сколько идея доступно и понятно изложена

### Abstract
Pairwise testing has become an indispensable tool in a software tester’s toolbox. This article pays special attention to usability of the pairwise-testing technique. In particular, it focuses on ways in which the pure pairwise-testing approach must be modified to become practically applicable, and on the features that tools must offer to support the tester who is trying to use pairwise testing in practice.

### Main
**How to run PICT on Ubuntu:**
	- Install gcc
	- Install clang
	- Install libstdc++
	- Download repo from here: https://github.com/microsoft/pict.git
	- Go to root repo directory
	- Run in console: <code> make pict test</code>
	- Run PICT: <code> ./pict name_of_the_model tool_options</code>

-  Pairwise-testing strategy is defined as follows:
Given a set of *N* independent test factors — *f1, f2, ..., fn* — with each factor *fi* having *Li* possible levels — *fi = {li,1,  ...,  li,Li}* — a set of tests *R* is produced. Each test in *R* contains *N* test levels, one for each test-factor *fi*; and, collectively, all tests in *R* cover all possible pairs of test-factor levels (belonging to different parameters); in other words, for each pair of factor levels *li,p* and *lj,q*—where *1 =< p =< Li, 1 =< q =< Lj*, and *i != j*—there exists at least one test in R that contains both *li,p* and *lj,q*.
- PICT was designed with three principles in mind: (1) speed of test generation, (2) ease of
use, and (3) extensibility of the core engine.
- Input to PICT is a plain-text file (model) in which a tester specifies test factors (referred to
as test parameters, later in this article) and test-factor levels (referred to as values of a parameter).
- The core generation algorithm is a greedy heuristic. (See Figure 5.) It builds one test case
at a time, locally optimizing the solution. It is similar to the algorithm that is used in AETG [6], with the key differences being that the PICT algorithm is deterministic and that it does not produce candidate tests.

**Advanced features:**
- Mixed-Strength Generation
	The feature can be used to specify which parameters should be, for example, 2-wise combined and which should be 3-wise combined: A, B 2-wise and C,D 3-wise
- Creating a Parameter Hierarchy
	Parameter Hierarchy allows to specify which of existing parameters should be t-wise combined and which could be skipped:  A, B 2-wise and C,D 3-wise and E,F don't need fully combined
- Excluding Unwanted Combinations
	When some combinations of parameters are invalid user can explicitly specify rules to get rid of them.
- Seeding
	Seeding can be used to:
		1.  Explicit specification of important combinations;
		2.  To minimize change in the output when the test-domain description is modified.
- Testing with Negative Values
	Can be used to control invalid parameter configuration and the number of error in it. 
- Specifying Expected Results
	Can be used to add one more Column in the result report to answer the qeuestion: Should the test PASS or FAIL? To calculate this result, PICT should get some rules form user, which could be written in similar to constraint manner. 
- Assigning Weights to Values
	Can be used to show that some parameters are more important and preferably should be used more often.


### Article References
1.  Czerwonka, J. “Pairwise Testing: Available Tools.” Available at:
2.  Ammann P. E., and A. J. Offutt. “Using Formal Methods to Derive Test Frames in Category-Partition Testing.” In Ninth Annual Conference on Computer Assurance (COMPASS’94), Gaithersburg, MD, pages 69–80, 1994.
3.  Bach, J., and P. Shroeder. “Pairwise Testing: A Best Practice that Isn’t.” In Proceedings of the 22nd Pacific  Northwest Software Quality Conference, pages 180–196, 2004.
4.  Burr, K., and W. Young. “Combinatorial Test Techniques: Table-Based Automation, Test Generation, and Test Coverage.” In Proceedings of the International Conference on Software Testing, Analysis, and Review (STAR), San Diego, CA, 1998. 
5.  Burroughs, K., A. Jain, and R. L. Erickson. “Improved Quality of Protocol Testing Through Techniques of Experimental Design.” In Proceedings of the IEEE International Conference on Communications (Supercomm/ICC’94), May 1–5, New Orleans, LA, pages 745–752, 1994.
6.  Cohen, D. M., S. R. Dalal, M. L. Fredman, and G. C. Patton. “The AETG System: An Approach to Testing Based on Combinatorial Design.” IEEE Transactions on Software Engineering, 23(7), 1997. AETG is a trademark of Telecordia Technologies.
7.  Cohen, D. M., S. R. Dalal, J. Parelius, and G. C. Patton. “The Combinatorial Design Approach to Automatic Test Generation.” IEEE Software, 13(5):83–87, 1996. 
8.  Colbourn, C. J., M. B. Cohen, and R. C. Turban. “A Deterministic Density Algorithm for Pairwise Interaction Coverage.” In Proceedings of the IASTED International Conference on Software Engineering, 2004.
9.  Dalal, S. R., A. J. N. Karunanithi, J. M. L. Leaton, G. C. P. Patton, and B. M. Horowitz. “Model-Based Testing in Practice.” In Proceedings of the International Conference on Software Engineering (ICSE 99), New York, pages 285–294, 1999.
10.  Dunietz, I. S., W. K. Ehrlich, B. D. Szablak, C. L. Mallows, and A. Iannino. “Applying Design of Experiments to Software Testing.” In Proceedings of the International Conference on Software Engineering (ICSE 97), New York, pages 205–215, 1997.

### Other LInks

### Article
![[Pairwise Testing in the Real World - Practical Extensions to Test-Case Scenarios.pdf]]