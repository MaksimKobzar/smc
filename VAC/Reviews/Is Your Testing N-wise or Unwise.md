Date: 20:01 07-04-2021

# Is Your Testing N-wise or Unwise?

### Reviewer: #Maksim 

### Tags: #UVM #STIMULUS #2-WISE #CODE

### Rates - 30
- Usefulness - 7 на сколько идея может быть полезна в использовании
- Applicability - 7 на сколько идея применима
- Innovativeness - 8 на сколько идея нова
- Availability - 8 на сколько идея доступно и понятно изложена

### Abstract
Pairwise, and more generally N-wise, pattern generation has long been known as an efficient and effective way to construct test stimulus and configurations for software testing. It is also highly applicable to digital design verification, where it can dramatically reduce the number and length of tests that need to be run in order to exercise a design under test adequately. Unfortunately, readily available tools for N-wise pattern generation do not fit conveniently into a standard hardware verification flow. This paper reviews the background to N-wise testing, and presents a new open-source SystemVerilog package that leverages the language's constrained randomization features to offer flexible and convenient N-wise generation in a pure SystemVerilog environment.

### Main
-  The article introduces in **pairwise testing** approach. This approach allows to reduce the amount of testing effort required to achieve necessary coverage and confidence. The key idea behind pairwise testing is that difficult bugs are most commonly triggered by the interaction, or coincidence, of two parameters and not more[2].
-  More difficult bugs requires more conditions to be satisfied. Bugs that occur only when three or more parameters have specific values are extremely rare. 2 conditions to be satisfied is a kind of golden mean. 
-  As a result of the previous item, to be almost fully confident in our DUT at least every possible combination of any pair of parameters should be tested.
-  Example, we have a 8-bit register with 5 fields (2,2,2,1,1). There are 256 possible combinations. And there are about 20 runs to cover all pairs. So, we have ~10x speed up here.
![[Pasted image 20210409163147.png]]
-  Author provides SV package with code with classes and macroses to support this approach.
-  As drawbacks author mentions: generation performance[2] and false verification confidence[3]. I can add that for me it looks unclear how to make sequential runs go through the patters which were generated once.
-  Author thinks that other generation algorithms could be used to improve performance and to provide additional features. Potential future enhancements:
>*    The ability to include pre-determined test patterns
>*    Smoother integration with the UVM
>*    The ability to modify parameter groupings to give more aggressive testing across
certain groups of parameters.
-  Verilab doesn't provide code example. Some code examples with C++ could be found here: https://github.com/microsoft/pict 

### Article References
1.  Accellera Systems Initiative, "UVM (Standard Universal Verification Methodology)," June 2014 
2. J. Czerwonka, "Pairwise Testing: Combinatorial Test Case Generation," January 2015. Available: http://www.pairwise.org/.
3. J. Bach and P. Shroeder, "Pairwise Testing - a Best Practice that Isn't," in 22nd Pacific Northwest Software, Quality Conference, 2004.
4. Apache Software Foundation, "Apache License, version 2.0," 2004. [Online]. Available:
http://www.apache.org/licenses/LICENSE-2.0.
5. J. Czerwonka, "Pairwise Testing in Real World," in Proceedings, 24th Pacific Northwest Software Quality Conference, 2006.
6. K.-C. Tai and Y. Lei, "A Test Generation Strategy for Pairwise Testing," IEEE Transactions on Software, Engineering, vol. 28, no. 1, 2002.
7.  IEEE, Standard 1800-2012 for SystemVerilog Hardware Design and Verification Language, New York, NJ:IEEE, 2012.
8.  IEEE, Standard 1800-2009 for SystemVerilog Hardware Design and Verification Language, Piscataway, NJ: IEEE, 2009.

### Other LInks
[Video with presentation] (https://solvnet.synopsys.com/video/customer/application_notes/attached_files/2289610/FA3c.mp4)
![[Is Your Testing N-wise or Unwise(pres).pdf]]

### Article
![[Is Your Testing N-wise or Unwise.pdf]]