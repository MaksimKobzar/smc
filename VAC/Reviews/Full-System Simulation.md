Date: 18:55 05-04-2021

# Full-System Simulation

### Reviewer: #Maksim

### Tags: #Simulation #Co-Verification

### Rates - 21
- Usefulness - 4 на сколько идея может быть полезна в использовании
- Applicability - 7 на сколько идея применима
- Innovativeness - 4 на сколько идея нова
- Availability - 6 на сколько идея доступно и понятно изложена

### Abstract
Full-System Simulation is a technology where the hardware of a computer system is simulated at such a level of detail that the complete real software stack can be executed. It has wide applicability in the development and research of computer systems, especially embedded systems. This talk gives an overview of the full-system simulation and some examples of its industrial and academic applications.

### Main
- Simulation is a method of scientific and engineering inquiry that is based on the idea of building a model of a system, and then performing experiments on this model. Provided that the model has a good fidelity to the system being modeled, the results from the simulation experiments can be used to predict the behavior of the real system.
- The key concept of full system simulation (cores, devices, memories, network connections, peripheries) is possibility to simulate full software stack with a whole system environment.
- The simulation is on demand now because of 2 factors:
>* cheap computers became very fast
>* the simulation speed was grown by magnitudes
- The idea of full-system simulation is to create model with sufficient level of abstraction to be able to run needed software on it.
- The more detailed model you have the slower it simulates. For full-system simulation, the most appropriate level of abstraction is the instruction set and control register level.
- In the most cases, the most complex a part of a SoC is CPU. Instruction processing also uses most of the execution time of the simulation. Creating a fast model of the instruction set is key to good simulation performance.
- In order to run all the software of a system, the processor model must implement both the user-level and supervisor level interfaces of the processors, as well as the memory management unit and various low-level machine registers. **Anything that can be seen from the software has to be modeled.**
- The simulation high level results should match with real system results.  A difference in computation results compared to a real machine is not acceptable.
- Device models can be either transaction-oriented or bit level:
>*    A transaction-oriented model handles each interaction to a device as a unit: the device is presented with a request, computes the reply, and returns it in a single function call. This is a very efficient model.
>*     A bit-level model instead models the actual bit patterns traveling over buses and pins in the computer. Instead of a single transaction, each cycle on the bus is played out.
- Advantages compared to a real machine:
>1. Configurability. Any machine configuration can be used, unconstrained by available physical hardware.
>2. Controllability. The execution of the simulation can be controlled arbitrarily, disturbed, stopped, and started.
>3. Determinism. A simulation is completely deterministic (provided it is properly programmed).
>4. Globally synchronous. Multiple processors, multiple devices, multiple machines in a network: all can be stopped instantly in a simulation, and a global snapshot of the state inspected.
>5. Checkpointing. The state of the simulation can be written to disk and restored in an instant.
>6. Availability. Creating a new machine is just a matter of copying the setup. There is no need to procure hardware prototypes or development boards.
>7. Inspectability. The complete state of the simulated machine can be investigated without disturbing the execution.
>8. Sandboxing. The simulation environment offers a perfect sandbox, out of which no code or data can escape unless explicitly allowed
- Full-system simulation is also used in the development of computer systems, not just components. By using full-system simulation, designers of complex computer systems such as servers, flight controllers, or network routers can build virtual prototypes.
- **Note that the slowest simulated component of a system will
determine the overall simulation speed.**
- Disturbances and faults can be injected into a system with ease and precision, since there is no need to actually disturb physical links.
- An interesting special case is the testing of large network configurations. In most cases, building a very large test network is prohibitively expensive. Here, full-system simulation allows hundreds of network nodes to be simulated using a handful of standard PCs or server machines. This leads to very large cost savings, as well as an increase in product quality and developer productivity thanks to better testing, easier setup and reconfiguration, and troubleshooting abilities.
- Virtual hardware comes with all the benefits of simulation: by using the checkpointing, determinism, and inspection abilities, software bugs are easier to repeat and fix.


### Article References
1. Peter S. Magnusson, Magnus Christensson, Jesper Eskilson, Daniel Forsgren, Gustav Hållberg, Johan Högberg, Fredrik Larsson, Andreas Moestedt, Bengt Werner, “Simics: A Full System Simulation Platform”, IEEE Computer, Feb 2002.
2. Alaa R. Alameldeen, Milo M.K. Martin, Carl J. Mauer, Kevin E. Moore, Min Xu, Daniel J. Sorin, Mark D. Hill and David A. Wood, “Simulating a $2M Commercial Server on a $2K PC”, IEEE Computer, Feb 2003.
3. Kevin Skadron, Margaret Martonosi, David I. August, Mark D. Hill, David J. Lilja, Vijay S. Pai, “Challenges in Computer Architecture Simulation”, IEEE Computer, August 2003.
4. H. Shafi, P. J. Bohrer, J. Phelan, C. A. Rusu, and J. L. Peterson, “Design and validation of a performance and power simulator for PowerPC systems”, IBM Journal of Research and Development, Vol 47, No 5/6, September/November 2003.
5. Steven E. Gemeny and Michael W. Gemeny, “Ground System Planning for Long Duration Space Missions Helped by Lessons Learned Resurrecting Obsolete Computers”, The John Hopkins University Applied Physics Laboratory, 2003.
6. Andrew Hodges, “Alan Turing: the Enigma”, page 326, ISBN 0-09-911641-3, Random House, London, 1992.

### Other LInks

### Article
![[Full-System Simulation.pdf]]

