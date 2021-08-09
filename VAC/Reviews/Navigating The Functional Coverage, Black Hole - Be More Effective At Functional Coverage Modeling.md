Date: 16:45 09-08-2021

# Navigating The Functional Coverage, Black Hole - Be More Effective At Functional Coverage Modeling

### Reviewer: #Maksim 

### Tags: #FUNCCOV #COVERAGE #PLANNING

### Rates - 27
- Usefulness - 7 на сколько идея может быть полезна в использовании
- Applicability - 8 на сколько идея применима
- Innovativeness - 5 на сколько идея нова
- Availability - 7 на сколько идея доступно и понятно изложена

### Abstract
Coverage modeling is an essential component of today’s verification methodologies, but it’s often
badly planned and poorly executed. The topics discussed in this paper are based on the experiences of the authors, working on SoC and IP projects for more than a decade. The aim of this paper is to enable readers to do a better job of developing their coverage models, by understanding the objectives and requirements more clearly, using some best practice styling, and taking reviews of implementation more seriously.

### Main
The verification plan itself, acts as a bridge for traceability between the multitude of requirements defined in specifications and use-modeling, and the results of the simulations.
When planning functional coverage, the corresponding checks must also be planned. They are
tightly coupled.
The most important criteria when planning coverage:
* Accurate - think about when and what is sampled
* Representative - think what this coverage means and what is the priority of it
* Complete - identify an exhaustive list of features 

##### Kinds of functional coverage:
* Use-cases - scenarios of usage
* Interesting scenarios - special configuration or special sequence of events
* Register coverage - access policies, reset values, etc
* Protocol coverage
* Modes of operations - close to use-cases, related to DUT configuration
* Responses - to cover all variety of DUT's responses
* Temporal proximity or pattern-based - detecting the specific data or sequence pattern
* State (machines) - FSM code coverage crossing with something else
* Cross-cutting concerns - something like reset and changing power domains
* Error injection - to cover injected errors
* Illegal conditions - can show that you thought about particular illegal cases
* Analog-mixed signal - interaction between digital and analog domains

##### Mutually Exclusive, Collectively Exhaustive (MECE) mindset
We break down a DUT requirement into independent definitions. Our aim is to make these definitions independent from one another, so as to avoid repetition, but at the same time cover the whole intent, without gaps. Independent coverage entities + crossing allow to see more information than just 1 single coverage entity.

During coverage planning ruthless prioritization is required. The priority should guide the verification. There should be 3 axis: Value (priority from HVP), Complexity (complexity from HVP), Risk (possibly be added to HVP). The 1st order of verification is the functionality with High Value + Low Complexity + High Risk.
![[Pasted image 20210809171315.png]]
![[Pasted image 20210809171320.png]]

##### Practical advice
* Protocol-specific coverage should be divided from DUT-specific to facilitate the coverage reuse.
* Implementing the coverage structure, think more about the abstraction level of coverage statements and dependencies. 
* The moment of sampling is often more important than what is covered. For example, reset->empty vs full->empty. Ask yourself: "When to ignore this coverage?" 
*  During reg & reset tests remaining functional coverage should be disabled.
*  Conditionals: A | B -> C. It is not enough to cover only C. [A & !B -> C, !A & B -> C] 

##### Coverage implementation best practice checklist
1. Ensure any reused coverage is still accurate and meaningful, e.g. observing accesses modes on a bus interface may need to be tuned, when using at higher levels, based on target destination, or slave responses.
2. Name/Comment coverage based on coverage intent not simply the feature name. Thinking about how someone should interpret the code can speed up both analysis and review.
3. Group multiple conditions/threads appropriately, i.e. don’t potentially hide untaken paths.
4. Use bin ranges to help rationalize the amount of data to analyze, but ensure the ranges are both meaningful and don’t hide important corner cases.
5. Coverage should be focused on functionality, not simply bit toggling (which can be observed using code coverage tools). If bit values, in a register for example, are being covered any correlation with other modes should be accounted for in the sampling, conditional triggering, or crossing.
6. Reduce coverage, especially complex crosses, to the useful values.
7. Use illegal bins in covergroups sparingly, for situations where generating an error is useful to debug assumptions, or stimulus, rather than functional correctness checking (better done explicitly in a checker). Provide a mechanism to disable.
8. Utilize coverage in register packages for access policy and generic register related behaviors, but full toggle and design feature functionality are typically better handled differently.
9. Split covergroup and SVA cover statement implementation according to their strengths, e.g. SVA can be more practical when collecting temporal behavior on a physical interface.
10. Include sequence/scenario coverage. Some simple functional coverage to determine what “abstracted” sequences or use cases have been exercised can be very helpful. Don’t assume the scenarios get executed simply because they are written.

##### Coverage implementation review
   1. Review the verification plan and consult it when reviewing the coverage. Coverage is part of the   signoff criteria for the device, and should be given equal scrutiny to the RTL and verification   environment code.  
   2. Review the coverage that is being analyzed. There may be a great deal of coverage that is not part   of the verification plan, or that is not being analyzed. Don’t review its implementation in detail if it’s not part of the signoff criteria.
   3. Coverage that is implemented or collected that is NOT part of the verification plan should be   reviewed in so far as understanding WHY it’s not part of the verification plan. There are many  legitimate reasons why implemented and collected coverage is not part of the verification plan, but they should all be scrutinized and confirmed.
   4. Each piece of functional coverage should have an associated check. Capturing statistics about features exercised in the device is useless if there is no corresponding check to determine if the device operated correctly in response to the stimulus. Both the check and the coverage should be part of the verification plan section for the given feature.
   5. When reviewing the verification plan, scrutinize whether all relevant coverage has been mapped to the specific section. Are there portions of code coverage, other covergroups, additional assertions, etc. that can and should be included to determine completeness of the verification of a specific feature.
   6. Sampling of functional coverage should be reviewed to ensure that coverage is not oversampled, or sampled incorrectly. Oversampling can lead to false positive results, indicating scenarios as being covered when they have not been appropriately exercised.
   7. Binning and illegal conditions in coverpoints should be reviewed to ensure the values are correct and meaningful. Bins need not be too large or too small to capture actual interesting corners of the design or implementation.
   8. Sections of the coverage plan, and their mapped coverage, should be reviewed to ensure alignment with functional specification and business goals. If a particular section of the verification plan is difficult to connect to either of these two sources, it may be poorly defined, or redundant.
   9. Prioritization or weighting of specific coverage elements and sections of the verification plan  should be aligned with priorities of technical and business goals. This should include reviewing which sections of the device have the greatest percentage of “new code” compared to previous revisions, as well as which are the most critical to the end customer.
   10. The verification plan and coverage implementation represents one of the key signoff criteria for ASIC development. Involving all stakeholders, including SW, HW, system, etc. in the review of the plan and potentially the coverage implementation is critical.


### Article References
1. Paul Marriott and Steven Bailey, Functional Coverage Using SystemVerilog, DVCon 2006
2. Andrew Piziali, Functional coverage measurement and analysis, ISBN 1-4020-8025-5
3. Bishnupriya Bhattacharya et al, Advanced verification topics
4. http://en.wikipedia.org/wiki/Write_combining
5. Barbara Minto, The pyramid principle – logic in writing and thinking, 3rd Edition

### Other Links

### Article
![[Navigating The Functional Coverage Black Hole - Be More Effective At Functional Coverage Modeling.pdf]]