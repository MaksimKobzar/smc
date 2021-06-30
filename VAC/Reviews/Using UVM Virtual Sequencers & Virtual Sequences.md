Date: 21:15 30-06-2021

# Using UVM Virtual Sequencers & Virtual Sequences

### Reviewer: #Maksim

### Tags: #UVM #VIRTUAL #SEQUENCE #SEQUENCER

### Rates - 20
- Usefulness - 5 на сколько идея может быть полезна в использовании
- Applicability - 7 на сколько идея применима
- Innovativeness - 1 на сколько идея нова
- Availability - 7 на сколько идея доступно и понятно изложена

### Abstract
This paper will clarify important concepts and usage techniques related to virtual sequencers and virtual sequences that are not well documented in existing UVM reference materials. This paper will also detail the __m_sequencer__ and __p_sequencer__ handles and the macros and methods that are used with these handles. The objective of this paper is to simplify the understanding of virtual sequencers, virtual sequences and how they work.

### Main
Virtual sequence is used as mechanism that manages a lot of different transaction flows. 1 flow = 1 sequence. If you have a single transaction flow or there are a lot of different flow but they independent then virtual sequence isn't need. But you can have it just to take an advantage of it in the future. 

Three attributes of a virtual sequencer are:  
* It controls other sequencers.  
* It is not attached to a driver.  
* It does not process items itself.

It is possible to use virtual sequence without virtual sequencer. In such case, you should store all common sequencer pointers in virtual sequence and run this virtual sequence on __null__.

Every sequence has a handle to the sequencer that is running that sequence. That handle is called the m_sequencer handle. Furthermore, the m\_sequencer variable is an internal implementation variable that is poorly documented and should not be used directly by verification engineers. You can add p_sequencer to any sequence by macros \`uvm\_declare\_p\_sequencer. The pointer from m\_sequencer is copied to p\_sequencer at the moment of start() call.

### Article References
1. Reference 0
2. Reference 1

### Article
![[Using UVM Virtual Sequencers & Virtual Sequences.pdf]]