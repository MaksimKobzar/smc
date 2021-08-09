Date: 15:54 2021-08-09

# Verification Learns a New Language: An IEEE 1800.2 Python Implementation

### Reviewer: #Alexander 

### Tags: #Python #UVM

### Rates - 23
- Usefulness - 7 на сколько идея может быть полезна в использовании
- Applicability - 5 на сколько идея применима
- Innovativeness - 6 на сколько идея нова
- Availability - 6 на сколько идея доступно и понятно изложена

### Abstract
UVM testbenches are powerful, reusable programs that generate transaction-level stimulus and analyze transaction-level results, leaving the signal-level control to bus functional models. One has to wonder why we are writing this complex software using a language intended to describe RTL in an event-driven simulator. Wouldn’t we be better off using the most popular software development language, Python?

### Main
#### Why to consider Python?
- Lack of knowledge of SV
- Nobody learns SV at University
- Many know Python
- A TB is only software making function calls through a BFM proxy
- Cocotb can be used to connect Python and simulators

#### What's different about Python?
- Everything in Python is an Object: No typing issues -> Reuse
- Forgiveness instead of permission

#### PyUVM
- Implements UVM1.2. You can get it via pip install pyuvm
- The factory is realized by using metaclasses (implementation of functions like interface classes)
- Simplified singleton implementation - no type parameters
- Threads in pyuvm  like for uvm_queue's get method utilize cocotb queue with timeout
- You can't control messages via ID. Can't demote specific error by ID


### Other Links

- [Verification Academy](https://verificationacademy.com/conferences/dvcon-2021/verification-learns-a-new-language_an-ieee-18002-python-implementation)
- [COCOTB github](https://github.com/cocotb/)


### Article
![[dvcon-us-2021_paper_verification-learns-a-new-language_an-ieee-18002-python-implementation_rsalemi.pdf]]