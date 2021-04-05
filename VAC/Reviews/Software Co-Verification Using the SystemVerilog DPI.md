Date: 19:38 05-04-2021

# Hardware/Software Co-Verification Using the SystemVerilog DPI

### Reviewer: #Maksim

### Tags: #Simulation #ISS #Co-Verification #DPI #Debugger

### Rates - 28
- Usefulness - 8 на сколько идея может быть полезна в использовании
- Applicability - 8 на сколько идея применима
- Innovativeness - 4 на сколько идея нова
- Availability - 8 на сколько идея доступно и понятно изложена

### Abstract
During the design and verification of the Hyperstone S5 flash memory controller, we developed a highly effective way to use the SystemVerilog direct programming interface (DPI) to integrate an instruction set simulator (ISS) and a software debugger in logic simulation. The processor simulation was performed by the ISS, while all other hardware components were simulated in the logic simulator. The ISS integration allowed us to filter many of the bus accesses out of the logic simulation, accelerating runtime drastically. The software debugger integration freed both hardware and software engineers to work in their chosen development environments. Other benefits of this approach include testing and integrating code earlier in the design cycle and more easily reproducing, in simulation, problems found in FPGA prototypes.

### Main
- HW&SW co-verification provides the possibility to verify not yet existent SoC. For example, when you have a partly designed system and some parts of it are replaced by high level models. Moreover, this replacement could be done when SoC is ready but you can gain performance improvement using some, for example, behavioral memory models.
- The most cost effective solution is usually to integrate an ISS model of the existing CPUs. Also ISS can support in SW debugging. ISS+debugger allow FW team to debug their code drafts faster with a high level of debugability. And before running FW on FPGA, FW team can run and debug it using SoC + ISS + SW debugger.
- Commonly, the ISS model is written using C/C++ language. It is very convenient because C/C++ language is simple and natively paired with SV. There is the possibility to write ISS models using SystemC as well.
- ISS model usually contains all internal CPU memories and registers. Sometimes it also contains additional SoC memories to maximize speed up. So, the processor cycles used to fetch the code, and read, and write static variables are no longer simulated by the logic simulator.
- ISS model usage adds one more possibility to simulate HOST CPUs. For example, in NVMe subsystem we can add ISS model in TB instead of HOST CPU and then run some FW on this HOST CPU to fill SQ/CQ queues. It is not possible (or at least much more costly) using real HW cores.
- DPI. An import declaration can occur where ever a Verilog task or function definition is allowed. A task or function can be exported only from the same scope where it is defined.
- Programs are run in a sequential manner, neither instruction pipelining nor any timing of the microprocessor at the hardware level is modeled.
- To integrate the ISS model, its memory interface had to be adapted to call the logic simulator (for example, VCS) to satisfy accesses to the surrounding hardware: resets, interrupts, some specific system pins could be necessary to be reported to the ISS. Without these signals ISS model is not fully functioned and the possibilities of FW debugging will be severely curtailed.
- Usually, ISS integration method implies a near cycle-accurate system where the ISS is a slave of the logic simulator. SV wrapper calls some imported task every cycle with important signals (resets, interrupts etc) as arguments. Within this task instruction processing is carried out. In the case of LOAD/STORE commands IO exported methods are called like io_mem_write() & io_mem_read(). As the result of each task call the CPU state is saved in a set of global variables. It is recommended to synchronize ISS model processing with the positive edge of the system clock.
- Logic simulators are very good for source level debugging of Verilog or VHDL, as well as tracing signals, but you have virtually no visibility into the assembly or C firmware driving the simulation. You can use the compiler and linker to generate map and listing files, which help to find the line of firmware that was being executed for a particular program counter (PC) value. You can also set conditional breakpoints on the PC to stop the simulation before a specific instruction is executed.
- If SW debugger is connected via UART it allows using the same debugging mechanism for simulation and prototyping. Behavioral model of the UART endpoint should be replaced by DPI wrapper. Within this wrapper there are methods which use API to open the serial port connected to the SW debugger.
- Gained runtime improvements of more than 200 times over the actual netlist simulation. It is important to mention that the current article compares gate level (not RTL) system vs improved ISS ones. But compared with RTL the difference should increase dramatically.

### Article References
1. “SystemVerilog 3.1a language reference manual”, Accellera Organization, Inc. Napa, CA  
2. Arthur Freitas “accelerating system verification using c model integration and systemverilog dpi,” Mentor U2U 2006  
3. Stuart Sutherland “Integrating systemc models into verilog using the systemverilog dpi,”  SNUG Europe 2004.  
4. Stuart Sutherland “The verilog pli is dead (maybe) -- long live the the systemverilog dpi!” SNUG 2004.  
5. Jim Kenney, "Using a processor-driven testbench for functional verification of embedded  SoCs," Embedded.com 2006.  
6. Russell Klein, “Hardware/software co-verification” Embedded Systems Conference 2003.  
7. Jason R. Andrews, “Co-Verification of Hardware and Software for ARM SoC Design”  2005, Elsevier Inc, ISBN 0-7506-7730-9.  
8. Arthur Freitas, "Hardware/Firmware Co-Verification Using ISS Integration and a  SystemVerilog DPI", DVCon, 2007  
9. Arthur Freitas, “Abgedeckt und Integriert”, Design&Elektronik Magazine, Heft 11 -  November 2006.

### Other LInks

### Article
![[HardwareSoftware Co-Verification Using the SystemVerilog DPI.pdf]]

