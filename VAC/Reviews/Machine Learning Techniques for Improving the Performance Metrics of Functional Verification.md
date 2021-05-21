Date: 18:33 21-05-2021

# Machine Learning Techniques for Improving the Performance Metrics of Functional Verification

### Reviewer: #Maksim

### Tags: #ML #AI #SVM #IntelligentVerification #NLP

### Rates - 28
- Usefulness - 9 на сколько идея может быть полезна в использовании
- Applicability - 6 на сколько идея применима
- Innovativeness - 9 на сколько идея нова
- Availability - 4 на сколько идея доступно и понятно изложена

### Abstract
In this paper, it is explored how machine learning techniques help improve the performance metrics of functional verification. The article outlines a landscape of the current practice, underlines some of the most prominent solutions, compares different approaches, and locates other possible synergy points. In the end, a personal vision is expressed for future research directions.

### Main
Types of ML approaches:
* Supervised learning, where the system learns a general rule;
* Unsupervised learning, where the system discovers hidden patterns in the data;
* Reinforcement learning, where the system tries its best to accomplish a mission.

Common structure:
![[Pasted image 20210521184034.png]]

Trends of using ML in verification:
* Automatic code generation (i.e. specification and constraint mining), where the IV framework recommends assertions and constraints to engineers, and thus reduces the VE implementation time. Mostly this approach requires working with specifications which comply with some document standard or it requires some proxy between human-readable version and ML model. Also, it can require the manual effort for annotation. More information can be found in NLP (Natural Language Processing) algorithm topics.
	SRS (Software Requirements Specification) / IEEE-STD-830 standard
* Feedback-based coverage-directed test generation, where the stimuli are automatically adjusted by some coverage model feedback. It allows dramatically reduce simulation time via stimuli optimization. For me, It looks as one of the most perspective approach. Basic comparison between ML techniques is presented: Evolutionary Programming, Bayesian Network, Markov Chain, Data Mining, Inductive Logic Programming.
* Automated failure root-cause debug, where the framework points out more detailed information about the identified functional bugs. This trend includes the approach to estimate bug probability. It requires to analyze previous design revisions, DUT simulation traces. The higher quality of history you have the more you can get from this approach.
* Speed-up formal verification processes, where the theorem proving task can be enhanced with an automatic solver mechanism. It solves the problem of predicting/optimizing runtime of an instance by switching from an algorithm that becomes inefficient to an algorithm that is more efficient for the current computation task. Because the end-user has the difficult task of setting the right parameter values for the chosen strategies.

Comparison of strategies:
![[Pasted image 20210521184132.png]]



### Article References
[1] FINE S., et. al., Coverage Directed Test Generation for Functional Verification using Bayesian Networks,
IEEE Proceedings 2003, DAC 2003.
Machine Learning Techniques for Improving the Performance Metrics of Functional Verification115
[2] WIEMANN A., Standardized Functional Verification, Springer 2008.
[3] Lifting the Fog on Intelligent Verification, SCDSource, May 2008, Available at: https://en.
wikipedia.org/wiki/Intelligent_verification
[4] ELLA A., et. al., Advances in Intelligent Systems and Computing, Springer 2020, AMLTA 2019.
[5] PANDEY M., Machine Learning and Systems for Building the Next Generation of EDA tools, IEEE
2018, ASP-DAC 2018.
[6] GHOSH S., ARSENAL: Automatic Requirements Specification Extraction from Natural Language,
Springer 2016, NASA Formal Methods 2016.
[7] WANG Y., Semantic Information Extraction for Software Requirements using Semantic Role Labeling,
IEEE 2016, PIC 2015.
[8] The Stanford Natural Language Processing Group, Stanford Parser, August 2020, Available at:
http://nlp.stanford.edu:8080/parser/
[9] IEEE Recommended Practice for Software Requirements Specifications, IEEE Standard 830-1998.
[10] HARRIS C., et. al., GLAsT: Learning Formal Grammars to Translate Natural Language Specifications
into Hardware Assertions, IEEE 2016, DATE 2016.
[11] GUO Q., et. al., On-the-Fly Reduction of Stimuli for Functional Verification, IEEE 2011, ATS 2010.
[12] GUGLIELMO G. D., et. al., On the validation of embedded systems through functional ATPG, IEEE
2008, PRIME 2008.

### Other Links

### Article
![[Machine_Learning_Techniques_for_Improving_the_Performance_Metrics.pdf]]