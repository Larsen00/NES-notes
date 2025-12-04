![[All_slides_nes.pdf#page=111]]  
**Week 4 Slide 3 – Embedded Software**

**Core idea**  
Embedded software is the code running directly on the processor inside an embedded system. It differs from general-purpose software because it is tightly constrained by the hardware it controls.

---

### **Key Points (Exam-relevant, simple)**

#### **1. What embedded software is**

- Software executing on a microcontroller (MCU) or SoC inside a device.
    
- Often stored in **flash memory** and changes infrequently → also called **firmware**.
    

#### **2. Why it is “close to hardware”**

- The code interacts directly with:
    
    - **Sensors**
        
    - **Actuators**
        
    - **Communication peripherals** (UART, SPI, I2C, radio modules)
        
- Must respect **hardware constraints**:
    
    - Very limited RAM/flash
        
    - Low CPU frequency
        
    - Energy restrictions
        

#### **3. Characteristics**

- **Hardware-specific**: usually written for one exact platform.
    
- **Performance- and energy-critical**: software must use minimal CPU cycles.
    
- **Static behaviour**: updates are less frequent and more controlled than in laptops/phones.
    

#### **4. Why C is the dominant language**

- Produces predictable, efficient machine code.
    
- Gives direct access to memory-mapped peripheral registers.
    
- Low overhead → fits into small memory budgets.
    

---

### **Mini Comparison Table**

|Type of Software|Where it runs|Flexibility|Hardware awareness|Common Language|
|---|---|---|---|---|
|**Embedded software**|Microcontroller/SoC|Low|Very high|C|
|**General-purpose software**|PC, laptop, servers|High|Low|Many (Python, Java, etc.)|
![[All_slides_nes.pdf#page=112]]  
**Week 4 Slide 4 – Stages of Embedded Software Development**

### **Key Points (Clear, concise, exam-relevant)**

#### **1. Development vs. Execution Environments**

- **Development happens on a normal computer**
    
    - You write the code
        
    - You compile (build) it into a binary file
        
- **Execution happens on the embedded device**
    
    - The binary is loaded into the device’s **flash memory**
        

#### **2. Build → Flash → Test → Deploy Workflow**

|Stage|What Happens|Why Important|
|---|---|---|
|**Source**|Write code (often in C)|Defines program logic|
|**Build**|Compiler + linker create a binary|Must match the hardware architecture|
|**Flash**|Binary is uploaded to the microcontroller via a programmer/debugger|Makes code runnable on the device|
|**Test**|Check behaviour on the actual hardware|Hardware-specific issues only appear here|
|**Deploy**|Device is delivered/used in real setting|Final production step|

#### **3. Why Testing Must Be Done on the Device**

- Embedded systems interact with sensors, actuators, and real timing conditions that cannot be fully simulated on a computer.
    

![[All_slides_nes.pdf#page=113]]  
**Week 4 Slide 5 – Embedded Operating Systems**

### **Key Points (Clear, simple, exam-relevant)**

#### **1. Purpose of an Operating System (OS)**

An **Operating System** manages and abstracts hardware resources so applications do not have to interact with raw hardware directly.

Examples of what an OS normally provides:

- Access to CPU, memory, timers
    
- Communication interfaces
    
- File or data management
    
- Process/thread management
    

#### **2. Why this matters in embedded systems**

Even though embedded devices are small and specialized, they still need:

- Controlled access to peripherals
    
- Safe sharing of hardware resources
    
- A structured way to run software
    

The slide asks: **“What is the role of an operating system?”**  
→ _To manage hardware and provide abstractions that simplify programming._

![[All_slides_nes.pdf#page=114]]  
**Week 4 Slide 6 – Embedded Operating Systems**  

### **Role of an Embedded OS**

- Manages and abstracts hardware so applications don’t directly control CPU, memory, and peripherals.
    
- Traditional desktop OSs are often unsuitable due to size, energy use, and complexity.
    

### **Systems Without an OS (Bare Metal)**

- Application talks directly to hardware registers.
    
- **Advantages:** maximum efficiency, minimal overhead.
    
- **Disadvantages:** no flexibility, developer must manually manage all hardware.
    

### **What an Embedded OS Provides**

- **Hardware abstractions:** hides low-level register operations behind APIs.
    
- **Drivers:** for common peripherals (GPIO, UART, SPI, I2C, sensors, radio).
    
- **Programming models:** event-driven systems, threads, timers, processes.
    

### **Key Concept**

An embedded OS helps manage complexity while staying lightweight enough to fit strict memory and energy constraints.


![[All_slides_nes.pdf#page=115]]  
**Week 4 Slide 7 – Requirements for Embedded OS**  

### **Small Memory Footprint**

- Must fit into devices with only a few **kilobytes** of RAM and flash.
    

### **Support for Heterogeneous Hardware**

- Works across different CPU architectures (8-bit, 16-bit, 32-bit).
    
- Adapts to varying memory sizes and different networking interfaces (wired/wireless).
    

### **Energy Efficiency**

- OS should allow or perform **duty cycling** of CPU, radio, and peripherals to reduce energy use.
    

### **Real-Time Capabilities**

- Some applications require tasks to run within strict timing limits.
    
- An **RTOS (Real-Time Operating System)** provides guarantees on worst-case execution time.
    

### **Security Requirements**

- Confidentiality, authentication, data integrity, and access control, depending on application domain.

![[All_slides_nes.pdf#page=116]]  
**Week 4 Slide 8 – Modules of an Embedded OS**  

### **Core Idea: Modularity**

- Embedded OSs are built from many small, independent modules.
    
- The developer includes **only** the modules needed for the specific application and hardware.
    

### **Build-Time Configuration**

- Selection is done using:
    
    - **Build system rules** (e.g., _make_ deciding which files to compile).
        
    - **Preprocessor directives** (`#ifdef`, `#endif`) to include/exclude code sections.
        
- This keeps the final binary small and efficient.
    

### **Binary Output**

- The resulting firmware excludes:
    
    - Drivers for peripherals the device does not have
        
    - Support for other CPU architectures
        
    - Communication protocols not used
        
- Only essential components remain.
    

---

### **Figure Explanation (Right side of slide)**

The figure shows a **stacked modular architecture**, illustrating how an embedded OS is constructed:

1. **Hardware Layer (bottom)**
    
    - Represents the physical components: CPU, memory, radios, sensors, timers, etc.
        
    - The OS must adapt to different hardware configurations.
        
2. **OS Modules (middle layers)**
    
    - Each block corresponds to a specific OS component:
        
        - Hardware abstraction layer (HAL)
            
        - Device drivers
            
        - Communication stacks (e.g., networking protocols)
            
        - Scheduling and timing modules
            
    - These modules are optional and only included if needed.
        
3. **Application Layer (top)**
    
    - The developer’s embedded application sits above the OS.
        
    - It interacts with hardware **only through the modules included** in the OS build.
        

**What the figure demonstrates:**  
A customizable, layered structure where unused modules are simply not compiled in, resulting in a minimal, efficient embedded system.

![[All_slides_nes.pdf#page=117]]  
**Week 4 Slide 9 – Event-Driven Embedded OS**  

### **Event-Driven Model**

- All processing is triggered by **events**.
    
- Events come from:
    
    - **Peripherals** (e.g., sensor ready, packet received)
        
    - **Timers** (scheduled callbacks)
        

### **Execution Structure**

- The system behaves like an **infinite loop** that waits for events and handles them one at a time.
    
- No separate processes/threads with independent stacks — everything runs in the **same context and address space**.
    

### **Benefits**

- **High efficiency** in:
    
    - Memory usage (no stacks per thread)
        
    - CPU usage (no context switching)
        
- Well suited for low-power embedded devices.
    

### **Limitations**

- Some applications are hard to express as **state machines**, especially those needing to block/wait or perform long tasks.
    

### **Example OS**

- **Contiki-NG**, a widely used event-driven embedded operating system.
    


![[All_slides_nes.pdf#page=118]]  
**Week 4 Slide 10 – Multi-Threading Operating Systems**  

---

### **Multi-Threading Concept**

- The OS allows multiple **threads** to run.
    
- Each thread has its **own context**:
    
    - Its own **stack**
        
    - Its own **program counter**
        
- The scheduler switches between threads, giving the illusion of parallel execution even on a single CPU.
    

---

### **Scheduler Responsibilities**

- Performs **context switching**:
    
    - Saves the current thread’s state
        
    - Restores another thread’s state
        
- This enables multiple tasks to progress independently.
    

---

### **Characteristics**

- Common in modern general-purpose OSs (e.g., Linux).
    
- More intuitive programming model compared to event-driven systems because:
    
    - Threads can block, sleep, and wait naturally.
        
    - Code is written sequentially instead of as state machines.
        

---

### **Costs / Limitations**

- **Memory overhead:** Each thread needs its own stack.
    
- **Runtime overhead:** Context switching consumes CPU cycles.
    
- **Energy impact:** More activity → higher power usage.
    

---

### **Example OS**

- **RIOT**, a microcontroller-focused OS using multi-threading.
  
  ![[All_slides_nes.pdf#page=119]]  
**Week 4 Slide 11 – Real-Time Operating Systems (RTOS)**  

---

### **Purpose of an RTOS**

- Main goal: provide **real-time guarantees**.
    
- Guarantees relate to **worst-case execution time (WCET)**—the maximum time a task can take.
    

---

### **Why Real-Time Guarantees Matter**

- Many embedded applications are time-sensitive:
    
    - Motor control
        
    - Medical devices
        
    - Industrial automation
        
    - Safety-critical systems
        
- Missing a deadline can cause system failure, not just a delay.
    

---

### **Development Constraints**

- RTOS development is **strict and disciplined**:
    
    - Code must be predictable.
        
    - Features that introduce uncertainty (e.g., dynamic memory allocation) are limited or forbidden.
        
    - Timing behavior must be verifiable.
        

---

### **Portability**

- Because the system must be so predictable, RTOSs are often:
    
    - Harder to port to new hardware
        
    - Less flexible than general embedded OSs
        

---

### **Example**

- **FreeRTOS**, a widely used real-time operating system for microcontrollers.


---
---

## **Comparison of Slides 9–11**

### **1. Programming Model**

|Feature|Event-Driven OS (Slide 9)|Multi-Threading OS (Slide 10)|RTOS (Slide 11)|
|---|---|---|---|
|How code runs|Single event loop|Multiple threads|Multiple threads with timing guarantees|
|Blocking allowed?|No — must return quickly|Yes — threads can block|Yes — but must meet timing constraints|
|Structure|State machines|Sequential code per thread|Sequential code per thread, but deterministic|

---

### **2. Resource Usage**

|Resource|Event-Driven|Multi-Threading|RTOS|
|---|---|---|---|
|Memory usage|**Very low** (no stacks per thread)|Higher (stack per thread)|Higher (thread stacks + timing mechanisms)|
|CPU overhead|**Very low** (no context switches)|Moderate (context switching)|Higher (context switching + scheduling analysis)|

---

### **3. Scheduling**

|Aspect|Event-Driven|Multi-Threading|RTOS|
|---|---|---|---|
|Scheduling type|Cooperative (event loop)|Preemptive or cooperative|Preemptive with timing guarantees|
|Real-time guarantees|None|None by default|**Yes** (must meet deadlines)|
|Determinism|Low|Medium|**High**|

---

### **4. Suitability / Typical Uses**

|Use Case|Event-Driven|Multi-Threading|RTOS|
|---|---|---|---|
|Low-power devices|**Excellent**|Moderate|Good but heavier|
|Simple sensor systems|**Excellent**|Overkill|Only if timing required|
|Complex apps needing concurrency|Weak|**Strong**|**Strong**|
|Time-critical systems|Not suitable|Not sufficient|**Designed for this**|

---

### **5. Development Complexity**

|Factor|Event-Driven|Multi-Threading|RTOS|
|---|---|---|---|
|Ease of coding|Harder (state machines)|Easier (natural thread model)|Hardest (strict constraints)|
|Debugging difficulty|Medium|Medium–High|High (timing behavior must be verified)|
|Portability|High|High|Lower (tight hardware constraints)|

---

## **Summary**

- **Event-driven OS** → minimal overhead, energy-efficient, but harder to write complex logic.
    
- **Multi-threading OS** → easier to program; supports concurrency; costs more memory and CPU.
    
- **RTOS** → like multithreading, but with **strict timing guarantees** and higher development rigor.
    

---

If you'd like, I can also provide a **single combined table**, or add these comparisons to your notes format.

![[All_slides_nes.pdf#page=120]]  
**Week 4 Slide 12 – Scheduling**  

---

### **Scheduling Overview**

- The **scheduler** decides which task (process/thread) uses the CPU and when.
    
- This is essential whenever multiple tasks share a processor.
    

---

### **Preemptive Scheduling**

- The scheduler can **interrupt** a running task at any time.
    
- The CPU is reassigned to another task based on scheduling rules.
    
- **Advantages:**
    
    - Fairness between tasks
        
    - Responsive user-facing systems (e.g., smartphones, PCs)
        
- **Disadvantages:**
    
    - More **context switches** → more overhead
        
    - Frequent timer interrupts prevent deep sleep → higher energy use
        

---

### **Non-Preemptive (Cooperative) Scheduling**

- A task runs **until it voluntarily yields** the CPU.
    
- **Advantages:**
    
    - More efficient and lower energy usage
        
    - Fewer context switches
        
- **Disadvantages:**
    
    - If a task forgets to yield, it can block the whole system
        
    - Timing becomes less predictable for other tasks
        

---

### **Tickless Preemptive Scheduling**

- A hybrid approach.
    
- Preemption occurs **only on interrupts** or when a task blocks naturally (not based on periodic timer ticks).
    
- **Benefits:**
    
    - More efficient than classic preemptive scheduling
        
    - Allows deeper sleep states due to fewer timer wakeups
        

---

### **Context for This Slide**

This slide introduces the fundamental ways an embedded OS can share the CPU across tasks, setting the stage for understanding real-time behavior and priority systems seen in later slides.

![[All_slides_nes.pdf#page=121]]  
**Week 4 Slide 13 – Priority Scheduling**  

---

### **Priority-Based Scheduling**

- Each task is assigned a **priority level**.
    
- The scheduler always selects the **highest-priority task** that is ready to run.
    

---

### **Behavior of the System**

- High-priority tasks (often system-level tasks) **preempt or block** lower-priority tasks.
    
- Low-priority tasks may experience **starvation** if higher-priority tasks are frequently runnable.
    

---

### **Starvation in Practice**

- In embedded systems, starvation is **less common** because:
    
    - Devices spend much of their time **idle or asleep**.
        
    - The CPU is often under low load.
        

---

### **Figure Explanation**

The figure (from Modern Operating Systems) illustrates:

- Several tasks with different priority levels stacked vertically.
    
- The scheduler chooses the **topmost (highest-priority)** runnable task.
    
- Lower-priority tasks remain pending until higher ones finish or yield.
    

---

### **Context for This Slide**

This slide expands the scheduling concepts from the previous slide by introducing **task prioritization**, which is especially important in systems needing predictable or real-time behavior.

![[All_slides_nes.pdf#page=122]]  
**Week 4 Slide 14 – Multithreading and Thread Synchronisation**  

---

## **1. Parallelism in Embedded Systems (What it means)**

### **Multicore CPUs**

- Some embedded devices have **more than one CPU core**.
    
- Each core can run a different thread at the same time → **true parallelism**.
    

### **Preemptive Scheduling on a Single Core**

- Even with only **one CPU core**, the OS can rapidly switch between threads.
    
- This creates the _illusion_ of parallelism → **pseudo-parallelism**.
    

### **Auxiliary Processors / Accelerators**

- Many SoCs (System-on-Chip) include small helper processors:
    
    - Radio processors
        
    - Sensor hubs
        
    - Cryptographic accelerators
        
- These can run tasks _in parallel_ with the main CPU.
    

---

## **2. Race Conditions (Why they happen)**

A **race condition** happens when:

- Two or more threads **access the same data or hardware**
    
- At least one thread **writes** to it
    
- Access is **not controlled**
    

This causes unpredictable results because threads “race” to use the resource.

**Example:**  
Two threads both try to update a variable called `counter`.  
If they interrupt each other, the final value may be wrong.

---

## **3. Thread Synchronisation Tools (How we avoid problems)**

### **Mutex (Mutual Exclusion Lock)**

- A mutex is like a **key** to a shared resource.
    
- Only the thread holding the key may use the resource.
    
- Prevents simultaneous access.
    

**Simple analogy:**  
One bathroom, one key.  
Only the person with the key can go in.

---

### **Condition Variables**

- A mechanism that lets a thread **wait** until some condition becomes true.
    
- Used when a thread must not continue until another thread signals something.
    

**Example:**  
A consumer thread waits until a producer thread puts data in a buffer.

---

## **4. Inter-Process Communication (IPC)**

### **Messages**

- Instead of sharing memory, threads exchange **messages**.
    
- This avoids race conditions because each message is private and copied.
    

**Example:**  
Thread A sends a sensor reading to Thread B in a message queue.

---

## **5. Figure Explanation**

The figure illustrates:

- Multiple threads running concurrently
    
- Shared resources that require protection
    
- The need for:
    
    - **Locks (mutexes)** to protect shared data
        
    - **Condition variables** to coordinate thread behavior
        
    - **Message passing** to avoid unsafe shared access
        

It visually emphasizes that multithreading introduces **coordination problems** that must be solved with synchronization tools.

---

## **6. Why This Slide Matters**

This slide shows that once an embedded system uses multithreading, **correctness** becomes a major challenge.  
You must manage _how_ threads interact to avoid crashes, data corruption, or unpredictable behavior.

![[All_slides_nes.pdf#page=123]]  
**Week 4 Slide 15 – Embedded Operating Systems**  

---

### **Overview of the Slide**

This slide presents a **visual comparison** of several embedded operating systems and how they differ in architecture, modularity, and layering.  
It shows how different OS designs stack their components, from hardware abstractions up to networking and applications.

---

### **Key Concepts in the Figure**

#### **1. Layered Architecture**

All shown OSs follow a **layered structure**, including:

- **Hardware layer** (bottom): CPU, radios, sensors, timers, memory
    
- **Hardware Abstraction Layer (HAL)**: drivers that hide hardware details
    
- **Core OS services**: scheduling, timers, memory management
    
- **Networking protocols**: IPv6, 6LoWPAN, RPL, MAC layers
    
- **Application layer** (top): the embed­ded application code
    

Each OS includes or excludes modules depending on its design philosophy.

---

### **2. Differences Between Operating Systems Shown**

The figure includes OSs such as:

- **TinyOS**
    
- **Contiki**
    
- **RIOT**
    
- **FreeRTOS** (depending on diagram context)
    

While details vary, the general comparison is:

|Aspect|Event-Driven OS (e.g., TinyOS, Contiki)|Multithreaded OS (e.g., RIOT)|
|---|---|---|
|**Programming model**|Event-driven, state machines|Threads with stacks|
|**Modularity**|Very high|High|
|**Networking stacks**|Often built-in and lightweight|More flexible, more memory usage|
|**Focus**|Low power, minimal overhead|More features, richer APIs|

---

### **3. Purpose of Showing Multiple OS Designs**

The slide demonstrates:

- There is **no single standard architecture** for embedded OSs.
    
- Each OS optimizes for a different goal:
    
    - **Low memory footprint**
        
    - **Real-time guarantees**
        
    - **Portability**
        
    - **Networking performance**
        
- The developer must choose an OS whose structure matches the system’s constraints.
    

---

### **4. High-Level Meaning of the Diagram**

The figure emphasizes that:

- Embedded OSs are built by **stacking modular components**.
    
- The network stack is often a major component in IoT-focused OSs.
    
- Hardware abstraction is essential for portability across devices.
    

![[All_slides_nes.pdf#page=124]]  
**Week 4 Slide 16 – Embedded Operating Systems**  

---

### **Purpose of the Slide**

This slide shows a **taxonomy (classification)** of embedded operating systems to highlight how different systems fit into different categories based on features, constraints, and design goals.

---

### **Main Categories in the Diagram**

The diagram presents several OS families and where they fall along important dimensions.

#### **1. General-Purpose vs. Embedded**

- **General-purpose OSs** (e.g., Linux) are powerful but too heavy for most embedded systems.
    
- **Embedded OSs** are smaller, modular, and optimized for memory, energy, and timing constraints.
    

#### **2. Real-Time vs. Non–Real-Time**

- **RTOS**: Systems providing guaranteed timing (FreeRTOS, VxWorks, etc.).
    
- **Non-RTOS**: Systems focusing on portability, networking, or low energy use (Contiki-NG, RIOT, TinyOS).
    

#### **3. Single-Core vs. Multi-Core Support**

Some OSs support multicore embedded processors, while others are optimized for ultra-low-power single-core MCUs.

#### **4. Networked Embedded OSs**

Several OSs in the chart are designed specifically for IoT devices:

- Contiki-NG
    
- RIOT
    
- TinyOS  
    These include built-in lightweight network stacks (6LoWPAN, RPL, IPv6).
    

---

### **Purpose of the Diagram**

- Shows the **ecosystem** of embedded OS options.
    
- Highlights how designs differ by:
    
    - Real-time needs
        
    - Resource availability
        
    - Networking requirements
        
    - Application complexity
        
- Helps developers select an OS appropriate for their constraints.
    

---

### **Context**

This slide complements previous ones by positioning various real operating systems relative to the conceptual frameworks already introduced (event-driven, multithreaded, RTOS).

![[All_slides_nes.pdf#page=125]]  
**Week 4 Slide 17 – How do we choose an Embedded OS?**  

---

### **Feature Considerations**

When selecting an embedded OS, developers must evaluate what the system needs:

#### **Supported Hardware**

- CPU architectures (8-bit, 16-bit, 32-bit)
    
- Available RAM/flash
    
- Peripherals (GPIO, UART, I2C, SPI, radios, sensors)
    
- Hardware accelerators
    

#### **Supported Software**

- Networking protocols (IPv6, 6LoWPAN, RPL, BLE, etc.)
    
- File systems
    
- Security libraries (crypto, authentication)
    
- Middleware or drivers
    

#### **Tools**

- Debuggers
    
- Simulators
    
- Build systems
    
- Monitoring/logging tools
    

---

### **Portability**

- **Vendor-based OS:** optimized for one hardware family but harder to port.
    
- **Generic OS:** broader support, easier to reuse code across platforms.
    
- **POSIX compliance:** improves portability and familiarity for developers.
    

---

### **Certification Needs**

- Real-time guarantees (important for safety-critical systems).
    
- Networking certification or interoperability requirements.
    

---

### **Licensing**

- **Proprietary:** may restrict usage or modification.
    
- **Permissive (e.g., MIT, BSD):** flexible for commercial use.
    
- **Copyleft (e.g., GPL):** requires sharing modifications.
    

---

### **Documentation, Support, Community**

- Quality documentation reduces development time.
    
- Active community improves stability, debugging, and long-term maintenance.
    

---

### **Context**

This slide provides a practical checklist for choosing the right embedded OS based on system requirements, hardware constraints, legal considerations, and development resources.

![[All_slides_nes.pdf#page=126]]  
**Week 4 Slide 18 – Embedded Programming**  

---

### **Interacting With Peripherals**

Embedded programming mainly involves communication with hardware peripherals:

#### **Internal peripherals (inside the SoC — System-on-Chip)**

- Timers
    
- ADC (Analog-to-Digital Converter)
    
- UART, SPI, I2C
    
- Radio modules
    

#### **External peripherals (connected on the board)**

- Sensors
    
- Actuators
    
- Displays
    
- Memory chips
    

---

### **Peripheral Registers**

Every peripheral has a set of **registers**, which the CPU reads or writes to control the hardware.

Types of registers:

- **Status registers (read-only):** indicate current state (e.g., “data ready”).
    
- **Command registers (write-only):** tell the device to perform an action.
    
- **Data/configuration registers (read/write):** store settings or data to send/receive.
    

Programmers manipulate these registers directly using memory-mapped I/O.

---

### **Bitwise and Fixed-Point Operations**

Because embedded systems operate close to hardware:

- **Bitwise operations** are used to set, clear, or read individual bits in registers.
    
- **Fixed-point arithmetic** is used instead of floating point to save CPU cycles.
    

---

### **Static Memory Allocation**

- Preferable because dynamic allocation (e.g., `malloc`) can cause fragmentation, unpredictability, and timing issues.
    
- Static allocation ensures deterministic memory usage — important for resource-constrained systems.
    

---

### **Context**

This slide introduces how embedded code interacts with hardware at a low level, preparing for later slides on interrupts and I/O behavior.

![[All_slides_nes.pdf#page=127]]  
**Week 4 Slide 19 – Events and Interrupts**  

---

### **Peripheral-Generated Events**

Peripherals can be configured to notify the CPU when something important happens.  
Examples:

- A sensor finishes a measurement
    
- A GPIO pin changes (button press, signal edge)
    
- A communication interface receives data
    

These notifications take the form of **interrupts**.

---

### **Interrupt Controller**

- A dedicated hardware module that manages interrupts from multiple devices.
    
- It decides:
    
    - Which interrupt has priority
        
    - Which handler the CPU should run
        
    - How to signal the CPU that something needs attention
        

---

### **Interrupt Request (IRQ)**

- An **IRQ** is the signal sent to the CPU when an interrupt occurs.
    
- Upon receiving an IRQ:
    
    1. The CPU **pauses** its normal execution.
        
    2. The CPU jumps to a specific function called an **interrupt handler** (or ISR: Interrupt Service Routine).
        
    3. After finishing the handler, the CPU returns to what it was doing.
        

---

### **Why Interrupts Matter**

- Allow the CPU to **sleep** until something important happens.
    
- Eliminate the need for constant polling of device status.
    
- Enable energy-efficient and responsive embedded systems.
    

---

### **Context**

This slide explains how hardware events trigger specific code execution paths, forming the foundation for interrupt-driven I/O and real-time responsiveness in embedded systems.

![[All_slides_nes.pdf#page=128]]  
**Week 4 Slide 20 – I/O Software with Busy Waiting**  

---

### **Busy Waiting Concept**

Busy waiting means the CPU repeatedly checks (“polls”) a device’s status register until the device is ready.  
The CPU does **not** perform other tasks while waiting.

---

### **Example Workflow (Printer or Any Output Peripheral)**

1. Copy the first character from memory into the peripheral’s **data register**.
    
2. Constantly read the **status register** in a loop until it says “ready.”
    
3. Copy the next character.
    
4. Repeat until the whole message/document is sent.
    

This loop occupies the CPU entirely.

---

### **Problems With Busy Waiting**

- **CPU is stuck doing nothing useful** → wastes processing time.
    
- **High energy consumption** → CPU cannot sleep.
    
- **Increased heat production** → inefficient for battery-powered systems.
    

---

### **Context**

Busy waiting is simple to implement but extremely inefficient.  
This slide prepares for the next slide, which introduces **interrupt-driven I/O**, a more efficient alternative.

![[All_slides_nes.pdf#page=129]]  
**Week 4 Slide 21 – I/O Software with Busy Waiting (Disadvantages)**  

---

### **Recap of the Example**

The example is the same as the previous slide:

- Send a string to a peripheral (e.g., printer).
    
- After writing each character, the CPU checks the peripheral's **status register** in a loop until it becomes ready.
    

---

### **Disadvantages of Busy Waiting**

This slide lists and emphasizes why busy waiting is problematic:

#### **1. Occupies the CPU Doing Nothing**

- The CPU constantly reads the status register.
    
- No other tasks can run during this time.
    
- Wastes computational resources.
    

#### **2. Wastes Energy**

- The CPU is active the entire time, even while “waiting.”
    
- Prevents entering low-power or sleep modes.
    
- Harmful for battery-powered devices.
    

#### **3. Heats Up the System**

- Unnecessary CPU activity produces heat.
    
- Can reduce device lifetime or require thermal management.
    

---

### **Context**

This slide concludes the explanation of busy waiting, highlighting why embedded systems avoid it and move toward **interrupt-driven I/O**, which solves these inefficiencies.

![[All_slides_nes.pdf#page=130]]  
**Week 4 Slide 22 – Interrupt-Driven I/O Software**  

---

### **Interrupt-Driven I/O Concept**

Instead of checking a device repeatedly, the CPU waits passively.  
A peripheral triggers an **interrupt** when it is ready, and the CPU responds only then.

---

### **Example Workflow**

1. Enable/configure interrupts for the peripheral.
    
2. Write the first character to the device’s **data register**.
    
3. CPU sleeps or performs other tasks.
    
4. When ready, the peripheral issues an **interrupt**.
    
5. Interrupt handler sends the next character.
    
6. Repeat until finished.
    

---

### **Advantages**

- **Energy efficient:** CPU can sleep between events.
    
- **No wasted cycles:** No polling loops consuming CPU time.
    
- **Better system responsiveness:** CPU can run other tasks while waiting.
    

---

## **Comparison Table: Busy Waiting vs. Interrupt-Driven I/O**

|Feature|Busy Waiting (Slides 20–21)|Interrupt-Driven I/O (Slide 22)|
|---|---|---|
|CPU usage|Constantly active, stuck in a loop|Idle or running other tasks until interrupt|
|Energy efficiency|**Poor** — CPU cannot sleep|**High** — CPU sleeps while waiting|
|Responsiveness|Only handles one task|Can process other tasks concurrently|
|Complexity|Simple to implement|Requires interrupt configuration and handlers|
|Heat generation|Higher (continuous CPU work)|Lower (reduced activity)|
|Scalability to multitasking|Poor|Good — interrupts integrate with schedulers|
|Typical use-case|Very simple or legacy systems|Modern, low-power embedded systems|

---

### **Context**

This slide marks the transition from inefficient polling-based designs to efficient, event-driven hardware interaction, a foundational concept for modern embedded software.

![[All_slides_nes.pdf#page=131]]  
**Week 4 Slide 23 – Timers**  

---

### **Hardware Timers in an SoC (System-on-Chip)**

A microcontroller typically includes several **hardware timers** with different characteristics:

#### **High-frequency timers (HF timers)**

- Run at high clock speeds (e.g., 24 MHz).
    
- Provide **fine resolution** (very small time steps).
    
- Useful for precise timing and short delays.
    

#### **Low-frequency timers (LF timers / RTC – Real-Time Clock)**

- Run at low speeds (e.g., 32 kHz).
    
- Provide **longer battery life** due to low power consumption.
    
- Used for long intervals (seconds, minutes).
    

---

### **Timer Resolution**

Timer resolution = **1 / frequency**

Examples from the slide:

- 32 kHz timer → ~30.5 µs resolution
    
- 24 MHz timer → ~41.7 ns resolution
    

Higher frequency → smaller time step → more precise timing.

---

### **Timer Overflow**

Timers have a fixed number of bits (e.g., 24-bit).  
When the counter reaches its maximum value, it wraps back to 0.

Examples:

- 24-bit + 32 kHz → overflows every **512 seconds**
    
- 24-bit + 24 MHz → overflows every **~0.7 seconds**
    

Overflow matters when scheduling long delays.

---

### **Multiple Software Timers Using One Hardware Timer**

A single hardware timer can support multiple **software timers** by using:

- A continuously running counter
    
- A **COMPARE** register: when the counter reaches this value, an interrupt fires
    
- Software updates COMPARE for each desired event
    

This enables many timers without additional hardware.

---

### **Context**

This slide introduces the fundamentals of how hardware timers operate, preparing for timing challenges and scheduling strategies in later slides.

Below is the **merged version of Slide 24 + Slide 25**, rewritten with **Obsidian-friendly math using `$$`** and structured as a single, continuous set of notes.

---

![[All_slides_nes.pdf#page=132]]  
![[All_slides_nes.pdf#page=133]]  
**Week 4 Slides 24–25 – A Timer Challenge**  

---

## **System Setup**

Two 24-bit hardware timers exist:

- **Low-frequency timer (LF timer)**
    
    - Frequency: $$f_{LF} = 32768\ \text{Hz}$$
        
    - Overflow: every **512 seconds**
        
- **High-frequency timer (HF timer)**
    
    - Frequency: $$f_{HF} = 24,000,000\ \text{Hz}$$
        
    - Overflow: **~0.7 seconds**
        

Because the HF timer overflows far too quickly, only the **LF timer** can be used for multi-minute delays.

---

# **Scheduling an Event in 5 Minutes (300 seconds)**

### **1. Read current timer value**

Let:  
$$  
\text{COUNTER} = \text{current LF timer value}  
$$

---

### **2. Convert required delay to timer ticks**

Delay = 300 seconds.

$$  
\text{INTERVAL} = 300 \times f_{LF}  
$$

Since  
$$f_{LF} = 32768\ \text{Hz}$$  
we get:

$$  
\text{INTERVAL} = 300 \times 32768 = 9,830,400  
$$

---

### **3. Compute COMPARE using wrap-around (modular arithmetic)**

Because it is a 24-bit timer:

$$  
\text{MAX} = 2^{24}  
$$

So:

$$  
\text{COMPARE} = (\text{COUNTER} + \text{INTERVAL}) \bmod 2^{24}  
$$

This guarantees the interrupt fires exactly 300 seconds from now, even if the timer wraps.

---

## **Figure Explanation (Slide 24)**

- Shows a **24-bit counter** progressing continuously.
    
- The desired delay is an **offset** added to the current value.
    
- If the sum exceeds the max (2²⁴), it **wraps** back to 0.
    
- The COMPARE register is set to the wrapped value.
    

This visualizes how long delays are scheduled using timers that overflow.

---

# **Scheduling an Event in 10 Minutes (600 seconds)**

### **Problem**

600 seconds is longer than the LF timer’s overflow period (512 seconds), so the naïve method fails.

---

## **Approach 1 – Generate More Events Than Needed**

Schedule an event every **300 seconds** and ignore every second interrupt:

- Event at 300 s → ignore
    
- Event at 600 s → handle
    

This works but is inelegant and wastes interrupts.

---

## **Approach 2 – Lower the Timer Frequency Using a Prescaler**

Set **PRESCALER = 1**, meaning the LF timer frequency halves:

$$  
f_{LF,new} = \frac{32768}{2} = 16384\ \text{Hz}  
$$

Now overflow becomes twice as long:

- Old overflow: 512 s
    
- New overflow:  
    $$  
    \frac{512}{2^{-1}} = 1024\ \text{seconds}  
    $$  
    (safely longer than 600 s)
    

Now compute the new interval:

$$  
\text{INTERVAL} = 600 \times 16384 = 9,830,400  
$$

Same number of ticks as before, but at a lower frequency → fits within overflow limits.

Then:

$$  
\text{COMPARE} = (\text{COUNTER} + \text{INTERVAL}) \bmod 2^{24}  
$$

---

## **Figure Explanation (Slide 25)**

- Shows how the **prescaler reduces resolution** but **increases overflow period**, making long delays possible.
    
- Also shows the idea of scheduling shorter intervals and selectively using interrupts.
    

---

## **Context**

Slides 24–25 teach how to schedule long-duration events with timers that overflow often.  
Key concepts learned:

- Converting seconds → timer ticks
    
- Using modular arithmetic for wrap-around timers
    
- Handling intervals longer than overflow
    
- Adjusting timer frequency with a **prescaler**
    

---

If you want, I can also create a comparison table summarizing the two strategies for handling intervals longer than the overflow period.

![[All_slides_nes.pdf#page=134]]  
**Week 4 Slide 26 – Watchdog Timer**  

---

### **What a Watchdog Timer Is**

A **watchdog timer** is a safety mechanism designed to detect when the system stops functioning correctly.

It is a hardware timer that counts down continuously.

---

### **How It Works**

- During normal operation, the software must **periodically reset (feed/kick)** the watchdog timer.
    
- If the software fails to reset it in time, the watchdog timer **expires**.
    
- When it expires, the watchdog automatically **resets the entire system**.
    

This prevents the device from getting permanently stuck due to software faults.

---

### **What Problems It Detects**

- Deadlocks
    
- Infinite loops
    
- Code stuck waiting on a resource that never becomes ready
    
- Unexpected hangs caused by bugs or corrupted state
    

---

### **Special Behaviors**

- Can be **paused** when the CPU enters long sleep modes.
    
- Can be **halted** by a debugger to avoid unintended resets during development.
    

---

### **Context**

The watchdog timer increases system robustness by ensuring the device can recover from failures without human intervention, which is crucial for embedded systems deployed in the field.

![[All_slides_nes.pdf#page=135]]  
**Week 4 Slide 27 – Direct Memory Access (DMA)**  

---

### **What DMA Is**

**Direct Memory Access (DMA)** is a hardware feature that allows data to move between **memory** and **peripherals** **without using the CPU**.

This offloads repetitive data-transfer work from the processor.

---

### **Why DMA Is Useful**

- Frees the CPU for other tasks
    
- Reduces CPU load → improves energy efficiency
    
- Provides consistent transfer speed without software overhead
    
- Ideal for large or continuous transfers (audio, sensors, radio packets, etc.)
    

---

### **Supported Transfer Types**

DMA controllers typically support:

- **Memory → Memory**  
    (e.g., copying a block of RAM to another location)
    
- **Memory → Peripheral**  
    (e.g., sending a buffer to a UART or SPI device)
    
- **Peripheral → Memory**  
    (e.g., receiving sensor data without CPU intervention)
    
- **Peripheral → Peripheral**  
    (less common but possible on some MCUs)
    

---

### **Interrupt on Completion**

- When the DMA transfer is finished, the DMA controller issues an **interrupt**.
    
- The CPU wakes (or switches tasks) to handle the result only when needed.
    

---

### **Advantages Summary**

- Lower energy consumption
    
- More predictable transfer timing
    
- CPU remains free for higher-level logic
    
- Reduces the risk of timing issues caused by software delays
    

---

### **Figure Explanation**

The diagram shows:

- Memory and peripherals connected through the DMA controller
    
- Data flowing **directly** between them without passing through the CPU
    
- CPU only reacting at the end via interrupt
    

This visually reinforces the idea that DMA bypasses the CPU during transfers.

![[All_slides_nes.pdf#page=136]]  
**Week 4 Slide 28 – MCU Power Modes**  

---

## **Purpose of the Slide**

Microcontrollers (MCUs) offer multiple **power modes** to balance energy consumption and available functionality.  
These modes control which hardware components remain active.

---

## **1. Active Mode**

- **CPU active**
    
- **RAM on**
    
- **High-frequency (HF) clock on**
    
- **Internal peripherals available**
    
- Highest energy consumption  
    Used when running computations or handling events immediately.
    

---

## **2. Idle Mode**

- **CPU off**
    
- **RAM on**
    
- **HF clock still on**
    
- **Internal peripherals available**  
    Useful when waiting briefly for events while still needing peripherals to run.
    

---

## **3. Sleep Mode (Standby Mode)**

- **CPU off**
    
- **RAM retention** (contents preserved)
    
- **HF clock off**
    
- **Internal peripherals not available**
    
- **Low-frequency (LF) clock on** → can schedule wake-up  
    This mode significantly reduces consumption while still supporting timed wakeups.
    

---

## **4. Deep Sleep Mode (Shutdown Mode)**

- **CPU off**
    
- **No RAM retention** → memory contents lost
    
- **HF clock off**
    
- **LF clock off**
    
- **Internal peripherals unavailable**
    
- Wakeup possible only by **pin edge** (external signal)  
    Lowest power state.
    

---

## **Figure Explanation**

The figure shows a layered block diagram illustrating:

- Different power modes arranged from **highest** to **lowest** energy usage
    
- Which components (CPU, RAM, clocks, peripherals) are active in each mode
    

It visually reinforces how functionality decreases as you enter deeper sleep states, but energy savings increase.

---

## **Context**

Understanding MCU power modes is essential for designing **energy-efficient embedded systems**, especially battery-powered IoT devices.

![[All_slides_nes.pdf#page=137]]  
**Week 4 Slide 29 – Example: CC2650 Power Modes**  

---

## **Purpose of the Slide**

This slide shows **actual measurements** from the Texas Instruments CC2650 microcontroller to demonstrate how much energy each power mode consumes in practice.

---

## **Understanding the Diagram**

The figure provides current consumption values for different states of the CC2650:

### **Active + Radio TX/RX Modes**

- When the radio is transmitting or receiving, current draw is **tens of milliamps**.
    
- These are the **highest-power** states of the MCU.
    

### **Active CPU Mode**

- CPU running (HF clock on) uses **several milliamps**.
    
- Cost depends on workload and clock frequency.
    

---

### **Idle and Sleep Modes**

- With CPU off but RAM retained and HF clock disabled, consumption drops dramatically.
    
- Typical currents: **microamps**.
    

---

### **Standby Mode**

- LF clock stays on for timed wakeups.
    
- Consumption typically in the **low microamp** range.
    

---

### **Shutdown Mode**

- RAM lost, nearly everything off.
    
- Consumption reaches **sub-microamp** levels.
    

---

## **Meaning of the Data**

- Shows the **orders-of-magnitude difference** between power states.
    
- Highlights why MCU software must carefully choose when to sleep and which peripherals to keep active.
    
- Confirms the theoretical model from Slide 28 with real hardware numbers.
    

---

## **Context**

This slide reinforces the importance of power-mode management by showing **real-world power consumption** from a popular IoT microcontroller.

![[All_slides_nes.pdf#page=138]]  
**Week 4 Slide 30 – Example: CC2650 Consumption**  

---

## **Purpose of the Slide**

This slide provides **measured current consumption values** for different operation states of the CC2650 MCU, giving a concrete understanding of how much energy various activities cost.

---

## **Interpreting the Figure**

The chart lists current consumption for a range of activities:

### **Radio Operations (Highest Consumption)**

- **TX (Transmit)** and **RX (Receive)** modes consume the most power.
    
- Values are typically **tens of milliamps**, depending on:
    
    - Output power
        
    - Modulation settings
        
    - Radio protocol (BLE, IEEE 802.15.4)
        

These dominate the energy budget in wireless IoT devices.

---

### **Active CPU Mode**

- CPU running with HF clock enabled consumes **milliamps**.
    
- Exact value depends on:
    
    - CPU frequency
        
    - Amount of code executed
        
    - Peripheral activity
        

---

### **Peripheral Activity**

- Sensors, ADC, SPI, I2C, timers, and other modules add smaller but noticeable current contributions.
    
- Each peripheral increases energy usage depending on whether it is active or idle.
    

---

### **Sleep / Standby Modes**

- **Standby:**
    
    - RAM retention + LF clock running → typically **microamp** range.
        
- **Shutdown:**
    
    - RAM lost, all clocks off → **sub-microamp** consumption.
        

These modes enable long battery life when the MCU spends most time sleeping.

---

## **What the Slide Demonstrates**

- The **radio** is often the single largest energy consumer.
    
- The **CPU** is significantly cheaper than radio activity but still costly.
    
- **Deep sleep modes** are essential for battery-operated systems.
    
- Understanding these values is crucial for designing energy-efficient firmware.
    

---

## **Context**

This slide builds on the previous ones by connecting theoretical power-mode concepts to real-world consumption numbers taken from an actual MCU (TI CC2650).

![[All_slides_nes.pdf#page=139]]  
**Week 4 Slide 31 – Embedded Programming Tricks**  

---

## **Two’s Complement for Signed Numbers**

Most embedded systems use **two’s complement** to represent signed integers.

### **How to compute a negative N-bit value**

To represent a negative number in two’s complement:

$$  
\text{value} = 2^N - |\text{number}|  
$$

**Example (8-bit):**  
To represent **–100**:

$$  
256 - 100 = 156 = 0x9C  
$$

This is how the hardware expects negative numbers to be encoded.

---

## **Use Explicit and Minimal Data Types**

Embedded systems vary in how large `int` is (sometimes 16 bits, not 32).  
To avoid bugs, always use fixed-width types:

- `int32_t`, `uint32_t`
    
- `int16_t`, `uint16_t`
    
- `int8_t`, `uint8_t`
    

### **Why?**

- Guarantees the number of bits
    
- Avoids overflow mistakes
    
- Saves memory (especially important for RAM-constrained devices)
    

---

## **Static Variables**

Defined as:

```c
static uint8_t A;
```

### **What this means**

- Stored in **global/static memory**, not on the stack
    
- The value **persists between function calls**
    
- Useful for state machines or preserving values without using global variables
    

---

## **Volatile Variables**

Defined as:

```c
volatile uint8_t A;
```

### **What this means**

- Tells the compiler **“this value may change unexpectedly”**  
    (e.g., updated by an interrupt handler or peripheral)
    
- Compiler is **not allowed** to optimize the variable into a register or cache
    

### **Why volatile is critical**

Without `volatile`, the compiler may:

- Assume the variable never changes
    
- Remove necessary reads
    
- Break interrupt-driven functionality
    

---

## **Context**

This slide teaches essential low-level C concepts required for reliable embedded programming—especially where hardware interactions, timing, and memory constraints matter.

![[All_slides_nes.pdf#page=140]]  
**Week 4 Slide 32 – Embedded Programming Tricks: Inline Functions**  

---

## **Inline Functions**

An **inline function** asks the compiler to replace the function call with the function’s code directly.

### **Why this matters in embedded systems**

- **Removes call overhead**  
    Function calls usually require pushing registers, jumping, returning, etc.  
    Inlining avoids all of that overhead.
    
- **Improves performance**  
    Especially helpful for very small, frequently used functions.
    
- **Prevents code duplication**  
    Unlike manually copy-pasting logic, inline functions keep the code clean.
    

---

## **Example From the Slide**

```c
inline sum (int a, int b){
    int result;
    result = a + b;
    return result;
}
```

Using it:

```c
c = sum(a,b);
```

This becomes equivalent to:

```c
c = a + b;
```

Because the compiler replaces the call with the actual computation.

---

## **When to Use Inline Functions**

- Short functions (1–3 operations)
    
- Frequently called inside loops or timing-critical code
    
- Situations where even small performance gains matter
    

---

## **When Not to Use Inline**

- Large functions → code bloat
    
- Recursive functions → cannot be inlined
    
- Functions needed for debugging breakpoints → harder to inspect
    

---

## **Context**

Inline functions provide a safer alternative to macros for eliminating function-call overhead while keeping code readable and maintainable.

![[All_slides_nes.pdf#page=141]]  
**Week 4 Slide 33 – Embedded Programming Tricks: Macros**  

---

## **Avoid Hardcoded Numbers**

Using macros prevents magic numbers from being scattered through the code.

Example:

```c
#define TICKS_IN_SECOND 32768
```

Makes code easier to understand and maintain.

---

## **Remove Unneeded Functionality at Compile-Time**

Conditional compilation:

```c
#ifdef FEATURE
    ...
#endif
```

Allows enabling or excluding code before building the binary — important for keeping firmware small.

---

## **Use Parentheses to Avoid Macro Bugs**

Macros are simple text replacements, so missing parentheses can change meaning.

### **Broken example:**

```c
#define ONE_PLUS_ONE 1+1
A = ONE_PLUS_ONE * 10; // becomes 1 + 1 * 10 = 11 (WRONG)
```

### **Correct version:**

```c
#define ONE_PLUS_ONE (1+1)
```

---

## **Function-Like Macros**

These also require parentheses.

### **Broken example:**

```c
#define TIMES_TWO(x) x*2
A = TIMES_TWO(1+1); // becomes 1 + 1*2 = 3 (WRONG)
```

### **Correct version:**

```c
#define TIMES_TWO(x) (x)*2
```

---

## **Key Takeaway**

Macros are powerful but **dangerous** because they do not respect C’s type system or scoping rules — they are purely text substitution.

Inline functions (from the previous slide) are generally safer.

---

## **Context**

This slide highlights the importance of writing safe, predictable macro definitions to avoid subtle and hard-to-find bugs in embedded projects.

![[All_slides_nes.pdf#page=142]]  
**Week 4 Slide 34 – Embedded Programming Tricks: Efficient Math**  

---

## **Bit Shifting for Fast Multiplication and Division**

### **Left Shift (`<<`) = Multiply by powers of 2**

Shifting left by **N** bits multiplies a number by **2ⁿ**.

Example:

```c
A = A << 2;
```

This is equivalent to:

$$  
A = A \times 4  
$$

### **Right Shift (`>>`) = Divide by powers of 2**

Shifting right by **N** bits divides by **2ⁿ** (fractional remainder is discarded).

Example:

```c
A = A >> 2;
```

Equivalent to:

$$  
A = \left\lfloor \frac{A}{4} \right\rfloor  
$$

---

## **Use Fixed-Point Instead of Floating-Point**

Floating-point operations are:

- Slower
    
- More energy-consuming
    
- Sometimes unsupported in hardware
    

Fixed-point stores scaled integer values representing real numbers.

### **Example From the Slide**

Temperature stored as a **16-bit integer** in units of 1/100 °C.

If:  
$$  
T = 2535  
$$  
It represents:

$$  
25.35^\circ \text{C}  
$$

Dividing by 2 using a right shift:

```c
T = T >> 1;
```

gives:

$$  
T = 1267  
$$

which corresponds to:

$$  
12.67^\circ \text{C}  
$$

This avoids expensive floating-point operations.

---

## **Context**

This slide explains how low-level arithmetic tricks significantly improve performance and energy efficiency — crucial for time-sensitive or power-constrained embedded systems.


![[All_slides_nes.pdf#page=143]]  
**Week 4 Slide 35 – Specific Bits**  

---

## **Purpose of the Slide**

Many embedded tasks require manipulating **individual bits** inside a byte (8-bit value).  
This is essential when configuring hardware registers, since each bit often enables/disables a feature.

---

## **Why Individual Bits Matter**

A peripheral register may pack multiple settings into one byte.  
For example:

- Bit 0 → Enable sensor
    
- Bit 1 → Set range
    
- Bit 2 → Reset flag
    
- Bits 3–7 → Reserved or additional configuration
    

To change **one setting**, you must modify only **one bit** without affecting the others.

---

## **Understanding the Figure**

The figure shows a byte divided into 8 bits:

```
bit7 bit6 bit5 bit4 bit3 bit2 bit1 bit0
```

It highlights:

- How a single bit can represent a configuration parameter
    
- That you may need to read, set, clear, or toggle _just one_ of these bits
    
- That incorrect bit manipulation can corrupt other settings stored in the same byte
    

---

## **Context**

This slide sets up the concept behind the next slide, which introduces the **actual bitwise operations** (AND, OR, XOR, masks) used in embedded programming to safely manipulate specific bits in hardware registers.

![[All_slides_nes.pdf#page=144]]  
**Week 4 Slide 36 – Embedded Programming Tricks: Bitwise Operations**  

---

## **Purpose of the Slide**

This slide teaches how to **set, clear, toggle, and read** specific bits in a byte — a fundamental skill when working with hardware registers.

---

## **1. Creating a Bit Mask**

To isolate a specific bit, create a mask by shifting `0x01` left:

```c
M = (0x1 << 6);   // mask for bit 6 → 0b01000000
```

This mask has a **1** at the position of the bit you care about and **0** elsewhere.

---

## **2. Setting a Bit**

Use **OR (`|`)** to set a bit to 1:

```c
A = A | (0x1 << 6);   // sets bit 6
```

- OR with 1 → bit becomes 1
    
- OR with 0 → bit stays unchanged
    

---

## **3. Toggling a Bit**

Use **XOR (`^`)** to invert a bit:

```c
A = A ^ (0x1 << 6);   // toggles bit 6
```

- XOR with 1 → flips the bit
    
- XOR with 0 → keeps the bit
    

---

## **4. Clearing a Bit**

Use **AND (`&`)** with the **inverse of the mask** to force a bit to 0:

```c
A = A & ((0x1 << 6) ^ 0xFF);   // clears bit 6
```

Here:

- `(0x1 << 6)` = mask for bit 6
    
- `^ 0xFF` flips the mask → bit 6 becomes 0, all others 1
    
- AND with this clears bit 6 while preserving all other bits
    

---

## **5. Checking if a Bit Is Set**

Use **AND** with the mask:

```c
if (A & (0x1 << 6)) {
    // bit 6 is set
}
```

If the result is non-zero, the bit is **1**.

---

## **Context**

These operations allow precise control of hardware configuration registers, enabling embedded software to enable features, disable features, detect hardware states, or modify device behavior at the granularity of single bits.

![[All_slides_nes.pdf#page=145]]  
**Week 4 Slide 37 – Sets of Bits**  

---

## **Purpose of the Slide**

Some hardware registers pack **multiple related configuration bits** into a group (e.g., 2-bit mode, 3-bit rate).  
This slide introduces the idea of working with **bit fields**, not just single bits.

---

## **Why Sets of Bits Matter**

A byte may contain:

- A **3-bit field** (e.g., output data rate)
    
- A **2-bit field** (e.g., measurement range)
    
- Other control bits
    

To modify or read such fields, you must:

- Extract only those bits
    
- Change them without touching the rest of the byte
    

---

## **Understanding the Figure**

The figure shows a hardware register (example from the ADXL362 accelerometer):

```
bit7  bit6  bit5  bit4  bit3  bit2  bit1  bit0
 |     |     |     |    <---3-bit field--->   |
```

It illustrates:

- A **3-bit field** occupying bits 0–2
    
- A **2-bit field** occupying bits 6–7
    
- Middle bits used for other purposes
    

This demonstrates why masks must sometimes cover **multiple bits**, not just one.

---

## **Context**

This slide prepares for the next one, which teaches how to actually **read** and **write** multi-bit fields using masks, shifts, and bitwise operations.

![[All_slides_nes.pdf#page=146]]  
**Week 4 Slide 38 – Embedded Programming Tricks: More Bitwise Operations**  

---

## **Purpose of the Slide**

This slide explains how to **read and write multi-bit fields** inside a byte, such as configuration fields in hardware registers.

These operations combine:

- Masks
    
- Bit shifting
    
- AND, OR
    

---

## **1. Creating Masks for Multi-Bit Fields**

To isolate a group of bits, you create a mask that covers multiple positions.

### **Example Masks**

- Mask for the **first 3 bits** (bits 0–2):
    

$$  
\text{MASK3} = (0x1 << 3) - 1 = 0b00000111  
$$

- Mask for **2 bits** (bits 0–1):
    

$$  
\text{MASK2} = (0x1 << 2) - 1 = 0b00000011  
$$

These masks allow you to cleanly extract or replace fields.

---

## **2. Reading a Set of Bits**

### **Reading the 3-bit ODR field (bits 0–2)**

```c
ODR = FILTER_CTRL & MASK3;
```

This keeps the lowest 3 bits and clears the others.

### **Reading the 2-bit RANGE field (bits 6–7)**

```c
RANGE = (FILTER_CTRL >> 6) & MASK2;
```

Steps:

1. Shift right 6 → moves bits 6–7 down to positions 0–1
    
2. Mask them → clears everything else
    

---

## **3. Writing a Set of Bits (Safely)**

To write a field, you must **clear the old bits** first, then **insert the new bits**.

### **Writing the 3-bit ODR field (bits 0–2)**

```c
FILTER_CTRL = (FILTER_CTRL & (0xFF ^ MASK3)) | (new_odr & MASK3);
```

- `(0xFF ^ MASK3)` clears bits 0–2
    
- `new_odr & MASK3` ensures only the lower 3 bits are written
    
- OR combines the preserved bits + new field
    

---

### **Writing the 2-bit RANGE field (bits 6–7)**

```c
FILTER_CTRL = (FILTER_CTRL & (0xFF ^ (MASK2 << 6))) | ((new_range & MASK2) << 6);
```

Steps:

1. `(MASK2 << 6)` → aligns the 2-bit mask to bits 6–7
    
2. Clear those bits in the original byte
    
3. Insert the new value, shifted to the correct position
    

---

## **Key Takeaway**

Working with multi-bit fields requires:

- Masks for the correct width
    
- Shifting fields into the right position
    
- Clearing before writing
    
- Careful use of AND/OR operations
    

These operations are essential for writing safe and correct hardware configurations.


![[All_slides_nes.pdf#page=147]]  
**Week 4 Slide 39 – Programming Embedded Systems**  

---

## **Purpose of the Slide**

This slide explains how the final compiled firmware is **uploaded (flashed)** onto an embedded device and what hardware tools are involved.

---

## **Build Output: The Binary File**

- The toolchain (compiler + linker) produces a **binary file** such as `.bin`, `.hex`, or `.elf`.
    
- This binary contains the machine code that runs on the microcontroller.
    

---

## **Flashing the Device**

Uploading the binary into the microcontroller’s **flash memory** is known as “flashing.”

This is typically done using a **programmer / debugger** device that connects to the MCU via specialized pins.

---

## **Programmer / Debugger Hardware**

A programmer/debugger:

- Communicates with the PC over **USB or serial**
    
- Converts commands into the MCU’s programming protocol
    
- Can:
    
    - Upload code
        
    - Read memory
        
    - Set breakpoints
        
    - Debug running software
        

Many development boards include this hardware **built in**, so no external programmer is needed.

---

## **Bootloader-Based Flashing**

Some MCUs include a **bootloader** that can receive firmware over UART or another interface.

Advantages:

- No special hardware required
    
- Useful for field updates
    

---

## **Figure Explanation**

The figure shows:

- A TI LaunchPad development board
    
- On-board programmer/debugger chip
    
- MCU connected to the programmer through a standard debug/programming interface
    

It illustrates how flashing works in real hardware.

---

## **Context**

This slide forms the bridge between software development on a PC and deployment to an embedded device, highlighting how firmware is physically transferred into the MCU.

![[All_slides_nes.pdf#page=148]]  
**Week 4 Slide 40 – Programming/Debugging Interfaces**  

---

## **Purpose of the Slide**

This slide presents the **standard hardware interfaces** used to program and debug microcontrollers.  
These interfaces allow tools to upload firmware, read memory, set breakpoints, and control execution.

---

## **1. JTAG (Joint Test Action Group) – IEEE 1149.1**

- **Wires:** TCK, TMS, TDI, TDO (+ optional RESET)
    
- **Topology:** Daisy-chain (multiple devices in a chain)
    
- **Use cases:**
    
    - Programming
        
    - Debugging
        
    - Boundary scan testing
        
- Very common in industry.
    

---

## **2. cJTAG (Compact JTAG) – IEEE 1149.7**

- **Wires:** TMSC, TCKC (+ optional RESET)
    
- Reduced pin count (2-wire instead of 4-wire).
    
- **Topology:** Star topology → supports multiple devices individually.
    
- Designed for low-power, low-pin microcontrollers.
    

---

## **3. SWD (Serial Wire Debug)**

- **Wires:** SWDIO, SWCLK (+ optional RESET)
    
- ARM Cortex-specific debugging interface.
    
- Also 2-wire like cJTAG.
    
- Supports star topology.
    
- Most ARM MCUs today use SWD instead of full JTAG.
    

---

## **Comparison Summary**

|Interface|Wires|Typical Use|Topology|Notes|
|---|---|---|---|---|
|**JTAG**|4–5|Debugging, programming, boundary scan|Daisy chain|Most flexible, more pins|
|**cJTAG**|2–3|Programming + debugging|Star|Reduced-pin JTAG variant|
|**SWD**|2–3|ARM debugging + programming|Star|Standard on ARM Cortex MCUs|

---

## **Figure Explanation**

The images show:

- A CC2650 MCU with labeled debug pins
    
- Pin assignments for both **SWD** and **JTAG** on example boards
    

Visually reinforcing:

- How few pins are required for programming
    
- Differences between the interfaces
    

---

## **Context**

Understanding debug/programming interfaces is essential when selecting hardware, designing PCBs, or diagnosing embedded systems in development.

![[All_slides_nes.pdf#page=149]]  
**Week 4 Slide 41 – Debugging Embedded Software**  

---

## **Purpose of the Slide**

This slide summarizes the main tools and techniques used to debug embedded systems, highlighting that debugging embedded software often requires **hardware-aware methods**.

---

## **1. Hardware Debuggers**

Debuggers allow:

- Setting **breakpoints**
    
- Inspecting or modifying **memory**
    
- Stepping through instructions
    
- Monitoring CPU registers
    

### **Limitations**

- Breakpoints can break timing-sensitive or distributed systems.
    
- Debuggers may not be available in deployed (in-the-field) systems.
    

---

## **2. LEDs as Debugging Indicators**

A simple but effective method:

- Blink LED when entering/exiting certain code sections.
    
- Turn on an LED when hitting an error state.
    

Useful when no serial or debugger is available.

---

## **3. Log Messages / Printing**

- Send output through UART to a serial terminal.
    
- Write logs to flash memory.
    
- Transmit debug messages wirelessly (if supported).
    

Printing is powerful but:

- Adds overhead
    
- May require peripheral initialization
    
- Can change timing behavior
    

---

## **4. Electrical Measurement Tools**

These tools debug **hardware–software interaction**:

- **Oscilloscopes**: visualize voltage signals over time
    
- **Multimeters**: check voltage/current levels
    
- **Logic analyzers**: view digital buses (SPI, I2C, UART) and decode protocols
    

Useful when debugging communication issues or timing problems.

---

## **Figure Explanation**

The figure shows a **logic analyzer** capturing digital signals, emphasizing that low-level signal inspection is often required in embedded debugging.

---

## **Context**

Embedded debugging often combines **software debugging tools** with **electrical measurement tools**, because failures may involve interactions between the MCU, peripherals, timing, and hardware signals.

---
---
---
Here are **5 multiple-choice questions** covering concepts from the entire slide set.  
(As requested: **answers are NOT shown**.)

---

## **MCQ 1 — Embedded Operating Systems**

Which of the following is **NOT** a requirement typically associated with embedded operating systems?

A. Small memory footprint  
B. Energy efficiency  
C. Real-time capabilities  
D. Full desktop-grade multitasking and GUI support

---

## **MCQ 2 — Busy Waiting vs. Interrupt-Driven I/O**

Busy waiting is inefficient mainly because:

A. It requires additional hardware timers  
B. It prevents the CPU from sleeping while waiting  
C. It disables access to peripherals  
D. It requires complex interrupt handlers

---

## **MCQ 3 — Timers and Overflow**

A 24-bit timer running at 32 kHz will overflow approximately every:

A. 0.7 seconds  
B. 512 seconds  
C. 1024 seconds  
D. 600 seconds

---

## **MCQ 4 — Bitwise Operations**

Which operation would **clear** bit 4 of an 8-bit register called `REG`?

A. `REG = REG | (1 << 4)`  
B. `REG = REG ^ (1 << 4)`  
C. `REG = REG & ~(1 << 4)`  
D. `REG = REG + (1 << 4)`

---

## **MCQ 5 — Multithreading and Synchronisation**

A mutex is used to:

A. Multiply two numbers efficiently  
B. Avoid race conditions by giving exclusive access to a resource  
C. Put the CPU into sleep mode  
D. Convert floating-point numbers into fixed-point form

---

If you want, I can generate **more MCQs**, **short-answer questions**, or **exam-style problems**.

Here are the answers:

---

## **MCQ Answers**

1. **D** – Full desktop-grade multitasking and GUI support
    
2. **B** – It prevents the CPU from sleeping while waiting
    
3. **B** – 512 seconds
    
4. **C** – `REG = REG & ~(1 << 4)`
    
5. **B** – Avoid race conditions by giving exclusive access to a resource
    

---

If you'd like, I can generate more questions or create a full practice exam.