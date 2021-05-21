Date: 07:51 2021-05-20

# Improving X debug in X prop and GLS simulations

### Reviewer: #Alexander 

### Tags: #XPROP #GLS #DEBUG

### Rates - 33
- Usefulness - 9 на сколько идея может быть полезна в использовании
- Applicability - 9 на сколько идея применима
- Innovativeness - 8 на сколько идея нова
- Availability - 7 на сколько идея доступно и понятно изложена

### Abstract
In RTL simulation the unknown state, X, which can be 0 or 1 introduces a verification challenge. X-optimism inherent in RTL simulation of some coding styles can filter an X and prevent it from reaching an observation point where it can be detected. As a consequence, time-consuming gate-level simulation (GLS) has been traditionally used to catch X-issues late in the design flow. 

X’s may simply be introduced by flip flops which due to oversight have not been initialized. The challenge of X is further complicated both by modern power-management techniques which turn off power to parts of the design which are not in use and initialize related registers to X. Also, if 3rd party IP is used, it may not be practical to design out X-optimism in the IP code. The risk of non-detection of X errors increases. 

RTL-based simulation X-propagation features can help in catching X issues by alleviating X-optimism. X’s created by uninitialized flip flops or power management techniques can propagate through logic, even 3rd party IP. Multiple detections of X, however, may trace back to a single source. Consequently, X debug, even with X-propagation techniques can be tedious and time-consuming task. 

In this paper we present an algorithm that aims to minimize debug time of Xprop simulation failures, and locate potential root cause of failures in fully automated way. An implementation of Verdi-based algorithm is also presented.

### Main
#### Understanding X problem
- Source of X:
	- Power island
	- Explicit X assignment
	- Implicit X sources(uninitialized flops, latches, memories)
	- Functional violations such as divide by 0
	- Multiple drivers
- In silicon the value of X means 0 or 1 and must propagate as 0 or 1. In this paper they refer to this behavior as X-optimism
- The Optimistic X was filtered out ![[Pasted image 20210520105651.png]]
- How to find X issues
	- GLS
	- XPROP
	- Formal X verification (not discussed here)

- Main drawbacks of GLS:
	- it is run to late in the design cycle
	- slow (because of event-based simulation)
	- Difficulties in debug
	- Overly X-pessimistic
- Different GL implementations of picture above ![[Pasted image 20210520112858.png]]
- X-propagation option aims to propagate X-value where ever conditional statement (if,case..) encounter X  ![[Pasted image 20210520142506.png]]


#### Current X debug challenges
- One important consideration of simulation based X-propagation solution is that place where the error is detected and the actual X root cause could be in entirely different parts of the design separated by ==1000==’s of clock cycles.
- Driver tracing can be applied for the debugging. However, the challenge is to identify unique root causes of X

#### Debug automation using Verdi
- Verdi Apps using API calls (TCL and C) available from Verdi
- There is an option to get signal values from FSDB and KDB and automate X debug traceability

#### X debug proposals
- Proposal relies on Verdi application
- Inputs
	- Failing FSDB with XPROP
	- Passing FSDB without XPROP
	- KDB
- Steps
	- Extract X signals from the failing simulation
	- Remove inactive signals
	- Remove signals that are also have X values in non-XPROP simulation
	- Checks active driver on X signals and remove the former signals from the list

#### Summary and thoughts
- Paper shows how Verdi App can be used to reduce debug effort 
- look into all Verdi and categorize them. Are they useful or not?
- What else can you do with this API?

### Article References
\[1\] Lionel Bening. A two-state methodology for rtl logic simulation. In Design Automation Conference,  1999\. Proceedings. 36th, pages 672{677, 1999. doi: 10.1109/DAC.1999.782029. 
\[2\] Adrian Evans, Julius Yam, and Craig Forward. X-propagation: An alternative to gate level simulation. In Synopsys Users Group Conference, San Jose, 2012. 
\[3\] Lisa Piper and Vishnu Vimjam. X-propagation woes: masking bugs at rtl and unnecessary debug at the netlist. In Design and Veri\_cation Conference, San Jose, 2012. 
\[4\] Stuart Sutherland. I'm still in love with my x! In Design and Veri\_cation Conference, San Jose, 2013. 
\[5\] Synopsys. VCS, 2015. URL http://www.synopsys.com/Tools/Verification/FunctionalVerification/Pages/VCS.aspx. \[Online; accessed 09-May-2015\]. 
\[6\] Synopsys. Verdi automated debug system, 2015. URL  www.synopsys.com/Tools/Verification/debug/Pages/Verdi-ds.aspx. \[Online; accessed 09-May-2015\]. 
\[7\] Mike Turpin. The dangers of living with an x. In Synopsys Users Group Conference (SNUG), Boston, 2003. 
\[8\] Mike Turpin. Solving verilog x-issues by sequentially comparing a design with itself. In Synopsys Users Group Conference (SNUG), Boston, 2005. 
\[9\] Synopsys Verdi Apps https://www.vc-apps.org/gettingstarted.php 
\[10\] Challenges of VHDL X Propagation DVCon\_Europe\_2015\_TA5\_2\_Paper.pdf

### Other Links

### Article
![[snug_2016_uk_x_debug_gls_paper.pdf]]