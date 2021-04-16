Date: 08:43 2021-04-16

# Predictable and Scalable End-to-End Formal Verification

### Reviewer: #Alexander 

### Tags: #Formal #FVP

### Rates - 30
- Usefulness - 9 на сколько идея может быть полезна в использовании
- Applicability - 6 на сколько идея применима
- Innovativeness - 8 на сколько идея нова
- Availability - 7 на сколько идея доступно и понятно изложена

### Abstract
In this article, we discuss why formal verification adoption has been limited in industry, and how abstraction-based methodology in formal verification can help DV engineers become successful in adopting formal property checking more widely. Abstraction is the key to obtaining scalability and predictability. It provides an efficient bug-hunting technique and helps in establishing exhaustive proof convergence. We illustrate our methodology on a FIFO in this article, but similar methods are used in the verification of a range of designs ranging from a RISC-V processor to multi-million gate designs.

### Main
#### Why formal isn't so widely used?
- Harry Foster research shows that only 35-40% projects use formal 
- Benefits: bugs are caught sooner, corner case bugs are found easily, mathematical proofs, discover and redefine requirements, deal with complected cases such as deadlocks
- The key hindrance is writing SVA for efficiency to ensure **high coverage, predictable proof convergence and scalability with design size**
#### How to deal with that problem?
- We need to understand how to conquer sequential design complexity in formal
- Try to answer the question above with a FIFO example. It's a deep sequential nature
#### FIFO requirements
- the data ordered, does not duplicate data internally, does not lose data, and is empty and full when it should be
- Main goal is to check ordering correctness: *if d1 is sampled ==in== before d2 then d1 is sampled ==out== before d2*
#### How to check this with formal?
- If we consider dynamic verification we can apply a reference model such a queue
- We **cannot apply non-synthesizable constructions for formal tool**
- We need to apply an abstraction
	- data - formal relies on symbolic execution and checking is done on symbolic representations. each symbol is an abstraction of a binary value 0 and 1. These symbols obtain a *logarithmic reduction* in data encoding when they are manipulated by the formal verification search algorithms in formal tools
	- temporal - to not observe every clock cycle but only a few
- Abstraction here that we will sample data in and data out values only when the certain conditions are met
	- sample data_in and data_out only when they match constant values
	- check only once

### Thoughts
- Applying abstraction should reduce check time
- Is there work around to apply non-synthesizable constructions?
- Different mindset should be considered

### Article References
### Other Links
[WEB format](https://verificationacademy.com/verification-horizons/march-2021-volume-17-issue-1/predictable-and-scalable-end-to-end-formal-verification)
[The ABC of Formal Verification](https://verificationacademy.com/sessions/the-abc-of-formal-verification) (webinar)

### Article
![[predictable-and-scalable-end-to-end-formal-verification_vh-v17-i1.pdf]]