Date: 20:30 2021-04-08

# Portable Stimulus versus UVM: What's the Difference?

### Reviewer: #Alexander 

### Tags: #PSS #PORTABLESTIMULUS #UVM 

### Rates - 29
- Usefulness - 8 на сколько идея может быть полезна в использовании
- Applicability - 5 на сколько идея применима
- Innovativeness - 7 на сколько идея нова
- Availability - 9 на сколько идея доступно и понятно изложена

### Abstract
Actually it isn't a paper, thus there is no abstract:) It's the video that I found while searching something about pss vs uvm. The video describes basics of pss. How to use uvm with pss. What's an advantage of using pss. Pss semantics.

### Main
 *PSS overview*
- pss is a ==constraint random on steroids==
- pss is a new language. It's DSL (domain specific language) or C++. There are 2 different formats to describe the same thing. It depends on a tool vendor whether it supports both representations
- pss is an abstract way to describe your test specification. It includes stimulus, checkers and coverage
- There is a following process: abstract test specification -> tool -> test implementation(C or SV)
- advantage of abstract test specification that it's readable/writable by many guys such as architects, hw/sw developers, dv engineers
- the dream of pss that the test intent is written once and then tool will create test cases for all platforms

*Using PSS with UVM*
- pss doesn't replace uvm it's built on top of uvm
- we have to create an entry points for pss in the uvm tb. Like read or write register sequences. Basically, we need to separate tasks and methods in order to use them as an atomic operations from pss layer
- pss code then will contain those SV fragments encapsulated in ``""" <uvm code> """``

*PSS vs UVM*
- when we create pss test scenario we can specify that we need  a write register operation following by read. The most interesting thing here is that tool can insert something else (random operations) between those write and read
- pss code is declarative while uvm code is procedural
- when you write in pss 
<pre><code>activity {
	do write_data
	do read_data
}</code></pre>
it means that you say to tool do whatever you want to do but there should be <code>write_data</code> following by <code>read_data</code>. That's why pss is a ==constraint on steroids==
- pss gives us ability to write our intent using constraints
- constraints allow composition that's great way of reuse
- **in pss everything is a constraint**

*PSS semantics*
- ``action`` is fragment of behavior
- ``buffer`` must be written before it will be read
- <pre><code>write_data w1, w2;
read_data r1, r2;
clear_data c1, c2;
activity {
	w1;
	r1;
}</code></pre> using this code tool can produce the following sequence: 
w1 -> w2 -> r2 -> r1 -> r2
- <pre><code>activity {
	select {
		r2;
		r1;
	}
}</code></pre> 
It's like ``randndcase`` statement
- and lots more


### Article References
1. [portable stimulus and uvm](https://www.techdesignforums.com/practice/technique/portable-stimulus-and-uvm/)

### Other Links
[video](https://verificationacademy.com/sessions/dac-2018/portable-stimulus-versus-uvm-whats-the-difference/video/1458?play=1)

### Article
![[Portable Stimulus versus UVM.pdf]]