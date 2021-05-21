Date: 14:49 20-04-2021

# Verification Prowess with the UVM Harness

### Reviewer: #Maksim

### Tags: #TAG0 #TAG-1

### Rates - X
- Usefulness - X на сколько идея может быть полезна в использовании
- Applicability - X на сколько идея применима
- Innovativeness - X на сколько идея нова
- Availability - X на сколько идея доступно и понятно изложена

### Abstract
In this paper we show how to create a UVM testbench with interface connections that universally work in any design simulation context. A harness is a common solution for encapsulating interfaces, binding them to the DUT, and publishing virtual interface assignments. We show how to enhance the harness with interfaces that work with both master and slave agents, in active and passive modes, with active RTL or stub modules, and can tolerate changes to design hierarchy. We accomplish this using interfaces with standard SystemVerilog features of binding and port coercion. Examples demonstrate how we can now encapsulate methods that access internal signals, change UVM agent roles between tests, and dynamically inject stimulus to any portion of a design without impact to how we connect and use interfaces from testbench components. This also allows us to efficiently run tests that verify different portions of a design using a single compile.

### Main
- Your reviews
- Something else

### Article References
1. Reference 0
2. Reference 1

### Other Links

### Article
![[Verification Prowess with the UVM Harness.pdf]]