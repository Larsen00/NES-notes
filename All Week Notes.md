WEEK 1 NOTES
## Slide 4
![[All_slides_nes.pdf#page=4]]

---
### What the slide says
- An embedded system is **a computer inside a device** whose main purpose is *not* general computation.  
- It performs a **dedicated function** within a larger system or product.  
- Typically involves measuring and controlling **physical operations**.  
- Contrasted with **general-purpose computers** (laptops, desktops, servers).  
- Embedded systems are **everywhere** (washing machines, GPS, pacemakers, printers, etc.).

### My own understanding
- The key difference is **purpose**:  
  - Embedded = specialized, single purpose  
  - General computers = versatile, multi-purpose  
- Embedded systems often run **real-time tasks** and interact with physical sensors/actuators.

### Possible questions to think about
- Why do embedded systems need to be optimized for power, size, and reliability?  
- What makes an embedded system “embedded” vs. “just a computer”?  
- How does specialization allow cost or power savings?


## Slide  - Washing Machine as an Embedded System
![[All_slides_nes.pdf#page=5]]

![[All_slides_nes.pdf#page=6]]
**Week 1 Slide 6 – Washing Machine as an Embedded System**

*Notes:*
*   This slide breaks down a **washing machine** as a classic example of an **embedded system**, detailing its key functions.
*   **I/O Functions:**
    *   **Input:** User provides settings via buttons, switches, or a touchscreen (programme, temperature, etc.).
    *   **Output:** System provides feedback via a screen or LEDs (status, errors).
*   **Control Functions (Sensing & Actuation - Cyber-Physical Link):**
    *   **Sensing:** Measures physical parameters (water level, temperature, weight).
    *   **Actuation:** Controls physical components based on sensor data and programme (water valves, heater, motor RPM).
*   **Safety Functions:** Implements checks to prevent damage or hazardous operation (door closed, load not too heavy, water present before heating).
*   **Time Keeping:** Schedules the sequence of washing stages and enables features like delayed start.
*   **Exam Relevance:** This is a perfect case study. You should be able to **decompose a familiar appliance** (like a microwave or thermostat) into similar embedded system components: **Input, Output, Control (Sensing/Actuation), Safety, and Timing**. It demonstrates that an embedded system is a **special-purpose computer controlling a physical process**.

![[All_slides_nes.pdf#page=7]]
**Week 1 Slide 7 – Connecting the Digital to the Physical World**

*Notes:*
*   This slide highlights the defining characteristic of embedded systems: they are **cyber-physical systems** that **bridge the digital and physical worlds**.
*   **Sensors:** **Input transducers**. They convert a **physical phenomenon** (light, sound, temperature, pressure, motion) into an **electrical signal** that the digital processor can read. Examples: cameras, microphones, thermometers, motion sensors (PIR), radar.
*   **Actuators & Output Devices:** **Output transducers**. They convert an **electrical signal** from the processor into a **physical action or output**. Examples: motors, valves, heaters, speakers, screens, lights.
*   **Key Concept:** This **sensing → processing → actuation loop** is the core of most embedded systems. The "embedded" computer is in the middle, making decisions based on sensor data to control the physical world.
*   **Exam Relevance:** You must understand the roles of **sensors** (input from physical world) and **actuators** (output to physical world). Be able to give examples. This is fundamental to defining what an embedded system does.

![[All_slides_nes.pdf#page=8]]
**Week 1 Slide 8 – Two big trends in Embedded Systems**

*Notes:*
*   This slide introduces the **two major, overarching trends** that define modern embedded systems and set the context for the entire course.
*   **1. Connectivity:** Embedded systems are increasingly **networked**. They communicate with other devices, systems, or the cloud to share data and coordinate actions. This leads to **Networked Embedded Systems** and the **Internet of Things (IoT)**.
*   **2. Intelligence:** Embedded systems are becoming **smarter**. They incorporate **Artificial Intelligence (AI)** and **Machine Learning (ML)** to extract knowledge from data, reason, and make autonomous decisions. This moves them beyond simple pre-programmed rules.
*   **Exam Relevance:** These two trends are the **core themes of the course**. Everything that follows (networking protocols, time sync, embedded ML) relates to enabling **connectivity** and/or **intelligence**. You will likely need to discuss these trends in an exam context.

![[All_slides_nes.pdf#page=9]]
**Week 1 Slide 9 – Networked Embedded Systems**

*Notes:*
*   This slide defines the evolution from isolated to **Networked Embedded Systems** (also called Distributed Embedded Systems).
*   **Isolated Embedded System:** A single computer dedicated to controlling one machine (e.g., a thermostat inside a boiler).
*   **Networked Embedded System:** A **group of embedded devices** connected via a network (wired or wireless) that **cooperate to achieve a common goal**. This enables more complex, distributed applications.
*   **Historical Note:** The first networked systems used **wired networks** (like the CAN Bus in cars) due to reliability and real-time requirements.
*   **Exam Relevance:** Understand the distinction between isolated and networked. The key idea is **cooperation over a network**. This is the foundation for concepts like sensor networks and IoT. The example of a car's internal network (CAN Bus) is a classic wired networked embedded system.

![[All_slides_nes.pdf#page=10]]
**Week 1 Slide 10 – CAN Bus**

*Notes:*
*   This slide presents **CAN Bus** (Controller Area Network) as a seminal example of a **wired networked embedded system**.
*   **Purpose:** Designed for **vehicles** to allow microcontrollers and devices (ECUs - Electronic Control Units) to communicate reliably without a central computer.
*   **Key Facts:** Developed by Bosch (1983), first used by Mercedes-Benz (1991), ISO standard (1993).
*   **How it works:** It's a **broadcast serial bus** – all nodes see all messages, and message priority is determined by identifier.
*   **Application in Cars:** Connects subsystems like engine control, transmission, airbags, lights, windows, locks, etc., into a single collaborative network.
*   **Diagram Insight:** Shows a car's network segmented into **High-Speed CAN** (for critical, real-time functions like engine control) and **Low-Speed CAN** (for body electronics like windows and seats).
*   **Exam Relevance:** CAN Bus is a quintessential example of a **wired, real-time, networked embedded system**. It demonstrates the need for reliable, lightweight communication within a complex machine. You should know its primary application domain (automotive) and its purpose (interconnecting ECUs).

![[All_slides_nes.pdf#page=11]]
**Week 1 Slide 11 – From Wired to Wireless Embedded Systems**

*Notes:*
*   This slide explains the drivers behind the shift from wired to **wireless embedded systems**.
*   **Advantages of Wireless:**
    1.  **Flexibility & Easy Deployment:** No need to install physical cables, making retrofits and installations in existing structures much easier.
    2.  **Extended Coverage:** Enables **multi-hop networks**, where devices relay messages to cover large areas (e.g., a farm, forest, factory).
    3.  **Mobility:** Supports **wearable** and **portable** devices that move (e.g., fitness trackers, handheld scanners).
*   **Resulting Systems:**
    *   **Wireless Sensor Networks (WSNs):** Networks of sensing devices.
    *   **Wireless Sensor and Actuator Networks (WSANs):** Networks that include devices capable of affecting the environment (actuators).
*   **Exam Relevance:** Understand the **three key benefits of wireless** (flexibility, coverage, mobility) and the types of networks they enable (WSN, WSAN). This shift is what enables large-scale environmental monitoring, smart agriculture, and personal wearable tech.


![[All_slides_nes.pdf#page=12]]
**Week 1 Slide 12 – Wireless Embedded Systems in Agriculture**

*Notes:*
*   This slide provides a **concrete application example**: using a wireless sensor network for **precision agriculture**.
*   **System Architecture:**
    *   **Sensor Nodes:** Deployed in the field to measure soil moisture, temperature, etc.
    *   **Gateway Node:** Collects data from sensor nodes and acts as a bridge to the wider internet.
    *   **Server/Database:** Stores and processes data in the cloud.
    *   **End-User:** Accesses information (e.g., irrigation recommendations) via a cell phone or computer.
*   **This exemplifies the "Connectivity" trend:** Isolated sensors become a collaborative network, and data is made globally accessible.
*   **Exam Relevance:** This is a classic WSN/IoT case study. You should be able to describe the layered architecture (sensors → gateway → cloud → user) and its benefits (remote monitoring, data-driven decisions, resource efficiency like water savings). It shows wireless solving the "easy deployment" and "extended coverage" challenges in a large, open area.


![[All_slides_nes.pdf#page=13]]
**Week 1 Slide 13 – The Internet of Things**

*Notes:*
*   This slide defines the **Internet of Things (IoT)** as the next evolutionary step: connecting isolated networks of embedded systems into a **global, interconnected fabric**.
*   **Core Idea:** IoT integrates the **physical world** (via sensors/actuators) with the **digital world** (via internet connectivity) on a massive scale.
*   **Application Domains (Extremely Broad):**
    *   Smart Cities & Transportation
    *   Environmental & Disaster Monitoring
    *   Industrial Automation (Industry 4.0)
    *   Agriculture & Maritime
    *   Energy Management (Smart Grid)
    *   Healthcare & Fitness
    *   Consumer Electronics & Smart Homes
    *   Military
*   **Exam Relevance:** IoT is the ultimate expression of the **"Connectivity" trend**. You should recognize it as a **superset of networked embedded systems** with internet connectivity. Be prepared to give examples across different domains. The key is the **scale and internet integration**.


![[All_slides_nes.pdf#page=14]]
**Week 1 Slide 14 – The Connectivity Trend**

*Notes:*
*   This slide summarizes the **connectivity trend** as a progressive evolution, illustrating the expanding scope of networked embedded systems.
*   **The Evolution:**
    1.  **Isolated Embedded Systems** (single device, e.g., a thermostat).
    2.  **Networks within a Machine** (e.g., CAN Bus in a car).
    3.  **Wired Networked Embedded Systems** (e.g., industrial control systems).
    4.  **Wireless Embedded Systems** (e.g., sensor networks for agriculture).
    5.  **The Internet of Things** (global integration, potentially including satellites).
*   **Key Takeaway:** The trend is towards **increasingly pervasive, wide-area, and integrated connectivity**. This enables more complex, data-rich, and collaborative applications.
*   **Exam Relevance:** This is a good framework for understanding the historical and conceptual progression. You may be asked to place a given system on this spectrum or describe how connectivity expands system capabilities.

![[All_slides_nes.pdf#page=15]]
**Week 1 Slide 15 – Intelligent Embedded Systems**

*Notes:*
*   This slide explores the **"Intelligence" trend**, defining key related terms.
*   **Artificial Intelligence (AI):** The broad field of enabling machines to perform tasks that typically require human intelligence—**finding patterns, extracting knowledge from data, and using it for reasoning and decision-making**.
*   **Cognitive Systems:** A subset of AI that aims to **mimic human brain functions** like perception, attention, memory, and problem-solving.
*   **Autonomous Systems:** Systems capable of **operating independently with little or no human intervention**. Intelligence (often AI) is what enables autonomy.
*   **Relationship:** AI provides the tools (like machine learning). Cognitive systems are one approach. Autonomy is a desired capability enabled by intelligence.
*   **Exam Relevance:** Understand these definitions, especially **AI** as pattern-finding/knowledge extraction and **autonomy** as independent operation. For embedded systems, intelligence often means moving from simple **rule-based control** to **data-driven, adaptive, and potentially autonomous** operation.

![[All_slides_nes.pdf#page=16]]
**Week 1 Slide 16 – Control Systems**

*Notes:*
*   This slide revisits the **classic application** of embedded systems: **Control Systems**. This is the foundation upon which intelligence is added.
*   **What is a Control System?** A system that **regulates a physical variable** (Process Value - PV) to match a desired **Set Point (SP)**. It does this in a continuous **loop**:
    1.  **Sense** the current state (via a **sensor/transmitter**).
    2.  **Compare** it to the desired state (SP).
    3.  **Compute** a corrective action using a **control algorithm** (e.g., PID) in the **controller**.
    4.  **Actuate** to change the system (via an **actuator/final control element**, like a valve).
*   **Example:** A **flow controller** maintains a specific fluid flow rate by adjusting a valve.
*   **Exam Relevance:** This is **fundamental**. You must understand the **sense-compute-actuate loop** and the components involved (sensor, controller, actuator). This is the "classic" embedded system. Modern "intelligent" systems often replace the simple PID controller with a more complex, AI-based decision-making component.


![[All_slides_nes.pdf#page=17]]
**Week 1 Slide 17 – Rule-Based Machine Intelligence**

*Notes:*
*   This slide describes the simplest form of machine intelligence: **Rule-Based (Deductive) Systems**.
*   **Deductive Reasoning:** Starting from general **rules (axioms)** and applying them to specific situations to derive **conclusions**. (e.g., All humans are mortal. Alice is human. Therefore, Alice is mortal).
*   **Implementation:** Encoded as **"if-then" statements**.
*   **Application in Networked Embedded Systems:** A common form of automation in domains like **Building Automation Systems (BAS)**.
    *   **Example Rule
![[All_slides_nes.pdf#page=18]]
**Week 1 Slide 18 – Data-Driven Machine Intelligence**

*Notes:*
*   This slide introduces a more advanced paradigm: **Data-Driven (Inductive) Machine Intelligence**, which leads to **Machine Learning (ML)**.
*   **Inductive Reasoning:** Deriving **general models or rules** from **specific observations**. (e.g., Observing many white swans leads to the model "All swans are white").
*   **Spectrum of Problems:**
    *   **"Simple" & Well-Understood:** Models can be **hand-crafted** from physics (e.g., Newton's Laws for planetary motion).
    *   **"Complex":** The underlying model is unknown or too complicated. We use **machines to find the model** from data. This is **Machine Learning**.
*   **Machine Learning (ML):** A subset of AI where algorithms **learn patterns and models directly from data**, without being explicitly programmed for the specific task.
*   **Exam Relevance:** This is a key conceptual shift. Understand the difference between **deductive** (apply known rules) and **inductive** (learn rules from data). ML is inductive. This trend enables embedded systems to handle complex, non-linear, or poorly understood phenomena (e.g., image recognition, predictive maintenance).

![[All_slides_nes.pdf#page=19]]
**Week 1 Slide 19 – Deep (Artificial) Neural Networks**

*Notes:*
*   This slide focuses on **Deep Neural Networks (DNNs)**, a powerful class of **Machine Learning models** that have driven recent AI breakthroughs.
*   **What they are good at:** Learning **extremely complex, non-linear relationships** from vast amounts of data (e.g., image recognition, natural language processing).
*   **Requirements:** They are computationally **very heavy** and require **massive datasets** for training.
*   **Enabling Technologies:** The rise of DNNs was enabled by **Cloud Computing** (providing vast compute power) and **Big Data** (providing the massive datasets).
*   **Role of Networked Embedded Systems:** In this cloud-centric model, embedded systems often act as **data generators**, collecting and sending sensor data to the cloud for training and complex inference.
*   **Exam Relevance:** DNNs are the workhorse of modern AI. Understand that they are powerful but resource-hungry, which initially confined them to the cloud. This sets the stage for the next slide's discussion on the limitations of cloud-only AI and the move towards edge computing.

![[All_slides_nes.pdf#page=20]]
**Week 1 Slide 20 – Cloud-based IoT Systems**

*Notes:*
*   This slide evaluates the **cloud-centric model** for IoT/intelligent systems, listing its pros and cons.
*   **Advantages of Cloud-Centric AI:**
    *   **Vast Compute & Storage:** Can train and run massive DNN models.
    *   **Centralized Data:** Enables aggregation and learning from many devices.
*   **Disadvantages of Cloud-Centric AI:**
    *   **High Cost:** Bandwidth and cloud service fees for transmitting/storing all raw data.
    *   **High Latency:** Round-trip to the cloud is too slow for **real-time, delay-sensitive applications** (e.g., autonomous drone obstacle avoidance).
    *   **Dependency & Reliability:** Requires constant, high-quality internet connectivity.
    *   **Privacy & Security:** Sensitive raw data (e.g., from home cameras, health monitors) leaves the device and is stored by third parties.
*   **Exam Relevance:** You **must** know these trade-offs. They are the primary motivation for moving intelligence away from the cloud and towards the **edge device** itself—a core topic in later weeks (Embedded ML). The disadvantages directly map to the **BLERP** motivations from Week 10.


![[All_slides_nes.pdf#page=21]]
**Week 1 Slide 21 – Cloud-Fog-Edge Continuum**

*Notes:*
*   This slide presents the solution to cloud-centric limitations: distributing intelligence across the **Cloud-Fog-Edge continuum**.
*   **The Continuum:**
    *   **Cloud:** Massive data centers for the most demanding tasks (e.g., training large models).
    *   **Fog:** Intermediate computing nodes (gateways, local servers). Used for **data fusion, aggregation, and heavier processing** closer to the source. Can be private or a service.
    *   **Edge:** The **embedded devices themselves** (sensors, actuators). **Embedded AI** runs here, performing **local sensing, inference, and decision-making**.
*   **Embedded AI:** Bringing AI (both inference and potentially light training) to the device. This enables **autonomy, low latency, privacy, and reduced bandwidth**.
*   **Exam Relevance:** This is a **crucial architecture concept**. Understand the roles of each layer: **Edge for instant response and privacy, Fog for local aggregation, Cloud for heavy lifting**. The trend is to push intelligence as far towards the edge as the device's resources allow. This continuum is the architectural backbone of modern intelligent IoT.

![[All_slides_nes.pdf#page=22]]
**Week 1 Slide 22 – Two big trends in Embedded Systems (Recap)**

*Notes:*
*   This slide is a **summary**, reiterating the two mega-trends that frame the entire course.
*   **1. Connectivity:** Evolution from isolated systems → wired networks → wireless networks → the globally interconnected **Internet of Things (IoT)**.
*   **2. Intelligence:** Evolution from simple control loops → rule-based automation → data-driven **Machine Learning (ML)** → **Deep Neural Networks (DNNs)** → intelligence distributed across the **Cloud-Fog-Edge continuum** as **Embedded AI**.
*   **Synthesis:** The future of embedded systems lies at the **intersection of these trends**: **networks of intelligent, collaborative devices**.
*   **Exam Relevance:** This provides a cohesive narrative for the course. You should be able to articulate these two trends and give examples of how they manifest together (e.g., a swarm of autonomous drones using local AI for navigation while coordinating via a wireless network).


![[All_slides_nes.pdf#page=23]]
**Week 1 Slide 23 – What are the main components of an Embedded System?**

*Notes:*
*   This slide poses the core question that the following slides will answer: **What hardware makes up an embedded system?**
*   It hints at the **Microcontroller (MCU)** or **System-on-Chip (SoC)** as the central "brain."
*   **Exam Relevance:** This transitions from high-level concepts (connectivity, intelligence) to the **practical hardware foundations**. The next slides detail the anatomy you need to understand for designing or analyzing embedded systems.


![[All_slides_nes.pdf#page=24]]
**Week 1 Slide 24 – Anatomy of an Embedded System**

*Notes:*
*   This slide provides a **block diagram** of a typical embedded system's hardware components.
*   **Core (System-on-Chip - SoC):**
    *   **CPU:** The processor that executes software.
    *   **RAM:** Volatile memory for running programs and data.
    *   **Flash:** Non-volatile memory for storing the program code and permanent data.
    *   **I/O Interfaces:** Circuits to communicate with the outside world (GPIO, ADC, UART, SPI, I2C).
    *   **Radio:** For wireless connectivity (integrated in many SoCs).
*   **Peripherals & External Components:**
    *   **Sensors:** Input from the physical world (connected via I/O).
    *   **Actuators & User Interface:** Output to the physical world/user (motors, LEDs, screens, buttons).
    *   **Power Source:** Battery or energy harvester, managed by power regulation circuits.
*   **Key Concept:** The SoC integrates the core digital functions. Everything else connects to it via its I/O interfaces.
*   **Exam Relevance:** You should be able to draw or label a similar high-level block diagram. Know the function of each major block and how they connect (peripherals ↔ I/O ↔ SoC). This is the fundamental hardware architecture.


![[All_slides_nes.pdf#page=25]]
**Week 1 Slide 25 – Microcontrollers (MCU) and Systems-on-Chip (SoC)**

*Notes:*
*   This slide defines and compares the two most common integrated chips at the heart of embedded systems.
*   **Microcontroller (MCU):** A "small computer on a chip." It integrates:
    *   A **Processor (CPU)**
    *   **Memory (RAM)**
    *   **Programmable I/O Peripherals** (e.g., GPIO, timers, ADCs, communication interfaces).
*   **System-on-Chip (SoC):** A more complex integration. It typically includes:
    *   An **MCU** (CPU, RAM, I/O) as a subsystem.
    *   **Non-volatile storage** (Flash memory).
    *   **Dedicated processing units** (GPU, DSP, AI accelerators).
    *   **Network interfaces** (Wi-Fi, Bluetooth radio cores).
    *   Sometimes even **integrated sensors**.
*   **Relationship:** An SoC is often an **MCU plus additional specialized components**. The term "SoC" emphasizes the integration of *all* major system components onto one chip.
*   **Exam Relevance:** Understand the definitions. An **MCU** is the classic core for simple control. An **SoC** is what enables complex, connected, intelligent devices (like smartphones or advanced sensor nodes) by integrating more functions. The CC2650 (next slide) is an example of an SoC for wireless embedded systems.


![[All_slides_nes.pdf#page=26]]
**Week 1 Slide 26 – Example SoC**

*Notes:*
*   This slide analyzes the **Texas Instruments CC2650**, a real-world **SoC** designed for wireless embedded systems (e.g., IoT sensor nodes).
*   **Key Integrated Components:**
    *   **Main CPU:** ARM Cortex-M3 for application code.
    *   **Memory:** 128KB Flash, various SRAM/ROM.
    *   **Radio Core:** A *dedicated* ARM Cortex-M0 processor + hardware modules (ADC, PLL, modem) to handle all wireless protocol tasks. This offloads the main CPU.
    *   **Sensor Controller:** A low-power co-processor for autonomously reading analog sensors (ADC, comparator) while the main system sleeps.
    *   **Rich Peripherals:** Timers, crypto (AES), DMA (Direct Memory Access for efficient data movement), UART, I2C, SPI, many GPIOs.
    *   **Power Management:** DC-DC converter, RTC.
*   **Why it's an SoC:** It integrates the **application processor, radio subsystem, sensor interface, power management, and security** all on one chip.
*   **Exam Relevance:** The CC2650 is a canonical example. You don't need to memorize specs, but you should understand the **types of specialized cores it includes** (main CPU, radio CPU, sensor controller) and why this integration is beneficial for building efficient, capable wireless sensor nodes.


![[All_slides_nes.pdf#page=27]]
**Week 1 Slide 27 – Processors**

*Notes:*
*   This slide categorizes the **processors (CPUs)** found in embedded systems.
*   **Architecture Bit-width:** 8-bit, 16-bit, 32-bit, 64-bit. Refers to the size of data the processor handles natively. Wider = generally more powerful and capable of handling more memory. **32-bit (like ARM Cortex-M) is dominant in modern embedded systems**.
*   **Popular Architectures/Vendors:**
    *   **Proprietary Architectures:** AVR (Atmel), PIC (Microchip), MSP (TI) – common in simpler, cost-sensitive devices.
    *   **ARM Architecture:** A company that designs CPU cores and licenses them to chip manufacturers (like TI, ST). It's the **industry standard** for a wide range of devices.
*   **ARM Cortex Series (Key for the course):**
    *   **Cortex-A:** "Application" processors. High performance, runs complex OS (Linux, Android). Used in smartphones, Raspberry Pi.
    *   **Cortex-R:** "Real-time" processors. For extremely fast, deterministic response. Used in automotive brake systems, hard disk controllers.
    *   **Cortex-M:** "Microcontroller" processors. **Low-power, low-cost, designed for embedded control**. The **core of most IoT and networked embedded systems** we study (e.g., CC2650 uses Cortex-M3/M0).
*   **Exam Relevance:** Know the **ARM Cortex series distinctions**, especially that **Cortex-M** is the go-to for the low-power embedded domain of this course. Understand that bit-width affects capability. You may encounter names like AVR or PIC for simpler devices.

![[All_slides_nes.pdf#page=28]]
**Week 1 Slide 28 – Transducers: Sensors and Actuators**

*Notes:*
*   This slide formally defines **transducers** and introduces their categories based on the **energy conversion** they perform.
*   **Transducer:** Any device that **converts one form of energy into another**.
    *   **Sensor (Input Transducer):** Converts a **physical quantity** (e.g., heat, light, force) into an **electrical signal**.
    *   **Actuator/Output Device (Output Transducer):** Converts an **electrical signal** into a **physical action or quantity** (e.g., motion, heat, light).
*   **Categories (by Energy Domain):**
    *   **Electromechanical** (e.g., accelerometer, motor)
    *   **Electromagnetic** (e.g., magnetometer)
    *   **Electrochemical** (e.g., gas sensor)
    *   **Electroacoustic** (e.g., microphone, speaker)
    *   **Electro-optical** (e.g., camera, LED)
    *   **Thermoelectric** (e.g., temperature sensor, heater)
*   **Exam Relevance:** This is foundational vocabulary. You should know that sensors and actuators are both **transducers** performing inverse functions. The categories help understand *how* a device works (e.g., a temperature sensor is *thermoelectric*). This is more about classification than deep physics.


![[All_slides_nes.pdf#page=29]]
**Week 1 Slide 29 – Sensors**

*Notes:*
*   This slide differentiates between **analogue** and **digital** sensors, a critical practical distinction.
*   **Analogue Sensor:** Produces a **continuous electrical signal** (voltage, current) that is proportional to the measured physical quantity.
    *   **Challenge:** A digital MCU cannot understand analogue signals directly.
    *   **Solution:** Requires an **Analogue-to-Digital Converter (ADC)** to sample the signal and convert it to a digital number.
*   **Digital Sensor:** An **analogue sensor packaged with an ADC and a simple controller** in one chip. It provides a **digital interface** (e.g., I2C, SPI) to the MCU.
    *   **Benefit:** Simplifies design, often includes calibration and processing (e.g., the ADXL362 accelerometer in the diagram).
*   **Modern Trend:** Most sensors used in embedded systems are **digital sensors** because they are easier to interface with and provide more stable, processed data.
*   **Exam Relevance:** Understand the **key difference** and the role of the **ADC**. Know that a digital sensor is essentially an analogue sensor with a built-in ADC and digital interface. This affects how you connect a sensor to your MCU.

![[All_slides_nes.pdf#page=30]]
**Week 1 Slide 30 – Types of Sensors**

*Notes:*
*   This slide provides concrete **examples of sensors** categorized by their energy conversion type (from Slide 28).
*   **Electromechanical:** Measures mechanical forces/motion (accelerometer, gyroscope, pressure, flow).
*   **Electromagnetic:** Measures magnetic fields or uses electromagnetic principles (magnetometer, RADAR, simple contact switch).
*   **Electrochemical:** Detects chemical composition (pH, gas sensors).
*   **Electroacoustic:** Converts sound/pressure waves to/from electrical signals (microphone, ultrasound sensor, piezoelectric sensor).
*   **Electro-optical:** Involves light (camera, IR sensor, light sensor, PIR motion detector, LIDAR, heart rate monitor using PPG).
*   **Thermoelectric:** Converts temperature differences to/from electrical signals (thermometer, body temperature sensor).
*   **Exam Relevance:** You should be able to **categorize common sensors**. This is useful for understanding what a sensor measures and how it might work at a high level. For example, know that a camera is *electro-optical*, a microphone is *electroacoustic*, and an accelerometer is *electromechanical*.

![[All_slides_nes.pdf#page=31]]
**Week 1 Slide 31 – Actuators/Output Devices**

*Notes:*
*   This slide explains how **actuators and output devices** are controlled by a digital system.
*   **Core Function:** They **convert an electrical control signal into a physical action or output**.
*   **The Interface Challenge (Inverse of Sensors):** A digital MCU outputs digital signals. To control an analogue actuator (like a motor speed or heater power), you need:
    *   A **Switch** (for on/off control).
    *   A **Digital-to-Analogue Converter (DAC)** (to produce an analogue voltage/current level).
    *   A **Signal Generator/Modulator** (for complex outputs like sound or radio waves).
*   **Controller Chips:** Many complex output devices (like displays, motor drivers) have their own **dedicated controller chip**. The MCU sends high-level **commands** over a digital bus (I2C, SPI), and the controller chip handles the low-level details of driving the hardware (e.g., the SSD1306 drives an OLED pixel matrix).
*   **Exam Relevance:** Understand that driving actuators often requires additional hardware (DAC, driver circuit, controller chip). The concept of a **controller chip** (like a display driver) is very common and simplifies the MCU's job. It's the output equivalent of a digital sensor.

![[All_slides_nes.pdf#page=32]]
**Week 1 Slide 32 – Types of Actuators/Output Devices**

*Notes:*
*   This slide provides concrete **examples of actuators and output devices**, categorized by their energy conversion type.
*   **Electromechanical:** Converts electrical energy to **mechanical motion** (motor, valve, vibration motor).
*   **Electroacoustic:** Converts electrical signals to **sound** (loudspeaker).
*   **Electro-optical:** Converts electrical signals to **light** (screen/LED display, status LED).
*   **Thermoelectric:** Converts electrical energy to **heat** (heater).
*   **Exam Relevance:** Similar to sensors, you should be able to **categorize common actuators**. This is a shorter list than sensors because actuators are generally about causing motion, light, sound, or heat. Know that a motor is *electromechanical* and a screen is *electro-optical*.

![[All_slides_nes.pdf#page=33]]
**Week 1 Slide 33 – Other Input/Output Components**

*Notes:*
*   This slide lists miscellaneous but important **supporting hardware components** in an embedded system.
*   **External Storage:** Used when the integrated Flash on the SoC is insufficient.
    *   **Flash Memory Chips:** Connected via SPI for additional data logging space.
    *   **SD Cards:** Removable storage, often with a file system.
*   **Connectors & Interfaces:**
    *   **Jacks, Headers, Sockets:** For plugging in peripherals, programming, or power (e.g., USB, JTAG).
    *   **Antenna Connectors:** For attaching external antennas to the radio (e.g., U.FL, printed antenna on PCB).
    *   **Jumpers/Solder Bridges:** For hardware configuration (e.g., setting a device address, enabling a feature).
*   **Exam Relevance:** These are the "glue" components. You should be aware that external storage exists and why it's used (more data). Connectors are how the embedded system interacts with the outside world (user, programmer, network). They are part of a complete system design.


![[All_slides_nes.pdf#page=34]]
**Week 1 Slide 34 – Power Management**

*Notes:*
*   This slide covers the critical subsystem responsible for providing clean, stable, and appropriate power to all components: **Power Management**.
*   **Power Source:** Typically **DC** (Direct Current) from a battery or a rectified AC mains supply. These sources are often "noisy" (voltage fluctuates).
*   **Voltage Regulator:** Maintains a **constant output voltage** despite changes in input voltage or load. Two main types:
    *   **Linear Regulator:** Simple, cheap, but **inefficient** (dissipates excess power as heat).
    *   **Switching Regulator:** More complex, but **highly efficient** (uses rapid switching).
*   **DC-DC Converter:** A type of switching regulator that can also **change the voltage level**.
    *   **Buck Converter (Step-down):** Output voltage is **lower** than input (e.g., convert 5V battery to 3.3V for the MCU).
    *   **Boost Converter (Step-up):** Output voltage is **higher** than input (e.g., power an LED from a single 1.5V battery).
*   **Exam Relevance:** Power is a first-class concern in embedded design, especially for battery-operated devices. Understand the roles of **regulators** (stable voltage) and **converters** (change voltage level). Know that **switching converters are preferred for efficiency** in low-power devices. The CC2650 SoC includes a DC-DC converter for this reason.


![[All_slides_nes.pdf#page=35]]
**Week 1 Slide 35 – Power Management (Continued)**

*Notes:*
*   This slide continues power management topics, focusing on **energy sources and harvesting**.
*   **Battery Charging:** Many embedded devices include circuits to recharge their batteries.
    *   **Battery Charger IC:** Manages charging safely from a source like USB.
    *   **Inductive Wireless Charging Receiver:** (e.g., Qi standard) allows charging without physical connectors.
*   **Energy Harvesting:** The process of capturing ambient energy (light, heat, vibration, RF) to power the device, potentially making it battery-less or extending battery life.
    *   Requires a **Power Manager IC** specific to the energy source (e.g., Solar Power Manager, RF Power Manager) to condition the harvested energy and charge a battery or supercapacitor.
*   **Exam Relevance:** For **truly autonomous and maintenance-free** embedded systems (a key IoT goal), energy harvesting is a crucial technology. Understand its purpose and that it requires specialized power management circuits. Battery charging is standard for rechargeable devices. These topics highlight the focus on long-term, sustainable operation.


![[All_slides_nes.pdf#page=36]]
**Week 1 Slide 36 – The main components of an Embedded System**

*Notes:*
*   This final slide is a **pictorial summary** showing a **realistic PCB (Printed Circuit Board)** integrating many of the components discussed.
*   **Components Labeled in the Image:**
    *   **SoC:** The central integrated chip (e.g., something like a CC2650).
    *   **Sensors:** Accelerometer, Gyroscope.
    *   **Actuators/Output:** LED.
    *   **Power Management:** Voltage Regulator, Wireless Charger coil and IC.
    *   **Connectivity:** Printed Antenna (for radio), Serial Interface (e.g., for programming/debugging).
    *   **Storage:** Flash Memory chip.
    *   **Supporting:** Passives (resistors, capacitors), connectors.
*   **Key Takeaway:** An embedded system is a **tightly integrated collection of specialized components** soldered onto a PCB, with the **SoC at its heart coordinating everything**.
*   **Exam Relevance:** This visual ties the entire lecture together. You should be able to look at such an image and identify the major functional blocks: **processing, sensing, actuation, power, connectivity, and storage**. It represents the physical manifestation of the "Anatomy" block diagram from Slide 24.


WEEK 2 NOTES

![[All_slides_nes.pdf#page=39]]  
**Week 2 Slide 3 – A Wearable Embedded System**  

---

### **Notes**

**Purpose of the slide:**  
This slide shows a **real wearable embedded system** and its **full electronic schematic**, introducing how complex embedded hardware looks in practice.

---

### **Key Points**

#### **1. What a Wearable Embedded System Contains**

- A wearable device is a **self-contained electronic system** designed to be worn on the body.
    
- It typically includes:
    
    - **Sensors** (e.g., accelerometers — visible here as ADXL362 chips)
        
    - **Microcontroller (MCU)** (main brain — CC2650 in this schematic)
        
    - **Power management** (LDOs, DC/DC converters)
        
    - **Wireless communication** (RF antenna + matching network)
        
    - **Memory storage** (flash)
        
    - **User interface parts** (LED, button)
        
    - **Battery and charging circuit** (Qi wireless charging chip shown)
        

This slide provides the **complete schematic** of such a system.

---

### **3. Why This Matters for Exam**

You should understand:

- Embedded systems combine **many different circuit blocks**.
    
- Each block plays a specific role (sensing, computing, power, RF).
    
- Real schematics look complicated, but they follow modular principles.
    

---

### **4. Main Components Identified in the Schematic**

(You do not need to memorize the specific part numbers, but know the categories.)

|Component Type|Example on Schematic|Function|
|---|---|---|
|**MCU**|CC2650|Runs firmware, processes data, handles wireless (BLE)|
|**Sensors**|ADXL362|Measure motion/acceleration|
|**Power Management**|TPS62746, TPS78318|Create stable voltages for components|
|**Charging Circuit**|bq51050b|Wireless charging receiver|
|**Memory**|GD5F1GQ4UAY|Stores firmware/data|
|**RF Section**|Antenna + inductors/capacitors|Enables wireless communication|
|**Passive components**|Capacitors, resistors|Filtering, decoupling, biasing|
|**LED + Button**|D1, S1|User interface|

---

### **5. Important Concept Introduced**

RF = **Radio Frequency**

- These parts handle wireless communication at high frequencies.
    
- They require **special components** (inductors/capacitors) for tuning.
    


![[All_slides_nes.pdf#page=40]]  
**Week 2 Slide 4 – Schematic (or Circuit Diagram)**  

---

### **Notes**

### **1. What a Schematic Is**

- A **schematic** is a _model_ of an electronic circuit.
    
- It uses symbols to represent components and lines to represent electrical connections.
    
- It is **not** a physical layout — it is a **logical diagram**.
    

---

### **2. What an Electronic Circuit Is**

- A circuit is made of **electronic components interconnected in a closed loop**.
    
- A closed loop means current has a complete path to flow.
    

---

### **3. Why Schematics Make Life Easier**

Schematics **abstract** away messy physical details.

They:

- Show each component as a **simple symbol**, reducing visual clutter.
    
- Make the system **easier to read** than a real circuit on a PCB.
    
- Help engineers understand and debug electronic designs.
    
- Provide a clean reference that can be directly translated into PCB layout later.
    

---

### **4. Visual Reference (Image on the Slide)**

The slide includes:

- A physical LED glove circuit.
    
- Its corresponding schematic diagram.
    

This demonstrates how a **complex-looking real circuit** becomes much easier to understand once abstracted into a schematic.

---

### **5. Exam-Relevant Understanding**

You should recognize that:

- Schematic diagrams are fundamental design tools.
    
- They tell you _what connects to what_, not _where it physically is_.
    
- They use **standardized symbols** that all engineers understand.
    

This forms the basis for all circuit analysis and PCB design later in the lecture.

![[All_slides_nes.pdf#page=41]]  
**Week 2 Slide 5 – Basic Concepts**  

---

### **Notes**

### **1. Core Electrical Quantities**

|Quantity|Symbol|Unit|Meaning|
|---|---|---|---|
|**Voltage**|V|Volts (V)|Electric potential difference between two points|
|**Current**|I|Amperes (A)|Flow of electric charge (electrons) through a conductor|
|**Resistance**|R|Ohms (Ω)|How much a component resists the flow of current|

---

### **2. Ohm’s Law**

- **Formula:**                      **I = V / R**
    
- Describes the relationship between:
    
    - **I**: Current
        
    - **V**: Voltage
        
    - **R**: Resistance
        

This law is foundational for all circuit calculations:

- Increase voltage → current increases
    
- Increase resistance → current decreases
    

---

### **3. How This Applies to Circuits**

- Every resistor, wire, or component affects current flow based on its resistance.
    
- Designers use Ohm’s Law to:
    
    - Size resistors properly
        
    - Ensure components receive the correct amount of current
        
    - Diagnose issues like short circuits or power drops
        

---

### **4. Key Insight for Exam**

Expect questions that require:

- Using Ohm’s Law to solve for unknown values.
    
- Understanding how changing V or R affects current.
    
- Interpreting units and relationships between these quantities.

![[All_slides_nes.pdf#page=42]]  
**Week 2 Slide 6 – Electric Power Source**  

---

### **Notes**

### **1. Two Types of Electric Power Sources**

#### **Direct Current (DC)**

- Current flows in **one direction only**.
    
- Example: **Battery**.
    
- Most **embedded systems** require DC because digital electronics need a stable, one-way voltage.
    

#### **Alternating Current (AC)**

- Current **reverses direction periodically**.
    
- Example: **mains electricity** (wall outlet).
    
- AC is good for long-distance distribution but **must be converted** before electronics can use it.
    

---

### **2. Rectifier**

- A rectifier converts **AC → DC**.
    
- Needed when an embedded system is powered from AC mains.
    
- Often found in power adapters and chargers.
    

---

### **3. Key Concept for Embedded Systems**

Embedded devices (microcontrollers, sensors, wireless chips, etc.) cannot run on AC.  
They always need a **DC supply**, typically in the range of:

- 1.8V
    
- 3.3V
    
- 5V
    

So AC from the wall must go through:

1. Transformer + rectifier → produces DC
    
2. Regulators → stabilize the voltage
    

---

### **4. Exam-Relevant Points**

You should know:

- Recognize the difference between **AC** and **DC**.
    
- Understand why embedded systems **cannot** use AC directly.
    
- Understand **rectification** as the process that enables AC-powered devices to run digital circuits

![[All_slides_nes.pdf#page=43]]  
**Week 2 Slide 7 – Voltage Sources**  

---

### **Notes**

### **1. DC Voltage Sources**

- Can come from **batteries** directly.
    
- Or from **AC mains** after rectification (AC → DC).
    

---

### **2. Voltage as a Potential Difference**

- Voltage is always measured **between two points**.
    
- But in practice, we almost always measure it relative to a **common reference** called **ground (GND)**.
    

---

### **3. Ground (GND)**

- A shared reference point for _all_ voltage measurements in the circuit.
    
- Sometimes physically connected to Earth, sometimes not (in battery devices, it usually isn’t).
    
- Allows designers to say “this node is at 3.3V” meaning “3.3V above ground”.
    

---

### **4. Using Labels in Schematics**

As circuits grow more complex:

- Instead of drawing wires everywhere, designers use **labels** such as:
    
    - **Vsource**, **VDD**, **3V3**, **GND**, etc.
        
- Any points with the **same label** are assumed to be **electrically connected**, even if no physical wire is shown on that page.
    

This keeps schematics readable.

---

### **5. Visuals on the Slide**

- Examples of circuits showing voltage sources, resistors, and LEDs.
    
- The diagrams illustrate:
    
    - Voltage measured with respect to ground.
        
    - The convenience of using labels rather than long wires.
        

---

### **6. Exam-Relevant Concepts**

You should be comfortable with:

- What “ground” actually means.
    
- Interpreting voltage labels on schematics.
    
- Understanding that voltage is always relative to something — usually GND.

![[All_slides_nes.pdf#page=44]]  
**Week 2 Slide 8 – Electric Load (Power Consumers)**  

---

### **Notes**

### **1. What Is an Electric Load?**

An **electric load** is _anything in a circuit that consumes electrical energy_.

Examples:

- LEDs (convert electricity → light)
    
- Motors (convert electricity → motion)
    
- Heaters (convert electricity → heat)
    
- Microcontrollers and sensors (convert → internal processing work)
    

---

### **2. Electric Power (P)**

- Defines **how fast** electrical energy is being consumed.
    
- Formula:  
    **P = V × I**
    
    - V = voltage across load
        
    - I = current through load
        
- Units: **Watt (W)**
    

Higher power means:

- More energy used per second.
    
- More heat generated.
    

---

### **3. Electric Energy (E)**

- Total consumed energy over time.
    
- Formula:  
    **E = P × t = V × I × t**
    
- Units: **Joules (J)**  
    (or Watt-hours, Wh, in battery contexts)
    

---

### **4. Why This Matters for Embedded Systems**

- Power consumption determines **battery life**.
    
- Designers must calculate:
    
    - How much current each component draws.
        
    - How long the system can run before the battery drains.
        
    - Whether components need heat dissipation (usually minimal in low-power systems).
        

---

### **5. Exam-Relevant Concepts**

You should be able to:

- Calculate power using P = VI.
    
- Use E = VIt to estimate energy usage.
    
- Recognize examples of electric loads in a circuit.

![[All_slides_nes.pdf#page=45]]  
**Week 2 Slide 9 – Everything Has Resistance**  

---

### **Notes**

### **1. Resistance Exists Everywhere**

Even though schematics simplify things, **all real materials have resistance**.

#### **Fixed Resistors**

- Have a set value (e.g., 1 kΩ, 10 Ω, 1 MΩ).
    
- Available from **0 Ω** (practically a wire) to **hundreds of GΩ** (huge resistance).
    

---

### **2. Insulators**

- Ideal insulators are assumed to have **infinite resistance**.
    
- Reality: insulators like **air** have _very high_ resistance, not infinite.
    
- Extremely tiny currents can still leak through high resistance paths.
    

---

### **3. Conductors**

- Ideal wires are assumed to have **zero resistance**.
    
- Reality: metals like copper still have a **very small resistance**.
    
    - Small enough to ignore in many circuits.
        
    - But not zero → becomes important in high-current or precision designs.
        

---

### **4. Why This Matters**

Understanding real vs. ideal resistance helps you reason about:

- **Voltage drops** on wires.
    
- **Power losses** due to resistance.
    
- Why short circuits produce large currents (wires still have small resistance).
    
- Why insulators can sometimes break down at high voltages.
    

---

### **5. Exam-Relevant Understanding**

Expect to reason about:

- Differences between **ideal** and **real** components.
    
- Why wires are treated as 0 Ω in diagrams.
    
- Why insulators are treated as infinite Ω in diagrams.
    
- But also why, physically, neither is perfectly true.

![[All_slides_nes.pdf#page=46]]  
**Week 2 Slide 10 – Quiz (Current Through Different Resistors)**  

---

### **Notes**

### **1. Purpose of the Slide**

This is a conceptual quiz to test your understanding of **Ohm’s Law** and how **slight resistance differences** affect current.

---

### **2. The Setup**

Two resistor paths:

- **Left:** 1 kΩ
    
- **Right:** 1 kΩ + 0.1% or 1% or 10% more (depending on the example)
    

You apply the **same voltage** across both.

---

### **3. The Key Question**

**Which path draws more current? And how much more?**

Using Ohm’s Law:

- **I = V / R**
    

Smaller resistance → larger current.

So the path with the **lower resistance** always has slightly **higher current**.

---

### **5. Practical Meaning**

In many circuits:

- Small differences in resistance (like from manufacturing tolerance) cause **tiny, often irrelevant** changes in current.
    
- This is why the concept of “**path of least resistance**” doesn’t mean current dramatically prefers one branch—it just shifts slightly.
    

This prepares you for the next slide, which goes deeper into this example.

![[All_slides_nes.pdf#page=47]]  
**Week 2 Slide 11 – “Path of Least Resistance”**  

---
### **1. Purpose of the Slide**

Clarifies a common misconception:  
Current does **not** exclusively choose the lowest-resistance path — it divides **proportionally** based on resistance.

---

### **2. The Setup**

We apply:

- Supply voltage: **1 V**
    
- **Left branch:**  
    $$R_L = 1000\ \Omega$$
    
- **Right branch:** two resistors in parallel:  
    $$R_1 = 1000\ \Omega,\qquad R_2 = 1,000,000\ \Omega$$
    

---

### **3. Equivalent Resistance of the Right Branch**

Parallel resistance formula:

$$  
R_{\text{eq}}=\frac{R_1 R_2}{R_1 + R_2}  
$$

Plugging in:

$$  
R_{\text{eq}}=\frac{1000 \times 1,000,000}{1000 + 1,000,000}  
\approx 999\ \Omega  
$$

---

### **4. Currents Through Each Branch**

Using Ohm’s Law:

Left branch:

$$  
I_L = \frac{V}{R_L} = \frac{1}{1000} = 1.000\ \text{mA}  
$$

Right branch:

$$  
I_R = \frac{V}{R_{\text{eq}}} = \frac{1}{999} \approx 1.001\ \text{mA}  
$$

---

### **5. Interpretation**

- Resistance difference:  
    $$1000\ \Omega \quad \text{vs.} \quad 999\ \Omega$$
    
- Current difference:  
    About **0.1%**
    

So:

- Both branches carry _almost exactly_ the same current.
    
- Current does **not** strongly favor one branch unless resistance differences are large.
    

---

### **6. Exam-Relevant Points**

You should understand:

- How to compute **parallel resistances** using  
    $$R_{\text{eq}}=\frac{R_1 R_2}{R_1+R_2}$$
    
- How current splits based on resistance.
    
- Why “path of least resistance” is an **oversimplification** — the correct concept is **current division**.

![[All_slides_nes.pdf#page=48]]  
**Week 2 Slide 12 – Short Circuit (or short)**  

---
### **1. What Is a Short Circuit?**

A **short circuit** is an (often accidental) connection of **very low or nearly zero resistance** between:

- A **high-voltage node**, and
    
- **Ground** (or a lower-voltage node)
    

This creates an unintended path where current can rush through almost freely.

---

### **2. Theoretical Model**

A perfect short means:

$$  
R_{\text{short}} = 0\ \Omega  
$$

Using Ohm’s Law:

$$  
I = \frac{V}{R}  
$$

Substituting:

$$  
I = \frac{V}{0} \rightarrow \infty  
$$

So mathematically, the current would be **infinite**.

---

### **3. Real-World Reality**

In practice, nothing has truly zero resistance:

- Wires have very small resistance (milliohms).
    
- Batteries have **internal resistance**:
    
    $$R_I > 0$$
    

Therefore:

$$  
I = \frac{V}{R_{\text{short}} + R_I}  
$$

The current is **very large**, but not infinite.  
The limiting factor is usually the **battery or power supply**.

---

### **4. Why Shorts Are Dangerous**

A large current can:

- Burn or damage components
    
- Overheat wires
    
- Destroy ICs (chips)
    
- In high-power systems: start fires or be lethal
    
- In low-power systems: still enough to ruin delicate electronics
    

Even tiny wearable devices can be damaged by a small short.

---

### **5. Key Concept for Embedded Systems**

Short circuits usually occur because of:

- Solder bridges
    
- Miswiring
    
- Damaged insulation
    
- Conductive debris (e.g., metal shavings)
    

Detecting and preventing shorts is a **critical skill** when building prototypes.

---

### **6. Exam-Relevant Understanding**

You must understand:

- Why shorts cause huge currents.
    
- Mathematical ideal vs. real-world behavior.
    
- Role of **internal resistance** of the power source.
    
- Practical consequences of a short in low-power electronics.

![[All_slides_nes.pdf#page=49]]  
**Week 2 Slide 13 – Resistance Can Be Variable**  

---

### **1. Not All Resistance Is Fixed**

Many components have **resistance that changes** depending on:

- Mechanical movement
    
- Temperature
    
- Light level
    
- Frequency
    
- Electrical control signals
    

This makes them extremely useful for sensing and control.

---

### **2. Types of Variable Resistors Introduced**

#### **Potentiometer (mechanically controlled)**

- A knob or slider that changes resistance by moving a **wiper**.
    
- Used for:
    
    - Volume control
        
    - User input
        
    - Adjustable tuning
        

#### **Thermistor (temperature-dependent)**

- Resistance changes with temperature.
    
- Two types:
    
    - **NTC:** resistance ↓ when temperature ↑
        
    - **PTC:** resistance ↑ when temperature ↑
        
- Used in temperature sensing, protection circuits.
    

#### **Photoresistor (light-dependent)**

- Resistance decreases when exposed to more light.
    
- Used to detect ambient light levels.
    

---

### **3. Frequency-Dependent Resistors**

Capacitors and inductors **act like resistors only for AC signals**, where their resistance depends on **frequency**.

This is called **reactance**:

- Capacitive reactance:  
    $$X_C = \frac{1}{2\pi f C}$$  
    (↓ with increasing frequency)
    
- Inductive reactance:  
    $$X_L = 2\pi f L$$  
    (↑ with increasing frequency)
    

These formulas help determine how AC signals behave through these components.

---

### **4. Transistor (electrically controlled resistor)**

A MOSFET’s resistance between its **drain** and **source** terminals:

- Becomes **very small** when gate voltage is high → behaves like a closed switch
    
- Becomes **very large** when gate voltage is low → behaves like an open switch
    

So in many circuits a transistor is essentially a **resistance you can turn on/off with voltage**.

---

### **5. Why This Matters for Embedded Systems**

Variable resistors allow embedded systems to measure or control physical quantities:

- Temperature
    
- Light
    
- Position
    
- User inputs
    
- Signal levels
    

They are the foundation of analog sensing.

---

### **6. Exam-Relevant Points**

You should know:

- Examples of variable resistors.
    
- Their behaviors (mechanical, thermal, optical, AC, electrical control).
    
- Basic formulas for **reactance** (as above).
    
- That these components convert physical changes → electrical resistance changes.

![[All_slides_nes.pdf#page=50]]  
**Week 2 Slide 14 – Voltage Divider**  

---

### **1. What a Voltage Divider Does**

A **voltage divider** takes an input voltage and outputs a **fraction** of it.

It is built using **two resistors in series**.

---

### **2. Voltage Divider Formula**

Given two resistors:

- Top resistor:  
    $$R_1$$
    
- Bottom resistor:  
    $$R_2$$
    

Input voltage at the top:  
$$V_{\text{in}}$$

Output voltage between the two resistors:  
$$V_{\text{out}}$$

The formula is:

$$  
V_{\text{out}}  
= V_{\text{in}} \cdot \frac{R_2}{R_1 + R_2}  
$$

---

### **3. Understanding Attenuation** (dæmpning)

#### **If (R_1 \ll R_2):** R1 << R2

- Very small attenuation
    
- Most of the input voltage “gets through”
    
- Output is close to **Vin**
    

#### **If (R_1 \gg R_2):** R1 >> R2

- Large attenuation
    
- Only a small portion of Vin becomes Vout
    
- Output is much **smaller**
    

---

### **4. Where Voltage Dividers Are Used**

- Adjust a signal to a lower voltage that another device can safely read
    
- Convert larger voltage ranges to smaller ranges for ADCs
    
- Create reference voltages
    
- Light sensing (photoresistor circuits)
    
- Temperature sensing (thermistor circuits)
    

---

### **5. Important Limitations**

Voltage dividers **do not work well** when the output is loaded heavily.  
If a device connected to Vout draws current, the formula changes.

This is why voltage dividers are good for **signals**, but not for powering loads.

---

### **6. Exam-Relevant Concepts**

Understand:

- The formula
    
- When a divider attenuates a lot vs. a little
    
- Typical use cases
    
- Why loading affects accuracy

![[All_slides_nes.pdf#page=51]]  
**Week 2 Slide 15 – Level Shifter**  

---

### **1. Purpose of a Level Shifter**

A **level shifter** safely connects two digital devices that use **different logic voltage levels**.

Example scenario:

- Device A outputs logic “1” as **5 V**
    
- Device B expects a maximum of **3.3 V** on its inputs
    

Direct connection would **damage** the 3.3 V device.

A level shifter solves this by **reducing the voltage** of the signal before it reaches the lower-voltage device.

---

### **2. Why This Is Necessary in Embedded Systems**

Different components operate at different supply voltages:

- Microcontroller at 3.3 V
    
- Sensor module at 1.8 V
    
- Legacy device at 5 V
    

Without voltage shifting:

- Inputs can be destroyed
    
- Chips can latch up or behave unpredictably
    
- Communication becomes unreliable
    

---

### **3. How a Level Shifter Typically Works**

Common approaches:

- **Resistive voltage divider** (simple but only works in one direction and slows signals)
    
- **MOSFET-based bidirectional level shifter** (common for I²C, UART)
    
- **Dedicated IC level shifters** (fast, reliable, multi-channel)
    

The slide shows a resistive divider example:  
**Two resistors reduce a 5 V high level to a safe 3.3 V.**

---

### **4. Key Requirement**

The receiving device must **never** see a voltage higher than its supply voltage.  
Exceeding this often destroys input protection diodes or internal transistors.

---

### **5. Exam-Relevant Understanding**

You should know:

- What problem a level shifter solves
    
- What happens if you don’t use one
    
- Common ways to implement it (resistors, MOSFETs, ICs)
    
- That logic “1” has different meanings depending on the voltage domain

![[All_slides_nes.pdf#page=52]]  
**Week 2 Slide 16 – Volume Control (Potentiometer as Variable Attenuator)**  

---

### **1. How a Potentiometer Works**

A **potentiometer (pot)** is a mechanically adjustable resistor with:

- Two end terminals (full resistor)
    
- One **wiper** terminal that moves along the resistive track
    

By turning the knob, you change the ratio between the two parts of the resistor.

---

### **2. Using It as a Volume Control**

When wired as a **voltage divider**:

- Input audio signal goes across the full resistor
    
- The wiper outputs a fraction of that signal
    
- Turning the knob changes attenuation of the signal → **volume up/down**
    

This is exactly the same principle as the earlier voltage divider slide, but now **continuously adjustable**.

---

### **3. Using It for User Input**

If the wiper is connected to an ADC (Analog-to-Digital Converter):

- ADC reads a voltage proportional to the wiper position
    
- Software interprets this as a number
    
- Effectively gives the user an analog input control (e.g., sliders, knobs)
    

The output voltage is:

$$  
V_{\text{out}}  
= V_{\text{in}} \cdot \frac{R_{\text{bottom}}}{R_{\text{top}} + R_{\text{bottom}}}  
$$

where the ratio changes as the knob is turned.

---

### **4. Key Concept**

A potentiometer splits a resistor into two parts:

- **Top section:**  
    $$R_{\text{top}}$$
    
- **Bottom section:**  
    $$R_{\text{bottom}}$$
    

and the ratio is determined by mechanical movement.

---

### **5. Why This Matters in Embedded Systems**

Potentiometers are extremely common in:

- User interfaces
    
- Trimming/adjustments of analog circuits
    
- Sensor calibration
    
- Volume, contrast, brightness controls
    

They provide a **simple, intuitive** way for a user to set a variable level without digital complexity.

---

### **6. Exam-Relevant Understanding**

You should know:

- Potentiometer structure (two fixed ends + wiper)
    
- How it forms a variable voltage divider
    
- How ADCs read analog positions
    
- Use cases in both audio and general embedded input systems

![[All_slides_nes.pdf#page=53]]  
**Week 2 Slide 17 – Temperature Sensor (Thermistor-Based Measurement)**  

---

### **1. Embedded Systems Measure Voltage, Not Resistance**

A microcontroller cannot directly read “resistance.”  
It can only measure **voltage** using an ADC.

Therefore, to read a thermistor (whose resistance changes with temperature), we place it in a **voltage divider** so the changing resistance creates a changing **voltage**.

---

### **2. What the Slide Shows**

The figure displays:

- A **fixed resistor** at the top (labeled R₁)
    
- A **thermistor** at the bottom (labeled R₂)
    
- The output voltage taken between them
    
- A supply voltage feeding the divider
    

This is the standard thermistor measurement circuit.

---

### **3. How the Circuit Works**

- R₂ is the **thermistor**, whose resistance changes with temperature.
    
- R₁ is a **fixed resistor**, chosen to match the expected range of the thermistor.
    

As temperature changes:

- R₂ changes
    
- That changes the ratio between R₁ and R₂
    
- And that changes the output voltage the ADC reads
    


---

### **4. Behavior of an NTC Thermistor**

Most thermistors used in embedded systems are **NTC** (Negative Temperature Coefficient):

- When temperature **increases** → resistance **decreases**
    
- When temperature **decreases** → resistance **increases**
    

The voltage divider converts these resistance shifts into voltage shifts.

---

### **5. Why This Works in Practice**

The ADC reads the output voltage and converts it into a number.  
Software then maps that number to a temperature using:

- A lookup table, or
    
- A curve-fit equation (e.g., Steinhart–Hart)
    

This is how simple, low-cost temperature sensing is done.

---

### **6. Exam-Relevant Understanding**

Be sure you understand:

- Why a thermistor must be placed in a voltage divider
    
- That the _voltage_ (not resistance) is what the ADC measures
    
- The relationship between temperature and resistance for an NTC thermistor
    
- How the divider outputs a temperature-dependent voltage

![[All_slides_nes.pdf#page=54]]  
**Week 2 Slide 18 – Capacitors**  

---

### **1. What Capacitors Do**

A capacitor **stores electrical energy** in an electric field between two conductive plates separated by an insulator.

Key behaviors:

- Can **store and release** energy → acts like a tiny temporary power source.
    
- Acts differently for **DC** and **AC** signals.
    

---

### **2. Capacitors and DC**

- Capacitors **block DC** once fully charged.  
    After charging, no current flows through (in steady state).
    
- This makes them useful for:
    
    - Filtering out DC components
        
    - Coupling AC signals between stages
        

---

### **3. Capacitors and AC**

Capacitors **allow AC** to pass, and the ease with which AC flows depends on the signal frequency.

Important idea on the slide:

- High-frequency signals “see” the capacitor as having **low impedance** → pass through easier
    
- Low-frequency signals “see” **high impedance** → are attenuated
    

This property is why capacitors behave like **frequency-dependent resistors**.

---

### **4. RC Low-Pass Filter (Shown in the Figure)**

The slide shows a classic **RC low-pass filter**:

- A resistor in series
    
- A capacitor to ground
    

How it works:

- High frequencies: strongly attenuated (the capacitor shunts them to ground)
    
- Low frequencies: mostly passed through
    

This is used everywhere in embedded systems to smooth signals, remove noise, or stabilize sensor readings.

---

### **5. Practical Uses in Embedded Systems**

Capacitors are used for:

- Power supply smoothing (removing noise)
    
- Decoupling high-frequency spikes
    
- Signal filtering
    
- Timing circuits (RC delays)
    
- AC coupling between stages
    

You will see them constantly around microcontrollers, power regulators, and sensor inputs.

---

### **6. Exam-Relevant Understanding**

You should know:

- Capacitors block DC but allow AC
    
- Their “resistance” depends on frequency (called **impedance**)
    
- High frequencies pass more easily
    
- Basics of the RC low-pass filter and why it attenuates high-frequency signals


![[All_slides_nes.pdf#page=55]]  
**Week 2 Slide 19 – Batteries Are Imperfect Power Sources**  

---

### **1. Real Batteries Have Internal Resistance**

The slide shows a battery modeled as:

- An ideal voltage source **V**
    
- A small internal resistor **Rᵢ** in series
    

This resistor is not shown on physical batteries, but it **always exists**.

As a battery ages or discharges:

- **Rᵢ increases**
    
- This makes the battery perform worse under load
    

---

### **2. Voltage Drop Caused by Internal Resistance**

Whenever the system draws current **I**, the internal resistance creates its own voltage drop:

- Voltage drop inside the battery:  
    $$ \text{(conceptually)} V_{\text{drop}} = I \cdot R_i $$
    

Because of this:

- The voltage that actually reaches the system (**Vₛ**) is **less** than the battery’s rated voltage.
    

The slide illustrates this using:

- **Low current → small voltage drop → OK**
    
- **High current → large voltage drop → problematic**
    

---

### **3. Why This Is Dangerous for Embedded Systems**

Embedded systems have a **minimum operating voltage**.  
If Vₛ (the voltage after Rᵢ) drops below that threshold:

- The microcontroller may reset
    
- The system may malfunction
    
- Memory operations may fail
    
- Sensors can behave unpredictably
    

Even a short burst of high current (e.g., radio transmission, LED flash, motor start) can temporarily pull the voltage down.

---

### **4. Real-World Example**

A wearable device might run fine until the radio transmits using a high-current spike.  
The internal resistance of the nearly depleted battery causes a big voltage drop → the MCU crashes.

This is extremely common in battery-powered systems.

---

### **5. Why Understanding This Matters**

Designers must:

- Account for high-current peaks
    
- Add **decoupling capacitors** (next slide covers this)
    
- Ensure the battery can supply the peak current
    
- Avoid operating the battery too close to its depletion point
    

---

### **6. Exam-Relevant Understanding**

Know:

- That batteries are modeled as “ideal voltage source + internal resistance”
    
- Higher current → larger internal voltage drop
    
- Why high current spikes can **reset or crash** embedded systems
    
- Why internal resistance increases as batteries age or discharge

![[All_slides_nes.pdf#page=56]]  
**Week 2 Slide 20 – Decoupling Capacitors**  

---

### **1. What Decoupling Capacitors Are**

Decoupling capacitors are **small capacitors placed physically very close** to IC (integrated circuit) power pins.

Their purpose:  
To act as a tiny **local energy reservoir** that smooths and stabilizes the supply voltage.

---

### **2. Why They Are Needed**

Embedded systems often have:

- Sudden current spikes
    
- Switching noise
    
- Fast digital transitions
    

These cause **momentary voltage drops** or **noise** on the supply line.

Without decoupling capacitors:

- Microcontrollers can reset
    
- Sensors can behave incorrectly
    
- Wireless modules can malfunction
    

---

### **3. How They Work (as shown in the figure)**

The slide illustrates:

- A battery with internal resistance
    
- An IC that draws fast-changing current
    
- A capacitor placed **in parallel**, right next to the IC
    

What happens:

- When voltage suddenly dips, the capacitor **discharges**, supplying current instantly
    
- When voltage suddenly rises, the capacitor **absorbs** the excess energy
    
- High-frequency noise is filtered out because capacitors pass high-frequency components to ground
    

This keeps the IC’s supply voltage stable.

---

### **4. Key Behavioral Points**

- Capacitors oppose rapid voltage changes.
    
- Closer placement = better performance (shorter trace → lower inductance).
    
- Often multiple values are placed together (e.g., 100 nF + 1 µF) to cover different frequency ranges.
    

---

### **5. Typical Use**

You will typically find:

- **One 100 nF capacitor per power pin** of a microcontroller
    
- Additional bulk capacitors (1–10 µF) for larger current dips
    

This is standard PCB design practice.

---

### **6. Exam-Relevant Understanding**

You should know:

- Why decoupling capacitors are used
    
- How they stabilize supply voltage during noise or current spikes
    
- Why they must be placed close to the IC
    
- That they act as a short-term local energy buffer

![[All_slides_nes.pdf#page=57]]  
**Week 2 Slide 21 – Switches and Buttons**  

---

### **1. What Switches and Buttons Do**

Both switches and buttons are **mechanical devices** that physically **open or close a circuit**.

Their purpose is to let a user control whether current can flow.

---

### **2. Difference Between a Switch and a Button**

|Device|Behavior|Example Use|
|---|---|---|
|**Switch**|Stays in its position (open or closed)|Power switch, mode selector|
|**Button**|Only closed **while pressed**|Reset button, user input|

The slide shows a simple push button symbol (momentary contact).

---

### **3. Electrical Behavior**

- **Open** → no current can flow (infinite resistance)
    
- **Closed** → current flows freely (near-zero resistance)
    

This is the most basic form of digital input to an embedded system.

---

### **4. Real-World Notes**

- Mechanical contacts can “bounce” (rapid open/close transitions) → software often needs **debouncing**.
    
- Buttons are extremely common for resets, configuration, and user input.
    

---

### **5. Exam-Relevant Understanding**

You should know:

- The conceptual difference between switches and buttons
    
- That they physically open/close the circuit
    
- Why buttons are momentary while switches are latching


![[All_slides_nes.pdf#page=58]]  
**Week 2 Slide 22 – Detecting When a Button Is Pushed**  

---

### **1. Embedded Systems Measure Voltage, Not “Pressed/Not Pressed”**

A microcontroller cannot directly sense whether a button is physically pressed.  
It can only sense a **voltage level** on an input pin.

So the button must be wired in a way that pressing it changes the voltage.

---

### **2. How the Circuit Works (as shown in the slide)**

The slide shows a simple pull-up configuration:

#### **When the button is _not pressed_:**

- The circuit is **open**, meaning no current flows.
    
- Since no current flows through the resistor, there is **no voltage drop** across it.
    
- Therefore, the output node is pulled up to the supply voltage (**Vₛ**).
    
- Microcontroller reads **logic HIGH**.
    

#### **When the button is _pressed_:**

- The button **closes the circuit** and creates a direct path to ground.
    
- Current flows through the resistor to ground.
    
- The output node is now connected to **0 V**.
    
- Microcontroller reads **logic LOW**.
    

This is known as a **pull-up resistor** configuration.

---

### **3. Why You Need the Resistor**

The resistor prevents a **short circuit** between Vₛ and ground when the button is pressed.

- Without it, pressing the button would connect Vₛ → GND directly → dangerous current spike.
    

---

### **4. Common Implementation**

This is one of the most common digital input circuits in all embedded systems:

- Microcontroller input pin
    
- Resistor to supply voltage (pull-up)
    
- Button to ground
    

Microcontrollers often include **internal pull-up resistors**, so the external resistor may not be needed.

---

### **5. Exam-Relevant Understanding**

You should know:

- Why the button must be combined with a resistor
    
- How pressing/releasing affects voltage at the MCU pin
    
- Difference between **pull-up** and **pull-down** configurations
    
- Why this method avoids undefined or floating input states
![[All_slides_nes.pdf#page=59]]  
**Week 2 Slide 23 – Transistor (MOSFET) as a Switch**  

---

### **1. Purpose of the Slide**

This slide introduces how a **MOSFET transistor** can act as an **electronically controlled switch**, replacing a mechanical button.

This is essential in embedded systems when you want the microcontroller to turn something **on or off** electronically.

---

### **2. How a MOSFET Works (Conceptually)**

A MOSFET has three terminals:

- **Gate (G)** – control input
    
- **Drain (D)** – one side of the controlled path
    
- **Source (S)** – the other side
    

The key idea:

- The **gate voltage** controls the **resistance** between drain and source.
    

---

### **3. Two Operating States (as shown in the slide)**

#### **1. Gate = Vₛ (high)**

- MOSFET turns **on**
    
- Drain–source resistance becomes **very small**
    
- Behaves like a **closed switch**
    
- Current flows through the load → the load receives power
    

#### **2. Gate = 0 V (low)**

- MOSFET turns **off**
    
- Drain–source resistance becomes **very large**
    
- Behaves like an **open switch**
    
- No current flows → the load receives **no power**
    

This is exactly how you switch LEDs, motors, sensors, radios, etc.

---

### **4. Why We Use MOSFETs Instead of Mechanical Switches**

- **No moving parts** → highly reliable
    
- **Controlled by logic voltage** from the microcontroller
    
- Can switch **large currents** safely
    
- Can be switched **thousands of times per second** (or more)
    

Microcontrollers use MOSFETs to control devices that require more current than a GPIO pin can supply.

---

### **5. Real-World Embedded Example**

A microcontroller sets a GPIO pin HIGH → MOSFET turns ON → powers a motor/LED/transmitter.  
Set GPIO LOW → MOSFET turns OFF → cuts power.

This is power gating.

---

### **6. Exam-Relevant Understanding**

You should know:

- MOSFET is an electrically controlled switch
    
- Gate voltage controls whether the load receives power
    
- High at gate = switch closed (load on)
    
- Low at gate = switch open (load off)
    
- Why MOSFETs are preferred for electronic switching

![[All_slides_nes.pdf#page=60]]  
**Week 2 Slide 24 – Diodes and LEDs**  

---

### **1. What a Diode Does**

A **diode** is a component that allows current to flow in **one direction only**.

Ideal behavior:

- **Forward direction:** zero resistance
    
- **Reverse direction:** infinite resistance
    

Real behavior:

- Still one-way, but with imperfections.
    

---

### **2. Forward Voltage Drop**

When current flows through a diode in the correct direction, it has a **voltage drop** across it.  
This drop depends on diode type:

- Silicon diode: ~0.7 V
    
- LED: typically 1.8–3.3 V depending on color
    

This is why diodes consume power when conducting.

---

### **3. LEDs Are Just Light-Emitting Diodes**

An LED behaves like a diode but:

- Emits **light** when forward-biased
    
- Has a specific forward voltage depending on color/material
    

Since LEDs allow current in only one direction, they must be oriented correctly.

---

### **4. Why You Need a Series Resistor**

LEDs are very sensitive to excessive current.  
A resistor is placed in series to limit the current to a safe value.

Without it:

- The LED would draw too much current
    
- It could be destroyed within milliseconds
    

This resistor ensures the current stays in the intended safe operating range.

---

### **5. What the Slide’s Diagram Shows**

- A diode symbol indicating directionality
    
- An LED with a resistor in series
    
- Demonstrates that the resistor sets the maximum current through the LED
    

---

### **6. Exam-Relevant Understanding**

You should know:

- Diodes conduct one way and block the other
    
- LEDs are diodes that emit light
    
- There is always a forward voltage drop
    
- A series resistor is required to protect LEDs from overcurrent
- 
![[All_slides_nes.pdf#page=61]]  
**Week 2 Slide 25 – Reverse Voltage Protection**  

---

### **1. Purpose of Reverse Voltage Protection**

If a user accidentally connects a battery **backwards**, the entire system could be damaged instantly.  
Reverse voltage protection prevents this by using a **diode** that only allows current to flow when the battery is connected correctly.

---

### **2. How the Circuit Works (as shown on the slide)**

#### **When the battery is connected correctly:**

- The diode is **forward-biased**.
    
- Current flows normally into the circuit.
    
- The system receives power and works as expected.
    

#### **When the battery is connected backwards:**

- The diode becomes **reverse-biased**.
    
- It blocks current completely.
    
- The system receives **no power**, but is **safe** from damage.
    

---

### **3. Why This Works**

Diodes inherently block current in the reverse direction.  
This simple behavior prevents:

- Overcurrent
    
- Component burnout
    
- Reverse polarity damage to ICs and regulators
    

Even a moment of reverse connection can destroy sensitive electronics, so this protection is very common.

---

### **4. Practical Considerations**

- The diode must handle the system’s maximum current.
    
- Because diodes have a forward voltage drop, they waste a small amount of power (typically ~0.2–0.7 V).
    
- To minimize this drop, designers often use **Schottky diodes** (lower forward drop).
    

More advanced designs sometimes use MOSFET-based ideal diodes to reduce the drop further.

---

### **5. Exam-Relevant Understanding**

You should know:

- What reverse polarity means
    
- Why a diode prevents damage
    
- How the diode’s orientation determines whether current can flow
    
- That this is a **common and simple protective technique** in embedded hardware

![[All_slides_nes.pdf#page=62]]  
**Week 2 Slide 26 – PCB Prototyping**  

---

### **1. Why Prototyping Is Important**

Before designing a full **Printed Circuit Board (PCB)**, it is often necessary to **prototype the circuit** or certain subsystems.  
This helps verify:

- That the circuit works as intended
    
- That component choices are correct
    
- That software/hardware interaction is stable
    

Prototyping avoids costly PCB redesigns.

---

### **2. Three Prototyping Tools Shown on the Slide**

#### **1. Breadboard**

- No soldering required
    
- Components and wires plug in easily
    
- Best for quick experiments and low-frequency circuits
    
- Not suitable for high-speed signals or RF
    

#### **2. Veroboard (Stripboard)**

- Copper strips on a board
    
- Requires soldering
    
- More permanent than a breadboard
    
- Good for small custom circuits or early prototypes
    

#### **3. Breakout Boards**

- Small PCBs that “break out” tiny IC pins into a usable pin header
    
- Essential for chips that are too small to be used on a breadboard
    
- Common for sensors, regulators, accelerometers, wireless modules
    

Breakout boards are extremely important because modern components are rarely available in breadboard-friendly packages.

---

### **3. Why This Matters for Embedded Systems**

Prototyping:

- Saves time
    
- Avoids manufacturing errors
    
- Enables testing before committing to a full PCB design
    
- Makes debugging much easier
    

---

### **4. Exam-Relevant Understanding**

You should know:

- The differences between breadboard, veroboard, and breakout boards
    
- Why breakout boards exist
    
- Why prototyping is done before PCB design
![[All_slides_nes.pdf#page=63]]  
**Week 2 Slide 27 – PCB Design**  

---

### **1. What a PCB Is**

A **Printed Circuit Board (PCB)** is a rigid board with **copper tracks** printed on its surface (or internal layers).  
These tracks replace wires and electrically connect components.

A PCB includes:

- **Copper traces** (electrical connections)
    
- **Pads** (where components are soldered)
    
- **Substrate material** (such as FR4 fiberglass)
    

---

### **2. Why PCBs Are Used**

Compared to hand-wired circuits:

- PCBs are **smaller**
    
- **More reliable**
    
- **Reproducible**
    
- Support **high-speed**, **low-noise**, and **dense** designs
    

All modern embedded systems use PCBs.

---

### **3. PCB Design Tools**

PCB design is done with specialized software called:

- **Electronic Design Automation (EDA)** or
    
- **Electronic Computer-Aided Design (ECAD)** tools
    

Examples commonly used in academia/industry:

- Altium Designer
    
- KiCad
    
- Eagle
    
- OrCAD
    
- EasyEDA
    

These tools handle schematics, component placement, routing, and manufacturing outputs.

---

### **4. What the Slide Shows**

Images illustrating:

- Copper traces on a PCB
    
- A PCB layout example with components and routing
    
- Demonstrating how physical design corresponds to schematic connections
    

---

### **5. Exam-Relevant Understanding**

You should know:

- What a PCB is
    
- Why PCBs are essential for embedded systems
    
- That ECAD tools are used to design them
    
- How PCB layout represents physical implementation of the schematic

![[All_slides_nes.pdf#page=64]]  
**Week 2 Slide 28 – PCB Design: Schematic**  

---

### **1. First Step of PCB Design: Build the Schematic**

Before laying out the physical board, you must create a **schematic diagram** of the entire circuit.

This step includes:

- Identifying **key components** (MCU, sensors, regulators, connectors, etc.)
    
- Identifying the **power source** and voltage levels
    
- Ensuring all components are **electrically compatible**
    

---

### **2. Using Reference Circuits**

Many components (especially ICs) provide:

- **Datasheet-recommended circuits**
    
- **Example applications**
    
- **Required passive components** (e.g., a 100 nF decoupling capacitor)
    

Designers often:

- Reuse values from reference designs
    
- Borrow circuits from **open hardware** examples  
    This reduces mistakes and speeds up development.
    

---

### **3. Creating a Schematic Symbol**

Every component must have a schematic symbol that matches:

- The **pin numbers**
    
- The **pin functions**
    

Example in the slide:

- A portion of the **ADXL362 accelerometer** datasheet
    
- Showing pinouts and how they translate into a schematic symbol
    

This ensures the PCB routing will match the real-world chip pin positions.

---

### **4. Why This Step Matters**

If the schematic is wrong:

- The PCB will be wrong
    
- The board may be unusable
    
- Redesigns cost time and money
    

The schematic is the **logical blueprint** of the circuit.

---

### **5. Exam-Relevant Understanding**

You should know:

- Why schematics come before layout
    
- Why datasheet pin information must match the schematic symbol
    
- Why passive components are often chosen based on reference designs
    
- The importance of identifying power sources and voltage levels early
Below is a clean table for all **ADXL362 pins shown in the slide’s figure** (Slide 28).  
This table maps **pin names → function/purpose**, based on the diagram in the slide.  

---

# **ADXL362 Pin Table (Slide Figure Breakdown)**

|**Pin Name**|**Type**|**Meaning / Function**|
|---|---|---|
|**VDDIO**|Power|I/O supply voltage (logic level power for digital pins)|
|**VS**|Power|Main analog/digital supply voltage for the sensor core|
|**GND**|Power|Ground reference (multiple GND pins for noise reduction)|
|**SCLK**|Digital Input|SPI clock input — driven by MCU|
|**MOSI**|Digital Input|SPI data input (Master Out, Slave In)|
|**MISO**|Digital Output|SPI data output (Master In, Slave Out)|
|**CS**|Digital Input|Chip Select for SPI (active low)|
|**INT1**|Digital Output|Interrupt output #1 — sensor event notification|
|**INT2**|Digital Output|Interrupt output #2 — programmable events/wakeup|
|**RSVD**|—|Reserved pins (must not be connected / follow datasheet)|
|**NC**|—|Not connected internally — leave floating|
|**DIO_XX**|Digital I/O|General-purpose digital I/O from main system (MCU connections)|
|**100 nF capacitor pins**|Passive|Decoupling capacitor for local power stability|

**Note:**  
The slide shows **two ADXL362 chips**, both using the same pin naming and functions.

---

# **Grouped Explanation (Easier for Exam Use)**

### **1. Power Pins**

|Pins|Purpose|
|---|---|
|VDDIO|Logic I/O voltage|
|VS|Core supply voltage|
|GND (multiple)|Ground reference|

Multiple grounds help reduce noise because accelerometers are sensitive analog devices.

---

### **2. SPI Communication Pins**

|Pin|Direction|Purpose|
|---|---|---|
|SCLK|Input|SPI clock|
|MOSI|Input|MCU → ADXL362 data|
|MISO|Output|ADXL362 → MCU data|
|CS|Input|Chip select to activate the device|

This is a standard **4-wire SPI interface**.

---

### **3. Interrupt Pins**

|Pin|Purpose|
|---|---|
|INT1|Programmable interrupt (motion detect, activity, etc.)|
|INT2|Second interrupt (activity, inactivity, FIFO events, etc.)|

These allow the sensor to wake the MCU from sleep to save power.

---

### **4. Reserved & NC Pins**

|Pin Type|Meaning|
|---|---|
|RSVD|Must follow datasheet — often used internally, not user-accessible|
|NC|Not connected — leave floating|

Important: **Never connect RSVD to other signals unless the datasheet says so.**

---

### **5. Related Passives**

|Component|Purpose|
|---|---|
|C13, C19 (100 nF caps)|Decoupling capacitors to stabilize power for each ADXL362|

![[All_slides_nes.pdf#page=65]]  
**Week 2 Slide 29 – PCB Design: Component Layout**  

---

### **1. Purpose of This Stage**

After drawing the schematic, the next PCB design step is creating the **physical footprint** for each component.  
A footprint defines:

- The pad shapes
    
- Pad spacing
    
- Component outline
    
- Orientation
    
- Exact physical dimensions
    

This ensures the component can be soldered correctly on the PCB.

---

### **2. What the Slide Shows**

#### **Top image: ADXL362 footprint diagram**

- Shows exact pad layout from the datasheet
    
- Dimensions are given in **millimeters**
    
- Includes top-down and side views
    
- Highlights that designers must match **pin numbers** to the correct pads
    

#### **Bottom image: Standard SMD resistor/capacitor packages**

- Shows common package sizes such as:
    
    - **0402** (0.04" × 0.02")
        
    - **0603**
        
    - **0805**
        
- Demonstrates the difference between **imperial** and **metric** sizing systems
    

This explains why physical size matters in PCB layout.

---

### **3. Critical Point: Top vs. Bottom Views**

The slide emphasizes:

- Datasheets often show the **bottom view**
    
- When placing a footprint on the PCB, the view is effectively **mirrored**
    
- Misinterpreting this leads to **reversed pin assignments**, which can destroy the board
    

This is a common beginner mistake.

---

### **4. Why Footprints Matter**

If the footprint is wrong:

- The component cannot be soldered
    
- Pads won't align with the real pins
    
- The board may be unusable
    
- Re-spinning the PCB costs time and money
    

Footprint accuracy is just as important as the schematic.

---

### **5. Importance of Standard Passive Sizes**

Typical SMD sizes:

- Smaller packages (0402, 0201) allow compact layouts but are harder to solder
    
- Larger packages (0603, 0805) are easier to hand-assemble
    
- Passive parts follow standardized dimensions, making layout faster
    

Knowing package sizes helps estimate:

- Space requirements
    
- Solderability
    
- PCB density
    

---

### **6. Exam-Relevant Understanding**

You should know:

- What a component footprint is
    
- Why datasheet dimensions must be matched exactly
    
- The meaning of package sizes like 0402 / 0603
    
- The issue of top vs. bottom views (mirroring)
    
- Why footprints are a critical step before routing the PCB

![[All_slides_nes.pdf#page=66]]  
**Week 2 Slide 30 – PCB Design: Board Layout**  

---

### **1. What Board Layout Is**

Board layout is the step where you:

- Place each component footprint on the actual PCB
    
- Draw copper traces to connect them
    
- Define how signals travel across layers
    

This is the **physical implementation** of your schematic.

---

### **2. Layers in a PCB (as shown in the slide)**

The slide mentions multiple copper layers:

#### **1. Top Layer**

- Components usually placed here
    
- Contains copper traces
    

#### **2. Bottom Layer**

- Also supports components and traces
    
- Often used for routing when top is crowded
    

#### **3. Internal Layers (for multi-layer PCBs)**

- Dedicated to power distribution (e.g., 3.3V plane)
    
- Dedicated to ground (ground plane)
    
- Used for routing high-density signals
    

More layers = more routing flexibility but higher cost.

---

### **3. Vias (Vertical Electrical Connections)**

The slide defines three types:

|Via Type|What It Connects|Use Case|
|---|---|---|
|**Through-hole via**|Top → bottom|Most common; cheapest|
|**Blind via**|Top → internal OR bottom → internal|Saves space; more complex|
|**Buried via**|Internal → internal|For dense PCBs; most expensive|

Vias are essential for connecting traces on different layers.

---

### **4. Ground Plane / Ground Layer**

A **ground plane** is a large copper area connected to ground.

Benefits:

- Reduces noise by providing a stable reference
    
- Improves electromagnetic interference (EMI) performance
    
- Helps with heat dissipation
    
- Simplifies routing by allowing easy grounding
    

Most embedded boards use a **continuous ground plane** for signal integrity.

---

### **5. What the Slide Images Represent**

- A 3D depiction of multi-layer PCB stack-up
    
- Examples of vias connecting different layers
    
- A real PCB showing traces, pads, and copper areas
    

These visuals help understand how signals move **inside** the PCB, not only on the surface.

---

### **6. Exam-Relevant Understanding**

You should know:

- Difference between top, bottom, and internal layers
    
- What vias do and the differences between via types
    
- Purpose of a ground plane
    
- That board layout is the step where schematic connections become real physical routing

![[All_slides_nes.pdf#page=67]]  
**Week 2 Slide 31 – PCB Design: Bill of Materials (BOM)**  

---

### **1. What a BOM Is**

A **Bill of Materials (BOM)** is essentially a **shopping list** for all the components required to build the PCB.

It includes:

- Part names / types
    
- Manufacturer part numbers
    
- Quantities
    
- Supplier information
    
- Cost (sometimes)
    

This document allows a manufacturer or assembly house to order exactly the correct parts.

---

### **2. What the Slide Shows**

The slide includes a typical spreadsheet-style BOM, with columns for:

- **Item number**
    
- **Description**
    
- **Manufacturer**
    
- **Part number**
    
- **Quantity**
    
- **Package type**
    
- **Comments / notes**
    

This is the standard format used in industry.

---

### **3. Why the BOM Matters**

Without a correct BOM:

- Manufacturers may order the wrong components
    
- Assemblies may fail or be incomplete
    
- Production delays become extremely costly
    

A BOM is as important as the schematic and layout.

---

### **4. Key Points for Embedded Designers**

A good BOM must:

- Match the components used in the schematic AND layout
    
- Specify exact part numbers (because many components look similar but behave differently)
    
- Indicate package sizes (e.g., 0402 vs 0603)
    
- Include alternatives if needed (optional but helpful)
    

Special attention must be given to:

- Voltage ratings of capacitors
    
- Power ratings of resistors
    
- Temperature ranges
    
- IC variants (package, speed grade, memory size, etc.)
    

---

### **5. Exam-Relevant Understanding**

You should know:

- What a BOM is used for
    
- Why component selection must be precise
    
- What typical information appears in a BOM
    
- How it connects the schematic → manufacturing process

![[All_slides_nes.pdf#page=68]]  
**Week 2 Slide 32 – PCB Design: Manufacturing and Assembly**  

---

### **1. Two Distinct Stages: Manufacturing vs. Assembly**

#### **PCB Manufacturing**

This stage produces the **empty PCB**, including:

- Copper layers (etched or plated)
    
- Drill holes and vias
    
- Solder mask
    
- Silkscreen text
    
- Multilayer stack-up
    

No components are attached yet.

#### **PCB Assembly**

This stage solders components onto the manufactured PCB, typically using:

- **Pick-and-place machines** (shown in the slide)
    
- Reflow ovens
    
- Automated inspection systems
    

---

### **2. Why These Steps Are Often Outsourced**

Modern PCBs and assemblies require:

- High precision
    
- Specialized machinery
    
- Controlled environments
    

Because of cost and complexity, companies rely on **PCB fabrication services** (“fabs”) and **assembly houses**.

---

### **3. Cost Factors (important understanding)**

Costs increase when:

- Components become **smaller**
    
- PCB requires **more layers**
    
- Tolerances are **tighter**
    
- Via types are advanced (e.g., blind/buried)
    
- Assembly volume is low (prototype runs)
    

The slide hints at this with the caption:  
**“The smaller, the costlier.”**

---

### **4. What the Slide Images Show**

- A pick-and-place machine holding a reel of components
    
- This automated tool places tiny components at high speed (thousands per minute)
    
- Demonstrates how precise and automated modern assembly is
    

This visual emphasizes why manual assembly is unrealistic for dense embedded systems.

---

### **5. Exam-Relevant Understanding**

You should know:

- Difference between **manufacturing** (making the PCB) and **assembly** (populating it)
    
- Why these steps require specialized equipment
    
- Why smaller components and high precision increase cost
    
- What a pick-and-place machine does (automated component placement)

![[All_slides_nes.pdf#page=69]]  
**Week 2 Slide 33 – PCB Design: Testing**  

---

### **1. Why Testing Is Required**

Just like software can have bugs, **hardware designs can also have errors**—either from the design itself or from manufacturing defects.  
Testing ensures the PCB works as intended and meets performance requirements.

---

### **2. Who Performs the Testing**

Two layers of testing usually occur:

#### **1. Manufacturer Testing**

- Ensures PCBs are manufactured correctly (correct traces, no shorts/opens)
    
- Uses automated tools like electrical test fixtures
    
- Checks assembly quality (solder joints, component orientation)
    

#### **2. Designer/Engineer Testing**

- Ensures the **design** itself works
    
- Validates functionality, signal performance, power consumption, etc.
    

---

### **3. Types of Testing (as listed on the slide)**

|Test Type|Purpose|
|---|---|
|**Functional testing**|Does the board actually work as intended?|
|**Performance / power testing**|Does it meet energy and speed requirements?|
|**Signal quality testing**|Are signals clean, or is noise/EMI a problem?|
|**Mechanical testing**|Does the board withstand stress, vibration, etc.?|
|**Thermal testing**|Does heat dissipation work correctly?|
|**Specification verification**|Does the board meet the design specs?|
|**Safety certification**|Required for commercial products sold legally|

These are especially important for embedded devices used in healthcare, consumer electronics, or critical systems.

---

### **4. Why Testing Is Essential**

Testing catches:

- Incorrect footprints
    
- Routing mistakes
    
- Voltage/power issues
    
- Timing and signal integrity problems
    
- Component failures
    
- Manufacturing defects (e.g., solder bridges)
    

Even a small mistake may require a full **hardware revision**, which is costly in both time and money.

---

### **5. Exam-Relevant Understanding**

You should know:

- The difference between manufacturing testing and design-stage testing
    
- The key types of tests performed
    
- Why PCB/hardware testing is as important as software testing
    
- The consequences of inadequate testing

![[All_slides_nes.pdf#page=70]]  
**Week 2 Slide 34 – Electronic Testing Instruments: Multimeter**  

---

### **1. What a Multimeter Is**

A **multimeter** (specifically a digital multimeter, DMM) is a versatile tool used to measure basic electrical parameters in circuits.

It is one of the most essential tools in electronics debugging and testing.

---

### **2. Main Measurement Modes (as shown on the slide)**

|Mode|What It Measures|Use Case|
|---|---|---|
|**Voltmeter (DC/AC)**|Voltage|Checking supply rails, reading sensor outputs|
|**Ammeter (DC/AC)**|Current|Measuring consumption of a device|
|**Ohmmeter**|Resistance|Checking components, detecting open/closed circuits|
|**Continuity Mode**|Very low resistance (beeps)|Detecting shorts or verifying two points are connected|

These are the most commonly used functions.

---

### **3. Measurement Ranges**

Multimeters operate in selectable ranges:

- Too high a range → less resolution
    
- Too low a range → overload / out of range
    

For precise readings, the correct range must be selected.

---

### **4. When Multimeters Are Useful**

They excel at measuring **steady-state** (non-changing) values:

- Checking if a board has 3.3 V or 5 V properly
    
- Verifying connections and resistors
    
- Measuring battery voltage
    
- Testing LEDs, switches, continuity
    
- Verifying power consumption in idle/active states
    

They are **not** ideal for rapidly changing signals—that requires an oscilloscope.

---

### **5. What the Slide Image Shows**

A typical digital multimeter:

- LCD display
    
- Rotary selection knob
    
- Input jacks for probes
    
- Common measurement symbols
    

This helps you identify and use the tool in a lab setting.

---

### **6. Exam-Relevant Understanding**

You should know:

- The four main functions of a DMM
    
- When to use a multimeter vs. an oscilloscope
    
- What continuity mode is and why it’s useful
    
- Why the correct range must be selected

![[All_slides_nes.pdf#page=71]]  
**Week 2 Slide 35 – Electronic Testing Instruments: DC Power Supply**  

---

### **1. Purpose of a DC Power Supply**

A **bench DC power supply** provides a stable, controllable voltage source for testing circuits.  
It replaces batteries during development because it is:

- Adjustable
    
- Stable
    
- Safe (current limiting)
    

This makes it ideal for powering prototypes.

---

### **2. Key Features (as shown on the slide)**

#### **Adjustable Output Voltage**

- You can set the exact voltage your circuit requires (e.g., 1.8 V, 3.3 V, 5 V).
    
- Supports fine resolution adjustments.
    

#### **Multiple Independent Outputs**

- Many supplies have 2–4 channels.
    
- Allows powering several parts of a circuit at different voltages.
    

#### **Current Limiting**

- You set a maximum current.
    
- If your circuit tries to draw more, the supply **limits** it.
    
- Prevents damage from shorts or wiring mistakes.
    

This is one of the biggest advantages over a battery.

---

### **3. Use Cases in Embedded Systems**

- Powering a prototype MCU board
    
- Testing current consumption
    
- Detecting shorts (supply goes into current limit mode)
    
- Simulating battery voltages at different charge levels
    
- Measuring power profiles
    

---

### **4. What the Slide Image Shows**

- A typical lab DC supply with:
    
    - Display for voltage and current
        
    - Output terminals
        
    - Mode indicators
        
    - Buttons/dials for adjusting settings
        

These devices are standard in electronics labs.

---

### **5. Exam-Relevant Understanding**

You should know:

- Why adjustable DC power supplies are used during development
    
- How current limiting prevents damage
    
- That bench supplies can replace batteries during testing
    
- Why having multiple channels is useful for multi-voltage systems

![[All_slides_nes.pdf#page=72]]  
**Week 2 Slide 36 – Electronic Testing Instruments: Oscilloscope**  

---

### **1. What an Oscilloscope Does**

An **oscilloscope** measures and displays **voltage over time**.  
This makes it essential for observing signals that **change quickly**, unlike a multimeter which only measures steady values.

Embedded systems rely heavily on timing, so oscilloscopes are a core debugging tool.

---

### **2. Key Capabilities (as listed on the slide)**

#### **Measure and display time-varying signals**

- View waveforms such as square waves, sensor outputs, clock signals, communication signals.
    

#### **Multiple channels**

- Compare two or more signals at once (e.g., input vs. output).
    

#### **Triggering**

- Set conditions so the oscilloscope captures the waveform only when a specific event occurs  
    (e.g., rising edge, specific voltage threshold).
    

#### **Statistics**

- Measure:
    
    - Minimum voltage
        
    - Maximum voltage
        
    - Frequency
        
    - Period / time duration
        
    - Rise/fall times
        

#### **Data extraction**

- Save signal data to a file for analysis.
    

---

### **3. When Oscilloscopes Are Used**

Oscilloscopes are used for:

- Debugging digital communication (SPI, I²C, UART)
    
- Checking PWM signals
    
- Measuring clock signals
    
- Observing noise or ripple on power supplies
    
- Verifying timing relationships between signals
    
- Viewing sensor waveforms
    

If something is not working but a multimeter says “looks fine,” the oscilloscope usually reveals the real problem.

---

### **4. What the Slide Image Shows**

A modern digital oscilloscope with:

- Large waveform display
    
- Control knobs for voltage, time, and triggering
    
- Multiple input channels
    
- Measurement indicators
    

This is the standard tool you’ll find in engineering labs.

---

### **5. Exam-Relevant Understanding**

You should know:

- Difference between multimeter and oscilloscope
    
- What signals look like on an oscilloscope
    
- The meaning of “triggering”
    
- When to use an oscilloscope in embedded debugging

![[All_slides_nes.pdf#page=73]]  
**Week 2 Slide 37 – Electronic Testing Instruments (Additional Tools)**  

---

### **1. Overview of Additional Electronic Test Instruments**

This slide introduces four more tools commonly used when debugging or characterizing embedded systems—particularly when working with **digital signals**, **RF**, or **precision measurements**.

These tools complement the multimeter and oscilloscope.

---

### **2. Logic Analyzer**

A logic analyzer captures **digital** voltage signals across many channels at once.

Used for:

- Debugging digital protocols (I²C, SPI, UART, I²S, etc.)
    
- Timing analysis (when do signals change?)
    
- Checking if communication lines are correct
    
- Recording long sequences of digital activity
    

Key point:  
A logic analyzer reads **digital 0s and 1s**, not analog voltages.

---

### **3. Spectrum Analyzer**

A spectrum analyzer shows how **signal power is distributed across frequency**.

Used for:

- RF design (Bluetooth, Wi-Fi, antennas)
    
- Measuring harmonic content
    
- Identifying interference sources
    
- Checking transmitter output power and frequency stability
    

Unlike an oscilloscope (time-domain), a spectrum analyzer shows the **frequency-domain** representation.

---

### **4. Signal/Function Generator**

A function generator **creates electrical signals** with selectable:

- Waveform shape (sine, square, triangle, pulse)
    
- Amplitude
    
- Frequency
    
- DC offset
    

Used for:

- Testing circuit response
    
- Injecting known signals into filters, amplifiers, ADC inputs
    
- Replacing a sensor temporarily with a predictable signal
    

This tool is often paired with an oscilloscope.

---

### **5. Source Measurement Unit (SMU)**

An SMU can **supply power** _and_ **measure voltage and current** with extreme precision at the same time.

Used for:

- Characterizing sensors
    
- Measuring battery behavior
    
- Testing ultra-low-power devices (microamp or nanoamp currents)
    
- IV curve tracing of components (LEDs, diodes, transistors)
    

SMUs are more advanced and expensive than typical lab tools.

---

### **6. Exam-Relevant Understanding**

You should know:

- Differences between oscilloscope vs. logic analyzer vs. spectrum analyzer
    
- Which tool is used for **digital timing**, **RF frequency**, or **stimulus generation**
    
- That an SMU provides highly accurate power + measurement simultaneously
    

These tools appear often in embedded system labs and exam contexts.



--- 
---
---

## **MCQ 1 — Basic Electrical Concepts**

Which of the following statements about **Ohm’s Law** is correct?

A. Current is inversely proportional to voltage  
B. Voltage equals resistance divided by current  
C. Current increases when resistance increases (at fixed voltage)  
D. Current equals voltage divided by resistance

---

## **MCQ 2 — Power and Batteries**

A battery has internal resistance. When the device suddenly draws a high current, what happens?

A. The supply voltage increases  
B. The internal resistance decreases to compensate  
C. The supply voltage drops below the battery’s nominal voltage  
D. The battery outputs AC instead of DC

---

## **MCQ 3 — Components and Circuits**

A **voltage divider** is typically used to:

A. Convert AC to DC  
B. Produce an output that is a fraction of an input voltage  
C. Store energy for later use  
D. Amplify small signals

---

## **MCQ 4 — PCB Design**

Which of the following best describes the purpose of a **ground plane** in a PCB?

A. To physically support the components  
B. To reduce noise and improve electromagnetic performance  
C. To convert digital signals into analog signals  
D. To increase the board’s overall resistance

---

## **MCQ 5 — Electronic Testing Instruments**

A **logic analyzer** is the best tool for:

A. Measuring high-frequency analog waveforms  
B. Capturing digital 0/1 transitions on multiple lines simultaneously  
C. Measuring power consumption at microamp levels  
D. Viewing frequency-domain RF spectra

---

**MCQ 1:** **D**  
(Current = Voltage / Resistance)

**MCQ 2:** **C**  
(High current through internal resistance causes a supply voltage drop)

**MCQ 3:** **B**  
(Voltage dividers output a fraction of the input voltage)

**MCQ 4:** **B**  
(Ground planes reduce noise and improve EMI performance)

**MCQ 5:** **B**  
(Logic analyzers capture digital transitions across multiple channels)


WEEK 3 NOTES


![[All_slides_nes.pdf#page=76]]  
**Week 3 Slide 3 – Digital Logic**  

**Notes:**

- Digital systems interpret two voltage levels as binary values.
    
- High voltage → logical **1**; low voltage → logical **0**.
    
- Real-world signals are noisy, but thresholds (e.g., above (V_S/2) = ‘1’) allow correct interpretation.
    
- Noise near the threshold can cause unstable readings, motivating later concepts such as **hysteresis**.

![[All_slides_nes.pdf#page=77]]  
**Week 3 Slide 4 – General Purpose Input/Output (GPIO)**  

**Notes**

- A **GPIO** pin is fully controlled by software.
    
- It can:
    
    - **Drive output high** (‘1’)
        
    - **Drive output low** (‘0’)
        
    - **Read** the logic level present on the pin
        
- Example: the **nRF52832** MCU provides **32 GPIOs**, labelled **P0.00–P0.31** (shown in the diagram).
    
- These pins serve as the MCU’s basic interface to the external world—sensors, LEDs, switches, communication lines, etc.

![[All_slides_nes.pdf#page=78]]  
**Week 3 Slide 5 – GPIO Output: Push-Pull Mode**  

**Notes (with deeper explanation)**

- In **push-pull mode**, the MCU actively drives the pin **both high and low** using internal transistor switches.
    
    - When output = ‘1’, the MCU **pushes** the pin up to (V_S).
        
    - When output = ‘0’, the MCU **pulls** the pin down to ground.
        
- Because the MCU is actively forcing the voltage, the pin behaves like a **strong, low-impedance source**—it can reliably drive LEDs, digital inputs on other chips, etc.
    
- This is the **default output mode** in most MCUs because it offers:
    
    - **Fast transitions** between logic levels
        
    - **Clear, well-defined voltage states**
        
    - **Ability to source or sink modest current**
        
- Key idea for understanding:
    
    - Push-pull mode gives you **full control**.
        
    - But because you actively drive both high and low, you **must not connect two push-pull outputs together**, or they might drive in opposite directions and cause a short circuit.
        

**Concept clarity**

- Think of the pin as a _muscle_ that can push upward and pull downward.
    
- Since it is always actively doing something, conflicts are dangerous if multiple devices try to drive the same line.

![[All_slides_nes.pdf#page=79]]  
**Week 3 Slide 6 – GPIO Output: Push-Pull Mode (MOSFET Implementation)**  

**Notes**

- Push-pull is implemented using **two MOSFETs** arranged so only one conducts at a time.
    
- When the control input = ‘1’:
    
    - The **upper MOSFET** connects the pin to (V_S).
        
    - The **lower MOSFET** disconnects from ground.
        
- When the control input = ‘0’:
    
    - The **upper MOSFET** disconnects from (V_S).
        
    - The **lower MOSFET** connects the pin to ground.
        
- Internally, this ensures:
    
    - A strong, clean logic level
        
    - Fast switching
        
    - No undefined voltage region (the pin is _always_ driven)
        

**What you should know for the exam**

- Be able to explain **how push-pull works** conceptually and electrically (two transistors, one sourcing, one sinking).
    
- Understand **why only one device may drive a push-pull output line** (otherwise shorts).
    
- Know that push-pull **actively drives both high and low**, unlike open-drain.

![[All_slides_nes.pdf#page=80]]  
**Week 3 Slide 7 – GPIO as a Current Source**  

**Notes**

- Besides carrying logic signals, a GPIO can **source current** to power small external components (e.g., an LED, a sensor enable pin).
    
- The GPIO acts like a small **on/off switch** controlled by software.
    
- However, GPIO pins have **strict current limits**: typically **2–12 mA**, sometimes up to **40 mA** for special “high-drive” pins.
    
- Exceeding this limit can **damage the pin or the MCU**.
    
- High-power components (motors, relays, power LEDs) must be powered directly from the supply and controlled indirectly via **transistors, MOSFETs, or driver circuits**.
    

**What you should know for the exam**

- Understand that GPIOs are **not general power outputs**—they can only supply small currents.
    
- Know the difference between **logic signalling** (very low current) and **current sourcing** (limited but finite).
    
- Be able to explain when to use a **driver circuit** instead of powering a component directly from a GPIO.

![[All_slides_nes.pdf#page=81]]  
**Week 3 Slide 8 – GPIO as a Current Sink**  

**Notes**

- A GPIO can also **sink current**, meaning current flows _into_ the pin toward ground.
    
- This is the opposite of current sourcing: instead of providing current, the pin completes the circuit by pulling the line to ground.
    
- When configured as a sink:
    
    - Writing **‘0’** → the pin connects to ground → current flows → an LED **turns on**.
        
    - Writing **‘1’** → the pin becomes high (no current flow) → LED **turns off**.
        
- This reverses the intuitive logic: **0 = ON**, **1 = OFF**.
    
- Sink current is also **limited**, just like source current.
    

**Comparison Table: Source vs Sink**

|Concept|Current Source|Current Sink|
|---|---|---|
|Direction of current|Out of GPIO pin|Into GPIO pin|
|LED wiring|LED → GND|Vcc → LED|
|LED ON when|Output = ‘1’|Output = ‘0’|
|Risk|Exceeding source limit|Exceeding sink limit|

**What you should know for the exam**

- Be able to explain the difference between **sourcing** and **sinking** current.
    
- Understand why an LED may be wired differently depending on whether the MCU **sources** or **sinks** current.
    
- Remember that **logic inversion** occurs in sink configurations (0 turns things on).

![[All_slides_nes.pdf#page=82]]  
**Week 3 Slide 9 – Two MCUs**  

**Notes**

- The slide introduces the problem of **multiple devices sharing the same output line**.
    
- If two MCUs are connected to the same line and both are configured as **outputs**, they may try to drive **different logic levels** at the same time.
    
- This sets up the concept of **output conflicts**, which can damage hardware.
    

**Concept clarity**

- Think of the shared line as a “tug-of-war”:
    
    - If both MCUs try to push/pull the line in opposite directions, they effectively short **Vcc → GND** through their output drivers.
        
- The slide sets the stage for why we need more than just ‘0’ and ‘1’ output states.
    

**What you should know for the exam**

- Understand _why_ two push-pull outputs must **never** drive the same line simultaneously.
    
- Be able to describe the risk: **short circuit due to opposing drive levels**.
    
- Recognize that this motivates the need for a **third state** (Hi-Z), introduced in the next slides.

![[All_slides_nes.pdf#page=83]]  
**Week 3 Slide 10 – Two MCUs (Short Circuit Problem)**  

**Notes**

- When two devices share the same output line, the danger becomes clear:
    
    - If one MCU outputs **‘1’** (pushes the line to (V_S))
        
    - And the other outputs **‘0’** (pulls the line to ground)  
        → This forms a **direct short circuit** through the two output drivers.
        
- Because push-pull outputs are _actively_ driven, neither side “lets go,” so current spikes can occur that may:
    
    - Overheat pins
        
    - Damage MOSFETs inside the MCU
        
    - Corrupt signals or reset devices
        
- The key limitation:
    
    - With only two output states (‘0’ and ‘1’), there is **no safe way** to share a line between multiple drivers.
        
    - We need a way for devices to **disconnect** themselves → the motivation for **tri-state logic / Hi-Z**.
        

**What you should know for the exam**

- Be able to explain **exactly why** output conflicts cause shorts.
    
- Recognize that the problem arises because push-pull outputs **actively drive both high and low**.
    
- Understand that this leads to the requirement for a third state (**Hi-Z**) to enable safe bus sharing.


![[All_slides_nes.pdf#page=84]]  
**Week 3 Slide 11 – Tri-State Logic**  

**Notes**

- Tri-state logic introduces a **third output state** beyond ‘0’ and ‘1’:
    
    - **‘0’** → actively driven low
        
    - **‘1’** → actively driven high
        
    - **Hi-Z** (high impedance) → **disconnected**, behaving like an open circuit
        
- In Hi-Z, the output driver’s MOSFETs are **both off**, making the pin effectively invisible to the circuit.
    
- Because Hi-Z presents extremely high resistance, **no current flows**, so multiple devices can be connected to the same line **as long as only one drives it at a time**.
    
- This enables shared-bus communication systems (e.g., memory buses, some digital protocols).
    
- The tri-state buffer uses MOSFET switches controlled by an **enable signal**:
    
    - EN = 1 → output is active (‘0’ or ‘1’)
        
    - EN = 0 → output is Hi-Z
        

**Comparison Table: Push-Pull vs Tri-State**

|Feature|Push-Pull|Tri-State|
|---|---|---|
|Possible states|‘0’, ‘1’|‘0’, ‘1’, **Hi-Z**|
|Can share line with others|❌ No|✅ Yes (if only one enabled)|
|Risk of short|High if multiple drivers|Avoided via Hi-Z|
|Use case|Simple GPIO output|Shared buses, multi-device lines|

**What you should know for the exam**

- Know the **definition** of the Hi-Z state and why it is essential.
    
- Understand the **MOSFET-based mechanism** that disconnects the pin.
    
- Be able to explain how tri-state logic **prevents short circuits** when multiple devices share a line.

![[All_slides_nes.pdf#page=85]]  
**Week 3 Slide 12 – GPIO Output States**  

**Notes**

- A GPIO’s output behavior is controlled by two internal signals:
    
    - **A** → the output value (‘0’ or ‘1’)
        
    - **EN** → the enable signal that determines whether the output driver is active
        
- This produces **three possible states**:
    
    1. **EN = 1, A = 1 → actively driven high**
        
    2. **EN = 1, A = 0 → actively driven low**
        
    3. **EN = 0 → Hi-Z (output disconnected)**
        
- This is how MCUs implement **tri-state functionality** on GPIO pins.
    
- When in Hi-Z, the pin does not affect the line; it can instead be **read** by the MCU or left floating unless external pull resistors set a default level.
    

**Concept clarity**

- EN acts like a _master switch_:
    
    - When EN is off, A no longer matters.
        
    - This is crucial for shared lines or when temporarily giving control to another device.
        

**What you should know for the exam**

- Understand the relationship between **A** and **EN** and how these two signals produce the three GPIO states.
    
- Be able to explain why Hi-Z is necessary for **safe multi-device connections**.
    
- Know that EN = 0 allows the pin to be used as an **input** or left floating for external circuitry to control.
![[All_slides_nes.pdf#page=86]]  
**Week 3 Slide 13 – GPIO Input and Input Hysteresis**  

**Notes**

- A GPIO input uses a **comparator**: it compares the pin voltage to a threshold to decide whether the input is ‘0’ or ‘1’.
    
- Typically, the threshold is around **(V_S/2)**.
    
- Problem: if the input voltage hovers near the threshold, **noise** can cause rapid switching between ‘0’ and ‘1’.
    
- Solution: **input hysteresis**, which introduces **two thresholds**:
    
    - To switch from **0 → 1**, voltage must exceed ((V_S/2) + V_H).
        
    - To switch from **1 → 0**, voltage must fall below ((V_S/2) - V_H).
        
- This creates a “dead band” where small fluctuations **do not** change the digital reading.
    
- Hysteresis dramatically improves stability for noisy or slowly changing signals (e.g., long wires, mechanical buttons without debouncing).
    

**Concept clarity**

- This is similar to how a thermostat avoids rapid on/off cycling by having separate temperature thresholds for heating and cooling.
    
- The input becomes immune to minor, fast disturbances.
    

**What you should know for the exam**

- Be able to **define hysteresis** and explain why it prevents spurious toggling.
    
- Know the meaning of the two thresholds and why they differ.
    
- Understand that hysteresis makes GPIO inputs **more robust to noise** and is common in real MCUs.

![[All_slides_nes.pdf#page=87]]  
**Week 3 Slide 14 – GPIO Input Mode**  

**Notes**

- This slide shows how the GPIO circuitry behaves when used as an **input** rather than an output.
    
- Key rule: **When EN = 1, the internal input signal (IN) simply equals A**, the logic level present on the pin.
    
    - In input mode, the MCU is _not_ driving the pin; instead, it is **sampling** the voltage on it.
        
- The diagram highlights that the pin’s logic level is determined by external circuitry (e.g., sensors, switches).
    
- No internal push-pull driving occurs in input mode; the pin must be given a valid high or low level externally or via pull resistors.
    

**Concept clarity**

- Think of EN as choosing whether the pin is “talking” (output) or “listening” (input).
    
- When listening, the pin must receive a clean signal from outside; otherwise, noise or floating behavior may occur (addressed in later slides).
    

**What you should know for the exam**

- Understand that **input mode disables the output driver**, allowing the pin voltage to be controlled externally.
    
- Know that the MCU reads the pin through an internal **comparator**.
    
- Recognize why floating inputs are problematic and require **pull resistors** (explained in upcoming slides).

![[All_slides_nes.pdf#page=88]]  
**Week 3 Slide 15 – Hardwired Input**  

**Notes**

- A **hardwired input** is a pin permanently tied to a fixed logic level (‘0’ or ‘1’) in the circuit.
    
- This input is **not meant to change** during operation.
    
- Typical uses:
    
    - **Permanent configuration** (e.g., selecting modes or enabling features).
        
    - **Device identification**:
        
        - Two MCUs may run the same firmware, but if one has Pin3 wired to ‘0’ and the other to ‘1’, the software can read the pin and know which board it is running on.
            
- This method avoids needing different code versions for different hardware variants.
    

**Concept clarity**

- Hardwired inputs act like **hardware constants**.
    
- They let the software adapt dynamically to the board’s wiring without needing external components or extra memory.
    

**What you should know for the exam**

- Know the purpose of a **hardwired input** and why it is used.
    
- Be able to explain how hardwired pins help with **board identification** or **permanent configuration settings**.
    
- Recognize that these inputs do **not change at runtime** and require no external driver circuitry.

![[All_slides_nes.pdf#page=89]]  
**Week 3 Slide 16 – Reading a Hi-Z Output**  

**Notes**

- A Hi-Z (high-impedance) output is **electrically disconnected** from the circuit.
    
- When you try to **read** a pin that is in Hi-Z, the voltage on the line is **not defined** because nothing is driving it.
    
- The pin can randomly register as ‘0’ or ‘1’ due to:
    
    - Ambient electrical noise
        
    - Capacitive coupling from nearby signals
        
    - Leakage currents
        
- This behavior is called a **floating input**.
    
- Floating inputs are **unreliable** and must be avoided when a stable digital value is required.
    

**Concept clarity**

- A Hi-Z pin behaves like a tiny **antenna**, easily picking up noise.
    
- Without a defined driving source or pull resistor, the voltage can wander unpredictably.
    

**What you should know for the exam**

- Be able to explain what happens when reading a **floating (Hi-Z) input**.
    
- Understand why a Hi-Z line provides **no guaranteed logic level**.
    
- Know that this issue motivates the use of **pull-up or pull-down resistors**, introduced next.

![[All_slides_nes.pdf#page=90]]  
**Week 3 Slide 17 – Reading a Hi-Z Output (Floating Input Explained)**  

**Notes**

- When the output is **disabled (Hi-Z)** and you attempt to read it, the input value is **undefined**.
    
- Because no circuit drives the line, the voltage can:
    
    - Drift to random levels
        
    - Flip between ‘0’ and ‘1’ unpredictably
        
    - Respond to tiny external electrical influences
        
- This is why a Hi-Z pin is described as **floating**.
    
- Floating inputs lead to **unstable behavior**, such as false triggers, random toggling, or noisy readings.
    

**Concept clarity**

- A floating pin has **no reference**—it tries to settle somewhere but even slight environmental interference changes its state.
    
- Reliable digital logic requires **defined voltage levels**, not arbitrary noise-influenced values.
    

**What you should know for the exam**

- Know the definition of a **floating input** and why it is unstable.
    
- Understand that **Hi-Z does not imply a known logic level**.
    
- Recognize that this problem is solved using **pull-up or pull-down resistors**, which set a default logic value.

![[All_slides_nes.pdf#page=91]]  
**Week 3 Slide 18 – Pullup and Pulldown Resistors**  

**Notes**

- Pull resistors give a **default logic level** when no device is actively driving the line.
    
- **Pullup resistor**:
    
    - Connects the line weakly to **‘1’**.
        
    - If nothing drives the line, it reads as **1**.
        
    - If an external device actively pulls the line low, that wins, because the pullup is weak.
        
- **Pulldown resistor**:
    
    - Connects the line weakly to **‘0’**.
        
    - If nothing drives the line, it reads as **0**.
        
- Key behavior of a pullup:
    
    - If the line is actively driven to ‘1’ → **no current flows** (both sides are at the same voltage).
        
    - If the line is actively driven to ‘0’ → **current flows through the resistor**, allowing the driven ‘0’ to dominate.
        
- MCUs often provide **internal pullups/pulldowns**, eliminating the need for external resistors in many designs.
    

**Concept clarity**

- Pull resistors ensure that a pin **never floats**.
    
- They are “weak” on purpose so that a real driver can easily override them.
    

**Comparison Table**

|Feature|Pullup|Pulldown|
|---|---|---|
|Default state|‘1’|‘0’|
|Connection|Line → Vcc through resistor|Line → GND through resistor|
|Overridden by|Driving ‘0’|Driving ‘1’|

**What you should know for the exam**

- Be able to explain why floating inputs are bad and how pull resistors fix the problem.
    
- Know the behavior of pullups vs pulldowns and how they interact with actively driven signals.
    
- Understand that pull resistors provide a **stable default** but do **not** act like strong drivers.

![[All_slides_nes.pdf#page=92]]  
**Week 3 Slide 19 – GPIO Output with Pullup**  

**Notes**

- When a GPIO has an **internal pullup resistor** and:
    
    - **EN = 0 (Hi-Z)** → the pullup sets the input level to **‘1’**.
        
    - **EN = 1 (output enabled)** → the output driver takes over and the input simply equals **A** (either 0 or 1).
        
- This allows a single pin to behave predictably even when the MCU is **not driving** it.
    
- Useful when the pin must:
    
    - Be read during startup before the MCU configures its direction
        
    - Avoid floating during tri-state phases
        
    - Cooperate with open-drain systems that rely on pullups
        

**Concept clarity**

- When EN=0, the pullup provides a **weak default**.
    
- When EN=1, the MCU provides a **strong drive**, overriding the pullup easily.
    

**What you should know for the exam**

- Understand how the pullup defines a default input when the pin is disabled.
    
- Know that when EN=1, the output driver has priority over the pull resistor.
    
- Be able to explain why pullups are essential in shared-line and open-drain configurations.
![[All_slides_nes.pdf#page=93]]  
**Week 3 Slide 20 – Multiple MCUs**  

**Notes**

- When multiple MCUs share the same physical line, it is **only safe if exactly one device drives the line at a time**.
    
- Even with pull resistors present, **push-pull outputs can still cause short circuits** if two devices accidentally drive opposite values simultaneously.
    
- The slide asks: _Is this safe enough?_
    
    - The answer is **no**—push-pull GPIOs remain risky in multi-device scenarios.
        
- This is why communication buses (I²C, 1-Wire, open-collector logic, etc.) use **open-drain** instead of push-pull:
    
    - Open-drain avoids direct conflicts because devices can only pull the line **low**, never drive it **high**.
        

**Concept clarity**

- A shared line must have a guaranteed rule that prevents two drivers from ever forcing conflicting voltages.
    
- Push-pull cannot guarantee this → open-drain is the safe alternative.
    

**What you should know for the exam**

- Know why **push-pull outputs are unsafe** on shared lines.
    
- Understand that even with pull resistors, **two push-pull drivers can still short the line**.
    
- Recognize that this leads directly to the need for **open-drain** outputs, covered in the next slide.

![[All_slides_nes.pdf#page=94]]  
**Week 3 Slide 21 – GPIO Output: Open-Drain Mode**  

**Notes**

- **Open-drain** (or open-collector) outputs have **only two states**:
    
    1. **Drive low (‘0’) — actively pull the line to ground**
        
    2. **Hi-Z — disconnect and let a pullup resistor bring the line high (‘1’)**
        
- Importantly, the MCU **never actively drives the line high**.
    
- A pullup resistor (internal or external) creates the ‘1’ state by default; devices only **pull the line low** when needed.
    
- Because no device ever drives the line high, **multiple devices can share the same line without risking a short circuit**:
    
    - If two devices pull low → line stays low (no conflict).
        
    - If one pulls low and others are Hi-Z → still safe.
        
- This is why open-drain is used for multi-device buses (e.g., **I²C SDA/SCL**, interrupt lines, wired-OR logic).
    

**Concept clarity**

- Open-drain = “I can pull low, but I never push high.”
    
- This guarantees that a conflict can _never_ create a Vcc–GND short.
    

**Comparison Table**

|Feature|Push-Pull|Open-Drain|
|---|---|---|
|Drives high?|Yes|No (pullup needed)|
|Drives low?|Yes|Yes|
|Hi-Z possible?|Yes (tri-state)|Yes|
|Safe for shared lines?|No|**Yes**|
|Risk of short?|High if multiple active drivers|**None** when pulling low|

**What you should know for the exam**

- Be able to clearly define **open-drain** and how its two states work.
    
- Understand why open-drain enables **safe multi-device communication**.
    
- Know the role of the **pullup resistor** in generating the high level.

![[All_slides_nes.pdf#page=95]]  
**Week 3 Slide 22 – Analog-to-Digital Converter (ADC)**  

**Notes**

- An **ADC** converts a continuously varying **analog voltage** into a **digital number** the MCU can process.
    
- The ADC measures the input voltage and maps it into one of **(2^M)** discrete values, where **M = bit resolution**.
    
    - Example: a **12-bit ADC** outputs values from **0 to 4095**.
        
- The image shows the ADC sampling the input voltage and outputting a digit that corresponds to the voltage level.
    
- ADCs are essential for sensors (temperature, light, pressure, microphones, etc.) because most real-world measurements are **analog**.
    

**Concept clarity**

- The ADC does **not** give exact voltages—only the nearest discrete step allowed by its resolution.
    
- Higher resolution → **more precise representation** of small voltage differences.
    
- Lower resolution → larger quantization steps → “rougher” measurements.
    

**What you should know for the exam**

- Know what an ADC does: **maps analog voltages to digital numbers**.
    
- Understand the meaning of **bit resolution** and how it sets the range of possible output values.
    
- Be able to explain why higher resolution gives **finer voltage detail**.
    
- Recognize why ADCs are required when interfacing with **analog sensors**.

![[All_slides_nes.pdf#page=96]]  
**Week 3 Slide 23 – Single-Ended ADC**  

### **What a Single-Ended ADC Does**

Measures the input voltage relative to ground:

$$  
V_{\text{measured}} = V_{in}  
$$

Valid input range:

$$  
0 \le V_{in} \le V_{ref}  
$$

Digital output range:

$$  
D_{out} \in [0,; 2^M - 1]  
$$

Saturation occurs when:

$$  
V_{in} > V_{ref}  
\quad\Rightarrow\quad  
D_{out} = 2^M - 1  
$$

---

### **Example: 12-bit ADC with (V_{ref} = 5,\text{V})**

|Input Voltage (V_{in})|Digital Output (D_{out})|
|---|---|
|$$0,\text{V}$$|$$0$$|
|$$2.5,\text{V}$$|$$2048$$|
|$$5,\text{V}$$|$$4095$$|
|$$6,\text{V}$$|$$4095 ;(\text{saturation})$$|

---

### **Key Idea**

The ADC divides the voltage range into discrete steps.  
Example resolution step size:

$$  
Q = \frac{V_{ref}}{2^M}  
$$

---

### **What you should know for the exam**

- Single-ended ADC measures **relative to ground**.
    
- Understand saturation when:  
    $$  
    V_{in} > V_{ref}  
    $$
    
- Know how the ADC maps voltages to:  
    $$  
    D_{out} = \frac{V_{in}}{V_{ref}}(2^M - 1)  
    $$
    
- Understand how choosing (V_{ref}) affects measurement detail.
    


![[All_slides_nes.pdf#page=97]]  
**Week 3 Slide 24 – Single-Ended ADC: Quantisation Error & Resolution**  

---

### **Core Concepts**

#### **Quantisation**

An ADC converts a continuous voltage into discrete steps.  
This introduces **quantisation error** because real voltages rarely align perfectly with step boundaries.

#### **Voltage Resolution (Q)**

The size of each voltage step is:

$$  
Q = \frac{V_{ref}}{2^M}  
$$

This means the ADC can only represent voltages in increments of (Q).  
Smaller (Q) → finer resolution.

---

### **Examples**

(Using the formula (Q = \frac{V_{ref}}{2^M}))

|Bit Resolution (M)|(V_{ref})|Resolution (Q)|
|---|---|---|
|12-bit|$$5,\text{V}$$|$$1.22,\text{mV}$$|
|12-bit|$$2.5,\text{V}$$|$$0.61,\text{mV}$$|
|8-bit|$$5,\text{V}$$|$$19.5,\text{mV}$$|
|8-bit|$$2.5,\text{V}$$|$$9.7,\text{mV}$$|

---

### **Trade-Off: Range vs Resolution**

Lower (V_{ref}):

- Smaller steps
    
- Better resolution
    
- But smaller measurable range
    

Higher (V_{ref}):

- Larger steps
    
- Worse resolution
    
- Larger measurable range
    

---

### **What you should know for the exam**

- Be able to compute resolution using:  
    $$  
    Q = \frac{V_{ref}}{2^M}  
    $$
    
- Understand why quantisation error occurs.
    
- Recognize the **trade-off** between measurement range and resolution.

![[All_slides_nes.pdf#page=98]]  
**Week 3 Slide 25 – ADC: Range vs Resolution**  

---

### **Problem Setup**

We have an **8-bit ADC** with:

$$  
2^8 = 256 \text{ levels}  
$$

and supply voltage:

$$  
V_{ref} = 5,\text{V}  
$$

Resolution:

$$  
Q = \frac{5}{256} = 19.5,\text{mV}  
$$

---

### **Case 1 — Measuring a signal in ([0,5],\text{V})**

This works normally:

- Entire ADC range is used
    
- Resolution is:
    

$$  
Q = 19.5,\text{mV}  
$$

---

### **Case 2 — Measuring a signal in ([0,1],\text{V})**

With the same (V_{ref} = 5,\text{V}), the ADC cannot represent small voltage differences well:

- Only values:  
    $$  
    D_{out} \in [0,; 52]  
    $$  
    are used, since:  
    $$  
    \frac{1\text{V}}{19.5\text{mV}} \approx 52  
    $$
    

Most of the ADC’s range is **wasted**.  
Resolution is too coarse.

---

### **Fix: Lower the reference voltage**

If we set:

$$  
V_{ref} = 1,\text{V}  
$$

Then:

$$  
Q = \frac{1}{256} = 3.9,\text{mV}  
$$

- Entire ADC range (0 \rightarrow 255) is used
    
- Much finer measurement resolution
    

---

### **What you should know for the exam**

- Resolution depends on both **bit depth** and **(V_{ref})**:  
    $$  
    Q = \frac{V_{ref}}{2^M}  
    $$
    
- Lowering (V_{ref}) **improves resolution** but reduces maximum measurable voltage.
    
- High range → worse resolution; low range → better resolution.

![[All_slides_nes.pdf#page=99]]  
**Week 3 Slide 26 – ADC: Range vs Resolution (Reflecting on the Slide Question)**  

---

### **Slide question:**

**“How can I measure a signal in ([4,5],\text{V}) with resolution (3.9,\text{mV})?”**

---

### **Direct answer (no repetition, just the reasoning the slide implies)**

To achieve a resolution of:

$$  
Q = 3.9,\text{mV}  
$$

you need:

$$  
V_{ref} = 1,\text{V} \quad (\text{for an 8-bit ADC})  
$$

because:

$$  
Q = \frac{1}{256} = 3.9,\text{mV}  
$$

**But:**  
With (V_{ref} = 1,\text{V}), you can only measure:

$$  
0 \le V_{in} \le 1,\text{V}  
$$

so the range ([4,5],\text{V}) is **not directly measurable**.

---

### **The insight the slide wants you to reach**

To measure only the **small variation** inside the 4–5 V window with high resolution, you must:

1. **Remove the 4–5 V DC offset**,
    
2. So that the ADC only sees a small ±0.5 V signal.
    

This turns the desired range:

$$  
[4,;5],\text{V}  
$$

into a centered, narrow range:

$$  
[-0.5,;+0.5],\text{V}  
$$

Then you can set:

$$  
V_{ref} = 0.5,\text{V}  
$$

and achieve:

$$  
Q = \frac{0.5}{256} \approx 2,\text{mV}  
$$

which meets the target resolution.

---

### **What enables this?**

A **differential ADC** (next slide).  
It lets you measure:

$$  
V_{diff} = V_{in} - V_{offset}  
$$

so you can “zoom in” on the small range you care about.

---

### **What you should know for the exam**

- To get high resolution over a small portion of a large voltage range, you must **subtract an offset** so the ADC only processes the small window.
    
- This offset-removal technique is fundamental to using **differential ADC inputs**.
    
- You cannot simply lower (V_{ref}) unless the signal itself is shifted into that smaller measurement window.

![[All_slides_nes.pdf#page=100]]  
**Week 3 Slide 27 – Differential ADC**  

---

### **Core Idea**

A **differential ADC** measures the voltage difference:

$$  
V_{diff} = V_A - V_B  
$$

This difference can be **positive or negative**.

---

### **Measurement Range**

A differential ADC with reference (V_{ref}) measures:

$$

- V_{ref} ;\le; V_{diff} ;\le; +V_{ref}  
    $$
    

Digital output range is:

$$  
D_{out} \in [-2^{M-1},; 2^{M-1}-1]  
$$

---

### **Saturation**

If:

$$  
V_A - V_B > V_{ref}  
$$

then:

$$  
D_{out} = 2^{M-1}-1  
$$

If:

$$  
V_A - V_B < -V_{ref}  
$$

then:

$$  
D_{out} = -2^{M-1}  
$$

---

### **Why differential is useful**

- It naturally removes **common-mode noise** (noise present on both inputs).
    
- It allows you to **subtract an offset voltage**, enabling high-resolution measurement of a small window inside a large voltage range.
    
- This answers the previous slide’s question: a differential ADC can isolate tiny variations by subtracting a fixed reference input.
    

---

### **Examples from the slide**

- $$V_A = 0,, V_B = 5 ;\Rightarrow; V_{diff} = -5 ;\Rightarrow; D_{out} = -2048$$
    
- $$V_A = 5,, V_B = 0 ;\Rightarrow; V_{diff} = +5 ;\Rightarrow; D_{out} = 2047$$
    
- $$V_A = 5,, V_B = 5 ;\Rightarrow; V_{diff} = 0 ;\Rightarrow; D_{out} = 0$$
    
- $$V_A = 3,, V_B = 2 ;\Rightarrow; V_{diff} = 1 ;\Rightarrow; D_{out} = 410$$
    

---

### **What you should know for the exam**

- Differential ADC measures **voltage differences**, not absolute voltages.
    
- Output range includes **positive and negative digital values**.
    
- Differential inputs allow **offset removal** and **noise rejection**.
    
- Understand how saturation works for both positive and negative extremes.

![[All_slides_nes.pdf#page=101]]  
**Week 3 Slide 28 – ADC: Removing a DC Offset**  

---

### **Goal**

Measure a signal in:

$$  
[4,\text{V},;5,\text{V}]  
$$

with high resolution:

$$  
Q = 3.9,\text{mV}  
$$

---

### **Problem**

Using an 8-bit ADC, obtaining (Q = 3.9,\text{mV}) requires:

$$  
V_{ref} = 1,\text{V}  
$$

But then the ADC can only measure:

$$  
0 \le V_{in} \le 1,\text{V}  
$$

so the range 4–5 V is **outside** the measurable window.

---

### **Solution: Subtract a DC Offset**

Apply a fixed offset voltage to the _negative_ ADC input:

$$  
V_B = 4.5,\text{V}  
$$

The differential ADC then measures:

$$  
V_{diff} = V_{in} - 4.5,\text{V}  
$$

This transforms the original range:

- If (V_{in} = 4,\text{V}):  
    $$  
    V_{diff} = -0.5,\text{V}  
    $$
    
- If (V_{in} = 5,\text{V}):  
    $$  
    V_{diff} = +0.5,\text{V}  
    $$
    

So the ADC now only needs to measure:

$$  
[-0.5,\text{V},;+0.5,\text{V}]  
$$

---

### **Choose a New Reference Voltage**

Set:

$$  
V_{ref} = 0.5,\text{V}  
$$

Resolution becomes:

$$  
Q = \frac{0.5}{256} = 1.95,\text{mV}  
$$

(which satisfies the needed precision).

---

### **Concept clarity**

- The ADC is not measuring the _absolute_ voltage anymore.
    
- It is measuring only the **small variations** around 4.5 V.
    
- This is exactly what differential ADCs are designed for.
    

---

### **What you should know for the exam**

- High-resolution measurement of a small voltage window requires **offset removal**.
    
- Differential ADCs allow measuring:  
    $$  
    V_{diff} = V_A - V_B  
    $$
    
- By choosing (V_B) as a fixed offset, the ADC “zooms in” on the small range of interest.
    
- Lowering (V_{ref}) is only useful if the signal is first shifted into the accessible measurement range.


![[All_slides_nes.pdf#page=102]]  
**Week 3 Slide 29 – ADC Channels**  

---

### **Core Idea**

Most MCUs include an internal ADC whose input can be connected to **multiple external pins**, called **ADC channels**.

Only **one channel** can be sampled at a time, even though many channels exist.

---

### **How it works**

- The MCU contains a **single ADC module**.
    
- A **multiplexer (MUX)** selects which external pin is routed to the ADC input.
    
- Example from the slide:
    
    - The nRF52832 has  
        $$  
        \text{AIN0, AIN1, ..., AIN7}  
        $$  
        meaning 8 possible analog inputs.
        
- The MCU switches between them in software, choosing the pin to read.
    

---

### **Why this matters**

- You can measure many analog signals with just **one ADC**.
    
- But because only one channel is active at a time, simultaneous measurements require **fast switching** or **scan mode** (later slide).
    
- Each channel must obey:  
    $$  
    0 \le V_{in} \le V_{ref}  
    $$  
    (or the differential rules if differential mode is supported).
    

---

### **What you should know for the exam**

- An MCU may have multiple **ADC channels**, but usually only **one physical ADC**.
    
- A **multiplexer** selects which channel is read.
    
- Understand that channels do **not** measure simultaneously unless explicitly supported by the architecture.
    
- Know that each channel corresponds to a physical pin that can be connected to external analog signals.

![[All_slides_nes.pdf#page=103]]  
**Week 3 Slide 30 – ADC Modes of Operation**  

---

### **One-Shot Mode**

Takes a **single sample** and stops.

$$  
\text{One measurement} \rightarrow \text{Done}  
$$

Used for slow-changing signals (battery voltage, temperature, configuration inputs).

---

### **Continuous Mode**

ADC samples **repeatedly** at a fixed sampling frequency:

$$  
f_s = \text{samples per second}  
$$

To avoid distortion, sampling must follow **Nyquist’s theorem**:

$$  
f_s \ge 2 f_{\text{max}}  
$$

where (f_{\text{max}}) is the highest frequency component in the input signal.

---

### **Oversampling Mode**

ADC samples **faster** than Nyquist and then averages:

- Reduces noise
    
- Improves effective resolution
    
- Smooths the signal
    

Mathematically, oversampling reduces quantisation noise roughly proportional to:

$$  
\sqrt{N}  
$$

where (N) is the number of samples averaged.

---

### **Scan Mode**

The ADC automatically cycles through multiple channels:

$$  
\text{AIN0} \rightarrow \text{AIN1} \rightarrow \ldots  
$$

This provides **multi-channel monitoring**, though still not simultaneous, just sequential and automatic.

---

### **What you should know for the exam**

- Definitions and use cases of **one-shot**, **continuous**, **oversampling**, and **scan** modes.
    
- Nyquist condition:  
    $$  
    f_s \ge 2 f_{\text{max}}  
    $$
    
- Why oversampling improves signal quality.
    
- Scan mode = automated sampling across multiple ADC channels in sequence.

![[All_slides_nes.pdf#page=104]]  
**Week 3 Slide 31 – Digital-to-Analog Converter (DAC)**  

---

### **Core Idea**

A **DAC** performs the opposite function of an ADC:

$$  
D_{in} ;\longrightarrow; V_{out}  
$$

It converts digital numbers into a **continuous analog voltage**.

---

### **What the DAC actually does**

Given a digital input value (D_{in}) in:

$$  
[0,;2^M - 1]  
$$

the DAC outputs a corresponding voltage:

$$  
V_{out} = \frac{D_{in}}{2^M - 1} , V_{ref}  
$$

This produces a smooth (or stepped) analog signal.

---

### **Applications**

- Audio output (speakers, headphones)
    
- Video generation
    
- Wireless communications (waveform synthesis)
    
- Motor control
    
- Digitally controlled potentiometers
    

Any system where the MCU must **generate a voltage level**, not just read one.

---

### **Concept clarity**

A DAC allows the MCU to produce signals such as ramps, sine waves, control voltages, or adjustable reference levels — things not possible with GPIO alone.

---

### **What you should know for the exam**

- DAC converts **digital → analog**.
    
- Know the output formula:  
    $$  
    V_{out} = \frac{D_{in}}{2^M - 1} , V_{ref}  
    $$
    
- Understand why DACs are essential for producing realistic analog signals.

![[All_slides_nes.pdf#page=105]]  
**Week 3 Slide 32 – Power Control**  

---

### **Core Idea**

We compare how **R1** affects the power delivered to **R2 (the load)** when placed in series.

---

### **Obsidian-Friendly Table Format**

| Case                | Relationship            | Effect on Current (I)              | Effect on Power in R1                   | Effect on Power in R2 (Load)           | Key Insight                    |
| ------------------- | ----------------------- | ---------------------------------- | --------------------------------------- | -------------------------------------- | ------------------------------ |
| **1. R- << R2**     | R1 much smaller than R2 | $$I \approx \frac{V}{R_2}$$        | Very small: $$P_1 = I^2 R_1 \approx 0$$ | Nearly full power delivered            | R1 barely affects the system   |
| **2. (R_1 >> R_2)** | R1 much larger than R2  | $$I \approx \frac{V}{R_1}$$ (tiny) | Very small (low current)                | Very small (load gets almost no power) | R1 blocks almost all power     |
| **3. (R_1 = R_2)**  | Equal resistances       | $$I = \frac{V}{2R_2}$$             | $$P_1 = I^2 R_1$$                       | $$P_2 = I^2 R_2$$                      | Half the power is wasted in R1 |

---

### **Concept clarity**

- Using resistors for power control wastes energy because R1 **converts power into heat**.
    
- Case 3 is especially bad because **the resistor wastes exactly as much power as the load receives**.
    
- This is why MCUs prefer **PWM**, which controls power **without** dissipating wasted energy.
    

---

### **What you should know for the exam**

- The three operating cases and their effects on current and power.
    
- Why resistor-based power control is **inefficient**.
    
- That this inefficiency motivates **PWM** for motor and LED control.

![[All_slides_nes.pdf#page=106]]  
**Week 3 Slide 33 – Dimming an LED**  

---

### **Notes**

- The LED is turned **on and off rapidly** at a frequency high enough that the human eye cannot detect the switching.
    
- The human visual system has **persistence** (a built-in low-pass filter), so it perceives the _average_ brightness rather than the instantaneous on/off state.
    
- By adjusting the **ratio of ON time to OFF time**, we control how bright the LED _appears_, even though the electrical signal is only ever fully ON or fully OFF.
    
- This principle is the foundation for **PWM dimming**.
    

---

### **Obsidian-Friendly Concept Summary**

|Idea|Explanation|
|---|---|
|Human eye filtering|Acts like a low-pass filter, blending fast changes into a smooth perception.|
|LED drive method|LED is not driven with analog voltage—just rapid on/off switching.|
|Perceived brightness|Determined by the fraction of time the LED is ON within each cycle.|

---

### **What you should know for the exam**

- Dimming is achieved through **fast toggling**, not lowering voltage.
    
- The human eye’s **low-pass filtering** makes PWM dimming appear smooth.
    
- The concept prepares for PWM parameters: **frequency** and **duty cycle** (next slide).

![[All_slides_nes.pdf#page=107]]  
**Week 3 Slide 34 – Pulse Width Modulation (PWM)**  

---

### **Notes**

PWM is an **on/off digital signal** defined by two parameters:

#### **1. Frequency**

How many times per second the full ON–OFF cycle repeats:

$$  
f = \frac{1}{T}  
$$

where (T) is the period of one full cycle.

#### **2. Duty Cycle**

The fraction of the period where the signal is **ON**:

$$  
\text{Duty cycle} = \frac{t_{\text{on}}}{T}  
$$

- A higher duty cycle → more average power delivered
    
- A lower duty cycle → less average power
    

The signal itself is always **fully ON (V_S)** or **fully OFF (0 V)**.  
The perceived or effective output is based on the **average** due to low-pass behavior (like the LED dimming from the previous slide).

---

### **Obsidian-Friendly Summary Table**

|Parameter|Meaning|Effect|
|---|---|---|
|**Frequency**|$$f = 1/T$$|Must be high enough to avoid visible flicker or motor chatter|
|**Duty Cycle**|$$DC = t_{on}/T$$|Controls _average_ power delivered|
|**Signal shape**|Digital on/off|Hardware stays efficient (no wasted heat like resistors)|

---

### **What you should know for the exam**

- PWM uses digital switching but achieves **analog-like control** of power.
    
- Frequency sets _how fast_ cycles repeat; duty cycle sets _how strong_ the average output is.
    
- MCU GPIOs can generate PWM directly.
    
- PWM avoids resistor-power waste by using efficient switching rather than voltage reduction.

![[All_slides_nes.pdf#page=108]]  
**Week 3 Slide 35 – PWM Motor Control**  

---

### **Notes**

- The **PWM duty cycle** controls how much **average power** is delivered to the motor.
    
- Motors are **inductive loads**, meaning they do **not** respond instantly to changes in current.
    
    - Instead of following the rapid ON/OFF switching, the motor’s current **smooths out** due to inductance.
        
    - This makes PWM ideal for motor control because the motor experiences a **steady average current**, not choppy pulses.
        

---

### **Why PWM Instead of a Variable Resistor?**

|Method|Problem / Behavior|
|---|---|
|**Variable resistor in series**|Wastes energy as heat; reduces efficiency; limits available power to the motor|
|**PWM**|Nearly zero wasted energy; motor receives the full supply voltage during ON phases; simple to generate with an MCU|

Electrical transistors (e.g., MOSFETs or drivers like DRV8835) act as **switches**, not as analog resistors, making PWM extremely efficient.

---

### **Concept clarity**

- A motor doesn’t care about instantaneous voltage—it reacts to **average current**, which PWM controls elegantly.
    
- PWM allows both **speed control** and **power efficiency**; the motor “filters” the high-frequency switching naturally.
    

---

### **What you should know for the exam**

- Motors are **inductive**, so they average PWM into a smooth current.
    
- PWM avoids the inefficiency of resistor-based control.
    
- Duty cycle directly controls motor speed because it controls **average delivered power**.

---
---
---


Here are **5 multiple-choice questions** covering the full Week 3 slide set.  
(As requested: **no answers provided yet**.)

---

### **Question 1 — GPIO Output Modes**

Which statement about **push-pull vs open-drain** outputs is correct?

A. Push-pull outputs can safely share a line with multiple devices without risk of short circuits.  
B. Open-drain outputs require a pullup resistor to generate a logical ‘1’.  
C. Open-drain outputs actively drive both ‘0’ and ‘1’.  
D. Push-pull outputs can only drive a ‘0’, not a ‘1’.

---

### **Question 2 — ADC Resolution**

A 12-bit ADC with (V_{ref} = 3.3,\text{V}) has a voltage resolution:

A. (Q = \frac{3.3}{4096})  
B. (Q = \frac{3.3}{256})  
C. Always (1,\text{mV}), regardless of (V_{ref})  
D. Equal to the quantisation error of a differential ADC only

---

### **Question 3 — Floating Inputs**

A GPIO pin configured as an input with **no pull resistor** and **no external driver** will:

A. Always read as ‘0’  
B. Always read as ‘1’  
C. Produce undefined readings influenced by noise  
D. Remain in a safe, stable Hi-Z state with a known voltage

---

### **Question 4 — Differential ADC**

A differential ADC measures:

A. The absolute voltage of each input separately  
B. (V_A - V_B), allowing both positive and negative values  
C. Only voltages above (V_{ref})  
D. Only voltages below ground

---

### **Question 5 — PWM**

Which statement about PWM is true?

A. PWM varies the analog voltage level directly using a DAC.  
B. PWM uses resistor networks to control average power efficiently.  
C. Duty cycle determines the average delivered power.  
D. Increasing frequency increases the output voltage amplitude.

---

When you're ready, say **“give answers”** and I will provide the correct choices with explanations.


WEEK 4 NOTES


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


WEEK 5 NOTES


![[All_slides_nes.pdf#page=152]]  
**Week 5 Slide 3 – Serial Communication**  

---

### **What Serial Communication Is**

Serial communication means sending **bits one after another** over a single wire (plus ground).  
Only **one bit is on the line at a time**, unlike parallel communication where many bits are sent simultaneously.

---

### **How Bits Are Represented**

- A **voltage level** encodes each bit.
    
    - High voltage → logical **1**
        
    - Low voltage → logical **0**
        

This is the most basic building block of digital communication.

---

### **Key Idea of the Slide**

Serial communication sends data in a **sequence of bits over one wire**, with voltage levels representing binary values. This simplicity makes serial links cheap and widely used in embedded systems.

![[All_slides_nes.pdf#page=153]]  
**Week 5 Slide 4 – Timing the Receiver**  

---

## **Core Problem: When Should the Receiver Read the Line?**

The receiver can detect changes in the input voltage, but **it does not know exactly when the transmitter placed each bit on the wire**.

Because of this, two issues appear:

### **1. Sampling Frequency**

- How often should the receiver check the voltage?
    
- If it samples too slowly → it may miss bit transitions.
    
- If it samples too quickly → noise may cause false bit readings.
    

---

### **2. Interpreting the Voltage**

The slide shows two possible interpretations of the same voltage waveform:

- **bin1** → one sequence of binary values
    
- **bin2** → a _different_ sequence
    
- **Both interpretations could fit the same analog waveform** if timing is unknown.
    

---

## **Key Point**

Without a shared notion of _when_ each bit starts and ends, the receiver **cannot correctly decode the bits**.

This sets up the need for **synchronization** between transmitter and receiver, introduced in the next slide.


![[All_slides_nes.pdf#page=154]]  
**Week 5 Slide 5 – Timing the Receiver (Need for Synchronisation)**  

---

## **Why Timing Alone Is Not Enough**

This slide continues the problem from Slide 4:  
Even if the receiver watches the line carefully, it **still cannot know**:

- When exactly each bit begins
    
- How long each bit lasts
    
- Whether the sampled voltage corresponds to a 1 or a 0 at that moment
    

The waveform can still be interpreted as **bin1** _or_ **bin2**, and nothing ensures the receiver chooses the correct one.

---

## **Conclusion Stated on the Slide**

> _“We can’t know for sure! We need a way to synchronise the transmitter and the receiver!”_

This tells us that **timing must be coordinated** so both sides agree on:

- Bit boundaries
    
- When sampling should occur
    
- The duration of each bit
    

---

## **Key Concept**

Accurate serial communication **cannot work reliably without synchronization**.  
This problem motivates the introduction of **asynchronous serial communication framing** (start bit, stop bit, baud rate), which comes next.

![[All_slides_nes.pdf#page=155]]  
**Week 5 Slide 6 – Asynchronous Serial Communication**  

---

## **What “Asynchronous” Means**

The transmitter and receiver **do not share a clock signal**.  
Instead, they agree on a **baud rate** (bits per second), and use framing bits to stay synchronized during each transmission.

---

## **How Synchronisation Works Without a Shared Clock**

### **1. Idle Line = ‘1’**

When nothing is being sent, the line stays high.  
This helps the receiver detect when a new frame begins.

---

### **2. Start Bit**

- Transmission begins by forcing the line to **0**.
    
- This falling edge tells the receiver:  
    **“A new frame starts now—start your timing.”**
    

---

### **3. Data Bits**

- Sent at the agreed baud rate (e.g., 9600 baud).
    
- Typically **LSB first** (least significant bit first).
    
- Length is usually 8 bits but can be 5–9 bits depending on configuration.
    

---

### **4. Optional Parity Bit**

Used for simple error detection:

- **Even parity:** total number of 1s must be even
    
- **Odd parity:** total number of 1s must be odd
    

Optional because it slows the link but helps in noisy environments.

---

### **5. Stop Bit(s)**

- 1 or 2 bits of **‘1’** at the end.
    
- Allows the receiver time to recover before the next frame.
    

---

## **The Common Format: 8N1**

- **8** data bits
    
- **N** parity (none)
    
- **1** stop bit
    

This is the **default UART format** in most embedded systems.

---

## **Figure Explanation: ASCII ‘a’ in 8N1**

The slide shows the serial frame for the ASCII character **‘a’** (0x61):

- Start bit → **0**
    
- Data bits (LSB first) → **1 0 0 0 0 1 1 0**
    
- Stop bit → **1**
    

---

## **Key Concept**

Asynchronous serial communication solves the timing problem by embedding synchronization information **inside each frame**, instead of requiring a shared clock.

![[All_slides_nes.pdf#page=156]]  
**Week 5 Slide 7 – Error Detection: Parity**  

w5-serial-communication_251006_…

---

## **What Parity Is**

Parity is a simple form of **error detection** used in asynchronous serial communication.

A **parity bit** is added after the data bits to detect if one bit was corrupted during transmission.

---

## **Types of Parity**

### **Even Parity**

- The number of ‘1’ bits (including the parity bit) must be **even**.
    

### **Odd Parity**

- The number of ‘1’ bits (including the parity bit) must be **odd**.
    

---

## **What Parity Detects**

Parity can detect **any single-bit error**.  
If exactly one bit flips during transmission:

- The parity no longer matches the expected rule
    
- The receiver knows the frame was corrupted
    

---

## **Limitations**

- Cannot detect _all_ errors
    
- If _two_ bits flip, parity will not notice
    
- Adds overhead (extra bit)
    
- Often disabled in modern embedded systems because links are short and reliable
    

---

## **Why It Matters**

Parity is an optional safety feature that provides **basic protection** against noise in the physical medium.

![[All_slides_nes.pdf#page=157]]  
**Week 5 Slide 8 – Bidirectional Asynchronous Serial Communication**  

---

## **Full-Duplex vs Half-Duplex vs Simplex**

This slide explains the **directionality** of asynchronous serial links.

---

## **1. Full-Duplex Communication**

- Data can flow **in both directions at the same time**.
    
- Requires **two separate data wires**:
    
    - TX (transmit)
        
    - RX (receive)
        
- This is how a typical UART works.
    

### **Use Case**

MCU ↔ PC communication  
(both can send messages whenever they want)

---

## **2. Half-Duplex Communication**

- Data flows in **both directions**, but **not at the same time**.
    
- Direction changes depending on who is sending.
    
- Often uses a **single shared wire**.
    

### **Use Case**

Protocols like RS-485 in industrial networks.

---

## **3. Simplex Communication**

- **One-way only**.
    
- The receiver never sends data back.
    

### **Use Case**

Sensor → MCU streams  
like data loggers or GPS receivers.

---

## **Figure Explanation**

The slide’s diagram shows:

- **Full duplex:** two arrows in opposite directions
    
- **Half duplex:** one wire with alternating direction
    
- **Simplex:** single-direction arrow
    

This visually differentiates the three communication modes.

---

## **Key Concept**

Asynchronous serial lines can support multiple communication styles depending on wiring and application requirements.

![[All_slides_nes.pdf#page=158]]  
**Week 5 Slide 9 – Implementation of Asynchronous Serial Communication**  

---

## **Two Ways to Implement Asynchronous Serial Communication**

This slide compares **software-based** and **hardware-based** implementations of UART-style communication.

---

# **1. Software Implementation (Bit Banging)**

### **How It Works**

- The CPU manually:
    
    - Sets the TX line high/low for each bit
        
    - Times the duration of each bit
        
    - Reads the RX line at the correct sampling times
        

### **Characteristics**

- Requires **tight timing control** in software
    
- CPU must be active continuously
    
- Very **inefficient**
    
- Difficult to maintain precise baud timing
    
- Still useful when **no hardware UART is available**
    

### **Typical Use Case**

Simple MCUs or GPIO-only communication where hardware support is missing.

---

# **2. Hardware Implementation (Using the UART Peripheral)**

### **How It Works**

- The microcontroller includes a **dedicated UART peripheral** that:
    
    - Automatically handles start bits, stop bits, and sampling
        
    - Generates/parses data frames
        
    - Manages TX and RX buffers
        
    - Raises interrupts when ready
        

### **Characteristics**

- **Much more efficient**
    
- **Accurate timing** regardless of CPU load
    
- Supports higher baud rates
    
- CPU only processes bytes—not individual bits
    

### **Typical Use Case**

All modern microcontrollers for reliable, low-overhead serial communication.

---

## **Figure Explanation**

The left diagram shows the **CPU manually toggling pins**, while the right shows a **UART block** connected to TX/RX pins, illustrating how hardware offloads nearly all the work.

---

## **Key Concept**

Software serial is possible but inefficient.  
Whenever available, **hardware UART** is the correct choice in embedded systems.

---

## **Software vs Hardware Implementation (Bit-Banging vs UART Peripheral)**

|Feature|**Software UART (Bit Banging)**|**Hardware UART Peripheral**|
|---|---|---|
|**Who handles timing?**|CPU must generate exact bit timing|Dedicated UART hardware handles timing|
|**CPU load**|Very high (CPU busy each bit)|Very low (CPU handles bytes only)|
|**Timing accuracy**|Poor; depends on instruction timing and interrupts|Excellent; stable and reliable|
|**Baud rate capability**|Low to moderate|High baud rates supported|
|**Energy efficiency**|Poor (CPU cannot sleep)|Good (UART works independently)|
|**Complexity to implement**|High; requires careful timing loops|Low; just configure registers|
|**Use cases**|When no UART peripheral exists|Normal operation in modern MCUs|
|**Reliability**|Sensitive to jitter, CPU load, interrupts|Much more robust and predictable|
|**Interrupt support**|Must be done manually|Built-in TX/RX interrupts|
|**Overall recommendation**|Only as a fallback|Always preferred|

![[All_slides_nes.pdf#page=159]]  
**Week 5 Slide 10 – Example of a UART Peripheral**  

---

## **Purpose of the Slide**

This slide shows a **real-world UART peripheral** example from a sensor device, illustrating how UART is often used for **command/control interfaces** using ASCII text.

---

## **What the Example Shows**

The slide references a sensor (from the _CoZIR datasheet_) that exposes a UART interface supporting:

### **ASCII-Based Commands**

- Commands sent as **text strings** over UART
    
- Easy for humans to read and debug
    
- E.g., sending `"G\r"` might request a measurement
    
- Responses also come back as ASCII text (e.g., `"21.5\r"`)
    

---

## **Role of UART in This Device**

The UART acts as:

- A **control channel** for configuring the sensor
    
- A **data channel** for receiving readings
    
- A simple and universal interface usable from MCUs, PCs, or test equipment
    

---

## **Figure Explanation**

The image shows:

- A UART-connected sensor module
    
- TX/RX lines used for communication
    
- Example ASCII commands printed on the slide
    

It demonstrates how UART is used outside the MCU world—many peripherals expose UART for configuration or measurement output.

---

## **Key Concept**

UART is widely used for **human-readable command interfaces**, not just raw binary data.  
This makes debugging and integration easier in embedded systems.

![[All_slides_nes.pdf#page=161]]  
**Week 5 Slide 12 – UART Cannot Be Shared (Why Synchronisation Alone Doesn’t Solve It)**

---

## **Core Message of the Slide**

UART **cannot** be shared between multiple devices because the electrical design of UART outputs makes it unsafe and unreliable to connect more than one transmitter to the same line.

This slide emphasises the **hardware limitation**, not just a protocol limitation.

---

## **Why UART Cannot Be Shared**

### **1. UART Uses Push-Pull Outputs**

- A transmitter actively drives the line **high** or **low**.
    
- If two transmitters drive the line at the same time:
    
    - One may drive **high**, another **low**
        
    - This creates a **short-circuit** condition
        
    - Can cause **hardware damage** and **communication failure**
        

This is shown in the diagram: two TX pins tied together → unsafe.

---

### **2. UART Is Designed for _Point-to-Point_**

- Only **one transmitter** and **one receiver**
    
- No addressing, no arbitration
    
- No mechanism to let multiple devices share the medium
    

UART is fundamentally unlike I2C (open-drain) or SPI with chip-selects.

---

### **3. Even Multiple Receivers Are Not Proper Sharing**

The slide notes that connecting one TX to multiple RX devices is technically safe, **but not a real bus**:

- All receivers get the same data
    
- No way to choose which receiver should act
    
- Still not compliant with UART’s intended use-case
    

---

## **Key Takeaway**

> **UART cannot be shared because multiple transmitters electrically conflict and the protocol has no support for arbitration or addressing.**

Only one device can safely drive a UART TX line. Any design requiring more nodes must use a different interface (SPI, I2C, RS-485, CAN, etc.).

![[All_slides_nes.pdf#page=162]]  
**Week 5 Slide 13 – UART Cannot Be Shared (Multiple Receivers)**

---

## **Purpose of the Slide**

This slide expands on the previous one by explaining the **only scenario** where UART _seems_ shareable:  
→ **One transmitter feeding multiple receivers**.

But it also clarifies why this is still **not proper UART usage**.

---

## **Key Points**

### **1. Multiple UART Receivers Are Electrically Safe**

- RX pins are **inputs**, so connecting many of them to a single TX line:
    
    - Does **not** damage hardware
        
    - Does **not** cause contention
        
- The diagram shows one TX → two RX lines, which is electrically fine.
    

---

### **2. BUT Communication Still Fails Logically**

Even though the wiring is safe, UART cannot distinguish receivers:

- **The transmitter cannot select a receiver**
    
- **All receivers get the same bytes**
    
- No addressing, no filtering, no bus protocol
    

So the system behaves like a **broadcast-only** channel.

---

### **3. Why This Is Not Proper UART Use**

- UART was never designed to support multiple receivers
    
- No mechanism for:
    
    - Addressing
        
    - Arbitration
        
    - Per-device communication
        
- Each receiver must treat every frame as if it were meant for it  
    → In most applications, this is **unacceptable**.
    

---

### **4. The Slide’s Note: “It may work in some applications”**

This means:

- If your application intentionally uses broadcast-only data  
    (e.g., one MCU sending a debug stream to multiple listeners)
    
- Then this setup can be acceptable.
    

But it is still not a general-purpose bus.

---

## **Key Takeaway**

> **You can connect one UART transmitter to multiple receivers, but it is not real multi-device communication. All receivers hear everything, and no device can be individually addressed.**

This is why UART is considered a **point-to-point protocol**, unlike SPI or I2C.

![[All_slides_nes.pdf#page=163]]  
**Week 5 Slide 14 – Synchronous Serial Communications**

---

## **Purpose of the Slide**

This slide introduces **synchronous serial communication**, where devices share a **clock line** to solve the timing/synchronisation issues inherent in UART.

---

## **What Synchronous Serial Means**

Unlike asynchronous serial (UART), synchronous communication uses a **shared clock signal**:

- One device acts as the **controller** (or master)
    
- The controller generates the **clock (CLK)**
    
- All devices synchronise their transmit/receive actions to this clock
    

This solves the problem of _“when should the receiver sample the data?”_ because the clock tells it exactly when to do so.

---

## **How Data Is Transmitted**

### **Clock Edges Define Timing**

- Data is put on the line (driven) on either:
    
    - The **falling edge** of the clock
        
    - Or the **rising edge** (depending on mode)
        
- Data is sampled (read) on the opposite edge
    

This ensures both sides agree precisely on bit boundaries.

---

## **Advantages of Synchronous Serial**

### **1. No Need to Pre-Agree on a Baud Rate**

The clock controls timing, so:

- No drift problems
    
- No baud mismatch issues
    

---

### **2. No Start/Stop Bits**

Since timing is explicit, there is:

- No need for start bits
    
- No need for stop bits
    
- **No overhead per byte → higher efficiency**
    

---

### **3. Simpler Hardware Than UART**

UART requires:

- Asynchronous sampling
    
- Frame detection
    
- Oversampling logic
    

Synchronous protocols are simpler—data changes are tied directly to the clock.

---

## **Diagram Explanation**

On the slide:

- The controller provides **CLK**, **TX**, and **RX** lines.
    
- Devices synchronise transmissions to the same clock waveform.
    
- The timing graphic shows:
    
    - Clock oscillating
        
    - Data bits aligned exactly to clock transitions
        
    - Sampling occurring at a consistent edge
        

---

## **Key Takeaway**

> **Synchronous serial solves timing uncertainty by sharing a clock.  
> It is more efficient and simpler than UART but requires extra wiring (a clock line).**

This concept leads directly into SPI, introduced next.

![[All_slides_nes.pdf#page=164]]  
**Week 5 Slide 15 – SPI (Serial Peripheral Interface)**

---

## **Purpose of the Slide**

This slide introduces **SPI**, the most widely used synchronous serial protocol in embedded systems.  
SPI uses a dedicated clock and two data lines to support **fast, full-duplex** communication.

---

## **SPI Signals**

### **1. SCLK — Serial Clock**

- Generated by the **SPI controller (master)**
    
- Determines the communication speed (typically MHz)
    
- All peripherals must support the chosen frequency
    

---

### **2. MOSI — Master Out, Slave In**

- Data flowing **from controller → peripheral**
    

---

### **3. MISO — Master In, Slave Out**

- Data flowing **from peripheral → controller**
    

---

## **Full-Duplex Operation**

SPI is inherently **full-duplex**:

- On **every** clock pulse:
    
    - Controller writes 1 bit to the peripheral (via MOSI)
        
    - Peripheral writes 1 bit to the controller (via MISO)
        

Even if only one direction is logically needed, both lines shift bits simultaneously.

---

## **How Data Shifting Works**

- Each rising or falling clock edge (depending on SPI mode):
    
    - Moves shift registers in both devices
        
    - Causes one new bit to be output and one to be read
        

This makes SPI extremely fast and predictable.

---

## **Diagram Explanation**

The slide’s timing diagram shows:

- A shared clock waveform
    
- Bits being output on MOSI and MISO at each edge
    
- The controller and peripheral shifting data at the same pace
    

---

## **Key Characteristics of SPI**

- **Fast** (1–20+ MHz common)
    
- **Full-duplex** (unlike I2C)
    
- **Simple protocol** (no addressing)
    
- Requires **more wires** than I2C
    
- Requires additional **chip-select** lines (introduced next slide)
    

---

## **Key Takeaway**

> **SPI provides fast, clock-synchronised, full-duplex communication using SCLK, MOSI, and MISO.  
> It is simple, predictable, and widely used for sensors, displays, memory chips, and more.**


---

![[All_slides_nes.pdf#page=165]]  
**Week 5 Slide 16 – SPI Modes (CPOL & CPHA)**

---

## **SPI Mode Parameters in Table Form**

### **CPOL – Clock Polarity (Idle State of SCLK)**

|**CPOL Value**|**Clock Idle Level**|**Leading Edge**|**Trailing Edge**|
|---|---|---|---|
|**0**|0 (low)|Rising|Falling|
|**1**|1 (high)|Falling|Rising|

---

### **CPHA – Clock Phase (When Data Is Sampled vs Changed)**

|**CPHA Value**|**Data Is Sampled On**|**Data Is Changed On**|
|---|---|---|
|**0**|Leading edge|Trailing edge|
|**1**|Trailing edge|Leading edge|

---

## **Combined SPI Modes**

|**SPI Mode**|**CPOL**|**CPHA**|**Clock Idle Level**|**Data Sampled On**|**Data Changed On**|
|---|---|---|---|---|---|
|**0**|0|0|Low|Rising (leading)|Falling (trailing)|
|**1**|0|1|Low|Falling (trailing)|Rising (leading)|
|**2**|1|0|High|Falling (leading)|Rising (trailing)|
|**3**|1|1|High|Rising (trailing)|Falling (leading)|

---

## **Key Takeaway**

> **CPOL sets the idle level of the clock.  
> CPHA sets which clock edge samples data.  
> The four SPI modes are combinations of these two parameters.**


![[All_slides_nes.pdf#page=166]]  
**Week 5 Slide 17 – SPI: Chip Select (CS)**

---

## **Purpose of the Slide**

This slide explains how the **Chip Select (CS)** line lets the SPI controller choose which device to communicate with.  
CS ensures that only one peripheral is active on the SPI bus at any time.

---

## **Chip Select Behaviour**

### **1. CS Active Low**

- SPI peripherals are activated when **CS goes from high → low**
    
- This falling edge tells the peripheral to:
    
    - Wake up
        
    - Prepare to shift data
        
    - Pay attention to SCLK and MOSI
        

---

### **2. CS Deactivation**

- When CS transitions **low → high**:
    
    - The peripheral **deactivates**
        
    - It places its **MISO output into Hi-Z (high-impedance)**  
        → prevents interference with other devices
        
    - It ignores all further SCLK/MOSI activity
        

---

## **Why CS Is Required**

- SPI has **no addressing** (unlike I2C)
    
- All peripherals share SCLK, MOSI, MISO
    
- CS is the **only mechanism** to select a specific peripheral
    

---

## **Pull-Up Recommendation**

The slide notes:

- A **pull-up resistor** on CS is recommended because:
    
    - Many MCUs boot with GPIOs in a Hi-Z state
        
    - Without a pull-up, CS might float low and accidentally activate the peripheral during boot
        

---

## **Diagram Explanation**

The figure shows:

- CS lines controlling when devices listen or ignore communication
    
- MISO going high-impedance on CS high
    
- How enabling/disabling a peripheral prevents bus contention
    

---

## **Key Takeaway**

> **Chip Select ensures only one SPI peripheral is active.  
> When CS is high, the device disconnects from the bus (Hi-Z).  
> When CS goes low, the device becomes active and communicates.**

![[All_slides_nes.pdf#page=167]]  
**Week 5 Slide 18 – SPI: Multiple Peripherals**

---

## **Purpose of the Slide**

This slide explains how SPI supports **multiple peripherals** by giving each device its own **Chip Select (CS)** line.  
All peripherals share the **same SCLK, MOSI, and MISO**, but only the device with its CS pulled low is active.

---

## **How Multiple SPI Devices Are Connected**

|**Line**|**Shared or Unique?**|**Purpose**|
|---|---|---|
|**SCLK**|Shared|Clock from controller to all peripherals|
|**MOSI**|Shared|Data from controller to all peripherals|
|**MISO**|Shared|Data from peripherals to controller|
|**CS**|**One per peripheral**|Used to activate a single peripheral at a time|

---

## **Key Requirements**

### **1. Only One Device Active at a Time**

- The controller must ensure that **only one CS is low**
    
- All other peripherals must remain inactive (CS high → MISO in Hi-Z)
    
- Prevents bus contention on the MISO line
    

---

### **2. SPI Communication Is Always Controller ↔ One Peripheral**

- No communication between peripherals
    
- Always point-to-point, selected via CS
    

---

## **GPIO Usage**

SPI needs:

- **3 fixed lines**: SCLK, MOSI, MISO
    
- **+1 extra GPIO per peripheral** for its CS
    

Example: 5 SPI devices require **3 + 5 = 8 pins**.

---

## **Diagram Explanation**

The slide’s image shows:

- All devices sharing SCLK, MOSI, MISO
    
- Individual CS lines branching from the controller
    
- Only the selected device driving MISO; others remain disconnected
    

---

## **Key Takeaway**

> **SPI supports many peripherals, but each needs its own Chip Select line.  
> Only one peripheral may be selected at a time to avoid conflicts on the shared bus.**

![[All_slides_nes.pdf#page=168]]  
**Week 5 Slide 19 – SPI: Daisy Chain**

---

## **Purpose of the Slide**

This slide introduces an alternative wiring method for SPI peripherals called a **daisy chain**, where devices are connected in a loop rather than all sharing the same MISO line.

---

## **How Daisy-Chain SPI Works**

Instead of each peripheral having its own MISO line back to the controller, the devices are connected in a sequence:

|**Connection**|**Description**|
|---|---|
|Controller MOSI → Peripheral 1 Input|First device receives the controller’s data|
|Peripheral 1 Output → Peripheral 2 Input|Device forwards bits to the next device|
|... continues|Each device passes data to the next|
|Last Peripheral Output → Controller MISO|Final device sends the combined shifted data back|

This creates a **circular shift-register-like path** for data.

---

## **Key Characteristics**

### **1. All Peripherals Are Active Together**

- Daisy-chain operation requires **every** device to be enabled at the same time
    
- No individual chip select per device
    
- CS typically controls **the entire chain**
    

---

### **2. Each Peripheral Shifts Data Forward**

- Every clock pulse moves bits through the chain
    
- Example:
    
    - Peripheral 1 receives bit 0 from MOSI and outputs bit -1 to Peripheral 2
        
    - Peripheral 2 outputs bit -2 to Peripheral 3
        
    - Eventually → controller receives a bit from the end of the chain
        

It behaves like one long combined shift register.

---

### **3. Fewer Pins Required**

|Configuration|CS Pins Needed|
|---|---|
|**Traditional SPI**|1 per device|
|**Daisy Chain**|1 total|

This can dramatically reduce GPIO usage.

---

### **4. Trade-Off: All Devices Must Participate**

- Even if you need to control **only one** peripheral:
    
    - All peripherals must shift data simultaneously
        
- Devices must support daisy-chain mode; not all SPI devices do
    

---

## **Diagram Explanation**

The slide shows:

- A controller on the left
    
- Daisy-chained peripherals forming a ring
    
- Single CS controlling the chain
    
- Data flowing around the loop
    

---

## **Key Takeaway**

> **Daisy-chain SPI reduces the number of required CS lines, but all peripherals must shift data together.  
> It is useful for devices designed to operate as chained shift registers (e.g., LED drivers, some DACs).**


![[All_slides_nes.pdf#page=169]]  
**Week 5 Slide 20 – Example of an SPI Peripheral**

---

## **Purpose of the Slide**

This slide shows a **real device** that communicates over SPI:  
the **ADXL362**, a 3-axis accelerometer.  
The goal is to link the theoretical SPI concepts to an actual hardware example.

---

## **What the ADXL362 Demonstrates**

### **1. It Uses SPI as Its Communication Interface**

- All configuration and data reads happen through SPI
    
- The MCU acts as the SPI controller
    
- The ADXL362 is the SPI peripheral (target)
    

---

### **2. It Exposes a Command/Control Interface**

Using SPI, the MCU can:

- Read acceleration measurements
    
- Configure sensitivity ranges
    
- Configure sample rates
    
- Access registers inside the device
    

The communication is **register-based**, meaning SPI frames map to specific internal registers.

---

## **Key SPI Features Used by This Peripheral**

|Feature|How the ADXL362 Uses It|
|---|---|
|**Chip Select (CS)**|Enables the device before any SPI transaction|
|**MOSI**|MCU sends register addresses and write data|
|**MISO**|ADXL362 returns measurement and register data|
|**Full-duplex shifting**|Command bytes go to the device while response bits shift back|

---

## **Diagram Explanation**

The slide image shows:

- The ADXL362 sensor module
    
- Wiring pins for SPI (SCLK, MOSI, MISO, CS)
    
- A simplified block diagram of the sensor’s digital SPI logic
    

This visually reinforces how a real SPI peripheral fits into the system.

---

## **Key Takeaway**

> **The ADXL362 accelerometer is an example of a sensor that uses SPI for fast, reliable register-based communication.  
> SPI allows the MCU to configure the device and read measurements efficiently.**

![[All_slides_nes.pdf#page=170]]  
**Week 5 Slide 21 – Synchronous Serial with Less Wires**

---

## **Purpose of the Slide**

This slide raises the question:  
**SPI is fast and simple, but it uses too many GPIO pins.  
How can we reduce the wiring?**

It prepares for the introduction of **I2C**, which solves this problem.

---

## **Problem with SPI: Too Many Pins**

SPI requires:

- **SCLK**
    
- **MOSI**
    
- **MISO**
    
- **1 CS per peripheral**
    

This means:

|Number of SPI Peripherals|Total Pins Needed|
|---|---|
|1|4 pins|
|2|5 pins|
|5|8 pins|
|10|13 pins|

MCUs often run out of GPIOs when many SPI devices are attached.

---

## **Key Limitations of SPI Highlighted on This Slide**

### **1. Fast and Cheap Hardware, But Not Scalable**

- SPI works very well at high speeds
    
- Hardware is simple
    
- But adding many peripherals becomes impractical because of the **CS pins**
    

---

### **2. Practical Limit on Number of Peripherals**

Even though SPI can theoretically support many devices,  
the **chip-select wiring** becomes the bottleneck.

---

## **Leading Question**

The slide ends with:

> **“How can we reduce the number of required GPIOs?”**

The upcoming slide (Slide 22) answers this by hinting at the ideas behind I2C:

- Eliminate chip-select lines
    
- Use a shared bus
    
- Use addressing instead of dedicated CS wires
    

---

## **Key Takeaway**

> **SPI is fast but doesn’t scale well because it requires too many pins.  
> We need a serial protocol that supports multiple peripherals with fewer wires → this leads to I2C.**


![[All_slides_nes.pdf#page=171]]  
**Week 5 Slide 22 – Synchronous Serial with Less Wires (Concepts Leading to I2C)**

---

## **Purpose of the Slide**

This slide introduces the **two key ideas** needed to reduce wiring in synchronous serial communication.  
It continues the transition from SPI → I2C by identifying _what must change_ to make a multi-device bus possible with fewer pins.

---

## **SPI’s Limitation Recap**

SPI requires:

- A clock line
    
- Two data lines
    
- **A dedicated CS line per peripheral**
    

This makes SPI **non-scalable** as the number of peripherals grows.

---

## **Two Strategies to Reduce GPIO Usage**

### **1. Eliminate Chip Select Lines**

Instead of:

- A unique CS pin for each device
    
- Devices watching for CS transitions
    

We move to a system where:

- All devices share the same wires
    
- Devices distinguish themselves using **addresses**, not wires
    

This is a fundamental shift toward a **bus architecture**, not point-to-point links.

---

### **2. Use a Bi-Directional Data Bus**

SPI uses two one-way data lines:

|Line|Direction|
|---|---|
|MOSI|Controller → Peripherals|
|MISO|Peripherals → Controller|

To reduce wiring, we merge these into **one shared data line** that can carry data in both directions.

This requires:

- Special electrical design (open-drain instead of push-pull)
    
- A shared pull-up resistor
    
- Rules for preventing collisions
    

This is exactly how **I2C** operates.

---

## **Why These Two Ideas Matter**

Combining:

- **No chip-select lines**
    
- **A shared bi-directional bus**
    

…creates a communication system where many devices can safely share only **two wires**:

1. **SCL** – shared clock
    
2. **SDA** – shared data
    

This is the foundation of the I2C protocol discussed next.

---

## **Key Takeaway**

> **To scale synchronous serial communication to many peripherals with minimal wiring, we must remove chip-select lines and use a shared bi-directional data bus — the core concepts behind I2C.**


![[All_slides_nes.pdf#page=172]]  
**Week 5 Slide 23 – I2C (Inter-Integrated Circuit)**

---

## **Purpose of the Slide**

This slide introduces **I2C**, a synchronous serial protocol designed to reduce wiring while supporting many devices safely.

I2C achieves this using only **two wires** shared by all devices.

---

## **I2C Bus Lines**

|**Line**|**Function**|
|---|---|
|**SCL**|Clock line generated by the controller|
|**SDA**|Bi-directional data line shared by all devices|

Both lines are connected using **pull-up resistors**.

---

## **Open-Drain Signalling**

This is the electrical foundation of I2C.

### **How It Works**

- A device can **pull the line low** (drive a ‘0’)
    
- A device can **release the line** (Hi-Z) to allow the pull-up to restore a ‘1’
    

### **Important Result**

> **‘0’ wins.  
> If two devices transmit at the same time, and one transmits ‘0’, the bus reads ‘0’.**

This enables:

- Safe sharing of the bus
    
- Arbitration between multiple controllers
    
- Collision avoidance
    

---

## **Comparison With UART/SPI Electrical Design**

|Feature|UART/SPI|I2C|
|---|---|---|
|Output Type|Push-pull (dangerous if shorted)|Open-drain (safe to share)|
|Number of Data Lines|1 TX + 1 RX (UART) / MOSI + MISO (SPI)|1 shared data line|
|Multi-Device Safety|No|Yes|

---

## **I2C Performance Characteristics**

- Clock typically **100–400 kHz**
    
- Faster than UART
    
- Slower than SPI
    
- Open-drain switching is inherently slower
    
- Consumes energy whenever transmitting a ‘0’ due to current through pull-up resistors
    
    - Example from slide:
        
        - 5V bus
            
        - 5kΩ resistor  
            → **5 mW** when pulling line low
            

---

## **Why I2C Can Support Many Devices**

- All peripherals connect to the same two wires
    
- No chip-select lines
    
- Each peripheral has a unique **7-bit address**
    
- The controller coordinates the bus
    

---

## **Key Takeaway**

> **I2C uses open-drain signalling and a shared clock to allow many devices to communicate over just two wires.  
> It is slower than SPI but far more scalable and GPIO-efficient.**

![[All_slides_nes.pdf#page=173]]  
**Week 5 Slide 24 – I2C: Multiple Peripherals**

---

## **Purpose of the Slide**

This slide explains how I2C supports **many peripherals simultaneously** on the same two-wire bus using **addresses instead of chip-selects**.

---

## **How I2C Connects Multiple Devices**

All peripherals (called **targets**) connect to the same:

- **SCL** (shared clock)
    
- **SDA** (shared bi-directional data line)
    

No additional lines are needed.

---

## **Address-Based Target Selection**

Each I2C target has a **7-bit address**.

- The controller begins every communication by sending an **address frame**
    
- Only the device whose address matches responds
    
- All others **ignore** the transaction completely
    

### Address Capacity:

- 7-bit addressing → up to **128** theoretical addresses
    
- Some addresses are reserved
    
- Practically usable ≈ **100+ devices** on one bus
    

---

## **Address Configuration**

- Many devices have **fixed** addresses
    
- Some allow **1–3 configurable bits** via pins or internal options
    
- Important rule:
    
    > **No two devices may share the same address on the same I2C bus**
    

Otherwise both try to respond, causing bus conflicts.

---

## **Why This Works**

Because I2C uses:

- **Open-drain outputs**
    
- **A shared bus**
    
- **Address-based selection**
    

it permits safe and scalable multi-device communication without extra GPIOs.

---

## **Diagram Explanation**

The slide shows:

- Multiple devices wired to the same SDA/SCL pair
    
- Controller at the top
    
- Each peripheral listening for its matching address
    
- No chip-select signals needed
    

---

## **Key Takeaway**

> **I2C can support many peripherals because all devices share the same data and clock lines, and are selected using unique 7-bit addresses instead of dedicated chip-select wires.**


![[All_slides_nes.pdf#page=174]]  
**Week 5 Slide 25 – I2C: Configurable Addresses**

---

## **Purpose of the Slide**

This slide explains how some I2C peripherals allow limited address configuration so multiple identical devices can coexist on the same I2C bus without address conflicts.

---

## **Why Configurable Addresses Are Needed**

- Many I2C devices ship with a **fixed 7-bit address**
    
- If you connect **two of the same sensor**, both would respond to the same address
    
- This causes **bus contention** and breaks communication
    

To solve this, some devices include **address pins** that modify part of the address.

---

## **How Configurable Addresses Work**

A device may define:

- **A fixed part** of the 7-bit address
    
- **One or more configurable bits** read from external pins
    

### Example from the Slide:

A sensor has base address:  
**0b011010x**

- The **x** bit is configurable via an address pin (ADR)
    
- Two possible addresses:
    
    - With ADR = 1 → **0b0110101**
        
    - With ADR = 0 → **0b0110100**
        

This allows **two identical chips** to be placed on the same bus.

---

## **Number of Selectable Address Variants**

|Number of Configurable Bits|Possible Addresses|
|---|---|
|0|1 fixed address|
|1|2 addresses|
|2|4 addresses|
|3|8 addresses|

Most sensors provide **1 or 2 bits**, rarely more.

---

## **Diagram Explanation**

The slide shows:

- Two identical sensors
    
- Each connected to the same SDA/SCL bus
    
- Their ADR labels set differently (0 or 1)
    
- Resulting in **two unique addresses** on the same bus
    

This visualizes how simple pin configuration avoids address conflicts.

---

## **Key Takeaway**

> **Configurable I2C address bits allow multiple identical devices to share the same bus by assigning each a unique address using hardware pins.**

![[All_slides_nes.pdf#page=175]]  
**Week 5 Slide 26 – I2C: Address Frame**

---

## **Purpose of the Slide**

This slide explains how every I2C transaction begins:  
with the **address frame**, which identifies the target peripheral and whether the controller wants to **read** or **write**.

---

## **Structure of the Address Frame**

The controller always sends the **first byte**:

|Bits|Meaning|
|---|---|
|**7 MSBs**|Target’s I2C address|
|**1 LSB**|Read/Write bit (R/W)|

### R/W Bit Meaning:

|R/W Bit|Value|Meaning|
|---|---|---|
|**0**|Write|Controller → Target|
|**1**|Read|Target → Controller|

---

## **How Devices Respond**

- Every peripheral listens to the address on SDA
    
- If the received address **matches its own**, the peripheral:
    
    - Prepares to communicate
        
    - Acknowledges the frame
        
- If not, it **ignores** the entire transaction
    

This enables many devices to share the same SDA/SCL lines safely.

---

## **Example from the Slide**

Peripheral address: **0b0110101**

### To write to it:

Controller sends:  
**0b0110101 0** → 0x6A

### To read from it:

Controller sends:  
**0b0110101 1** → 0x6B

---

## **Key Concepts Illustrated**

- The address + R/W bit are always the **first byte**
    
- This byte determines whether the rest of the communication is:
    
    - Controller writing data
        
    - Controller receiving data
        
- All other devices immediately ignore the rest of the transaction
    

---

## **Diagram Explanation**

The slide’s bits diagram shows:

- 7 address bits
    
- 1 R/W bit
    
- The resulting byte encoded in binary and hex
    

This visually reinforces how to construct the address byte.

---

## **Key Takeaway**

> **Every I2C transaction begins with an address frame that identifies the target device and the direction of communication.**

![[All_slides_nes.pdf#page=176]]  
**Week 5 Slide 27 – I2C Protocol: Start Condition and Acknowledgement (ACK)**

---

## **Purpose of the Slide**

This slide explains two fundamental I2C protocol concepts:

1. **How an I2C transaction begins** → _Start Condition_
    
2. **How the receiver confirms correct reception** → _ACK Bit_
    

These are essential for safe multi-device communication on a shared bus.

---

## **1. Start Condition**

The controller begins every transaction with a **start condition**, defined as:

- **SCL is high**
    
- **SDA transitions from high → low**
    

This signals to _all_ devices on the bus:

> **“A transaction is starting—prepare to listen.”**

The start condition is unique because SDA changes while SCL is high (which normally never occurs during data transfer).

---

## **2. Address Frame and Direction Bit**

After the start condition:

- The controller places the **7-bit address + R/W bit** onto SDA
    
- All peripherals compare it with their own address
    

Only matching devices will respond.

---

## **3. Acknowledgement Bit (ACK)**

After receiving the address frame:

- The controller **releases** the SDA line
    
- The addressed peripheral is expected to **pull SDA low**  
    → This is the **ACK** (acknowledge)
    
- Holding SDA high means **NACK** (no acknowledgement)
    

### Meaning of ACK/NACK:

|Bit State|Meaning|
|---|---|
|**0 (pulled low)**|Peripheral acknowledges (valid target, byte received)|
|**1 (line stays high)**|No device responded OR error occurred|

---

## **Examples from the Slide**

### **Example 1 — Valid Write Request**

- Address = `0b0110101`
    
- Controller sends write command
    
- Target matches address → pulls SDA low → **ACK received**
    

### **Example 2 — Invalid Read Request**

- Address = `0b0110101`
    
- Controller sends read command
    
- No device acknowledges → SDA stays high → **NACK**
    

---

## **Why ACK Is Important**

- Confirms that the intended device is present
    
- Confirms that each transmitted byte was received correctly
    
- Allows safe continuation or early termination of a transaction
    

This enables reliable communication even on a shared bus with many devices.

---

## **Key Takeaway**

> **The start condition notifies all devices that a transaction begins, and the ACK bit confirms that the addressed device received the byte successfully.**

![[All_slides_nes.pdf#page=177]]  
**Week 5 Slide 28 – I2C Protocol: Data Frame and Stop Condition**

---

## **Purpose of the Slide**

This slide explains what happens **after** the address frame is acknowledged:

1. **How data bytes are transmitted**
    
2. **How the bus signals the end of a transaction** using the **stop condition**
    

---

## **1. Data Frames**

After the target acknowledges the address:

- The controller continues generating clock pulses on **SCL**
    
- Data begins transferring over **SDA**
    
- Depending on the R/W bit:
    
    - **Controller writes data** (SDA controlled by controller)
        
    - **Peripheral sends data** (SDA controlled by target)
        

### **Structure of Each Data Frame**

|Part|Description|
|---|---|
|**8 data bits**|Actual payload byte|
|**1 ACK bit**|Receiver pulls SDA low to confirm|

This repeats for **one or more bytes**, depending on the transaction.

---

## **Read vs Write Behavior**

|Operation|SDA Controlled By|
|---|---|
|**Write**|Controller|
|**Read**|Target device|

In reads, the controller becomes the receiver.

---

## **NACK on Final Read Byte**

When **reading**, after the last byte:

- The controller sends a **NACK** (leaves SDA high)
    
- This signals:
    
    > “I am done reading—do not send more data.”
    

---

## **2. Stop Condition**

The transaction ends with a **stop condition**, defined as:

- **SCL is high**
    
- **SDA transitions from low → high**
    

This is the _inverse_ of the start condition.

It tells all devices:

> **“The bus is now free—communication complete.”**

---

## **Diagram Explanation**

The slide shows:

- Multiple data frames (each with 8 data bits + ACK bit)
    
- A target-controlled SDA during reads
    
- A final NACK for read termination
    
- A stop condition created with SDA rising while SCL is high
    

---

## **Key Takeaway**

> **Every I2C byte is followed by an ACK.  
> A NACK ends a read.  
> A stop condition ends the transaction and releases the bus.**

![[All_slides_nes.pdf#page=178]]  
**Week 5 Slide 29 – I2C: Transaction Examples**

---

## **Purpose of the Slide**

This slide provides two concrete examples showing how I2C transactions work in real scenarios:

1. **Controller writes one byte to a target**
    
2. **Controller reads one byte from a target**
    

These examples visually show how SDA is controlled differently in write vs. read operations.

---

## **Example 1 — Controller Writes a Byte to Target (Blue)**

### **Sequence**

1. **Start condition**
    
2. Controller sends **address + write bit (0)**
    
3. Target sends **ACK**
    
4. Controller sends **data byte (8 bits)**
    
5. Target sends **ACK**
    
6. **Stop condition**
    

### **SDA Control**

|Phase|SDA Driven By|
|---|---|
|Address byte|Controller|
|Data byte|Controller|
|ACK bits|Target|

### **Key Idea**

> **In write operations, the controller owns the SDA line for all data bits.**

---

## **Example 2 — Controller Reads a Byte from Target (Green)**

### **Sequence**

1. **Start condition**
    
2. Controller sends **address + read bit (1)**
    
3. Target sends **ACK**
    
4. Target sends **data byte (8 bits)**
    
5. Controller sends **NACK** to signal “no more bytes”
    
6. **Stop condition**
    

### **SDA Control**

|Phase|SDA Driven By|
|---|---|
|Address byte|Controller|
|ACK after address|Target|
|Data byte|Target|
|Final NACK|Controller|

### **Key Idea**

> **In read operations, the target controls SDA during the data byte transmission.**

---

## **Diagram Explanation**

The slide shows two waveforms:

- **Blue waveform**: Write example
    
- **Green waveform**: Read example
    

You can clearly see:

- Who controls SDA at each moment
    
- The ACK/NACK bits
    
- The start/stop conditions
    
- Clock pulses from the controller throughout
    

---

## **Key Takeaway**

> **I2C writes: Controller sends data.  
> I2C reads: Target sends data.  
> ACK/NACK bits separate each byte and control flow.**

![[All_slides_nes.pdf#page=179]]  
**Week 5 Slide 30 – Open-Drain Output**

---

## **Purpose of the Slide**

This slide explains the **electrical behavior** that makes I2C safe for multi-device communication:  
the **open-drain output**.

Open-drain is essential because it prevents electrical conflicts when multiple devices share the same line.

---

## **Two Output States of Open-Drain**

Open-drain pins can only do **two things**:

|State|Electrical Behaviour|Logical Meaning|
|---|---|---|
|**Pull line low**|Actively drives SDA/SCL to 0 V|Logical **0**|
|**Hi-Z (high-impedance)**|Disconnects from the bus|Logical **1** (via pull-up)|

The device **never** drives the line high.

---

## **Why a Pull-Up Resistor Is Required**

When the device releases the line (Hi-Z):

- The pull-up resistor slowly pulls the bus to **logical 1**
    
- This ensures:
    
    - Safe shared bus operation
        
    - No one device is responsible for driving a high state
        

---

## **Key Property: “0 Wins”**

If two devices act at once:

- One pulls SDA → 0
    
- Another releases SDA → floating → 1
    

Result:

> **The bus reads 0.**  
> **No electrical conflict occurs.**

This is the basis of:

- I2C multi-controller arbitration
    
- Clock stretching
    
- Collision-free multi-device communication
    

---

## **Comparison to Push-Pull Outputs (UART/SPI)**

|Feature|Push-Pull (UART/SPI)|Open-Drain (I2C)|
|---|---|---|
|Drives High?|Yes|No|
|Drives Low?|Yes|Yes|
|Safe for shared lines?|**No** (can short-circuit)|**Yes**|
|Supports multi-controller?|No|Yes|

---

## **Diagram Explanation**

The slide shows:

- Two states: **0 (low)** and **Hi-Z**
    
- Pull-up resistor creating the logical ‘1’
    
- The line only rises to ‘1’ when **no device** pulls it low
    

---

## **Key Takeaway**

> **Open-drain allows multiple devices to share a bus safely.  
> Only ‘0’ is actively driven; ‘1’ is created passively via pull-ups.  
> This prevents electrical conflicts and enables multi-device I2C operation.**

![[All_slides_nes.pdf#page=180]]  
**Week 5 Slide 31 – I2C: Clock Stretching**

---

## **Purpose of the Slide**

This slide explains **clock stretching**, a feature of I2C that allows a target device to slow down the communication if it needs more time to process data.

---

## **Why Clock Stretching Exists**

I2C uses **open-drain** signalling on both SDA and SCL:

- Any device can pull the lines low
    
- No device can force them high (only release)
    

Because of this design:

> **A target can hold SCL low to pause communication.**

This gives slower devices the ability to keep up with the controller.

---

## **How Clock Stretching Works**

### **Normal Operation**

- Controller toggles SCL (clock pulses)
    
- Target responds at the controller’s pace
    

### **When a Target Needs More Time**

1. Controller releases SCL to go high
    
2. Target **pulls SCL low**, preventing the rising edge
    
3. Controller **must wait** until SCL is released
    
4. Once the target is ready, it releases SCL
    
5. Controller resumes clocking normally
    

This effectively **stops time** from the controller’s perspective.

---

## **Key Principle: “0 Always Wins”**

Because ‘0’ overrides ‘1’ on an open-drain bus:

- The controller **cannot** force SCL high while the target holds it low
    
- This makes stretching reliable and safe for shared buses
    

---

## **When Clock Stretching Is Used**

- Target needs extra time to fetch sensor data
    
- Target needs to complete an internal operation
    
- Target is buffering data
    
- Slower devices on a fast bus prevent communication errors
    

Some modern devices avoid stretching to improve timing predictability,  
but many sensors rely on it.

---

## **Diagram Explanation**

The slide shows:

- SCL being held low longer by the target
    
- The controller’s attempt to raise SCL blocked
    
- SDA temporarily paused during the stretch
    
- Communication resumes once the target releases SCL
    

---

## **Key Takeaway**

> **Clock stretching allows a target to temporarily hold SCL low, pausing the transaction so it can catch up.  
> This is only possible because I2C uses open-drain signalling where ‘0’ overrides ‘1’.**

![[All_slides_nes.pdf#page=181]]  
**Week 5 Slide 32 – I2C: Multiple Controllers (Arbitration)**

---

## **Purpose of the Slide**

This slide explains how I2C can safely support **multiple controllers** on the same bus — a feature made possible by **open-drain signalling** and the rule that **‘0’ always wins**.

This mechanism is known as **arbitration**.

---

## **Why Multi-Controller I2C Is Possible**

Because:

- Devices never drive the line high
    
- If two devices try to transmit simultaneously:
    
    - A device sending **1** releases SDA
        
    - A device sending **0** pulls SDA low
        

Result:

> **The line becomes 0 with no electrical conflict.**

This allows controllers to _detect_ collisions rather than damage each other.

---

## **How Arbitration Works**

### Scenario: Two controllers start transmitting at the same time.

Both:

1. Detect the bus is free
    
2. Generate a **start condition**
    
3. Begin sending address/data bits
    

During transmission, each controller:

- **Samples SDA** while transmitting
    
- Compares the _actual_ bus value with the bit it intended to send
    

### Arbitration Rule:

|Controller Intends to Send|Bus State|What It Means|
|---|---|---|
|**1** (release line)|**0**|Another device is driving 0 → this controller **loses arbitration**|
|**0**|**0**|Still in control|
|**1**|**1**|Still in control|

The controller that detects a mismatch:

- **Stops transmitting immediately**
    
- Releases the bus
    
- Lets the other controller finish the transaction
    

### The Winner:

> **The last controller still able to send a ‘1’ wins arbitration.**

---

## **Example from the Slide**

The diagram shows:

- Two controllers attempting to send different bytes
    
- One sends a ‘1’ while the bus reads ‘0’
    
- It detects a conflict and stops
    
- The other controller completes the transaction uninterrupted
    

---

## **Why This Matters**

- No data corruption
    
- No electrical conflict
    
- No need for master negotiation outside the protocol
    
- Perfect for shared buses in complex systems
    

---

## **Key Takeaway**

> **I2C supports multiple controllers because open-drain buses allow safe arbitration.  
> A controller that tries to send a ‘1’ but reads a ‘0’ loses and stops.  
> The remaining controller continues the transaction.**

![[All_slides_nes.pdf#page=182]]  
**Week 5 Slide 33 – I2C: Repeated Start Condition**

---

## **Purpose of the Slide**

This slide explains the **repeated start condition** (also called a _restart_), which allows the controller to perform multiple back-to-back I2C operations **without releasing the bus**.

Repeated starts are essential for register reads and multi-part transactions.

---

## **Why Repeated Start Is Needed**

A normal I2C sequence is:

- **Start → Address → Data → Stop**
    

But many devices require:

- Write a register address
    
- Then **read** from that register
    
- Without allowing other controllers to interrupt
    

If a **stop** were issued between write and read, another controller could take over the bus.  
Repeated start prevents this.

---

## **How a Repeated Start Works**

### Normal Start Condition:

- **SCL high**
    
- **SDA falls from 1 → 0**
    

### Repeated Start Condition:

1. Controller first brings **both SDA and SCL high**  
    (but **does NOT issue a stop**)
    
2. While SCL stays high, the controller pulls **SDA low again**
    
3. This creates a **new start condition** without releasing the bus
    

This keeps the bus **busy** and prevents other controllers from issuing their own start.

---

## **Effect on Other Controllers**

Other controllers:

- See that the bus **never entered a stop condition**
    
- Understand the bus is still in use
    
- Do **not** attempt communication
    
- Wait until a true stop condition appears
    

Thus, repeated start allows:

> **Atomic multi-step I2C transactions.**

---

## **Use Cases**

Repeated start is used in:

- **Reading a sensor register**  
    (Write register address → Repeated Start → Read data)
    
- **Combined write-read operations**
    
- **Keeping control of the bus when multiple controllers exist**
    

---

## **Diagram Explanation**

The slide shows:

- SDA transitioning high → low while SCL stays high
    
- No stop condition beforehand
    
- Two consecutive start conditions chained together
    
- Bus remains owned by the controller through the entire sequence
    

---

## **Key Takeaway**

> **A repeated start allows the controller to begin a new transaction without releasing the bus, ensuring uninterrupted multi-part communication.**

![[All_slides_nes.pdf#page=183]]  
**Week 5 Slide 34 – I2C: Write/Read Target Register**

---

## **Purpose of the Slide**

This slide explains the **most common real-world I2C operation**:  
reading from or writing to a device’s internal register.

Almost all sensors, memory chips, and configuration ICs use this pattern.

---

## **Device Internal Structure: Registers**

I2C peripherals store configuration values and data in **registers**:

- Each register has an **address**
    
- Each register holds an **8-bit value**
    

To access a register, the controller must first tell the device **which register** is being referenced.

---

# **1. Writing to a Register (3 bytes)**

**Sequence:**

1. **Start**
    
2. **Target Address + Write (0)**
    
3. **Register Address** (which register to write)
    
4. **Register Value** (the data to store)
    
5. **Stop**
    

### Who Controls SDA?

|Step|Controller|Target|
|---|---|---|
|Address frame|✔|ACK|
|Register address|✔|ACK|
|Register value|✔|ACK|

---

# **2. Reading from a Register (4 bytes, uses Repeated Start)**

Because the target needs to know which register to send back, the controller must:

### Step A — Send Register Address

1. **Start**
    
2. **Target Address + Write (0)**
    
3. **Register Address**
    
4. **Repeated Start**
    

### Step B — Read the Register Value

5. **Target Address + Read (1)**
    
6. **Register Value** (sent by target)
    
7. **NACK** (controller signals “done”)
    
8. **Stop**
    

### SDA Control for Read

|Step|Controller|Target|
|---|---|---|
|Sending register address|✔|ACK|
|Sending repeated start|✔|—|
|Sending address+read|✔|ACK|
|Outputting register value|—|✔|
|Final NACK|✔|—|

---

## **Why Repeated Start Is Required**

Without repeated start:

- Another controller could take over the bus
    
- Register selection and register reading must remain **atomic**
    

Repeated start keeps the bus locked.

---

## **Diagram Explanation**

The slide shows two timelines:

- **Blue** = Controller drives SDA
    
- **Green** = Target drives SDA
    

Key moments highlighted:

- ACK bits
    
- Repeated start
    
- Correct transfer direction change
    
- Final NACK to end the read
    

---

## **Key Takeaway**

> **To read a register:  
> Write the register address → repeated start → read the register value.  
> To write a register:  
> Write device address → write register address → write value.**

![[All_slides_nes.pdf#page=184]]  
**Week 5 Slide 35 – Example of an I2C Peripheral**

---

## **Purpose of the Slide**

This slide presents a real device that uses I2C:  
the **TMP1075**, a digital temperature sensor.

It demonstrates how an I2C-based peripheral exposes:

- A **register interface**
    
- A **configurable address**
    
- A simple I2C command/control structure
    

---

## **About the TMP1075 Sensor**

### **1. It Uses I2C as Its Communication Interface**

All interactions occur via:

- **SCL** (clock from controller)
    
- **SDA** (bi-directional data)
    

No extra pins are required except optional address pins.

---

### **2. It Has a Configurable I2C Address**

Base address: **10010xx**

- The lower **two bits** (xx) are configurable
    
- This gives **4 possible addresses**
    

This allows connecting up to four TMP1075 sensors on the same I2C bus without address conflicts.

|ADR Pins|Resulting Address|
|---|---|
|00|1001000|
|01|1001001|
|10|1001010|
|11|1001011|

---

### **3. It Provides a Register-Based Interface**

The device contains memory-mapped registers, such as:

- Temperature register
    
- Configuration register
    
- Limit threshold registers
    

Access follows the standard I2C register pattern:

- **Write register address → repeated start → read register value**
    

---

## **What This Example Illustrates**

The TMP1075 demonstrates typical I2C peripheral behavior:

|Feature|How It Appears in TMP1075|
|---|---|
|**Addressing**|Fixed base + configurable bits|
|**Register access**|Read/write internal registers|
|**Shared bus compatibility**|Multiple sensors coexisting|
|**Simple wiring**|Only 2 wires regardless of device count|

---

## **Diagram Explanation**

The slide image shows:

- The TMP1075 chip/package
    
- Pinout including SDA, SCL, power, ground, address pins
    
- Highlight of the configurable address bits
    

This visually reinforces how a real device physically supports I2C.

---

## **Key Takeaway**

> **The TMP1075 sensor is a practical example of an I2C peripheral:  
> Uses 2-wire communication, supports configurable addressing, and exposes a register-based control interface.**

![[All_slides_nes.pdf#page=185]]  
**Week 5 Slide 36 – Summary: UART vs SPI vs I2C**

---

## **Purpose of the Slide**

This slide provides a **side-by-side comparison** of the three major serial communication protocols covered:

- **UART** (asynchronous)
    
- **SPI** (synchronous, point-to-point with CS)
    
- **I2C** (synchronous, multi-device bus)
    

It summarizes their key characteristics and trade-offs.

---

## **Comparison Table**

|**Property**|**UART**|**SPI**|**I2C**|
|---|---|---|---|
|**No. of Peripherals Supported**|Point-to-point (1:1 only)|Many (limited by CS pins)|Many (address-based)|
|**Multi-Controller Support**|❌ No|❌ No|✔️ Yes (arbitration)|
|**Typical Data Rate**|10–100 kbps|1–20 Mbps|100–400 kbps|
|**GPIO Required**|2 pins (TX, RX)|3 pins + 1 CS per device|2 pins total|
|**Simultaneous Tx/Rx**|Depends on hardware|✔️ Full-duplex|❌ Half-duplex|
|**Overhead (per byte)**|2–4 bits (start, stop, parity)|0 bits|11 bits + 1 ACK bit|
|**Energy Requirements**|++ (moderate)|+ (efficient)|+++ (highest due to pull-ups)|

---

## **Interpretation of Key Differences**

### **1. UART**

- Best for simple **1-to-1** communication
    
- No addressing, cannot share transmit lines
    
- Lower data rates
    
- Minimal wiring (just TX/RX)
    

---

### **2. SPI**

- Fastest protocol (MHz range)
    
- True **full-duplex**
    
- Hardware simple but wiring expensive due to CS per device
    
- Great for sensors, displays, memory chips
    
- Not multi-controller
    

---

### **3. I2C**

- Designed for **many devices on the same bus**
    
- Only 2 wires needed
    
- Lower speed than SPI
    
- Higher overhead and energy consumption
    
- Supports **multiple controllers** with robust bus arbitration
    
- Very common for configuration and sensor networks
    

---

## **Protocol Selection Rule of Thumb**

- Use **UART** → when only two devices need to talk, simple text or command interface
    
- Use **SPI** → when you need high speed and can afford extra pins
    
- Use **I2C** → when connecting many peripherals with minimal wiring
    

---

## **Key Takeaway**

> **UART: simple but point-to-point.  
> SPI: fast but pin-heavy.  
> I2C: multi-device, minimal wiring, slower with more overhead.**

![[All_slides_nes.pdf#page=186]]  
**Week 5 Slide 37 – I3C**

---

## **Purpose of the Slide**

This slide introduces **I3C**, a modern serial communication protocol designed to combine the strengths of **I2C** and **SPI**, while avoiding their limitations.

---

## **What I3C Aims to Achieve**

> **“Aim to be the best of both worlds.”**

I3C attempts to provide:

- The low-pin count and multi-device bus of **I2C**
    
- The high speed and efficiency closer to **SPI**
    

---

## **Key Features of I3C**

### **1. Primary Controller Manages the Clock**

- A **primary controller** always controls SCL
    
- A **secondary controller may exist**, similar to I2C’s multi-controller capability
    
- Ensures predictable bus timing and arbitration
    

---

### **2. Hybrid Signaling: Open-Drain + Push-Pull**

I3C uses:

|Mode|When Used|Why|
|---|---|---|
|**Open-drain**|During start condition|Ensures compatibility with I2C devices|
|**Push-pull**|After start condition|Allows high-speed transfers|

#### Important behaviour:

- After issuing the **start condition**,  
    the controller switches SDA to **push-pull** mode
    
- This enables much faster data rates — **up to 12.5 MHz**
    

This is a major improvement over I2C’s typical 100–400 kHz.

---

### **3. Pull-Up Resistors Provided by Controller**

- The I3C controller internally provides pull-ups
    
- No external resistors required
    
- Simplifies board design and reduces power consumption
    

---

### **4. Limitations vs I2C**

- **Clock stretching is not supported**  
    (targets must always be ready; contributes to higher speed)
    
- **10-bit I2C-style addressing is not supported**
    

These decisions simplify the protocol and help ensure tighter timing.

---

## **Comparison Context (from the diagram)**

The small Venn diagram on the slide shows:

- I3C overlaps between **I2C** and **SPI**
    
- Meaning it shares traits with both:
    
    - Multi-device bus (I2C)
        
    - Higher performance (SPI)
        

---

## **Key Takeaway**

> **I3C is a modern upgrade to I2C that supports higher speeds through dynamic switching to push-pull signaling, removes external pull-ups, and simplifies timing by eliminating clock stretching.**


Here are **5 multiple-choice questions** based on the full Week 5 slide set.  
(No answers included, as requested.)

---

### **MCQ 1 – UART Signalling**

Which of the following is **true** about asynchronous UART communication?

A. The transmitter and receiver share a common clock line.  
B. A start bit is used to synchronise each frame.  
C. UART can safely support multiple transmitters on the same line.  
D. Data is always transmitted MSB first.

---

### **MCQ 2 – SPI Bus Characteristics**

Which statement correctly describes SPI?

A. SPI supports multiple controllers due to open-drain outputs.  
B. SPI is half-duplex and transmits only on MOSI.  
C. Only one peripheral may be active at a time, selected by its CS line.  
D. SPI requires start and stop conditions for each transfer.

---

### **MCQ 3 – I2C Addressing**

Which of the following is **true** about I2C addressing?

A. Each I2C device must have a unique 7-bit address on the same bus.  
B. Chip-select lines determine which I2C device responds.  
C. Devices can drive the line high to transmit a logical 1.  
D. I2C does not support reading and writing registers.

---

### **MCQ 4 – Open-Drain Behaviour**

In an I2C bus using open-drain signalling:

A. A device can actively drive the line high or low.  
B. Pull-up resistors are not required.  
C. A ‘1’ always overrides a ‘0’.  
D. Multiple devices can pull the line low simultaneously without conflict.

---

### **MCQ 5 – I3C Enhancements**

Which improvement does **I3C** introduce compared to I2C?

A. Supports clock stretching for slow targets.  
B. Allows switching from open-drain to push-pull to increase speed.  
C. Requires external pull-up resistors on SDA and SCL.  
D. Maintains maximum speed of 400 kHz.

---

If you'd like, I can also provide:

- more MCQs
    
- answers separately
    
- short-answer questions
    
- exam-style problems
    
- a full quiz with difficulty scaling


Here are the answers:

---

### **MCQ 1 – Correct Answer: B**

UART uses a **start bit** for synchronisation.

---

### **MCQ 2 – Correct Answer: C**

Only one SPI peripheral may be active at a time, selected via its **CS** line.

---

### **MCQ 3 – Correct Answer: A**

All I2C devices on the same bus must have a **unique 7-bit address**.

---

### **MCQ 4 – Correct Answer: D**

Multiple devices can safely pull the line low at the same time because ‘0’ **wins** on an open-drain bus.

---

### **MCQ 5 – Correct Answer: B**

I3C switches from **open-drain to push-pull** to reach much higher speeds (up to ~12.5 MHz).

---

If you want another set of MCQs or exam-style questions, just say **next set**.


WEEK 7 NOTES


![[All_slides_nes.pdf#page=189]]  
Week 7 Slide 3 – OSI Model (7 Layers)

- The OSI model divides network communication into 7 layers to structure functions and ensure interoperability.
    
- Layer 7 – Application:
    
    - Closest to the user (apps, services).
        
    - User-facing protocols (HTTP, FTP, SMTP).
        
    - Ensures applications can send/receive data over the network.
        
- Layer 6 – Presentation:
    
    - Converts data between internal formats and network formats.
        
    - Handles encryption/decryption and compression.
        
    - Ensures sender and receiver interpret data in the same way.
        
- Layer 5 – Session:
    
    - Establishes, manages, and terminates communication sessions.
        
    - Handles login, dialogue control, and recovery from disconnections.
        
- Layer 4 – Transport:
    
    - End-to-end, process-to-process communication.
        
    - Segmentation, ordering, reliability (TCP) or low-overhead transfer (UDP).
        
- Layer 3 – Network:
    
    - Routing between networks and subnetworks.
        
    - Uses logical addressing (IP).
        
    - Handles forwarding of packets across multiple hops.
        
- Layer 2 – Data Link:
    
    - Creates frames for local delivery.
        
    - Uses physical addressing (MAC).
        
    - Provides link-level error detection (CRC).
        
- Layer 1 – Physical:
    
    - Sends raw bits as electrical/optical signals.
        
    - Defines cables, connectors, voltages, timing, etc.
        
    - Closely tied to hardware (PHY, transceivers).

![[All_slides_nes.pdf#page=190]]  
Week 7 Slide 4 – Physical Layer (PHY)

**What the PHY does**

- Converts digital bits ↔ electrical/optical signals.
    
- Defines voltage levels, timing, connectors, cabling, bandwidth.
    
- Handles modulation, encoding/decoding, synchronization.
    
- Very hardware-close: transceivers, magnetics, line drivers.
    

---

**Line Coding Overview (Purpose: sync + reliability)**

|Encoding|Key Idea|Advantages|Disadvantages|
|---|---|---|---|
|**NRZ**|0/1 = constant level|Simple, low bandwidth|Long runs of identical bits → loss of sync|
|**Manchester**|Mid-bit transition encodes data|Self-clocking, robust sync|Requires double bandwidth|
|**Differential signalling**|Two opposite signals on a pair|High noise immunity, good EMC|Needs differential pair wiring|
|**Bit stuffing**|Insert opposite bit after 5 identical bits|Maintains clock sync, avoids invalid patterns|Adds slight overhead|

---

**Why PHY matters for embedded systems**

- Determines achievable bitrate and cable length.
    
- Affects EMI/EMC performance (important in automotive/industry).
    
- Impacts power consumption and hardware complexity.
    

---

**Key takeaway**  
PHY ensures bits can travel safely and reliably across real physical media.

![[w7-wired-nes.pdf#page=5]]  
Week 7 Slide 5 – Line Coding

**Definition**

- Line coding defines how logical ‘0’ and ‘1’ are physically represented on the wire.
    

---

**NRZ (Non-Return-to-Zero)**

- Signal does _not_ return to zero mid-bit.
    
- Variants:
    
    - **NRZ-L:** ‘0’ = 0V, ‘1’ = +V
        
    - **NRZ-M / NRZ-I:** ‘0’ = same voltage, ‘1’ = transition
        
    - **NRZ-S:** ‘1’ = same voltage, ‘0’ = transition
        

---

**RZ (Return-to-Zero)**

- ‘1’ returns to zero in the middle of the bit.
    
- Uses more bandwidth.
    

---

**Comparison Table**

|Method|How it Encodes|Pros|Cons|
|---|---|---|---|
|**NRZ-L**|Fixed level per bit|Simple|Long sequences → sync loss|
|**NRZ-M / NRZ-I**|Transition = ‘1’|Good for avoiding long flatlines|Still lacks guaranteed transitions|
|**NRZ-S**|Transition = ‘0’|Similar benefit to NRZ-I|Same sync issues|
|**RZ**|Return to zero mid-bit|Better timing reference|Requires more bandwidth|

---

**Key Idea**

- Different schemes trade off bandwidth, complexity, and synchronization reliability.

![[All_slides_nes.pdf#page=192]]  
Week 7 Slide 6 – Manchester Coding

**Concept**

- Encodes each bit as a **transition in the middle of the bit period**.
    
- A transition _is_ the information.
    

---

**Original Manchester Encoding**

- ‘0’ = **low → high** transition
    
- ‘1’ = **high → low** transition
    

---

**IEEE 802.3 (Ethernet) Manchester**

- ‘0’ = **high → low** transition
    
- ‘1’ = **low → high** transition
    

---

**Properties**

- **Self-clocking**: receiver extracts timing from mid-bit transitions.
    
- No separate clock signal needed.
    
- **Robust synchronisation**, even over long wires.
    

---

**Trade-off**

- Requires **double the bandwidth** compared to NRZ, because every bit includes a transition.
    

---
![[All_slides_nes.pdf#page=193]]  
Week 7 Slide 7 – Transmission over Long Wires

**Why long wires cause problems**

- Wires have **resistance** and **capacitance** → distort signals.
    
- Imperfections increase with length.
    

---

**Side Effects of Long Cables**

- **EMI pickup:** wire acts like an antenna, receiving noise.
    
- **Ground potential differences:** ground level may not be identical at both ends.
    
- **High-frequency attenuation:** higher frequencies weaken more, causing signal smoothing.
    

---

**Result**

- **Bit errors** due to distorted or shifted signal levels.
    

---

**Visual Explanation (from slide)**

- Transmitted signal → clean square wave.
    
- Noise added over distance → irregular fluctuations.
    
- Received signal → distorted waveform, making bit decisions unreliable.
    
![[All_slides_nes.pdf#page=194]]  
Week 7 Slide 8 – Differential Signalling with Balanced Lines

**Concept**

- Uses **two wires of identical type and length** (balanced pair).
    
- Transmits:
    
    - **P (non-inverted signal):** ‘0’ = GND, ‘1’ = VS
        
    - **N (inverted signal):** ‘0’ = VS, ‘1’ = GND
        

---

**How the Receiver Interprets Bits**

- Receiver measures **P − N** (difference).
    
    - Positive → ‘1’
        
    - Negative → ‘0’
        

---

**Advantages**

- **Noise cancellation:** noise couples equally into both wires → removed by subtraction.
    
- **Higher noise resilience:** receiver sees _double_ the effective voltage difference.
    
- **Low-voltage operation:** reduces power and supports higher speeds.
    

---

**Why it Works**

- Interference affects both wires similarly → remains common-mode and is canceled out.
    
- Balanced lines ensure symmetrical behaviour → predictable signal integrity.

![[All_slides_nes.pdf#page=195]]  
Week 7 Slide 9 – Differential Signal: An Example

**What the slide shows**

- Three waveforms:
    
    - **P (Positive line):** carries the original signal.
        
    - **N (Negative line):** carries the inverted version of P.
        
    - **P − N (Differential output):** result after subtracting N from P.
        

---

**Signal Behaviour**

- When P = high, N = low → **P − N is strongly positive** → interpreted as ‘1’.
    
- When P = low, N = high → **P − N is strongly negative** → interpreted as ‘0’.
    

---

**Noise Effects**

- External noise couples into both wires _almost equally_.
    
- Noise added to P also appears on N (same polarity).
    
- During subtraction, this common noise cancels out:
    
    - P − N removes equal disturbances in both lines.
        
    - Remaining waveform is cleaner with sharper transitions.
        

---

**Why the differential signal looks better**

- The differential output exaggerates the difference between P and N.
    
- This increases the **signal-to-noise ratio (SNR)**.
    
- Even if both individual signals look distorted, the subtracted result recovers a clear digital pattern.
    

---

**Main takeaway**

- Differential signalling provides **robustness**, **noise immunity**, and **cleaner bit detection**, especially in electrically noisy environments or long cable runs.

![[All_slides_nes.pdf#page=196]]  
Week 7 Slide 10 – Synchronisation at Longer Distances

**Problem: No shared clock**

- Devices operate **asynchronously** using their own internal clocks.
    
- Even tiny differences cause **clock drift** over time.
    
- Without correction, sender and receiver will eventually disagree on bit boundaries.
    

---

**Pre-agreed transmission rate**

- Communication protocols define a fixed bitrate.
    
- Receiver samples bits assuming timing stays aligned.
    
- If timing drifts too far → **bit misinterpretation**.
    

---

**Role of transitions**

- Changes on the line (low→high or high→low) are used to **re-synchronise**.
    
- Transitions act as “timing anchors” for recovering the clock.
    
- Encoding schemes with frequent transitions are easier to sync to.
    

---

**Desynchronisation issue**

- Long sequences without transitions (e.g., many identical bits in NRZ) break timing recovery.
    
- Receiver clock drifts because it has no reference edges.
    

---

**Bit stuffing**

- Used to force periodic transitions.
    
- After a protocol-defined number of identical bits, the sender inserts an opposite bit.
    
- Ensures:
    
    - Minimum transition density
        
    - Maintained synchronisation
        
    - Avoidance of long flatline periods
        

---

**Key takeaway**

- Synchronisation relies on transitions.
    
- Bit stuffing ensures these transitions exist when the data itself would not.

![[All_slides_nes.pdf#page=197]]  
Week 7 Slide 11 – USB 2.0 (Universal Serial Bus)

**Physical Signalling**

- Uses **differential signalling** with a twisted pair:
    
    - **D+** and **D-** lines.
        
- Twisting reduces electromagnetic noise pickup.
    

---

**Differential Logic Levels**

- **Differential ‘1’:** D+ high, D− low
    
- **Differential ‘0’:** D+ low, D− high
    

---

**Encoding: NRZ-I with Bit Stuffing**

- **NRZ-I rules:**
    
    - Logic ‘1’ → **no change** in voltage level.
        
    - Logic ‘0’ → **transition** in voltage level.
        
- Without transitions, sync would drift, so USB uses **bit stuffing**:
    
    - After **6 consecutive ‘1’s**, USB inserts a **‘0’** (forces a transition).
        
    - Receiver removes stuffed bits automatically.
        

---

**Wire Functions (from table in slide)**

|Name|Color|Function|
|---|---|---|
|**VBUS**|Red|5V power|
|**D-**|White|Data (−), 3.3V|
|**D+**|Green|Data (+), 3.3V|
|**GND**|Black|Ground|

---

**Why USB uses this combination**

- Differential signalling → noise-resistant, supports higher speeds.
    
- NRZ-I → efficient encoding.
    
- Bit stuffing → maintains synchronisation even during long runs of ‘1’s.
    

---

**Key takeaway**  
USB balances **simplicity**, **noise robustness**, and **synchronisation stability** using differential signalling + NRZ-I + bit stuffing.


![[All_slides_nes.pdf#page=198]]  
Week 7 Slide 12 – Bus Topology

**Definition**

- All devices connect to and share a **single common cable** (the bus).
    

---

**Characteristics**

- Devices "tap" into the cable anywhere along its length.
    
- Communication is **broadcast-based**:
    
    - One device transmits → all others see the signal.
        
- Physically simple: no central coordinator or hub required.
    

---

**Advantages**

- **Easy to extend**: new devices can be added anywhere along the bus.
    
- **Well-suited for long, linear environments**, such as:
    
    - Elevators
        
    - Industrial assembly lines
        
    - Vehicles (common in embedded systems)
        

---

**Disadvantages**

- **Cable break = network split** into two isolated segments.
    
- Troubleshooting can be harder because many devices share the same medium.
    
- Only one device may transmit at a time → risk of **collisions**.
    

---

**Usage Context**

- Still very common in embedded controller networks that need simplicity and low wiring cost.
    

---

![[All_slides_nes.pdf#page=199]]  
Week 7 Slide 13 – Star Topology

**Definition**

- Each device connects to a **central hub** using its own dedicated cable.
    

---

**How It Works**

- The hub receives data from one device and **retransmits** it to all others.
    
- This effectively **emulates a bus**, but with point-to-point wiring.
    

---

**Advantages**

- **Easy fault isolation:**
    
    - A cable break affects only the device on that link.
        
- Hub can implement **more advanced features** (filtering, switching, monitoring).
    
- **Scalability:** devices can be added by plugging into the hub.
    

---

**Disadvantages**

- **Single point of failure:** if the hub dies, the entire network fails.
    
- Requires **more cabling** than a bus topology.
    

---

**Usage Context**

- Common in LANs and modern embedded systems where modularity and fault isolation are important.

---

**Comparison: Bus Topology vs. Star Topology**

|Property|**Bus Topology**|**Star Topology**|
|---|---|---|
|**Wiring Structure**|Single shared cable; all devices tap into it|Each device has its own cable to a central hub|
|**Cost & Cabling**|Low cost, minimal cabling|Higher cabling cost; more physical wires|
|**Fault Tolerance**|Cable break splits network into two non-functioning segments|Cable break affects only one device; hub failure breaks entire network|
|**Scalability**|Easy to add devices anywhere along the bus|Easy to add devices at hub; limited by hub port count|
|**Traffic Handling**|Shared medium → collisions possible|Hub manages traffic; no collisions if using a switch|
|**Performance**|Degrades as more devices share the bus|Better overall throughput, especially with switching|
|**Typical Use Cases**|Embedded controllers, vehicles, industrial lines|LANs, modern networks requiring reliability and flexibility|

---

**Key Idea**

- **Bus** = simple, cheap, but fragile under faults.
    
- **Star** = robust to cable faults, scalable, but relies on a central hub.

![[All_slides_nes.pdf#page=200]]  
Week 7 Slide 14 – Data Link Layer

**Role of the Data Link Layer**

- Handles communication between **physically connected nodes** (local networks).
    
- Converts raw bits from the physical layer into structured **frames**.
    
- Ensures reliable link-level communication.
    

---

**Logical Link Control (LLC) Sub-layer**

- Provides a common interface to higher-layer protocols.
    
- Handles:
    
    - **Error control** (ACKs, retransmissions)
        
    - **Flow control** (prevent overwhelming the receiver)
        

---

**Medium Access Control (MAC) Sub-layer**

- Defines **frame format** and **synchronisation** rules.
    
- Responsible for **physical addressing** (e.g., MAC addresses).
    
- Implements **error detection** (e.g., CRC).
    
- Manages **access to a shared medium**:
    
    - Ensures devices take turns
        
    - Prevents or resolves collisions
        

---

**Key Idea**  
Data Link Layer = framing + addressing + managing shared access + error handling.


![[All_slides_nes.pdf#page=201]]  
Week 7 Slide 15 – Frames

**Purpose of Frames**

- Give **structure and meaning** to raw bit sequences.
    
- Allow receivers to detect where a message starts, what it contains, and when it ends.
    

---

**Typical Frame Fields**

|Field|Purpose|
|---|---|
|**Start**|Marks beginning of frame; used for synchronisation.|
|**Header**|Contains protocol info, addresses, configuration, etc.|
|**Payload**|The actual higher-layer data being transported.|
|**Error Detection**|Code (e.g., CRC) generated from header/payload to detect bit errors.|
|**End**|Marks the end of the frame so receiver knows message is complete.|

---

**Key Idea**

- Frames allow reliable, structured communication on a shared medium.
    
- Without framing, devices cannot separate messages or detect corrupted data.
![[All_slides_nes.pdf#page=202]]  
Week 7 Slide 16 – Error Detection

**Core Idea**

- Sender computes an **error-detecting code** from the frame’s data.
    
- Receiver recomputes the code; if results differ → **frame is discarded**.
    

---

**Parity Check**

- Adds **1 extra bit** to enforce odd or even number of ‘1’s.
    
- Detects **single-bit errors**.
    
- Very lightweight but limited detection capability.
    

---

**Cyclic Redundancy Check (CRC)**

- Adds an **N-bit code** (e.g., CRC-15 adds 15 bits).
    
- Receiver performs same polynomial division to verify integrity.
    
- Detects:
    
    - Burst errors
        
    - Multiple-bit errors
        
    - Patterned errors
        
- Widely used in robust systems (Ethernet, CAN, USB).
    

---

**Key Idea**  
Parity = simple, low protection.  
CRC = strong detection for real-world noise and interference.

![[All_slides_nes.pdf#page=203]]  
Week 7 Slide 17 – Sharing the Medium (MAC)

**Problem**

- On a shared medium (e.g., bus), **two devices cannot transmit at the same time**.
    
- If they do, their signals interfere → **collision**.
    

---

**Key Questions**

- How can devices **avoid** collisions?
    
- If a collision happens, how can devices **recover**?
    
- How do we decide **which device gets priority**?
    

---

**MAC Responsibilities**

- Coordinate access so only one device transmits at a time.
    
- Provide mechanisms to detect or avoid collisions.
    
- Ensure fair or priority-based transmission depending on protocol.
    

---

**Takeaway**  
Medium Access Control determines **who talks when**, ensuring safe and organised communication on a shared channel.

![[All_slides_nes.pdf#page=204]]  
Week 7 Slide 18 – Polling

**How Polling Works**

- A **coordinator** (master) polls devices one by one.
    
- A device **may only transmit when polled**.
    
- All communication flows through the coordinator.
    

---

**Example**

- Polling order (flexible):  
    Device 1 → Device 2 → Device 3 → Device 3 → Device 4 → Device 1 → …
    

Coordinator can give more slots to devices needing more bandwidth.

---

**Advantages**

- **Simple** and predictable.
    
- **Bounded latency:** worst-case wait time is known.
    
- Supports **prioritisation** by adjusting polling frequency.
    

---

**Disadvantages**

- **Overhead:** many control messages.
    
- **No device-to-device communication** (everything goes through coordinator).
    
- **Not scalable** — adding many devices slows the cycle.
    
- **Single point of failure:** coordinator fails → entire network stops.
    

---

**Key takeaway**  
Polling gives controlled, predictable access but lacks flexibility and robustness.

![[All_slides_nes.pdf#page=205]]  
Week 7 Slide 19 – CSMA (Carrier Sense Multiple Access)

**Core Principle: Listen Before Talk**

- Device monitors the medium (**carrier sense**):
    
    - If **idle**, it transmits.
        
    - If **busy**, it waits until the line becomes idle.
        

---

**Collision Behaviour**

- If two devices transmit nearly simultaneously:
    
    - Their signals overlap → **collision**.
        
    - Neither transmitter initially knows the collision occurred.
        
    - Receivers see corrupted data (shown as **red** on the slide).
        

---

**Properties**

- Works well in **low traffic** situations.
    
- Simple to implement.
    
- Still allows collisions because sensing is not instantaneous.
    

---

**Visual Meaning from Slide**

- **Blue:** device transmitting.
    
- **Green:** device receiving.
    
- **Red:** corrupted reception due to collision.
    

---

**Key takeaway**  
CSMA reduces collisions by sensing the medium, but cannot eliminate them—especially under higher loads.

![[All_slides_nes.pdf#page=206]]  
Week 7 Slide 20 – CSMA/CD (Collision Detection)

**Collision Detection (CD)**

- While transmitting, a device **also listens** to the medium.
    
- If it detects a mismatch between what it sends and what it receives → **collision detected**.
    

---

**What Happens During a Collision**

- Transmission stops immediately.
    
- Device waits a **random time** before retrying.
    
- Prevents wasting bandwidth on long corrupted transmissions.
    

---

**Advantages**

- **Early collision termination** → saves bandwidth.
    
- Enables **retransmissions** without corrupting the entire frame.
    
- Improved efficiency compared to plain CSMA in moderate traffic.
    

---

**Visual Meaning from Slide**

- **Blue:** transmitting + listening
    
- **Green:** receiving
    
- **Red:** receiving corrupted data (collision)
    

---

**Key takeaway**  
CSMA/CD detects collisions during transmission and stops quickly, improving performance on shared Ethernet-like media.

![[All_slides_nes.pdf#page=208]]  
Week 7 Slide 22 – Probabilistic Prioritisation

**Concept**

- Devices can be given **different priorities** by assigning them **different initial contention window sizes (CW)**.
    
- Smaller CW → higher chance to transmit first.
    

---

**Priority Through CW**

- **High-priority devices:**
    
    - Start with **small CW** (e.g., CW = 1).
        
    - Less waiting → transmit sooner.
        
- **Low-priority devices:**
    
    - Start with **large CW** (e.g., CW = 8).
        
    - More waiting → reduced chance of accessing medium.
        

---

**Important Note**

- Despite differing CW values, transmissions are still **probabilistic**:
    
    - A low-priority device _can_ transmit before a high-priority one **by luck**.
        

---

**Visual Meaning**

- Blue = transmit & listen
    
- Green = receive
    
- Red = receive with errors
    

---

**Key takeaway**  
The binary exponential backoff mechanism can be tuned to favour certain devices, enabling **soft prioritisation** in shared-medium networks.

![[All_slides_nes.pdf#page=209]]  
Week 7 Slide 23 – CSMA/CA (Collision Avoidance)

**Why Collision Avoidance?**

- Used when a device **cannot detect collisions while transmitting** (e.g., wireless).
    
- Collisions are more expensive because they **cannot be stopped early**.
    

---

**Mechanism**

- If the channel is **busy**, device waits a **random time** before attempting its _first_ transmission.
    
- After a collision, uses **binary exponential backoff** (same idea as CSMA/CD but applied earlier).
    

---

**Core Idea**

- Reduce the _likelihood_ of collisions instead of detecting them.
    
- Works by spacing out transmissions in time.
    

---

**Trade-offs**

- Lower collision probability.
    
- **Wastes bandwidth** due to random waiting, even when no one else is transmitting.
    

---

**Visual Meaning**

- Blue = transmit
    
- Green = receive
    

---

**Key takeaway**  
CSMA/CA avoids collisions by adding controlled randomness before transmitting, essential in systems where collisions cannot be detected directly.

### **Comparison: CSMA vs. CSMA/CD vs. CSMA/CA**

|Feature|**CSMA**|**CSMA/CD**|**CSMA/CA**|
|---|---|---|---|
|**Stands for**|Carrier Sense Multiple Access|Carrier Sense Multiple Access with Collision Detection|Carrier Sense Multiple Access with Collision Avoidance|
|**Medium Access Method**|Listen before transmit|Listen before transmit + detect collisions|Listen before transmit + avoid collisions|
|**Collision Handling**|Collisions may occur and are only detected by receivers|Device detects collision **during** transmission and aborts|Device cannot detect collisions; tries to **avoid** them|
|**What happens on collision**|Transmission fails; must retry|Transmission stops immediately; random backoff|After collision, waits using backoff; prevention more important|
|**Use Cases**|Simple shared-wired networks|Classic Ethernet (wired, half-duplex)|Wireless networks (Wi-Fi), systems unable to sense while sending|
|**Efficiency under low load**|Good|Very good|Good|
|**Efficiency under high load**|Poor due to collisions|Better than CSMA (early abort)|Moderate; backoff delays increase|
|**Hardware Requirements**|Basic sensing|Ability to sense while transmitting|No collision detection hardware needed|
|**Key Weakness**|Many collisions under high load|Not suitable for wireless (cannot detect collisions)|More overhead due to random waiting|

---

**Summary**

- **CSMA:** simple, but collisions waste time.
    
- **CSMA/CD:** improves efficiency by stopping transmissions early.
    
- **CSMA/CA:** avoids collisions where detection is impossible.
    

![[All_slides_nes.pdf#page=210]]  
Week 7 Slide 24 – CSMA Trade-offs

**Pros**

- **Low latency in low traffic:**
    
    - If medium is idle, device transmits immediately (no polling or scheduling delays).
        
- **Flexible network structure:**
    
    - Easy to add or remove devices.
        
- **Supports probabilistic prioritisation:**
    
    - Smaller contention windows (CW) give higher priority devices more chances to transmit first.
        

---

**Cons**

- **Unbounded latency:**
    
    - Under heavy traffic, a device may wait indefinitely for a free medium.
        
- **Poor efficiency in high traffic:**
    
    - Many collisions → much time wasted on retries.
        
- **Throughput collapses** under sustained congestion.
    

---

**Key takeaway**  
CSMA works extremely well in **light-load** networks, but becomes unreliable, inefficient, and unpredictable when traffic increases.

![[All_slides_nes.pdf#page=211]]  
Week 7 Slide 25 – CAN Bus

**What CAN Is**

- A robust, widely used **controller network** bus (especially in vehicles).
    
- Designed for **real-time**, **reliable**, and **fault-tolerant** communication.
    

---

**Key Characteristics**

- **Broadcast-based:**
    
    - All nodes see every frame; higher layers decide what to process.
        
- **Multi-master:**
    
    - Any node may initiate transmission.
        
- **Prioritised access:**
    
    - Messages include an ID that determines priority.
        

---

**Physical Layer**

- Uses **differential signalling** over two balanced lines:
    
    - **CANH** (high line)
        
    - **CANL** (low line)
        

---

**Why CAN Is Popular**

- Highly reliable in noisy automotive environments.
    
- Very deterministic behaviour under low to moderate loads.
    
- Strong error detection and handling mechanisms.
    

---

**Key takeaway**  
CAN bus offers a **robust**, **priority-aware**, and **fault-tolerant** communication method ideal for embedded and automotive systems.

![[All_slides_nes.pdf#page=212]]  
Week 7 Slide 26 – CAN Bus (Diagram Overview)

**What the Slide Shows**

- A visual layout of a CAN bus with:
    
    - Multiple nodes connected along a **single differential pair** (CANH & CANL).
        
    - Termination resistors at both ends for signal integrity.
        
    - Nodes tapping into the bus in parallel.
        

---

**Core Points Illustrated**

- **Bus topology:** all devices share the same physical cable.
    
- **Multi-master capability:** any node may try to transmit.
    
- **Differential signalling:**
    
    - CANH and CANL carry opposite signals.
        
    - Increases noise immunity.
        
- **Termination:**
    
    - Needed at both ends to prevent reflections that distort signals.
        

---

**Behaviour Emphasised by the Diagram**

- Every transmitted bit is seen by all nodes instantly.
    
- Arbitration (handled at the bit level) ensures only one node continues transmitting.
    
- Physical layer enforces robustness across the entire shared network.
    

---

**Key takeaway**  
The diagram reinforces that CAN is a **shared differential bus** with termination and equal visibility of all traffic across every node.


![[All_slides_nes.pdf#page=213]]  
Week 7 Slide 27 – CAN Bus Signal

**Differential Signalling Basics**

- CAN uses two balanced lines:
    
    - **CANH (High line)**
        
    - **CANL (Low line)**
        
- Logical value determined by the **difference** between CANH and CANL.
    

---

**Recessive vs. Dominant Bits**

- **Recessive (‘1’):**
    
    - Bus is _not_ actively driven.
        
    - Levels set by resistors.
        
- **Dominant (‘0’):**
    
    - Bus is actively driven by the transmitter.
        
    - Overrides recessive state on the bus.
        

---

**Low-Speed CAN (≤ 125 Kbps)**

- To send **‘1’ (recessive):**
    
    - CANH → GND
        
    - CANL → 5V
        
    - Done via pull-up/pull-down resistors.
        
- To send **‘0’ (dominant):**
    
    - CANH actively driven to 5V
        
    - CANL actively driven to GND
        

---

**High-Speed CAN (≤ 1 Mbps)**

- To send **‘1’ (recessive):**
    
    - Pull-up resistors drive both CANH and CANL to **2.5V**.
        
- To send **‘0’ (dominant):**
    
    - CANH actively driven to **3.5V**
        
    - CANL actively driven to **1.5V**
        

---

**Why the Levels Matter**

- High-speed uses smaller voltage swings → faster transitions.
    
- Differential behaviour provides **noise immunity** and **robust bit detection**.4

Here is a clean comparison table for **Low-Speed CAN vs. High-Speed CAN**:

---

### **Comparison: Low-Speed CAN vs. High-Speed CAN**

|Feature|**Low-Speed CAN**|**High-Speed CAN**|
|---|---|---|
|**Max Bitrate**|Up to **125 Kbps**|Up to **1 Mbps**|
|**Use of Drivers**|‘1’ (recessive) created via resistors; only dominant is actively driven|Both lines actively driven during dominant; recessive created by biasing resistors|
|**Recessive (‘1’) Level**|CANH → 0V (GND), CANL → 5V|CANH → 2.5V, CANL → 2.5V|
|**Dominant (‘0’) Level**|CANH → 5V, CANL → 0V|CANH → 3.5V, CANL → 1.5V|
|**Voltage Swing**|Large (5V difference)|Smaller (2V difference)|
|**Transition Speed**|Slower (larger swings)|Faster (smaller swings)|
|**Primary Use Case**|Body electronics, comfort systems|Powertrain, real-time safety-critical systems|
|**Wiring Robustness**|More tolerant to wiring faults (fault-tolerant CAN)|Requires good wiring for high speed|
|**EMI Considerations**|Higher EMI due to large swings|Lower EMI due to reduced voltage range|
|**Cost**|Cheaper hardware|Slightly more expensive PHY|

---

**Key Summary**

- **Low-Speed CAN** favors robustness and fault tolerance.
    
- **High-Speed CAN** favors speed and faster transitions with lower EMI.

![[All_slides_nes.pdf#page=214]]  
Week 7 Slide 28 – Dominant State Wins!

**Dominant vs. Recessive Logic**

- In CAN, bits are defined as:
    
    - **Dominant = ‘0’**
        
    - **Recessive = ‘1’**
        

**Active vs. Passive Driving**

- Dominant (‘0’) is **actively driven** by the transmitter.
    
- Recessive (‘1’) is **passively pulled** by resistors.
    

---

**What Happens During Simultaneous Transmission**

- If one node sends **‘0’ (dominant)** and another sends **‘1’ (recessive)**:
    
    - The bus becomes **dominant (‘0’)**.
        
- This is because the actively driven signal overrides the passive state.
    

---

**Why This Matters**

- Allows **non-destructive arbitration**:
    
    - Nodes can detect if they "lost" arbitration by monitoring the bus.
        
    - A node sending ‘1’ but reading ‘0’ knows another node with higher priority is transmitting.
        

---

**Key takeaway**  
On a CAN bus, **dominant (‘0’) always wins**, enabling predictable, collision-free arbitration.


![[All_slides_nes.pdf#page=215]]  
Week 7 Slide 29 – CSMA/CD with Arbitration (CAN Arbitration)

**Arbitration Process**

- Every CAN node has a unique **11-bit ID**.
    
- Lower numeric ID = **higher priority**.
    
- Arbitration happens **bit-by-bit** immediately after the SOF.
    

---

**SOF (Start of Frame)**

- Always a **dominant ‘0’**.
    
- Used to synchronise all nodes before arbitration begins.
    

---

**How Arbitration Works**

1. Each node begins sending its ID bits simultaneously.
    
2. Node also **monitors the bus** while transmitting.
    
3. If a node transmits **‘1’ (recessive)** but reads **‘0’ (dominant)**:
    
    - It **loses arbitration**.
        
    - It stops transmitting immediately.
        
4. The node sending the highest-priority (lowest ID) message **continues without interruption**.
    

---

**Key Feature**

- Collisions are **non-destructive**.
    
- Only one frame survives, and it is always the highest-priority one.
    

---

**Outcome**

- Deterministic transmission behaviour.
    
- Critical messages (low IDs) always get through first.

![[All_slides_nes.pdf#page=216]]  
Week 7 Slide 30 – CAN Bus Frame Types

**Communication Model**

- **Sender-initiated**, **broadcast-based**:
    
    - All nodes receive every frame.
        
    - Higher layers decide whether to process or ignore it.
        

---

**Bit Stuffing**

- To maintain synchronisation:
    
    - After **5 consecutive identical bits**, a bit of **opposite polarity** is inserted.
        

---

### **Two Identifier Formats**

- **Standard frame:**
    
    - **11-bit ID** → 2048 possible identifiers.
        
- **Extended frame:**
    
    - **29-bit ID** → 537 million identifiers.
        

---

### **Four CAN Frame Types**

|Frame Type|Purpose|
|---|---|
|**Data Frame**|Contains actual data associated with an ID.|
|**Remote Frame**|Requests data from a node (same ID field).|
|**Error Frame**|Sent when a node detects an error; forces retransmission.|
|**Overload Frame**|Inserts delay between frames to give nodes more time.|

---

**Key takeaway**  
CAN supports multiple frame types to enable data transfer, requests, error handling, and timing control within a shared bus system.


![[All_slides_nes.pdf#page=217]]  
Week 7 Slide 31 – Standard Data Frame (CAN)

**Frame Fields**

1. **SOF (Start of Frame, 1 bit)**
    
    - Must be **dominant (‘0’)**.
        
    - Signals the start of a frame.
        
2. **ID (Identifier, 11 bits)**
    
    - Identifies the message and determines **priority**.
        
    - Lower binary value = higher priority.
        
3. **RTR (Remote Transmission Request, 1 bit)**
    
    - Must be **dominant (‘0’)** for data frames.
        
    - Indicates this is _not_ a remote request.
        
4. **IDE (Identifier Extension, 1 bit)**
    
    - Must be **dominant (‘0’)** for standard (11-bit) frames.
        
5. **R0 (Reserved, 1 bit)**
    
    - Reserved for future use.
        
6. **DLC (Data Length Code, 4 bits)**
    
    - Specifies number of data bytes (0–8 bytes).
        
7. **DATA (0–64 bits)**
    
    - Actual payload: 0 to 8 bytes.
        
8. **CRC (16 bits)**
    
    - CRC-15 + 1 delimiter bit (recessive ‘1’).
        
    - Provides strong error detection.
        
9. **ACK (2 bits)**
    
    - Transmitter sends recessive ‘1’.
        
    - Any node that received frame correctly overwrites it with dominant ‘0’.
        
    - Second bit is a recessive delimiter.
        
10. **EOF (End of Frame, 7 bits)**
    

- Must be all **recessive ‘1’**.
    

11. **IFS (Inter-Frame Space, 3 bits)**
    

- Must be all **recessive ‘1’**.
    
- Ensures spacing between frames.
    

---

**Key takeaway**  
The standard CAN data frame is tightly structured for reliability, priority arbitration, and robust error detection.

![[All_slides_nes.pdf#page=218]]  
Week 7 Slide 32 – Standard Remote Frame (CAN)

**Purpose**

- Used to **request data** from another node.
    
- Contains _no_ data field; instead it signals that the sender wants the data frame associated with the same ID.
    

---

**Frame Fields**

1. **SOF (1 bit)**
    
    - Dominant ‘0’ → start of frame.
        
2. **ID (11 bits)**
    
    - Identifies which data frame is being requested.
        
    - Priority works the same way as in data frames.
        
3. **RTR (1 bit)**
    
    - **Recessive ‘1’** for _remote frames_.
        
    - This distinguishes it from a data frame (where RTR = 0).
        
4. **IDE (1 bit)**
    
    - Must be **dominant ‘0’** for standard frames.
        
5. **R0 (1 bit)**
    
    - Reserved.
        
6. **DLC (4 bits)**
    
    - Specifies expected data length of the response (0–8 bytes).
        
7. **CRC (16 bits)**
    
    - Same CRC mechanism as data frames: 15-bit CRC + 1 delimiter bit.
        
8. **ACK (2 bits)**
    
    - Same as in data frames:
        
        - Transmitter sends recessive ‘1’
            
        - Receivers overwrite with dominant ‘0’ if received correctly
            
9. **EOF (7 bits)**
    
    - All recessive ‘1’s.
        
10. **IFS (3 bits)**
    

- Recessive ‘1’s separating frames.
    

---

**Key takeaway**  
Remote frames allow one node to _ask_ another node for data using the same ID that identifies the corresponding data frame.


![[All_slides_nes.pdf#page=219]]  
Week 7 Slide 33 – Extended Data Frame (CAN)

**Purpose**

- Supports **29-bit identifiers** for systems needing many unique message IDs.
    
- Used in more complex automotive/industrial networks.
    

---

### **Extended Data Frame Fields**

1. **SOF (1 bit)**
    
    - Dominant ‘0’.
        
2. **ID A (11 bits)**
    
    - Most significant part of the 29-bit ID.
        
3. **SRR (1 bit)**
    
    - Substitute Remote Request.
        
    - Always **recessive ‘1’**.
        
    - Used to ensure proper arbitration with standard frames.
        
4. **IDE (1 bit)**
    
    - **Recessive ‘1’** → indicates extended frame.
        
5. **ID B (18 bits)**
    
    - Least significant part of the 29-bit ID.
        
    - Together with ID A → full 29-bit identifier.
        
6. **RTR (1 bit)**
    
    - Dominant ‘0’ for data frames.
        
7. **RB (2 bits)**
    
    - Reserved.
        
8. **DLC (4 bits)**
    
    - Number of data bytes (0–8).
        
9. **DATA (0–64 bits)**
    
    - Payload.
        
10. **CRC (16 bits)**
    

- 15-bit CRC + 1-bit delimiter.
    

11. **ACK (2 bits)**
    

- Acknowledgement mechanism.
    

12. **EOF (7 bits)**
    

- Recessive ‘1’s.
    

13. **IFS (3 bits)**
    

- Recessive spacing between frames.
    

---

## **Comparison: Standard Data Frame vs. Remote Frame vs. Extended Data Frame**

|Feature|**Standard Data Frame**|**Standard Remote Frame**|**Extended Data Frame**|
|---|---|---|---|
|**Purpose**|Transmits data (0–8 bytes)|Requests data from another node|Transmits data with a long 29-bit ID|
|**Identifier Size**|11-bit|11-bit|29-bit (ID A + ID B)|
|**RTR Bit**|**0 (dominant)** → data frame|**1 (recessive)** → request frame|**0 (dominant)** → data frame|
|**IDE Bit**|0 (standard)|0 (standard)|**1 (extended)**|
|**Data Field**|Yes|**No**|Yes|
|**Arbitration Strength**|Shorter ID → may win arbitration over extended|Same as standard but has RTR=1|Longer ID → lower priority than standard during arbitration|
|**Use Case**|Normal CAN messaging|Asking for data via ID|Larger networks needing many IDs|

---

### **Key Differences (Explained Simply)**

- **Standard Data Frame:**  
    Contains actual payload. Most common frame type.
    
- **Remote Frame:**  
    Asks _another node_ to send its data frame.  
    (Think of it as: “Please send me the data for this ID.”)
    
- **Extended Data Frame:**  
    Same idea as the standard data frame, but with **much larger identifier space** (29 bits).  
    Used when 11 bits (2048 IDs) is not enough.
    
![[All_slides_nes.pdf#page=220]]  
Week 7 Slide 34 – CAN Bus: Advantages and Disadvantages

---

### **Advantages**

- **Low latency in light traffic:**
    
    - High-priority messages get through immediately due to arbitration.
        
- **Strong prioritisation:**
    
    - Lower ID = higher priority → critical messages always win the bus.
        
- **High robustness:**
    
    - Extensive error detection:
        
        - CRC
            
        - ACK mechanism
            
        - SOF, EOF, delimiters
            
        - Bit monitoring (transmitted bits are also read)
            
        - Bit stuffing rules (no more than 5 identical bits)
            
- **Non-destructive arbitration:**
    
    - Collisions do _not_ corrupt the winning message; only the losing node backs off.
        

---

### **Disadvantages**

- **Unfair to low-priority nodes:**
    
    - In heavy traffic, high-priority frames dominate → low-priority frames can starve.
        
- **Poor latency for low-priority messages:**
    
    - Some nodes may wait a long time before transmitting.
        

---

### **Key takeaway**

CAN bus is **robust and deterministic** for high-priority communication but can suffer from **latency and starvation** for low-priority traffic under heavy load.

![[All_slides_nes.pdf#page=221]]  
Week 7 Slide 35 – IEEE 802.3: Ethernet

**What Ethernet Is**

- A standardized family of **wired LAN protocols**.
    
- Evolving since **1983**, originally from Xerox (1976 prototype at 2.94 Mbps).
    
- Today supports speeds up to **400 Gbps** (data centers).
    

---

**Historical Standards**

- **10BASE5** → first official Ethernet standard (10 Mbps).
    
- Evolved through 10 Mbps → 100 Mbps → 1 Gbps → 10+ Gbps → 400 Gbps.
    

---

**Frame Size**

- Up to **1500 bytes of payload** per Ethernet frame.
    

---

**Key Characteristics**

- Widely adopted for local networking.
    
- Scalable across decades of speed improvements.
    
- Backbone of modern communication infrastructure.
    

---

**Key takeaway**  
Ethernet is a **highly scalable**, widely used wired networking standard that has grown from early 10 Mbps coax systems to today’s multi-hundred-gigabit links.

![[All_slides_nes.pdf#page=222]]  
Week 7 Slide 36 – Ethernet: MAC Addresses

**MAC Address Basics**

- Unique **48-bit (6-byte)** identifier assigned to every Ethernet interface.
    
- Written in hexadecimal, e.g.:  
    **AA:BB:CC:DD:EE:FF**
    

---

### **MAC Address Structure**

|Part|Size|Meaning|
|---|---|---|
|**OUI (Organizationally Unique Identifier)**|24 bits|Identifies the manufacturer (assigned by IEEE)|
|**Device Identifier**|24 bits|Uniquely identifies the hardware from that manufacturer|

---

### **Special Address**

- **FF:FF:FF:FF:FF:FF** → **Broadcast address**
    
    - Frame is delivered to **all nodes** on the network.
        

---

**Why MAC Addresses Matter**

- Used at the **Data Link Layer** for physical addressing.
    
- Ensure that Ethernet frames reach the correct device on a LAN.
    
- Hardware-level identification; does not change during normal operation.
    

---

**Key takeaway**  
MAC addresses provide globally unique, hardware-based identification for Ethernet devices, enabling correct frame delivery within local networks.

![[All_slides_nes.pdf#page=223]]  
Week 7 Slide 37 – Ethernet Frame

**Purpose of the Frame**

- Defines how data is structured on Ethernet links.
    
- Ensures synchronisation, addressing, payload handling, and error detection.
    

---

### **Ethernet Frame Fields**

1. **Preamble (7 bytes)**
    
    - Pattern: `10101010` repeated.
        
    - Used for **synchronisation** between sender and receiver.
        
2. **SOF (Start of Frame Delimiter, 1 byte)**
    
    - `10101011`
        
    - Marks the **start** of the actual frame.
        
3. **Destination MAC (6 bytes)**
    
    - MAC address of the intended receiver.
        
    - First thing in the frame so devices can quickly decide whether to process or ignore.
        
4. **Source MAC (6 bytes)**
    
    - MAC address of the sender.
        
5. **Length/Type (2 bytes)**
    
    - If value **< 1500** → payload length.
        
    - If value **≥ 1536** → identifies protocol type (e.g., IPv4, IPv6, ARP).
        
6. **Payload (46–1500 bytes)**
    
    - The actual data.
        
    - If less than 46 bytes, **padding** is added to meet minimum size.
        
7. **FCS (Frame Check Sequence, 4 bytes)**
    
    - CRC-32 for error detection.
        
8. **ESD (End of Stream Delimiter, 4 bytes)**
    
    - Marks the **end** of the frame.
        

---

**Key takeaway**  
Ethernet frames provide a rigid structure that enables reliable communication, quick filtering by MAC addresses, and strong error checking through CRC-32.


![[All_slides_nes.pdf#page=224]]  
Week 7 Slide 38 – The Original Ethernet

**Historical Implementation**

- **10BASE2** and **10BASE5** were the earliest Ethernet physical layers.
    
- Operated at **10 Mbps** over **coaxial cable**.
    
- Used **half-duplex** communication (cannot send and receive simultaneously).
    

---

### **Encoding**

- **Manchester encoding**:
    
    - ‘0’ = high → low transition
        
    - ‘1’ = low → high transition
        
- Provides strong synchronisation through guaranteed transitions.
    

---

### **Topology**

- **Bus topology** with coax cable.
    
- Repeater hubs used to extend cable length.
    
- Entire network shared the same medium → everyone could "hear" everyone.
    

---

### **Medium Access**

- **CSMA/CD** used for collision handling:
    
    - Listen before transmitting.
        
    - Detect collisions while transmitting.
        
    - Abort and retry using exponential backoff.
        

---

**Key takeaway**  
Original Ethernet was a coax-based, half-duplex, shared-medium network using Manchester encoding and CSMA/CD—simple but limited compared to modern switched Ethernet.

![[All_slides_nes.pdf#page=225]]  
Week 7 Slide 39 – Ethernet Switch

**Purpose of a Switch**

- Enables **efficient, collision-free** Ethernet communication.
    
- Unlike repeater hubs, switches do **not** broadcast everything to every port.
    

---

### **How a Switch Works**

#### **MAC Address Learning**

- Switch builds a **MAC address table**:
    
    - Maps each MAC address → the port it was last seen on.
        
- Entries have an **expiration timer** to remove stale mappings.
    

#### **Frame Forwarding**

- If destination MAC is **known**:  
    → Frame forwarded **only to the correct port**.
    
- If destination MAC is **unknown**:  
    → Frame is **flooded** to all ports (like a hub).
    

---

### **Advantages**

- **No collisions** in switched Ethernet (full-duplex links).
    
- **Higher aggregate throughput**—multiple conversations occur simultaneously.
    
- **Efficient use of bandwidth** by avoiding unnecessary broadcasting.
    

---

**Key takeaway**  
The Ethernet switch introduces intelligence to the network: learning MAC addresses, forwarding frames efficiently, and eliminating collisions. This enabled modern scalable, high-performance LANs.

![[All_slides_nes.pdf#page=226]]  
Week 7 Slide 40 – The Common Ethernet

**Modern Physical Layers**

- **10BASE-T (10 Mbps)**
    
- **100BASE-TX (100 Mbps)**  
    Both use **twisted-pair copper cables** and support **peer-to-peer** and **switched** topologies.
    

---

### **Full-Duplex Operation**

- Separate differential pairs for transmit (TX+, TX−) and receive (RX+, RX−).
    
- Allows simultaneous sending and receiving → **no collisions**.
    
- Medium no longer shared → CSMA/CD not needed.
    

---

### **Encoding Methods**

- **10BASE-T:**
    
    - Uses **Manchester encoding** (same as original Ethernet).
        
- **100BASE-TX:**
    
    - Uses **4B/5B encoding** followed by **MLT-3** signalling:
        
        - **4B/5B:** Ensures enough transitions for clock recovery.
            
        - **MLT-3:** Three-level signalling that reduces EMI and allows 100 Mbps operation.
            

---

**Key takeaway**  
Common twisted-pair Ethernet (10/100BASE) replaces coaxial buses with full-duplex, collision-free links using modern encoding schemes for higher performance and reliability.

![[All_slides_nes.pdf#page=227]]  
Week 7 Slide 41 – Multi-Level Transition 3 (MLT-3)

**MLT-3 Signalling**

- Uses **three voltage levels**:
    
    - **−1**, **0**, **+1**
        
- Follows a fixed transition sequence:
    
    - −1 → 0 → +1 → 0 → −1 → …
        
- **Encoding rule:**
    
    - Bit **‘0’** → **no transition**
        
    - Bit **‘1’** → **transition to next level**
        

---

### **Advantages**

- Lower frequency transitions → **reduced EMI**.
    
- Enables **higher data rates** without requiring excessive bandwidth.
    

---

### **Disadvantages**

- Long sequences of ‘0’s produce **no transitions**, which may lead to **loss of synchronisation**.
    
- Requires a higher-level encoding (like **4B/5B**) to ensure enough transitions.
    

---

### **Example (from slide):**

|Data Bit|1|1|1|0|1|1|0|1|
|---|---|---|---|---|---|---|---|---|
|Code|−1 → 0|0 → +1|+1 → 0|0 (no change)|0 → −1|−1 → 0|0 (no change)|0 → +1|

---

**Key takeaway**  
MLT-3 is a bandwidth-efficient signalling method used in 100BASE-TX to enable high-speed Ethernet while keeping EMI low, but it requires transition-rich encoding like 4B/5B to function reliably.

![[All_slides_nes.pdf#page=228]]  
Week 7 Slide 42 – 4B/5B Encoding

**Purpose**

- Ensures enough **signal transitions** for reliable clock recovery when used with MLT-3.
    
- Encodes **4 data bits** into **5-bit symbols**.
    

---

### **How It Works**

- 4-bit input (16 possible values) → mapped to 5-bit code (32 possible values).
    
- Unused 5-bit patterns reserved for:
    
    - Control symbols
        
    - Avoiding long runs of zeros
        
    - Maintaining transition density
        

---

### **Benefits**

- Guarantees at least **two ‘1’ bits** in many 5-bit symbols → ensures transitions.
    
- Prevents long sequences without edges → avoids loss of synchronisation.
    
- After encoding, the 5-bit symbols are transmitted using **MLT-3** signalling.
    

---

### **Impact on Transmission Rate**

- Due to 4→5 overhead, transmitting 100 Mbps of data requires:  
    **125 Mbps symbol rate**  
    (100 Mbps × 5 / 4 = 125 Mbps)
    

---

### **Key takeaway**

4B/5B adds controlled redundancy to ensure frequent transitions, enabling MLT-3 to operate reliably at 100 Mbps in 100BASE-TX Ethernet.

![[All_slides_nes.pdf#page=229]]  
Week 7 Slide 43 – The Automotive Ethernet

**Motivation**

- Modern vehicles need higher data rates than CAN can provide (e.g., cameras, radar, infotainment).
    
- Automotive constraints:
    
    - Reduce **weight**, **cost**, **EMI**, and power consumption.
        
    - Cable lengths in vehicles are short (≤ 15 m), so long-distance PHY features are unnecessary.
        

---

### **100BASE-T1 (Automotive Ethernet)**

- Uses **one** twisted pair instead of two.
    
- Supports **full-duplex** communication on a single pair through **echo cancellation**.
    
- Lower cabling weight and cost.
    

---

### **Encoding Pipeline**

1. **4B3B encoding**
    
    - Converts 4 data bits → 3 coded bits (transition-rich).
        
2. **3B2T encoding**
    
    - Converts 3 bits → 2 ternary symbols (three-level signals).
        
3. **PAM-3 modulation**
    
    - Maps ternary symbols to **−1 V, 0 V, +1 V**.
        

---

### **Key Features**

- Meets automotive EMI and robustness requirements.
    
- Transparent to the MAC layer (works like regular Ethernet at higher layers).
    
- Optimised for short in-vehicle links, not office networks.
    

---

**Key takeaway**  
Automotive Ethernet (100BASE-T1) achieves high-speed communication over a **single lightweight pair** using advanced encoding and echo cancellation, designed specifically for vehicle environments.

![[All_slides_nes.pdf#page=230]]  
Week 7 Slide 44 – 4B3B → 3B2T → PAM-3 Modulation (Automotive Ethernet)

---

### **4B3B Encoding**

- Input: **4-bit data** at **25 MHz** (→ 100 Mbps total).
    
- Output: **3-bit symbols** at **33.33 MHz**.
    
- Purpose:
    
    - Compress 4 bits into 3 coded bits.
        
    - Provide **transition-rich codes** suitable for further ternary mapping.
        

---

### **3B2T Encoding**

- Input: **3-bit symbols** from 4B3B at **33.33 MHz**.
    
- Output: **2 ternary bits** (TA, TB) at **66.66 MHz**.
    
- “Ternary bits” have **3 states** instead of 2.
    
- Purpose:
    
    - Convert binary-coded data into ternary symbols for PAM-3.
        

---

### **PAM-3 Modulation**

- Maps each ternary bit to **three voltage levels**:
    
    - **−1 V**, **0 V**, **+1 V**
        
- Produces the actual physical signal on the wire.
    

---

### **Table (from slide)**

Mapping from **3-bit data → TA, TB** (two ternary symbols):

|3-bit Data|TA|TB|
|---|---|---|
|000|−1|−1|
|001|−1|0|
|010|−1|1|
|011|0|−1|
|SSD/ESD|0|0|
|100|0|1|
|101|1|−1|
|110|1|0|
|111|1|1|

(SSD/ESD = Start/End of Stream Delimiters)

---

### **Key takeaway**

This 3-stage encoding chain converts binary data into ternary PAM-3 signals with guaranteed transitions, enabling **100 Mbps full-duplex** communication over a **single twisted pair** in automotive Ethernet.

![[All_slides_nes.pdf#page=231]]  
Week 7 Slide 45 – Echo Cancellation

**Why Echo Cancellation Is Needed**

- 100BASE-T1 uses **only one twisted pair** for _both_ transmitting and receiving.
    
- The transmitter’s own signal would overwhelm the incoming signal if not removed.
    
- Echo cancellation allows **full-duplex communication** on a single pair.
    

---

### **How Echo Cancellation Works**

1. The PHY knows the exact signal it is transmitting.
    
2. It measures the combined signal on the wire (transmit + receive).
    
3. It **subtracts** its own transmitted signal (the “echo”) from the measured line signal.
    
4. The remaining signal is the **actual data coming from the other device**.
    

---

### **Benefits**

- Enables **simultaneous TX and RX** on the same wire pair.
    
- Reduces cabling weight and cost (no need for separate TX and RX pairs).
    
- Improves EMI characteristics by reducing differential emissions.
    

---

**Key takeaway**  
Echo cancellation lets Automotive Ethernet achieve full-duplex communication over a **single lightweight twisted pair**, which is essential for reducing vehicle wiring complexity.

![[All_slides_nes.pdf#page=232]]  
Week 7 Slide 46 – Comparison: Classic Ethernet (100BASE-TX) vs. Automotive Ethernet (100BASE-T1)

---

### **Side-by-Side Comparison**

|Property|**100BASE-TX (Classic Ethernet)**|**100BASE-T1 (Automotive Ethernet)**|
|---|---|---|
|**Data Rate**|100 Mbps|100 Mbps|
|**Baud Rate / Clock**|125 MHz|66.66 MHz|
|**Twisted Pairs Required**|**2 pairs** (one TX, one RX)|**1 pair** (shared TX/RX via echo cancellation)|
|**Line Coding**|4B/5B + MLT-3|4B3B + PAM-3|
|**Max Cable Distance**|~100 m|~15 m|
|**Use Case**|Office / LAN networking|Automotive systems (short links, low EMI, low weight)|
|**Full Duplex**|Yes (separate TX/RX pairs)|Yes (single pair with echo cancellation)|
|**EMI Characteristics**|Higher due to more pairs and transitions|Lower due to PAM-3 and single balanced pair|

---

### **Key Points**

- Both provide **100 Mbps**, but **T1 is optimized for vehicles**, not buildings.
    
- **TX** prioritizes long distance and legacy compatibility.
    
- **T1** prioritizes **weight, EMI, and cost reduction**.


==[Full-duplex](https://www.google.com/search?q=Full-duplex&oq=full+du&gs_lcrp=EgZjaHJvbWUqBwgCEAAYgAQyBggAEEUYOTIHCAEQABiABDIHCAIQABiABDIHCAMQABiABDIHCAQQABiABDIHCAUQABiABDIHCAYQABiABDIHCAcQABiABDIHCAgQABiABDIHCAkQABiABNIBCDQ2MDZqMGo3qAIAsAIA&sourceid=chrome&ie=UTF-8&mstk=AUtExfAAfPMHpm7kFe7s03uh_jBtStil9i_YjfaeYSwPV86_ywhQl1bR2L-rEr3M_ZqklIG2mD8pMDgRgXWAvxuANDtrbOtQ44nKy10FI6qcwLHwUBCNyk8LeO1Oo_0fiNkOrwsdEQ85NTTM5m46v7TRJ3X7cezv7VOcr_CwWCzOiKWuBug&csui=3&ved=2ahUKEwi4i5_fgamRAxWJU1UIHVPTF-wQgK4QegQIARAE) allows simultaneous sending and receiving (like a phone call), offering high performance with two-way, real-time communication, while [half-duplex](https://www.google.com/search?q=half-duplex&oq=full+du&gs_lcrp=EgZjaHJvbWUqBwgCEAAYgAQyBggAEEUYOTIHCAEQABiABDIHCAIQABiABDIHCAMQABiABDIHCAQQABiABDIHCAUQABiABDIHCAYQABiABDIHCAcQABiABDIHCAgQABiABDIHCAkQABiABNIBCDQ2MDZqMGo3qAIAsAIA&sourceid=chrome&ie=UTF-8&mstk=AUtExfAAfPMHpm7kFe7s03uh_jBtStil9i_YjfaeYSwPV86_ywhQl1bR2L-rEr3M_ZqklIG2mD8pMDgRgXWAvxuANDtrbOtQ44nKy10FI6qcwLHwUBCNyk8LeO1Oo_0fiNkOrwsdEQ85NTTM5m46v7TRJ3X7cezv7VOcr_CwWCzOiKWuBug&csui=3&ved=2ahUKEwi4i5_fgamRAxWJU1UIHVPTF-wQgK4QegQIARAF) allows sending and receiving but only one direction at a time (like a walkie-talkie)==,

![[All_slides_nes.pdf#page=233]]  
Week 7 Slide 47 – Gigabit Ethernet

---

### **1000BASE-T (1 Gbps Ethernet)**

**Physical Layer**

- Uses **4 twisted pairs**, each operating in **full duplex**.
    
- Each pair runs at **125 MHz**.
    
- Uses **echo cancellation** (similar to automotive Ethernet but more advanced).
    

---

### **Encoding: 4D-PAM-5**

- **PAM-5** = 5 voltage levels: **−2, −1, 0, +1, +2**
    
- “4D” = encoding across **4 dimensions (4 wire pairs)** simultaneously.
    
- Encodes **2 bits per symbol per pair**, plus an additional symbol for **error correction (‘0’ symbol)**.
    
- 8 bits transmitted in parallel (4 pairs × 2 bits).
    

---

### **Automotive Variant**

- **1000BASE-T1**
    
    - Uses **one twisted pair** instead of four.
        
    - Requires even more advanced echo cancellation and signal processing.
        

---

### **Key takeaway**

Gigabit Ethernet achieves 1 Gbps by using multi-pair, multi-level signaling with echo cancellation and simultaneous parallel transmission across all pairs.


WEEK 8 NOTES


For Week 8, starting from offset 234, here is a structured breakdown of the content in the PDF, focusing on the main topics, concepts, and key takeaways:

---

## 📡 **Week 8: Wireless Networked Embedded Systems**

### **Overview**
This week covers the fundamentals of wireless communications, link budget, path loss, antennas, interference, medium access control, and energy-efficient MAC protocols for wireless embedded systems.

---

### **1. Wireless vs. Wired Embedded Systems**
- **Wireless**:  
  - Needed for mobility, remote deployment, flexibility, lower installation cost.  
  - Can be reliable and secure but vulnerable to interference and attacks.  
- **Wired**:  
  - More reliable (less interference) and more secure (harder to physically intercept).

---

### **2. Basics of Wireless Communications**
- **Transmission**: Radio transmitter → antenna → electromagnetic wave.  
- **Reception**: Antenna → electric current → receiver processes signal → demodulation.

---

### **3. Radio Waves and Decibels**
- Radio waves attenuate exponentially in space.  
- Power expressed in **decibels (dB)** (logarithmic scale).  
- **Rule of thumb**:  
  - +3 dB ≈ ×2 power  
  - −3 dB ≈ ÷2 power  
  - +10 dB ≈ ×10 power  
- Example: +17 dB = +10 + 10 − 3 = ×50.

---

### **4. Link Budget**
Formula:  
\[
P_{RX} = P_{TX} + G_{TX} - L_{TX} - L_P + G_{RX} - L_{RX}
\]
Where:
- \(P_{TX}, P_{RX}\): transmit/receive power  
- \(G_{TX}, G_{RX}\): antenna gains  
- \(L_{TX}, L_{RX}\): losses  
- \(L_P\): path loss (depends on distance, frequency, environment).

---

### **5. Path Loss and Interference**
- **Multipath fading**: Signals reflect, interfere constructively/destructively.  
- **Shadowing**: Obstacles attenuate signals.  
- **Interference**: Other signals, electronics, overlapping networks.

---

### **6. Antennas**
- **Passive**, reshape signal directionality.  
- **Isotropic antenna**: theoretical reference.  
- **Directivity/Gain (dBi)**: higher gain = more directional.

---

### **7. Requirements for Successful Reception**
1. Signal power > receiver sensitivity threshold.  
2. Signal power >> interference power.

---

### **8. Medium Access Control (MAC)**
- **CSMA/CA**: Sense before transmit, backoff if busy (used in WiFi).  
- **Contention-free MAC**: Time slots assigned (TDMA).  
- **Radio Duty Cycling**: Turn radio off to save energy.

---

### **9. Energy-Efficient MAC Protocols**
- **Asymmetric energy**: AP always on, devices duty-cycle.  
- **Symmetric energy**: All devices duty-cycle (multi-hop, mesh).  
- **Asynchronous MAC**:  
  - Sender-initiated (preamble sampling)  
  - Receiver-initiated (beacon-based)  
  - Wake-up radio (separate low-power radio)

- **Synchronous MAC**: Devices sync sleep/wake cycles.

---

### **10. Topologies**
- **Star**: Single AP, devices talk directly.  
- **Multi-hop**: Line, tree, mesh — extend coverage, increase latency/energy.

---

### **11. Classification of MAC Protocols**
Based on:
- **Duty cycle** (none, end devices only, all devices)  
- **Contention handling** (contention-based vs. contention-free)  
- **Sync method** (synchronous vs. asynchronous)

---

### **Key Takeaways**
- Wireless systems trade reliability/security for flexibility/mobility.  
- Link budget and path loss are critical for range and reliability.  
- Energy efficiency is achieved through smart duty cycling and MAC design.  
- Topology and energy constraints dictate MAC protocol choice.

---

Let me know if you'd like a summary table, flashcards, or a quiz on this material.


![[All_slides_nes.pdf#page=236]]

**Week 8 Slide 3 – Wireless vs Wired Embedded Systems**

*   This slide compares the two fundamental ways to connect embedded systems: wirelessly or with cables. Understanding this trade-off is crucial.
*   **Key exam point**: You must know the pros and cons of each to choose the right technology for a given application.

| Feature | Wireless Embedded Systems | Wired Embedded Systems |
| :--- | :--- | :--- |
| **Necessity** | **Mobile** systems (wearables, vehicles) or **remote** areas with no infrastructure. | Wherever physical cables can be run. |
| **Installation** | **Cheaper, more flexible, easier** to deploy. | More difficult and expensive to install. |
| **Reliability** | Can be reliable, but **vulnerable to interference and environmental noise**. | **More reliable** due to a controlled, shielded medium. |
| **Security** | Can be secure, but **more vulnerable to physical attacks** (e.g., signal jamming, interception). | **More secure** as physical access to the cable is needed for an attack. |

*   **For practice**: A sensor in a rotating machine part *must* be wireless. A sensor in a factory control panel could be wired for maximum reliability.

![[All_slides_nes.pdf#page=237]]

**Week 8 Slide 4 – Basics of Wireless Communications**

*   This slide explains the fundamental physical process of sending and receiving data wirelessly. Think of it as "how does the 0 or 1 become a radio wave and back again?"

**Transmission (Sending Data):**
1.  The **radio transmitter** generates an electric signal with the data.
2.  This signal is fed to the **antenna**.
3.  The antenna converts the electric signal into an **electromagnetic (radio) wave** that radiates into space.
4.  The data is **encoded** by modifying properties of this wave (like its frequency or phase).

**Reception (Receiving Data):**
1.  The **antenna** intercepts radio waves and converts them back into a tiny electric current.
2.  The **radio receiver** takes this weak, noisy signal.
3.  It **filters** out unwanted frequencies, **amplifies** it, and finally **demodulates** it to recover the original data.

*   **Key takeaway**: Antennas are the translators between electrical signals in the device and radio waves in the air. The receiver's job is to clean up the messy signal it picks up.

![[All_slides_nes.pdf#page=238]]

**Week 8 Slide 5 – Radio Waves and Decibels**

*   **Main Problem**: Radio wave power drops **extremely fast** with distance (exponential attenuation).
    *   *Analogy*: Like the rubber of a balloon getting thinner as it inflates.
    *   *Example*: A 0.2 Watt signal can become 0.1 picowatt (a trillion times smaller) by the time it reaches the receiver.
    *   **Result**: Wireless systems deal with an **enormous dynamic range** of signal power.

*   **Solution: Decibels (dB)**
    *   A **logarithmic unit** used to express relative power in a manageable way.
    *   Formula: `$$P_{dB} = 10 \log_{10} \frac{P}{P_0}$$`
        *   `P` is the power you're measuring.
        *   `P_0` is the reference power.
        *   The result tells you how much bigger or smaller `P` is compared to `P_0`.

*   **Crucial dB Arithmetic (Exam Rules of Thumb)**:
    *   Adding in dB = multiplying in linear scale.
    *   **+3 dB ≈ power ×2**
    *   **-3 dB ≈ power ÷2**
    *   **+10 dB ≈ power ×10**
    *   **-10 dB ≈ power ÷10**

*   **Practice Question**: +17 dB ≈ ?
    *   Break it down: +17 dB = +10 dB + 10 dB - 3 dB
    *   Calculate: ×10 ×10 ÷2 = **×50**
    *   A +17 dB gain means the power is **about 50 times stronger**.

![[All_slides_nes.pdf#page=240]]

**Week 8 Slide 6 – Decibels: Typical Power References**

*   This slide shows how to use dB with specific references, which is essential for real calculations.

**Two Main Ways to Use dB:**

| Type | Reference | Formula | Use Case | Example |
| :--- | :--- | :--- | :--- | :--- |
| **Relative Gain/Loss** | Input Power (`P_IN`) | `$$Gain(dB) = 10 \log_{10}\frac{P_{OUT}}{P_{IN}}$$` | Describing components like amplifiers or attenuators. | A **3 dB amplifier** doubles the power: `P_OUT = 2 × P_IN`. |
| **Absolute Power** | 1 milliwatt (1 mW) | `$$P_{dBm} = 10 \log_{10}\frac{P}{1\ \text{mW}}$$` | Stating an actual power level. The unit is **dBm**. | A **-10 dBm** signal has a power of ~0.1 mW (one-tenth of 1 mW). |

*   **Combining them is simple**: You just add the dB values.
    *   Example: Amplify a **-10 dBm** signal with a **+3 dB** amplifier.
    *   Result: `-10 dBm + 3 dB = -7 dBm`.

*   **Key Reference Points (Memorize for the exam)**:
    *   **0 dBm**: Typical TX power for small embedded systems.
    *   **30 dBm (1 Watt)**: Max TX power for a WiFi router.
    *   **-100 dBm**: Minimal received signal for WiFi (very weak).
    *   **-174 dBm**: Thermal noise floor (the fundamental limit of what can be detected).

![[All_slides_nes.pdf#page=241]]

**Week 8 Slide 7 – Link Budget**

*   A **link budget** is a crucial calculation to predict if a wireless link will work. It adds up all gains and losses from the transmitter to the receiver.

*   **The Formula:**
    `$$ P_{RX} = P_{TX} + G_{TX} - L_{TX} - L_P + G_{RX} - L_{RX} $$`

*   **What Each Term Means:**
    *   `P_RX`: **Received Power** (dBm) - This is what we want to calculate.
    *   `P_TX`: **Transmission Power** (dBm) - How strong the signal starts.
    *   `G_TX / G_RX`: **Antenna Gain** (dBi) - How much the antenna focuses energy.
    *   `L_TX / L_RX`: **Losses** (dB) - Cables, connectors, etc., that waste power.
    *   `L_P`: **Path Loss** (dB) - The *biggest loss*, caused by distance and environment.

*   **Path Loss (`L_P`) is the main challenge.** It depends on:
    1.  **Distance** between devices.
    2.  **Frequency** of the signal (higher frequency = higher loss).
    3.  **Environment** (walls, furniture, etc.).

*   **In Practice**: The Received Signal Strength Indicator (RSSI) on a device gives you a real-world measurement of `P_RX`, which you can use to work backwards and estimate the path loss for your specific environment.

![[All_slides_nes.pdf#page=242]]

**Week 8 Slide 8 – Path Loss**

*   **Core Concept**: Path loss (`L_P`) is **not just about distance**. In the real world, it's highly **dynamic and unpredictable** even when devices aren't moving.

*   **Why is it so unpredictable? Two main reasons:**
    1.  **Multipath Fading**:
        *   Signals bounce off walls, furniture, etc., creating multiple copies that take different paths to the receiver.
        *   These copies can arrive **in phase** (constructive interference, **stronger signal**) or **out of phase** (destructive interference, **weaker signal**).
        *   Tiny changes in position or environment cause big RSSI swings.

    2.  **Shadowing**:
        *   Obstacles (people, walls, metal objects) physically **attenuate or block** the signal.
        *   Metal objects are especially good at blocking radio waves completely.

*   **Exam Relevance**:
    *   **This is why wireless is less reliable than wired.** You cannot assume a static link budget.
    *   The figure shows RSSI fluctuating wildly over time for two **static** devices in an office. This is due to people moving, doors opening, etc., causing multipath and shadowing effects.

![[All_slides_nes.pdf#page=243]]

**Week 8 Slide 9 – Antenna Gain**

*   **Important Correction**: Antennas are **passive**. They do **not amplify** the signal. They **reshape** how energy is radiated or collected.

*   **Key Reference**: The **Isotropic Antenna**.
    *   A *theoretical* antenna that radiates/receives power **equally in all directions** (a perfect sphere).
    *   It is used as the **0 dBi reference point** for measuring real antenna performance.

*   **Directivity and Gain (dBi)**:
    *   Real antennas focus energy in **certain directions**.
    *   **Directivity** is the *geometric* shape of this focus.
    *   **Antenna Gain (dBi)** is the *measured* peak power in the best direction, **compared to an isotropic antenna**.
    *   **Trade-off**: High gain in one direction means **low gain in all others**.

*   **Choosing an Antenna (Exam Scenario)**:
    | Use Case | Recommended Antenna | Reason |
    | :--- | :--- | :--- |
    | **Mobile/Unknown Source** (e.g., sensor network) | **Low-directivity** (e.g., dipole, ~2 dBi) | Good all-around coverage. |
    | **Fixed Point-to-Point Link** (e.g., bridge between buildings) | **High-directivity** (e.g., dish, panel) | Focuses energy for longer range and less interference. |


Understood. The offset was miscalculated. Let's correct it and proceed from the "Connecting Antennas to Radios" slide at the proper offset.

![[All_slides_nes.pdf#page=244]]

**Week 8 Slide 10 – Connecting Antennas to Radios**

*   This slide is about the practical hardware interface between the radio chip and the antenna.
*   **Key Exam Concept**: **Impedance Matching** is critical. If not matched, power is reflected back into the radio instead of being radiated, reducing range and potentially damaging the circuit.

**Components of the RF Front-End:**
1.  **Antenna Types**:
    *   **External Antenna**: Connected via connectors (SMA, u.FL). Offers flexibility and often better performance.
    *   **Printed Antenna**: A copper trace on the PCB. Cheaper and more compact, but performance is tied to board design.

2.  **Matching Circuit**:
    *   A network of capacitors and inductors.
    *   **Goal**: Maximize power transfer to the antenna by making the antenna's impedance "look like" 50 ohms to the radio.

3.  **Balun (Balanced-to-Unbalanced)**:
    *   A **chip** (or discrete component) that performs two key jobs:
        *   **Conversion**: Radios often have a differential (balanced) output, but antennas are single-ended (unbalanced). The balun converts between them.
        *   **Impedance Matching**: Many balun chips (like the one shown) have an **integrated matching circuit**.

*   **For Design**: Many modern radio modules have an integrated balun. You often just connect the antenna directly to a designated pin. Always check the datasheet.


![[All_slides_nes.pdf#page=245]]

**Week 8 Slide 11 – Requirements for a Successful Reception**

*   A wireless receiver needs **two conditions** to be met to correctly decode a packet. If either fails, the packet is lost.

| Requirement | Description | Analogy | Consequence if Not Met |
| :--- | :--- | :--- | :--- |
| **1. Signal Detectability** | The received signal power (`P_RX`) must be **above the receiver's sensitivity threshold**. | The listener must be able to **hear** the speaker. | The signal is lost in the noise floor; the receiver doesn't even detect a packet. |
| **2. Signal Dominance** | The received signal must be **sufficiently stronger than the sum of all interference** captured by the antenna. | The listener must be able to **understand** the speaker over the background chatter. | Bit errors occur during decoding, causing a corrupted packet (even if CRC fails). |

*   **Key Terms**:
    *   **Sensitivity (e.g., -97 dBm)**: The **minimum** signal power from which the receiver can extract data. This is a hardware specification.
    *   **Interference**: Any unwanted signal in the same frequency band (from other networks, devices, electronics like microwaves).

*   **Exam Point**: In a real, noisy wireless environment, you need `P_RX` to be **significantly higher** than the sensitivity for **robust communication**, not just barely above it.


![[All_slides_nes.pdf#page=246]]

**Week 8 Slide 12 – Interference**

*   **Fundamental Wireless Problem**: The medium (air) is **shared and broadcast**. A receiver's antenna picks up **all** signals in its frequency range, not just the one you want.

*   **Interference is Subjective**:
    *   From **Receiver A's** perspective, **Transmitter B's** signal is the desired signal.
    *   From **Receiver C's** perspective, **Transmitter B's** signal is **interference**.
    *   *Analogy*: In a crowded room, someone else's conversation is interference to you, but desired communication for them.

*   **Sources of Interference**:
    1.  **Same Network**: Other devices in your own system transmitting.
    2.  **Overlapping Networks**: Neighboring WiFi, Bluetooth, etc.
    3.  **Non-communication Electronics**: Microwave ovens, LED lights, motors (they emit radio noise).

*   **Key Takeaway**: Unlike wired networks, you **cannot physically isolate** a wireless channel. You must manage interference through protocol design (like CSMA/CA), frequency choice, and antenna placement.


![[All_slides_nes.pdf#page=247]]

**Week 8 Slide 13 – Capture Effect**

*   This slide illustrates a specific and important phenomenon in wireless networks that occurs during **collisions**.

*   **Scenario**: Two transmitters (**Tx1** and **Tx2**) send packets **at the same time** on the same channel. The receiver (**Rx**) is closer to Tx2.

*   **What Happens**: Despite the collision, **Rx can successfully decode the packet from the stronger, closer transmitter (Tx2)**.
    *   From **Tx2's perspective**: The interference from the distant Tx1 is weak. Its signal "captures" the receiver.
    *   From **Tx1's perspective**: The interference from the nearby Tx2 is strong, so its packet is lost.

*   **Why This Matters for Exams**:
    *   **Collisions are not always a total loss**. The "capture effect" can allow one packet to get through.
    *   This effect makes network performance **unfair**. Nodes closer to the receiver (or with higher power) have a significant advantage.
    *   It must be considered in protocol design and network simulation—not all simultaneous transmissions result in both packets being lost.

![[All_slides_nes.pdf#page=248]]

**Week 8 Slide 14 – Wireless Coverage**

*   **Common Misconception**: Wireless coverage is **not a perfect circle** or static cell. It's a highly **dynamic and irregular** region.

*   **Why Coverage is "Patchy"**:
    1.  **Dynamic RSSI**: Due to multipath fading and shadowing (from Slide 8), signal strength fluctuates wildly with tiny location changes.
    2.  **Dynamic Bit Error Rate (BER)**: Interference levels change over time, affecting the error rate independently of signal strength.

*   **Packet Error Rate (PER)** is the key metric for practical coverage. PER depends on:
    *   **Transmission Parameters**: Power, antenna, data rate, packet size.
    *   **Environment**: Distance, obstacles, interference.

*   **Graph Insight (Exam-Relevant)**:
    *   The graph shows PER vs. RSSI for different protocols (BLE, IEEE 802.15.4) and packet sizes.
    *   **Key Observations**:
        1.  **Higher RSSI means lower PER** (better reliability).
        2.  **Larger packets (39B) have higher PER** than smaller packets (21B) at the same RSSI (more bits = more chance for error).
        3.  Different protocols have different PER curves for the same RSSI, due to modulation and coding.

*   **Takeaway**: To ensure reliable communication, you must design for the **worst-case PER** in your environment, not the average RSSI.

![[All_slides_nes.pdf#page=249]]

**Week 8 Slide 15 – Carrier Wave**

*   **Core Concept**: We don't transmit raw data (0s and 1s) directly as radio waves. Instead, we **modulate** them onto a **carrier wave**.

*   **What is a Carrier Wave?**
    *   A stable, high-frequency radio signal at frequency `\(f_c\)`.
    *   Data (0s and 1s) is encoded by **modifying** (keying) a property of this carrier (amplitude, frequency, or phase).

*   **Example: BFSK (Binary Frequency Shift Keying)**:
    *   To send a **'0'**: Transmit at frequency `\(f_c - f_0\)`.
    *   To send a **'1'**: Transmit at frequency `\(f_c + f_0\)`.
    *   The receiver measures the frequency shift to decode the data.

*   **Why Use a Carrier? Major Advantages**:
    1.  **Bandpass Filtering**: The receiver can use a filter to **only listen to frequencies near `\(f_c\)`**. This rejects most interference from other frequencies.
    2.  **Frequency Division**: Different systems can use **different carrier frequencies (`\(f_c\)`)** to communicate in parallel without interfering. This is the basis for **channels** (next slide).

*   **Exam Point**: The carrier frequency is what defines a "channel" (e.g., WiFi channel 6 is 2.437 GHz). Modulation is how you put data on it.


![[All_slides_nes.pdf#page=250]]

**Week 8 Slide 16 – Frequency Band: Trade-offs**

*   This slide explains the engineering trade-offs involved in choosing a frequency band for a wireless embedded system.

**Lower Frequency Bands (e.g., Sub-GHz: 300 MHz - 1 GHz):**
*   **Pros**: Lower path loss, better obstacle penetration, longer range, smaller antennas.
*   **Cons**: More interference (crowded), lower available bandwidth (lower data rates).

**Higher Frequency Bands (e.g., Microwave, mmWave: 1 GHz - 300 GHz):**
*   **Pros**: Higher bandwidth (higher data rates), less congestion.
*   **Cons**: Higher path loss, poor obstacle penetration (easily blocked), shorter range, more complex/costly hardware.

**For Embedded Systems**:
*   **Long-range, low-power, low-data-rate** sensors (e.g., agriculture, utilities) often use **Sub-GHz** bands (e.g., 868 MHz in EU, 915 MHz in US).
*   **Short-range, higher-data-rate** applications (e.g., device streaming, video) use **2.4 GHz or 5 GHz** bands (WiFi, Bluetooth).

**Safety Note**: Frequencies **above visible light** (Ultraviolet, X-ray, Gamma) are ionizing radiation and dangerous. Wireless embedded systems use **Radio and Microwave** frequencies, which are **non-ionizing**.

| Characteristic | Lower Frequency (e.g., 868 MHz) | Higher Frequency (e.g., 2.4 GHz) |
| :--- | :--- | :--- |
| **Range** | **Longer** | Shorter |
| **Wall Penetration** | **Better** | Worse |
| **Data Rate Potential** | Lower | **Higher** |
| **Interference** | Often more (narrower band) | Can be less (wider bands) |
| **Antenna Size** | **Larger** | Smaller |


![[All_slides_nes.pdf#page=251]]

**Week 8 Slide 17 – Frequency Bands: Rules**

*   **Key Point**: You **cannot** transmit on any frequency you want. Governments strictly regulate the radio spectrum to prevent chaos and interference.

*   **Two Main Types of Bands:**

| Type | Who Can Use | How to Get Permission | Typical Use |
| :--- | :--- | :--- | :--- |
| **Licensed Bands** | Exclusive rights holder | Purchase a **license** from the government (expensive). | Cellular networks (4G/5G), TV/Radio broadcasting, aviation, military. |
| **Unlicensed Bands** | **Anyone** (public use) | **No license needed**, but must follow strict technical rules (power, duty cycle). | WiFi, Bluetooth, Zigbee, LoRa, consumer devices. |

*   **Most Important Unlicensed Bands for Embedded Systems (ISM Bands)**:
    *   **2.4 - 2.5 GHz**: **Worldwide**. Most crowded (WiFi, Bluetooth, Zigbee, microwaves).
    *   **Sub-GHz Bands**: **Regional**.
        *   **868 - 870 MHz**: Europe.
        *   **902 - 928 MHz**: North/South America.
    *   **5.725 - 5.875 GHz**: Worldwide (WiFi 5/6).

*   **Exam Must-Know**:
    1.  Know the difference between **licensed** and **unlicensed** bands.
    2.  **2.4 GHz is global** but crowded.
    3.  **Sub-GHz bands offer better range/penetration but are region-specific**.
    4.  You **must** design your product for the legal band of the country where it will be sold.

![[All_slides_nes.pdf#page=252]]

**Week 8 Slide 18 – Wireless Channels**

*   **Concept**: A frequency band (e.g., 2.4 GHz) is **divided into smaller slices called channels**. This allows multiple networks to operate in parallel within the same band.

*   **Channel Types**:
    | Type | Interference? | Use Case | Illustration |
    | :--- | :--- | :--- | :--- |
    | **Overlapping Channels** | **Yes, high** | Should be avoided. Networks on overlapping channels interfere, reducing performance for both. | Channels that are too close together in frequency. |
    | **Orthogonal Channels** | **No (or minimal)** | The goal. Networks on orthogonal channels can operate **simultaneously without interference**. | Channels spaced far enough apart (e.g., WiFi channels 1, 6, 11 in 2.4 GHz band). |

*   **FDMA (Frequency Division Multiple Access)**:
    *   The foundational method for sharing a band.
    *   Different transmitters are assigned **different orthogonal channels**.
    *   They can transmit **in parallel** without colliding.
    *   *Analogy*: Multiple conversations happening in different rooms.

*   **For Embedded Network Design**:
    *   Always check which channels are **orthogonal** in your chosen band.
    *   Deploy networks on **different orthogonal channels** to minimize interference between them.
    *   This is a **static** form of interference avoidance.

![[All_slides_nes.pdf#page=253]]

**Week 8 Slide 19 – Radio States**

*   **Core Limitation**: A typical wireless radio can only be in **one primary state at a time: Transmit (TX) or Receive (RX)**. It **cannot do both simultaneously** (unlike wired Ethernet).

*   **Receive/Listen State**:
    *   The radio is **on**, filtering, amplifying, and trying to decode any incoming signal.
    *   **"Receive"** and **"Listen"** are the **same state** from a power/operation perspective.
    *   The radio listens for a special **preamble** at the start of a frame to synchronize and know a packet is coming.

*   **Critical Implications for Protocols (Exam Focus)**:
    1.  **Collision Detection is Impossible**: A device **cannot hear a collision while it is transmitting**. It's "shouting" and can't "listen" for others.
    2.  **Idle Listening Wastes Energy**: To detect incoming frames, a device must be in the **RX/Listen state**, which consumes significant power (similar to receiving).
    3.  **Half-Duplex Only**: Communication is one direction at a time.

*   **The Energy Problem**: Keeping the radio in RX mode waiting for possible traffic drains the battery. This leads to the central challenge of **Radio Duty Cycling** (next slides).


![[All_slides_nes.pdf#page=254]]

**Week 8 Slide 20 – Medium Access Control: Sharing a Channel**

*   **Topology**: This slide introduces the **Star Topology**, the simplest and most common for wireless embedded networks (e.g., WiFi, Zigbee, BLE).
*   **Components**:
    *   **Access Point (AP) / Sink / Gateway (GW)**: The central coordinator. It is usually mains-powered, collects data from devices, and often bridges the wireless network to a wired one (e.g., the Internet).
    *   **Wireless Devices (D1, D2, D3)**: Battery-powered sensors/actuators. They communicate **directly with the AP**, not with each other.

*   **Key Challenge in a Star**:
    *   All devices share the **same wireless channel** to talk to the AP.
    *   This creates a **single point of contention** and makes the network vulnerable to **collisions** (if two devices transmit at once) and **interference**.

*   **Basic Solution Shown**:
    *   Overlapping networks (e.g., your WiFi and your neighbor's) can be set to use **different orthogonal channels** to avoid interfering with each other.
    *   **This does not solve collisions *within* your own network**. For that, you need a **MAC protocol** like CSMA/CA (next slide).


![[All_slides_nes.pdf#page=255]]

**Week 8 Slide 21 – CSMA/CA**

*   **CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance)** is the fundamental **contention-based** MAC protocol used by WiFi (IEEE 802.11) and many others.

*   **How it works (step-by-step)**:
    1.  **Sense**: Before transmitting, a device performs **Clear Channel Assessment (CCA)**—it listens to check if the channel is free (idle).
    2.  **If Channel is FREE**: The device transmits its frame immediately.
    3.  **If Channel is BUSY**: The device **defers**. It waits for the channel to become free, then waits an **additional random backoff time** before trying again.
        *   This random backoff (often **binary exponential**) is the "Collision Avoidance" part—it prevents multiple waiting devices from transmitting simultaneously as soon as the channel is free.

*   **What the Timeline Shows**:
    *   Devices (Dev 1, 2, 3) and the AP (Access Point) all perform CCA before transmitting.
    *   The random backoff creates spacing between transmissions, minimizing collisions.
    *   The AP also uses CSMA/CA when it transmits to devices.

*   **Limitations for Embedded**:
    *   **Energy Cost**: Devices must **listen (CCA)** frequently, which consumes power.
    *   **No Guarantees**: Under high traffic, devices may experience long delays or never get a clear channel. This is not ideal for time-critical sensor data.
    *   **Hidden Terminal Problem**: Not shown here, but a major issue where two devices can't hear each other but both can hear the AP, causing collisions at the AP.

![[All_slides_nes.pdf#page=256]]

**Week 8 Slide 22 – Acknowledgements**

*   **Core Problem**: In wireless networks, packets are lost **frequently** due to collisions, interference, or weak signals—far more often than in wired networks.

*   **Solution**: **Acknowledgements (ACKs)**.
    *   After successfully receiving a frame, the receiver immediately sends back a short ACK packet to the sender.
    *   **If the sender gets an ACK**: It knows the transmission was successful.
    *   **If the sender does NOT get an ACK** (within a timeout): It assumes the frame was lost and **retransmits** it.

*   **Retransmission Logic**:
    1.  Sender transmits a frame and waits for ACK.
    2.  If no ACK, it retries (using CSMA/CA again).
    3.  After a **maximum number of retries**, the frame is **dropped**. The higher-layer protocol (e.g., TCP) must handle this loss.

*   **Why This Matters for Embedded Systems**:
    *   **Reliability**: ACKs+retries make an unreliable wireless link more reliable.
    *   **Energy Trade-off**: Every retransmission consumes extra energy.
    *   **Latency**: Retries add delay (jitter), which can be critical for control systems.

*   **Exam Point**: ACKs are a **link-layer** (not transport-layer like TCP) mechanism for reliability. They are essential for any robust wireless protocol.


![[All_slides_nes.pdf#page=257]]

**Week 8 Slide 23 – Radio Duty Cycle**

*   **The Central Energy Problem**: For battery-powered embedded devices, the radio is the **biggest power consumer**. Keeping it in RX (Listen) mode to receive possible traffic **wastes energy** (this is **idle listening**).

*   **Power Consumption Data (Example from CC2660 chip)**:
    *   **RX Mode**: ~6 mA (Listening for packets)
    *   **TX Mode**: ~6-9 mA (Transmitting)
    *   **Sleep Mode**: **Microamps (µA)** — *thousands of times less*.

*   **Solution: Radio Duty Cycling**
    *   Turn the radio **off (Sleep)** most of the time.
    *   Turn it **on (RX/TX)** only when needed.
    *   The radio now has **three states**: TX, RX, **Sleep**.

*   **The Fundamental Challenge**:
    *   How does the **receiver** know **when** to wake up and listen, so it doesn't miss the transmitter's message?
    *   *If the receiver is sleeping, any transmission to it is lost.*
    *   **Solving this synchronization problem is the goal of all low-power MAC protocols** (covered in next slides).

![[All_slides_nes.pdf#page=258]]

**Week 8 Slide 24 – Asymmetric Energy Availability (Uplink)**

*   **Common Scenario (Star Topology)**: The **Access Point/Gateway (AP/GW)** is **mains-powered** (plugged in). The **sensor devices** are **battery-powered** and must duty cycle their radios.

*   **MAC Protocol: Duty-Cycled CSMA for Uplink Traffic** (Device → AP):
    *   **AP Behavior**: Radio is **always in RX mode** (listening), ready to receive at any time.
    *   **Device Behavior**:
        1.  **Wake up** when it has data to send.
        2.  Perform **CCA** (sense the channel).
        3.  **If CCA succeeds (channel free)**: Transmit the packet, then immediately **switch to RX mode** to wait for the **ACK** from the AP.
        4.  **If CCA fails (channel busy)**: Go **back to sleep** immediately. Try again after a delay (random backoff).

*   **What the Timeline Shows**:
    *   Devices wake up independently (asynchronously).
    *   They contend for the channel using CSMA.
    *   The AP is always listening, so it can always send an ACK back.

*   **Limitation of This Simple Scheme**:
    *   It works perfectly for **uplink** traffic (device-initiated).
    *   **It does not work for downlink traffic (AP → device)**. If the AP has a command for a sleeping device, it has no way to deliver it. This is the **downlink problem**.

![[All_slides_nes.pdf#page=259]]

**Week 8 Slide 25 – Asymmetric Energy Availability (Downlink Problem)**

*   **Recap of the Problem**: In the previous duty-cycled CSMA scheme, battery-powered devices are **asleep most of the time**. The AP cannot send data to them because they are not listening.

*   **Proposed Solution: Extended Receive Window via ACK Piggybacking**
    *   When the AP sends an **ACK** for an uplink packet, it can include a **request** for the device to **stay awake** in RX mode for a short, additional period (a **receive window**).
    *   During this window, the AP can then transmit its downlink data (e.g., a configuration update, command).
    *   This only works **immediately after** the device has contacted the AP.

*   **Limitations of this Approach**:
    *   **AP cannot initiate communication**. It must *wait* for the device to contact it first.
    *   This causes **unpredictable and potentially long delays** for downlink traffic (e.g., a command from a user to a sensor).
    *   It is **inefficient** if the AP rarely has downlink traffic, as the device wastes energy staying awake.

*   **Key Exam Point**: With asymmetric energy, **downlink is the hard problem**. Solutions always involve some trade-off between downlink delay, device energy, and protocol complexity.


![[All_slides_nes.pdf#page=260]]

**Week 8 Slide 26 – Contention-based vs Contention-free MAC**

*   This slide compares two fundamental strategies for managing access to a shared wireless channel, highlighting their trade-offs.

| Feature | **Contention-based (e.g., CSMA/CA)** | **Contention-free (e.g., TDMA)** |
| :--- | :--- | :--- |
| **Core Idea** | Devices **compete** for the channel. "Listen before talk." | Transmission **time slots are pre-allocated** to specific devices. |
| **Efficiency** | **High at low/medium, sporadic traffic.** No wasted slots. | **High at high, predictable traffic.** Guaranteed access. |
| **Traffic Suitability** | **Unpredictable, bursty traffic** (e.g., event-driven sensors). | **Predictable, periodic traffic** (e.g., continuous monitoring). |
| **Collisions** | **Possible** (mitigated by random backoff). | **None** (if synchronized perfectly). |
| **Guarantees** | **No guarantees** of access (starvation possible). | **Guaranteed access** for important devices. |
| **Flexibility** | **Very flexible**, adapts to changing number of devices. | **Inflexible**, schedule changes require overhead. |
| **Overhead** | Low control overhead. | High control overhead (scheduling, synchronization). |
| **Analogy** | **Car lanes** – anyone can use them, may get congested. | **Bus lanes** – reserved for specific vehicles, empty if bus doesn't come. |

*   **For Embedded Systems**: The choice depends on **traffic pattern** and **energy constraints**. Many protocols (like IEEE 802.15.4) use a **hybrid** approach: a contention-free period for high-priority traffic and a contention period for others.


![[All_slides_nes.pdf#page=261]]

**Week 8 Slide 27 – Guaranteed Time Slots (TDMA)**

*   **TDMA (Time Division Multiple Access)** is a classic **contention-free** MAC protocol that solves the channel sharing problem by dividing time into slots.

*   **How it works in a Star Network**:
    1.  The **AP/Gateway** is the master. It periodically broadcasts a **beacon**.
    2.  The **beacon contains a schedule** (a TDMA frame) assigning specific future time slots to specific devices.
    3.  **Device 1** transmits only in its **assigned slot**, then listens for an ACK.
    4.  **Device 2** transmits only in its **different, assigned slot**.
    5.  This eliminates collisions completely, as long as devices are synchronized.

*   **Key Characteristics**:
    *   **Joining the Network**: A new device must listen (stay in RX mode) continuously until it hears a beacon to learn the schedule. This consumes energy.
    *   **Inefficiency with Unpredictable Traffic**: If a device has **nothing to send**, its assigned slot goes **idle (wasted)**. This is inefficient for sporadic traffic.
    *   **Overhead**: The AP must create, maintain, and broadcast the schedule. If the network changes, the schedule must be updated.

*   **Exam Point**: TDMA is excellent for **high-throughput, predictable, periodic data** (e.g., industrial sensor sampling). It is poor for **low-traffic, event-driven** applications due to slot wastage and synchronization overhead.

![[All_slides_nes.pdf#page=262]]

**Week 8 Slide 28 – Radio Duty Cycling with Asymmetric Energy Availability**

*   This slide summarizes the **paradigm** used by many common low-power wireless standards for star networks.

*   **Core Idea**: The **Access Point (AP)** is always-on (no duty cycle), acting as a **synchronization anchor**. **End devices** duty cycle aggressively to save energy, waking up only at specific times to communicate.

*   **Advantages**:
    *   **Simple & Robust**: Simple for end devices, complex logic is in the powered AP.
    *   **Very Energy-Efficient for Devices**: They sleep most of the time.
    *   **Low Overhead for Devices**: Synchronization burden is on the AP.

*   **Disadvantages**:
    *   **AP Must Be Mains-Powered**: Cannot be battery-powered.
    *   **No Direct Device-to-Device (D2D) Communication**: All traffic must go through the AP. **No mesh or multi-hop** support.
    *   **Downlink Delay**: As seen before, the AP cannot instantly reach a sleeping device.

*   **Real-World Standards Using This Paradigm**:
    *   **IEEE 802.15.4** (with beacons) – used by Zigbee and Thread.
    *   **Bluetooth Low Energy (BLE)** – in connection mode.
    *   **LoRaWAN** – uses scheduled receive windows.
    *   **Low-Power WiFi** – e.g., 802.11ah (WiFi HaLow).

*   **Exam Point**: Recognize that these popular protocols are all designed for **asymmetric energy** star topologies. Their limitations (no mesh, downlink delay) stem from this core design choice.



![[All_slides_nes.pdf#page=263]]

**Week 8 Slide 29 – Multi-hop Topology**

*   **Problem**: In a star network, a device may be out of **range** of the Gateway (GW), or the signal may be too **weak** (e.g., in a basement, behind many walls).

*   **Solution: Multi-hop Networking**
    *   Devices that **can** hear the GW forward messages on behalf of devices that **cannot**.
    *   A message travels through **intermediate nodes** (hops) to reach the GW.

*   **Cost-Benefit Trade-off**:
    | Aspect | Impact in Multi-hop |
    | :--- | :--- |
    | **Cost Increase** | A single frame is **transmitted and received multiple times**, consuming **more total network energy** and increasing **latency**. |
    | **Benefit (Coverage)** | **Network coverage is extended** beyond the single-hop range of the GW. |
    | **Benefit (Robustness)** | **Short links are more reliable** than one long, weak link. This can **reduce retransmissions**, potentially saving energy. |

*   **Key Insight**: Multi-hop is not about saving energy *for the network as a whole*. It's about **enabling communication when direct links fail** and can sometimes save energy by using reliable short hops instead of unreliable long ones with many retries.



![[All_slides_nes.pdf#page=264]]

**Week 8 Slide 30 – Types of Multi-Hop Topologies**

*   This slide shows three common multi-hop network topologies, each with different characteristics for routing and reliability.

| Topology | Structure | Characteristics | Use Case Example |
| :--- | :--- | :--- | :--- |
| **Line** | Nodes in a single chain. | • Simple routing.<br>• **Single point of failure**: If one node fails, the network splits.<br>• High latency for end nodes. | Sensors along a pipeline or road. |
| **Tree** | Hierarchical parent-child structure (like an org chart). | • Efficient data aggregation toward a root (GW).<br>• More resilient than a line.<br>• Still vulnerable to branch failure if a parent node dies. | Large-scale sensor networks (e.g., agricultural monitoring). |
| **Mesh** | Nodes have multiple possible connections. | • **Most resilient**: Multiple redundant paths.<br>• Complex routing protocols needed.<br>• Can self-heal around failures.<br>• Higher overhead for route maintenance. | Industrial monitoring, smart buildings, military networks. |

*   **For Embedded Systems**: The choice depends on **reliability needs**, **energy constraints**, and **mobility**. **Mesh** is the most robust but also the most complex and energy-intensive to maintain. **Tree** is a common compromise for static networks.



![[All_slides_nes.pdf#page=265]]

**Week 8 Slide 31 – Symmetric Energy Limitations**

*   **New Challenge**: In **multi-hop** networks (line, tree, mesh) and some star networks, **all devices are battery-powered**, including potential forwarders and even the Gateway. This is **symmetric energy limitation**.

*   **Core Problem**: If *both* the sender **and** the receiver need to duty cycle their radios to save energy, how do they **coordinate** their sleep/wake schedules so they are both awake at the same time to communicate?

*   **Walkie-Talkie Analogy**:
    *   **Alice** and **Bob** have battery-powered walkie-talkies.
    *   They both want to keep them **off (sleep)** to save batteries.
    *   To talk, they need to both turn them **on (RX)** at the same time.
    *   **Question**: How do they synchronize without wasting energy listening constantly?

*   **This is the fundamental problem of symmetric, duty-cycled MAC protocols**. The solutions fall into two main categories:
    1.  **Asynchronous MAC** (next slides): Devices do *not* synchronize clocks. They use long preambles or periodic beacons to "page" each other.
    2.  **Synchronous MAC** (later slide): Devices *do* synchronize their clocks to have common active/sleep periods.

*   **Exam Point**: Recognize that multi-hop networks require MAC protocols that work under **symmetric energy constraints**, which are more complex than the asymmetric case.



![[All_slides_nes.pdf#page=266]]

**Week 8 Slide 32 – Sender-Initiated Asynchronous MAC (Preamble Sampling / LPL)**

*   **Protocol Type**: **Asynchronous** (devices have **independent, unsynchronized** sleep schedules).

*   **How It Works**:
    *   **Idle Receiver (e.g., Dev 2)**:
        1.  Wakes up **periodically** (every `PERIOD`).
        2.  Turns radio to **RX mode and samples the channel very briefly** (e.g., to detect a preamble).
        3.  **If preamble detected**: Stays awake, sends a **CTS (Clear to Send)**, then receives the full frame.
        4.  **If nothing detected**: Goes **back to sleep immediately**.
    *   **Sender with Data (e.g., Dev 1)**:
        1.  Wants to send data to a sleeping receiver.
        2.  Transmits a **long preamble** (or **RTS - Ready to Send**) that lasts **at least as long as the receiver's sleep `PERIOD`**.
        3.  Listens for a **CTS**.
        4.  **If CTS received**: Sends the data frame.
        5.  **If no CTS**: Goes back to sleep, retries later.

*   **Trade-offs**:
    *   **Pro**: Very simple, no synchronization needed.
    *   **Con**: **Sender wastes huge energy** transmitting the long preamble. **Latency** is high (sender must wait for receiver's next check).
    *   The **listening PERIOD** is the key design parameter: a shorter period reduces latency but increases idle listening energy for receivers.

*   **Also known as**: Low-Power Listening (LPL), Preamble Sampling.


![[All_slides_nes.pdf#page=267]]

**Week 8 Slide 33 – Receiver-Initiated Asynchronous MAC**

*   **Protocol Type**: **Asynchronous**, but the **receiver initiates** the contact, reversing the energy cost.

*   **How It Works**:
    *   **Idle Receiver (e.g., Dev 2)**:
        1.  Wakes up **periodically** (every `PERIOD`).
        2.  Transmits a short **beacon** (or **CTS - Clear to Send**) announcing it is awake and listening.
        3.  Stays in **RX mode for a short window** waiting for a response.
        4.  **If a sender responds**: Receives the data frame.
        5.  **If no response**: Goes **back to sleep**.
    *   **Sender with Data (e.g., Dev 1)**:
        1.  Wants to send data.
        2.  Keeps its radio in **RX mode, listening continuously** for the receiver's beacon.
        3.  **Upon hearing the beacon**: Immediately transmits its data frame.
        4.  If it never hears a beacon, it times out (energy waste).

*   **Trade-offs**:
    *   **Pro**: **Sender does not waste energy on long preambles**. More efficient when senders have data infrequently.
    *   **Con**: **Sender must listen continuously** until it hears a beacon, which can be high energy cost if the receiver's period is long.
    *   Energy burden shifts from the sender (in preamble sampling) to the receiver (who transmits beacons) and the listening sender.

*   **Key Point**: The performance of **sender-initiated** and **receiver-initiated** approaches is comparable; the choice depends on the expected traffic pattern (who talks more often).


![[All_slides_nes.pdf#page=268]]

**Week 8 Slide 34 – Asynchronous MAC with Wakeup Radio**

*   **Advanced Solution**: Use **two radios** on each device to break the energy-latency trade-off of single-radio asynchronous MACs.
    *   **Main Radio**: High-performance, high data rate, **high power**. Used only for actual data transfer. Kept **OFF** when idle.
    *   **Wakeup Radio**: Very simple, very low data rate (can send a device ID), **extremely low power**. Can be kept in **RX mode continuously** or duty-cycled with a very short period.

*   **How It Works**:
    1.  **Idle Device**: Main radio **OFF**. Wakeup radio **ON (listening)**.
    2.  **Sender with Data**:
        *   Sends a **Wakeup Call (RTS)** via the **wakeup radio channel**.
        *   This signal contains the target receiver's ID.
    3.  **Receiver**:
        *   Its wakeup radio hears its ID.
        *   **Powers ON its main radio** and switches it to **RX mode**.
        *   Sends an acknowledgement via the wakeup radio.
    4.  **Data Transfer**: Both devices switch to their **main radios** and transfer the data frame using a conventional protocol.

*   **Advantages**:
    *   **Ultra-low idle listening power** (microamps from wakeup radio).
    *   **Very low latency** (receiver can be paged almost instantly).
*   **Disadvantages**:
    *   **Increased cost, size, and design complexity** (two radios).
    *   Wakeup radio typically has **limited range**.

*   **This is a cutting-edge research area** for ultra-low-power IoT nodes that need to be responsive.


![[All_slides_nes.pdf#page=269]]

**Week 8 Slide 35 – Synchronous MAC**

*   **Core Idea**: All devices **synchronize their clocks** and agree on a common schedule of **active periods** and **sleep periods**.

*   **How It Works**:
    1.  **Synchronization**: Devices periodically exchange timing information (e.g., in beacons) to align their clocks.
    2.  **Active Period**: All devices wake up simultaneously. During this window, they use a standard MAC scheme (like **CSMA/CA** or **Guaranteed Time Slots**) to communicate.
    3.  **Sleep Period**: All devices turn their radios **off** to save energy. No communication is possible.
    4.  **Cycle Repeats**.

*   **Characteristics**:
    *   **Idle Listening**: **Reduced but not eliminated**. Devices still listen during the active period when not transmitting.
    *   **Latency**: Packets generated during the sleep period must wait for the next active period, causing **bounded latency**.
    *   **Overhead**: Requires **periodic time synchronization messages**, which consume energy and bandwidth.
    *   **Scalability**: The active period must be long enough to accommodate all traffic, which can become inefficient with many devices.

*   **Used in protocols like**:
    *   **IEEE 802.15.4** in beacon-enabled mode (superframe structure).
    *   **TSCH** (Time-Slotted Channel Hopping) in industrial standards like WirelessHART and ISA100.11a.

*   **Exam Point**: Synchronous MAC provides a good balance. It's more efficient than pure asynchronous preamble sampling for frequent traffic, but adds complexity and sync overhead.


![[All_slides_nes.pdf#page=270]]

**Week 8 Slide 36 – Classification of MAC Protocols**

*   This is a **summary and classification slide**, crucial for the exam. It organizes all MAC protocols discussed in the lecture based on two key dimensions.

**1. Duty Cycle (Energy Constraint)**
*   **No Energy Constraints**: Radio always on. Classic CSMA/CA (like WiFi).
*   **Energy Constraints only on End Devices (Asymmetric)**: AP is always on, devices duty cycle.
    *   **Duty-Cycled CSMA** (for uplink).
    *   **Duty-Cycling with Downlink Windows**.
    *   **TDMA/Guaranteed Slots** (beacon-enabled).
*   **Energy Constraints on All Devices (Symmetric)**: Everyone must duty cycle.
    *   **Synchronous Duty Cycles**: All devices wake up at the same time (e.g., synchronized superframes).
    *   **Asynchronous Duty Cycles**:
        *   **Sender-Initiated**: Preamble Sampling / Low-Power Listening (LPL).
        *   **Receiver-Initiated**: Beacon-based polling.
        *   **Wakeup Radio**: Uses a second, ultra-low-power radio for signaling.

**2. Contention Handling**
*   **Contention-based**: Devices compete for the medium (e.g., **CSMA/CA**).
*   **Contention-free**: Access is scheduled or coordinated (e.g., **TDMA**, **Guaranteed Time Slots**).

*   **Exam Strategy**: Use this as a decision tree.
    1.  **Is the AP mains-powered?** → Yes → Use an **Asymmetric** protocol.
    2.  **Is the traffic predictable/periodic?** → Yes → Use a **Contention-free** (TDMA) approach within that paradigm.
    3.  **Are all nodes battery-powered?** → Yes → You need a **Symmetric** protocol.
    4.  **Is latency critical?** → Yes → Consider **Synchronous** or **Wakeup Radio** solutions.



You have reached the end of the slides for **Week 8: Wireless Networked Embedded Systems**.

The final slide (Slide 36) provides a comprehensive classification of MAC protocols based on **Duty Cycle** and **Contention Handling**, which serves as an excellent summary for exam preparation.

**Key topics covered in Week 8 include:**
- Wireless vs. wired trade-offs
- Radio wave propagation and link budget
- Path loss, interference, and antennas
- Carrier waves, frequency bands, and regulation
- Medium Access Control (MAC) protocols
- Energy-efficient MAC strategies for asymmetric and symmetric energy constraints
- Multi-hop topologies and their challenges

If you need to review any specific concept or want a quiz on this material, just let me know!



WEEK 9 NOTES

![[All_slides_nes.pdf#page=273]]
**Week 9 Slide 2 – Networked Embedded Systems**

*Notes:*
*   This is the title slide for **Week 9: Time Synchronisation**.
*   The lecturer is Xenofon (Fontas) Fafoutis.
*   **Exam Relevance:** This week's topic is fundamental for understanding how devices in a network coordinate their actions in time. It's crucial for protocols that require synchronized sleep/wake cycles (like Synchronous MAC) or for timestamping sensor data accurately across multiple nodes.

![[All_slides_nes.pdf#page=274]]
**Week 9 Slide 3 – Synchronous MAC**

*Notes:*
*   This slide introduces the core problem that motivates time synchronisation in **Networked Embedded Systems**: **Synchronous Medium Access Control (MAC)**.
*   **Synchronous MAC:** Devices coordinate their **radio duty cycles**—they all wake up at agreed-upon times to listen/transmit, then go back to sleep to save energy.
*   **The Challenge:** For this to work, all devices must agree on *when* to wake up. This requires:
    1.  A way to **measure time** (a local clock).
    2.  **Clock synchronisation** so that all devices' interpretations of "1 second from now" are the same.
*   The diagram shows a schedule where devices' active periods (blue/green/yellow) are aligned in time. Without synchronisation, these schedules would drift apart, causing communication failures.
*   **Exam Relevance:** This is the primary *application* of time sync in this course. You must understand that synchronisation enables energy-efficient, scheduled communication. The terms "duty cycle," "active/sleep periods," and "rendezvous" are key.

![[All_slides_nes.pdf#page=275]]
**Week 9 Slide 4 – Time Keeping in Distributed Embedded Systems**

*Notes:*
*   This slide poses the fundamental question: **When do distributed embedded systems need to keep time?**
*   It sets up the distinction between system-level and application-level timekeeping needs.
*   **Exam Relevance:** Understanding *why* we need time is just as important as *how* we synchronise it. This provides context for the techniques that follow. Be ready to list examples for both system and application functions.

![[All_slides_nes.pdf#page=276]]
**Week 9 Slide 5 – Time Keeping in Distributed Embedded Systems**

*Notes:*
*   This slide details the **reasons for timekeeping** in distributed embedded systems, split into two categories.
*   **System-Level Functions** (Internal coordination):
    *   Schedule periodic system events (e.g., housekeeping tasks).
    *   Schedule timeouts (e.g., for retransmissions).
    *   Schedule wake-up events (for duty cycling).
    *   Generate clock signals for peripherals.
*   **Application-Level Functions** (User/data-related):
    *   Schedule periodic events (e.g., take a sensor reading every minute).
    *   **Timestamping distributed events or sensor data** (critical for data fusion, e.g., knowing if two sensors detected the same event).
    *   Alarms.
    *   Provide real-world time to the user.
*   **Exam Relevance:** You should be able to categorise a given need (e.g., "waking up a radio every 100ms" is system-level; "logging the time a door opened" is application-level). Timestamping for data fusion is a key distributed systems concept.


![[All_slides_nes.pdf#page=277]]
**Week 9 Slide 6 – Oscillators**

*Notes:*
*   This slide introduces the **hardware foundation** of timekeeping: the **crystal oscillator**.
*   **Crystal Oscillator:** A component that generates a precise, stable electrical signal at a specific **frequency** (from KHz to GHz).
*   **Purpose:** Oscillators provide the "heartbeat" or **clock signal** that drives timers and counters to measure time.
*   **Internal vs. External:** They can be built into the MCU or added as separate external components for better precision.
*   **Example:** A common **32.768 kHz** oscillator (32768 Hz) is shown. This specific frequency is chosen because it's a power of two ($2^{15}$), making it easy to divide down to exactly 1 Hz (1 second) using binary counters.
*   **Exam Relevance:** You must know that **oscillators are the source of time measurement**. The frequency determines the timer's resolution. The 32.768 kHz oscillator is ubiquitous in low-power embedded systems for real-time clocks (RTCs).


![[All_slides_nes.pdf#page=278]]
**Week 9 Slide 7 – Programmable Timer**

*Notes:*
*   This slide explains how an **oscillator** and a **programmable timer** work together to measure time intervals.
*   **Mechanism:**
    1.  The crystal oscillator generates regular **pulses** at its frequency (e.g., 32768 pulses per second).
    2.  On each pulse, a **counter** is decremented.
    3.  When the counter reaches **zero**, it generates an **interrupt** (a clock event).
*   **Controlling Time:** The **initial value** loaded into the counter determines the time until the interrupt.
    *   **Example:** With a 32768 Hz oscillator, an initial value of 1000 results in an interrupt after $1000 / 32768 \approx 0.0305$ seconds (30.5 ms).
*   **Exam Relevance:** This is the basic principle of how software timers are implemented in hardware. Understand the relationship: **Time = (Counter Initial Value) / (Oscillator Frequency)**. The interrupt is how the CPU knows a time period has elapsed.

![[All_slides_nes.pdf#page=279]]
**Week 9 Slide 8 – Timer Configuration and Modes**

*Notes:*
*   This slide describes key **timer features** that provide flexibility in generating time events.
*   **Prescaler:** Divides the oscillator frequency *before* it reaches the counter. If prescaler = N, the counter decrements only once every N oscillator pulses. This allows you to **measure longer time intervals** with the same counter size.
*   **One-off Mode (One-shot):** The timer starts, counts down to zero, triggers an interrupt, and **stops**. Used for **timeouts and alarms**.
*   **Periodic Mode (Square-wave):** The timer automatically **reloads** the initial value and restarts after reaching zero. It generates a **continuous, periodic interrupt**. Used for **scheduling recurring events** (like the tick of a system clock).
*   **Exam Relevance:** You must know the difference between **one-off** and **periodic** timer modes and when to use each. The **prescaler** is crucial for understanding how to configure a timer for a desired period. It's a trade-off between range and resolution.


![[All_slides_nes.pdf#page=280]]
**Week 9 Slide 9 – Time Resolution**

*Notes:*
*   This slide discusses **time resolution** and the **energy trade-off** involved in oscillator choice.
*   **Resolution:** The smallest time increment a clock can measure. It is the period of one oscillator tick: $\text{Tick} = 1 / \text{Frequency}$.
    *   Example: 32 kHz → Tick = $1 / 32768 \approx 30.5 \mu s$.
    *   Example: 24 MHz → Tick = $1 / 24 \times 10^6 \approx 41.7 ps$.
*   **Clocks measure in ticks, not seconds.** Software converts ticks to seconds using the known frequency.
*   **Energy Trade-off:** Higher frequency = higher resolution **but** higher power consumption.
*   **Common Practice:** Many embedded devices use **two oscillators**:
    *   A **high-frequency** crystal (e.g., 24 MHz) for active operation (CPU, fast peripherals, high-res timing).
    *   A **low-power, low-frequency** crystal (e.g., 32.768 kHz) for keeping time during sleep and scheduling wake-ups (Real-Time Clock - RTC).
	*   **Exam Relevance:** Understand the **inverse relationship between frequency and tick period**. Know the **reason for using two clocks** (performance vs. energy savings). The 32 kHz clock is key for low-power operation.

![[All_slides_nes.pdf#page=281]]
**Week 9 Slide 10 – Crystal Oscillators on CC2650**

*Notes:*
*   This slide shows a **real-world circuit diagram** (for the TI CC2650 MCU) highlighting the two crystal oscillators.
*   **Key Components to Identify:**
    *   **X1 (24 MHz):** The high-frequency main crystal (`X24M_P`, `X24M_N`).
    *   **X2 (32.768 kHz):** The low-frequency Real-Time Clock (RTC) crystal (`X32K_Q1`, `X32K_Q2`).
*   Each crystal requires supporting **capacitors** (e.g., C4, C5 for the 24 MHz; internal caps for the 32 kHz) to form the oscillator circuit.
*   **Exam Relevance:** You are **not expected to know circuit details**. The takeaway is to **recognize the two physical crystals on a typical MCU board** and associate them with their roles: a high-speed clock and a low-power sleep clock. This concretizes the two-oscillator concept from the previous slide.

![[All_slides_nes.pdf#page=282]]
**Week 9 Slide 11 – Example: Uptime Counter**

*Notes:*
*   This slide presents a concrete **software example** of using a timer to build an **uptime counter** (seconds since boot).
*   **Implementation:**
    1.  System has a 32768 Hz timer.
    2.  Initialize a variable `UPTIME = 0`.
    3.  Configure a **periodic timer** with a starting value of **32768**.
    4.  On each timer interrupt (which occurs every 32768 ticks), increment `UPTIME`.
*   **Why it works:** 32768 ticks / 32768 Hz = **1 second** per interrupt.
*   **Question:** After one day (86400 seconds), `UPTIME` should be **86400**.
*   **Exam Relevance:** This is a fundamental programming pattern. You must understand how to calculate the timer initial value from a desired period. The math is: $\text{Initial Value} = \text{Desired Period (s)} \times \text{Frequency (Hz)}$. This example assumes a perfect oscillator, which leads to the next topic: drift.

![[All_slides_nes.pdf#page=283]]
**Week 9 Slide 12 – Clock Drift**

*Notes:*
*   This slide introduces the central problem of time synchronisation: **Clock Drift**. Real-world oscillators are **imperfect**.
*   **Cause: Production Spread.** During manufacturing, components have a tolerance error from their nominal value. The **maximum error** is in the datasheet.
*   **Quantifying Drift:** Measured in **parts per million (ppm)** or parts per billion (ppb). $1 \text{ ppm} = 10^{-6} = 0.0001\%$.
*   **Example:** A 32768 Hz crystal with **±20 ppm max drift**.
    *   Actual frequency range: $32768 \pm (32768 \times 20 \times 10^{-6}) = 32768 \pm 0.65536$ Hz.
    *   So frequency is between **32767.34464 Hz** and **32768.65536 Hz**.
    *   Period range: ~**30516.97 ns** to **30518.19 ns**.
*   **Impact:** The error per tick is tiny, but it **accumulates over time**, causing clocks to drift apart.
*   **Exam Relevance:** You **must** understand ppm and be able to calculate the actual frequency range given a ppm value. Drift is why synchronisation is necessary. The ±20 ppm example is classic.


![[All_slides_nes.pdf#page=284]]
**Week 9 Slide 13 – Error**

*Notes:*
*   This slide visualizes how clock **error accumulates linearly over time** due to constant drift.
*   **Error Definition:** Difference between **true elapsed time** and the time measured by the device's clock (`UPTIME`).
*   **Error = (Clock Drift Rate) × (Time Elapsed)**
*   The graph shows error growing from seconds to minutes, hours, days, and weeks. With a drift of just 20 ppm:
    *   Error after 1 day: $86400 \text{s} \times 20 \times 10^{-6} = 1.728 \text{ seconds}$.
    *   After 1 week: ~12 seconds.
*   **Key Insight:** Error is **negligible in the short term** (e.g., for a single packet transmission) but **significant in the long term** (e.g., for scheduling a rendezvous one hour later).
*   **Exam Relevance:** Understand that error is **additive and proportional to time**. You should be able to estimate the error after a given duration using the ppm drift rate. This explains why infrequent synchronisation leads to large errors.

![[All_slides_nes.pdf#page=285]]
**Week 9 Slide 14 – Other Sources of Clock Drift**

*Notes:*
*   This slide explains that **production spread** is not the only source of drift. Two other major factors are **ageing** and **temperature**.
*   **Ageing:** A systematic, long-term change in frequency (e.g., ±3 ppm per year). The crystal's properties slowly change over time.
*   **Temperature:** Crystal frequency varies with temperature, typically in a **parabolic** pattern centered around room temperature (25°C). It slows down at both very low and very high temperatures.
    *   Example: -0.04 ppm/°C² means the drift is proportional to the *square* of the difference from 25°C.
*   **Cumulative Effect:** Total drift = **Production Spread + Ageing + Temperature Effect**. These can compound, making the worst-case drift larger.
*   **Exam Relevance:** Know the three main sources of drift: **production, ageing, temperature.** Understand that temperature is a dynamic factor that can change during operation, affecting short-term drift. The graph shows why temperature-controlled oscillators (TCXOs) are used for high precision.


![[All_slides_nes.pdf#page=286]]
**Week 9 Slide 15 – Example: Synchronised Blinking**

*Notes:*
*   This slide poses a **thought experiment** to illustrate the problem of **relative clock drift** in a simple two-device system.
*   **Scenario:** Two MCUs start simultaneously (button press). Each uses its internal timer to blink an LED with a 1-second period.
*   **Questions:**
    *   **1 minute later:** They will likely **still appear synchronized**. The error (~1.2 ms with 20 ppm) is smaller than human perception.
    *   **1 hour later:** They will probably be **out of sync**. Error ~72 ms, which may be visible as slightly offset blinking.
    *   **1 day later:** They will be **clearly out of sync**. Error ~1.73 seconds, so one LED will blink while the other is off.
*   **Key Point:** Even if both devices use the same hardware, their individual drifts (due to production spread, temperature, etc.) will differ, causing them to drift **relative to each other**.
*   **Exam Relevance:** This demonstrates why applications requiring **long-term coordination between devices** (like synchronous MAC) absolutely need clock synchronisation. It's a practical motivation for the techniques that follow.


![[All_slides_nes.pdf#page=287]]
**Week 9 Slide 16 – Clock Drift vs Relative Clock Drift**

*Notes:*
*   This slide clarifies a crucial distinction between two types of drift, which matters for different applications.
*   **Clock Drift:** The rate at which a **single clock** drifts from **true time** (e.g., UTC). Important for applications that need real-world time (e.g., data logging with UTC timestamps).
*   **Relative Clock Drift:** The rate at which **two clocks** drift **apart from each other**. Calculated as: $\text{Relative Drift} = \text{Drift}_{\text{MCU1}} - \text{Drift}_{\text{MCU2}}$.
*   **Important Scenarios:**
    *   Devices can be **in sync with each other** but **both wrong** relative to true time (if they have the same drift).
    *   The **worst-case relative drift** is **double** the individual worst-case drift.
        *   Example: Each MCU has ±20 ppm drift. Worst case: MCU1 at +20 ppm, MCU2 at -20 ppm.
        *   Relative Drift = $20 - (-20) = 40$ ppm.
*   **Exam Relevance:** You **must** understand this difference. For **synchronous MAC**, we care about **relative drift**. For **timestamping with true time**, we care about **absolute clock drift**. Know how to calculate worst-case relative drift.


![[All_slides_nes.pdf#page=288]]
**Week 9 Slide 17 – What is true time anyway?**

*Notes:*
*   This slide explores the concept of "true time" and how we establish a global reference.
*   **Atomic Clocks:** The most accurate timekeeping devices, based on atomic resonance (e.g., cesium). They are extremely precise but **very expensive** ($30k+).
*   **International Atomic Time (TAI):** A weighted average of over 450 atomic clocks worldwide. It's a continuous, uniform time scale.
*   **Coordinated Universal Time (UTC):** The basis for civil time. It is **TAI adjusted by leap seconds** to account for irregularities in Earth's rotation. Local time zones are UTC offsets (e.g., CET = UTC+1).
*   **Implication for Embedded Systems:** We cannot put an atomic clock in every sensor node. Therefore, devices with imperfect clocks must **periodically synchronise** with a reference that has access to true time (e.g., via GPS or a network time server).
*   **Exam Relevance:** Understand that "true time" is defined by atomic clocks and disseminated as UTC. The challenge is getting this reference to cheap, distributed devices. This justifies the need for synchronisation protocols.

![[All_slides_nes.pdf#page=289]]
**Week 9 Slide 18 – Unidirectional Synchronisation**

*Notes:*
*   This slide presents the simplest synchronisation concept and its fundamental limitation.
*   **Method:**
    1.  Sender (Alice) records local time $T_1$ and sends it in a packet.
    2.  Receiver (Bob) records local time $T_2$ upon packet arrival.
*   **Relationship:** $T_2 = T_1 + D + o$, where:
    *   $D$ = Message delay (total time from send to receive).
    *   $o$ = Clock offset (difference between Bob's and Alice's clocks).
*   **The Core Problem:** To solve for offset $o = T_2 - T_1 - D$, you need to know the **message delay $D$**. However, **accurately measuring $D$ requires the clocks to already be synchronised**.
*   **Workaround:** If the delay $D$ is **stable and predictable**, you can **estimate** it (e.g., as a constant). The accuracy of synchronisation depends entirely on the accuracy of this delay estimation.
*   **Exam Relevance:** Understand the equation and the **circular dependency problem**: you need sync to measure delay, and you need delay to calculate sync. Unidirectional sync is only viable if you can *model* the delay very well (e.g., in a tightly controlled system).

![[All_slides_nes.pdf#page=290]]
**Week 9 Slide 19 – Components of Message Delay**

*Notes:*
*   This slide breaks down the **message delay ($D$)** into its constituent parts, explaining why it's hard to know precisely.
*   **Delay Components:**
    *   **Sender OS Delays:** Scheduling, processing, queuing, medium access (waiting for clear channel, receiver wake-up).
    *   **Transmission Delay:** Time to push all bits onto the wire. $L/R$, where $L$=packet size, $R$=data rate. **Calculable** if you know $L$ and $R$.
    *   **Propagation Delay:** Time for signal to travel the distance. $d/s$, where $d$=distance, $s$≈speed of light. **Calculable and often negligible** at short range.
    *   **Receiver OS Delays:** Scheduling, processing.
*   **Key Insight:** The **OS delays at sender and receiver are variable and unpredictable** (jitter), making $D$ uncertain. In multi-hop networks, these delays **add up per hop**.
*   **Exam Relevance:** You should be able to list the major components of message delay. Know which parts are **calculable** (transmission, propagation) and which are **variable/jitter** (OS scheduling, queuing, medium access). This variability is why unidirectional sync is inaccurate.

![[All_slides_nes.pdf#page=291]]
**Week 9 Slide 20 – Time Synchronisation with GPS**

*Notes:*
*   This slide describes **GPS** as a method for achieving **absolute time synchronisation** (sync to true time).
*   **How GPS Provides Time:**
    *   24+ satellites, each with an **atomic clock**.
    *   They broadcast their **precise time** and location on a dedicated frequency.
    *   The signal propagation delay from satellite to receiver is bounded and can be calculated based on known satellite orbits.
*   **GPS Receiver:** Listens to signals from at least 4 satellites.
    *   Uses **trilateration** to compute its 3D location.
    *   **In the process, it also computes the exact time offset** between its local clock and the atomic-clock-based GPS time.
*   **Result:** The receiver's clock is synchronised to **true time** with high precision.
*   **Exam Relevance:** GPS is a **primary reference** for true time. Understand that it provides **both location and time**. The synchronisation is a **by-product of the localization calculation**. It's a 1-hop sync to an atomic clock.

![[All_slides_nes.pdf#page=292]]
**Week 9 Slide 21 – A 1D Example**

*Notes:*
*   This slide simplifies the GPS concept to a **1-dimensional world** to show the intrinsic link between **time synchronisation** and **distance calculation** (lateration).
*   **Scenario:**
    *   Satellite S1 at known location 0m.
    *   Receiver R at unknown location.
    *   Signal speed $s = 1$ m/s.
*   **If Clocks are Synchronised:**
    *   S1 sends at $T_1=0$, R receives at $T_2$.
    *   Range $d = s \times (T_2 - T_1) = T_2$. If $T_2=200$, location is 200m. **Correct.**
*   **If Clocks are NOT Synchronised (offset $o=1$s):**
    *   R's local receive time $T_2' = T_2 + o$.
    *   Calculated range $d' = s \times (T_2' - T_1) = T_2 + 1 = 201$m. **Error of 1m.**
*   **Key Point:** A **time offset directly causes a location error**. To find the correct location, you must solve for both location *and* time offset. This requires multiple satellites.
*   **Exam Relevance:** This illustrates the fundamental principle that **localisation requires time synchronisation**. The math shows how a time error translates to a distance error. This is why GPS needs 4 satellites: 3 for 3D location, 1 to solve for the clock offset.


![[All_slides_nes.pdf#page=293]]
**Week 9 Slide 22 – A 1D Example (Continued)**

*Notes:*
*   This slide extends the 1D example to show how **using a second satellite** allows solving for both **location and time offset**.
*   **Scenario:**
    *   S1 at 0m, S2 at 300m, R at 200m.
    *   R has unknown clock offset $o=1$s.
*   **Calculations with Offset:**
    *   From S1: $T_2' = T_1 + d_{R-S1}/s + o$ → $d_{R-S1} = 201$m (est. location: 201m).
    *   From S2: $T_4' = T_3 + d_{R-S2}/s + o$ → $d_{R-S2} = 101$m (est. location: 199m).
*   **Observation:** The two estimated locations **disagree** (201m vs 199m).
*   **Solution:** The receiver can **adjust its assumed time offset $o$** until the location calculated from *all* satellites **converges to a single point**. This unique solution gives both the **true location** and the **true clock offset**.
*   **Exam Relevance:** This demonstrates the **mathematical necessity of multiple references** (satellites) to solve for both time and space when the clock is unknown. It's the core idea behind GPS operation. Understand that synchronisation is not a separate step but is solved *simultaneously* with localisation.


![[All_slides_nes.pdf#page=293]]
**Week 9 Slide 22 – A 1D Example (Continued)**

*Notes:*
*   This slide extends the 1D example to show how **using a second satellite** allows solving for both **location and time offset**.
*   **Scenario:**
    *   S1 at 0m, S2 at 300m, R at 200m.
    *   R has unknown clock offset $o=1$s.
*   **Calculations with Offset:**
    *   From S1: $T_2' = T_1 + d_{R-S1}/s + o$ → $d_{R-S1} = 201$m (est. location: 201m).
    *   From S2: $T_4' = T_3 + d_{R-S2}/s + o$ → $d_{R-S2} = 101$m (est. location: 199m).
*   **Observation:** The two estimated locations **disagree** (201m vs 199m).
*   **Solution:** The receiver can **adjust its assumed time offset $o$** until the location calculated from *all* satellites **converges to a single point**. This unique solution gives both the **true location** and the **true clock offset**.
*   **Exam Relevance:** This demonstrates the **mathematical necessity of multiple references** (satellites) to solve for both time and space when the clock is unknown. It's the core idea behind GPS operation. Understand that synchronisation is not a separate step but is solved *simultaneously* with localisation.

![[All_slides_nes.pdf#page=294]]
**Week 9 Slide 23 – 3D Trilateration**

*Notes:*
*   This slide visually summarizes how GPS works in **three dimensions**.
*   **Process with Multiple Satellites:**
    1.  **First Satellite:** Defines a **sphere** of possible locations (receiver is somewhere on that sphere).
    2.  **Second Satellite:** Intersection of two spheres is a **circle**.
    3.  **Third Satellite:** Intersection of the circle with a third sphere gives **two points**.
    4.  **Fourth Satellite:** Used to resolve ambiguity (one point is in space, the other on/near Earth) and, crucially, to **solve for the receiver's clock error**, refining the location estimate.
*   **Key Point:** The **fourth satellite** is needed primarily to calculate the **time offset** between the receiver's clock and GPS time, which eliminates the location error caused by that offset.
*   **Exam Relevance:** Understand the role of each satellite signal. Know that **4 satellites are the minimum** to get a 3D fix *with time correction*. The diagram helps visualize the geometric solution. This is why GPS receivers need a clear view of the sky to see multiple satellites.


![[All_slides_nes.pdf#page=295]]
**Week 9 Slide 24 – Time Synchronisation with GPS**

*Notes:*
*   This slide summarises the **advantages and disadvantages** of using GPS for time synchronisation in embedded systems.
*   **Advantages:**
    *   **High Precision:** Direct, 1-hop access to atomic-clock time.
    *   **Ease of Use:** The receiver hardware handles the complex calculations.
    *   **Relatively Cheap Hardware:** GPS modules are mass-produced.
*   **Disadvantages:**
    *   **Line of Sight Required:** Typically only works **outdoors**.
    *   **High Energy Consumption:** The GPS receiver is power-hungry, unsuitable for always-on, battery-powered sensors.
    *   **Cost & Integration:** A GPS module adds **cost, size, and complexity**. Not every device in a system can have one (e.g., not every sensor in a car).
*   **Exam Relevance:** Be able to **evaluate when GPS sync is appropriate**. It's great for **gateways** or **mobile assets** with ample power, but impractical for dense networks of **low-power indoor sensors**. It provides **absolute** (true time) synchronisation.

![[All_slides_nes.pdf#page=296]]
**Week 9 Slide 25 – Bidirectional Synchronisation**

*Notes:*
*   This slide presents a classic and widely-used method to overcome the "unknown delay" problem: **Bidirectional (Two-way) Message Exchange**.
*   **Assumptions:**
    1.  The **delay $D$ is identical** in both directions (symmetric path).
    2.  The **clock offset $o$ is constant** during the brief exchange.
*   **Message Exchange & Timestamps:**
    *   $T_1$: A sends to B.
    *   $T_2$: B receives (on B's clock).
    *   $T_3$: B sends reply to A.
    *   $T_4$: A receives reply (on A's clock).
*   **Equations:**
    *   $T_2 = T_1 + D + o$
    *   $T_4 = T_3 + D - o$
*   **Solving for Offset ($o$):** Subtracting the equations eliminates $D$.
    *   $o = \frac{(T_2 - T_1) - (T_4 - T_3)}{2}$
*   **Exam Relevance:** **This is a fundamental algorithm you must know.** Understand the derivation of the offset formula. The critical point is that it **measures round-trip delay to estimate one-way delay**, assuming symmetry. Network Time Protocol (NTP) uses this principle.


![[All_slides_nes.pdf#page=297]]
**Week 9 Slide 26 – Network Time Protocol (NTP)**

*Notes:*
*   This slide describes **NTP**, the standard protocol for synchronising clocks over networks like the internet.
*   **Model:** **Client/Server**. The client queries one or more **time servers** (which have access to precise time sources like GPS or atomic clocks).
*   **Method:** Uses the **bidirectional synchronisation** principle (from previous slide) to estimate offset and round-trip delay.
*   **Features for Robustness:**
    *   Queries **multiple servers** for redundancy.
    *   Maintains history to **estimate clock drift**.
    *   Applies **gradual corrections** (slewing) to avoid time jumps.
*   **Performance:** Achieves **millisecond accuracy** over the internet, **sub-millisecond** on LANs.
*   **Vulnerabilities:** Affected by network **congestion, asymmetric routes**, and variable delays.
*   **SNTP (Simple NTP):** A lightweight version for less critical applications; does a single query without history tracking (less accurate).
*   **Exam Relevance:** NTP is the workhorse for network time sync. Know its client-server model, that it uses bidirectional exchange, and its typical accuracy. Understand that **SNTP is simpler but less robust**.


![[All_slides_nes.pdf#page=298]]
**Week 9 Slide 27 – Precision Time Protocol (PTP)**

*Notes:*
*   This slide introduces **PTP (IEEE 1588)**, a protocol designed for **high-precision** synchronisation in **local area networks**, such as industrial automation or telecom.
*   **Principle:** Similar to NTP (bidirectional exchange), but with key optimisations for higher accuracy.
*   **How it Achieves Nanosecond Precision:**
    1.  **Hardware Timestamping:** Timestamps are applied by the **network interface hardware** (NIC) at the exact moment a frame is sent/received, bypassing variable OS and driver delays.
    2.  **Local Time Master:** A designated **grandmaster clock** in the local network provides the time source, minimising routing delays and asymmetry.
*   **Assumptions:** Same as NTP—**symmetric delay** and **constant offset** during exchange.
*   **Result:** Accuracy in the **nanosecond** range, compared to NTP's millisecond range.
*   **Exam Relevance:** Know that **PTP is for ultra-high precision on LANs**. The key differentiators from NTP are **hardware timestamping** and use of a **local grandmaster clock**. It's used where microsecond/nanosecond sync is critical (e.g., 5G base stations, factory robots).


![[All_slides_nes.pdf#page=299]]
**Week 9 Slide 28 – Reference-Based Synchronisation**

*Notes:*
*   This slide describes an alternative approach for achieving **relative synchronisation** (sync between devices, not necessarily to true time).
*   **Core Idea:** Devices capture a **shared physical event** and record their local timestamps. The difference between timestamps reveals their **relative offset**.
*   **Event Types:**
    *   **Natural:** A lightning flash, a loud noise.
    *   **Induced:** A deliberately generated signal (e.g., a light pulse, a radio beacon).
*   **Example - Cinema Clacket:** A device that creates a simultaneous audio "clack" and visual flash. A camera and microphone capture this event, and the difference between their timestamps synchronises audio and video tracks.
*   **In Networks:** A **broadcast packet** can serve as the shared event. All devices that receive it timestamp its arrival.
*   **Exam Relevance:** Understand the concept of using a **shared event as a reference point**. This is simpler than bidirectional protocols but only provides **relative sync** among the devices that observed the event. It's useful for data fusion (e.g., "did these two sensors feel the same vibration at the same time?").


![[All_slides_nes.pdf#page=300]]
**Week 9 Slide 29 – Reference-Broadcast Synchronisation**

*Notes:*
*   This slide details a specific and efficient network-based method for **relative synchronisation**: **Reference-Broadcast Synchronisation (RBS)**.
*   **Protocol:**
    1.  A **reference device (R)** broadcasts a beacon (no destination address, just a sync pulse).
    2.  Receivers **A** and **B** record their local receive times ($T_1$ and $T_2$).
    3.  **A** sends its timestamp $T_1$ to **B**.
    4.  **B** calculates the offset to A as $o = T_2 - T_1$.
*   **Why it's Accurate for Relative Sync:** The **sender-side delays** (processing, queuing, medium access, transmission) are **identical** for both receivers A and B because it's the same broadcast packet. The main remaining errors are differences in **receiver-side delays** (propagation difference, interrupt latency), which are typically much smaller.
*   **Exam Relevance:** RBS is a clever way to achieve good **relative sync** with low overhead. Understand that it **eliminates sender-side variability** by using a broadcast. It's excellent for synchronising a group of receivers with each other. Contrast with bidirectional sync, which aims to sync a client to a server's absolute time.


![[All_slides_nes.pdf#page=301]]
**Week 9 Slide 30 – Periodic Synchronisation**

*Notes:*
*   This slide addresses the necessity of **repeating** the synchronisation process over time.
*   **The Problem:** Clock **drift is continuous**. After a synchronisation event corrects the offset to (near) zero, drift immediately starts causing error to accumulate again.
*   **The Solution:** Perform synchronisation **periodically** to keep the error bounded.
*   **Trade-off:** 
    *   **Frequent Sync:** Small error bound, but high **energy and bandwidth cost**.
    *   **Infrequent Sync:** Low cost, but large error may accumulate between syncs.
*   **Graph Interpretation:** The sawtooth graph shows error building up linearly (due to drift) until a sync event resets it. The **height of the teeth** is the **maximum tolerable error**, which determines the **required sync period**.
*   **Exam Relevance:** You must understand that **synchronisation is not a one-time task**. The **sync period is a critical design choice** that balances **accuracy vs. overhead**. Given a drift rate and a max allowable error, you should be able to calculate the required sync period.

![[All_slides_nes.pdf#page=302]]
**Week 9 Slide 31 – Synchronising the Radio Duty Cycle**

*Notes:*
*   This slide returns to the original motivation (Slide 3) and shows **what happens without synchronisation** in a synchronous MAC protocol.
*   **Scenario:** Two devices agree to meet (rendezvous) in 1 minute to communicate.
    *   Each sets its local timer for 1 minute and sleeps.
    *   When its timer expires, Dev1 starts transmitting, Dev2 starts listening.
*   **The Problem - Relative Drift:** If their clocks drift relative to each other, their interpretations of "1 minute" differ.
    *   If **Dev1's clock is faster**, it will start transmitting **before** Dev2 is listening. Dev2 misses the transmission.
    *   If **Dev2's clock is faster**, it will start listening **before** Dev1 transmits, then give up and go back to sleep **before** Dev1 starts. Dev1's transmission is missed.
*   **Result:** Communication fails. The active slots (colored bars) do not overlap in time.
*   **Exam Relevance:** This is a concrete example of why sync is essential. For duty-cycled MAC protocols (like scheduled rendezvous), even small relative drift will cause communication blackouts over time. This leads to the solution: **Guard Time**.


![[All_slides_nes.pdf#page=303]]
**Week 9 Slide 32 – Synchronising the Radio Duty Cycle (Analysis)**

*Notes:*
*   This slide reiterates the problem from the previous slide, emphasizing the **dependence on relative drift**.
*   **Key Condition:** For successful rendezvous, the **relative drift over the sleep period** must be **smaller than the duration of the active listening window**.
*   **If relative drift = 0:** Works perfectly.
*   **If relative drift > 0:** The devices' schedules shift apart, causing misalignment.
*   **The Core Challenge:** In low-power networks, sleep periods can be **very long** (seconds to minutes) to save energy, while active listening windows are **very short** (milliseconds) to minimize idle listening. This makes them **highly sensitive to even tiny drift rates**.
*   **Exam Relevance:** Understand the relationship: $\text{Schedule Misalignment} = \text{Relative Drift (ppm)} \times \text{Sleep Period (s)}$. For a 1-minute sleep and 40 ppm drift, misalignment = $60 \times 40 \times 10^{-6} = 2.4$ ms. If the listening window is only 1 ms, they will miss each other. This quantifies the need for sync.

![[All_slides_nes.pdf#page=304]]
**Week 9 Slide 33 – Guard Time**

*Notes:*
*   This slide introduces the **primary technique** to combat synchronisation error in rendezvous-based MAC protocols: the **Guard Time**.
*   **What is Guard Time?** The receiver extends its listening window, starting **earlier** and ending **later** than the nominal rendezvous time. This creates a buffer to account for both positive and negative clock drift.
*   **Trade-off:**
    *   **Larger Guard Time:** More robust to sync error and drift. Higher chance of catching the transmission.
    *   **Smaller Guard Time:** Less **idle listening** (radio on but not receiving), which saves energy. More bandwidth efficient (radio is idle for less time).
*   **Visual:** In the diagram, the yellow "listen" period is expanded on both sides of the expected green "receive" slot.
*   **Exam Relevance:** **Guard time is a crucial concept.** You must understand its purpose and its inherent trade-off between **robustness and energy efficiency**. It's a practical, local solution to handle residual sync error after a periodic synchronisation.

![[All_slides_nes.pdf#page=305]]
**Week 9 Slide 34 – Guard Time vs Max Sync Period**

*Notes:*
*   This slide presents a **graphical relationship** between key synchronisation parameters, showing how to **design a system**.
*   **Graph Interpretation (Solid Lines):** Shows how the **required guard time** (y-axis) increases if you allow a longer **maximum time between re-synchronisations** (x-axis), for a given drift rate.
    *   Example: For 40 ppm drift, if you sync every 10 seconds, you need ~400 µs guard time. If you sync only every 100 seconds, you need ~4000 µs guard time.
*   **The Trade-off (Revisited):**
    *   **Long Sync Period:** Less sync overhead, **but** requires a **large guard time**, which wastes energy on idle listening.
    *   **Short Sync Period:** Needs frequent sync messages (overhead), **but** allows a **tiny guard time**, saving listening energy.
*   **Design Choice:** You can choose an operating point on this curve based on your system's priorities (minimise sync traffic vs. minimise idle listening).
*   **Exam Relevance:** This graph encapsulates the **system-level design trade-off**. You should be able to interpret it: guard time must be sized to cover the **accumulated error since the last sync**. The relationship is linear: $\text{Min Guard Time} \approx \text{Drift Rate} \times \text{Sync Period}$.


![[All_slides_nes.pdf#page=306]]
**Week 9 Slide 35 – Implicit Synchronisation**

*Notes:*
*   This slide describes an **optimisation** for synchronous MAC protocols that **eliminates dedicated sync messages**.
*   **Core Idea:** Use the **data frames themselves** as synchronisation events.
*   **How it works:**
    1.  Receiver expects a transmission at time $T_1$ (based on its schedule).
    2.  The actual transmission arrives at time $T_2$ (recorded on receiver's clock).
    3.  The receiver calculates the **instantaneous offset** $o = T_2 - T_1$.
    4.  This offset can be used to **correct the receiver's schedule** for the next rendezvous.
*   **Benefits:**
    *   **"Free" resynchronisation** with every successful data transmission.
    *   No extra sync overhead.
*   **Requirement:** A data frame must be transmitted **before the accumulated drift exceeds the guard time**; otherwise, communication fails and implicit sync is lost.
*   **Runtime Drift Compensation:** The receiver can estimate the **drift rate** by dividing the offset by the time since the last sync, allowing it to **predict and correct** for future drift.
*   **Exam Relevance:** Implicit sync is a smart technique for **reducing protocol overhead**. Understand that it turns every data exchange into a sync event. Its limitation is that it requires **regular data traffic** to maintain synchronisation.

![[All_slides_nes.pdf#page=307]]
**Week 9 Slide 36 – Conclusion**

*Notes:*
*   This slide provides a high-level summary of the key trade-offs in time synchronisation.
*   **Key Trade-offs:**
    1.  **Real-time vs. Relative Sync:** Synchronising to true time (e.g., via GPS, NTP) is more resource-intensive than synchronising devices only to each other (e.g., via RBS).
    2.  **Precision vs. Resources:** Higher precision (e.g., PTP vs. NTP) requires more sophisticated hardware (timestamping) and network control.
    3.  **Sync Frequency vs. Error:** The time between synchronisation events determines the maximum accumulated error. More frequent sync reduces error but consumes bandwidth and energy.
*   **Design Implications:** The choice of synchronisation method depends on the **application requirements** (Does it need true time? What is the tolerable error?) and the **system constraints** (energy, cost, network topology).
*   **Exam Relevance:** This is a good framework for answering synthesis or evaluation questions. You should be able to argue for a particular synchronisation approach given a set of system requirements and constraints, considering these three trade-offs.

You have reached the end of the Week 9 slides. The lecture on Time Synchronisation is now complete.

**Final Summary for Week 9:**
This week covered the fundamentals of timekeeping and synchronisation in networked embedded systems. You learned about hardware oscillators, clock drift, and the motivations for synchronisation (e.g., synchronous MAC). Key synchronisation methods were explained, including GPS (for absolute time), bidirectional protocols like NTP/PTP, and reference-based methods like RBS for relative sync. The critical concepts of **guard time** and the trade-offs between **sync frequency, error, and energy overhead** were emphasized, along with optimisations like **implicit synchronisation**.


WEEK 10 NOTES


![[All_slides_nes.pdf#page=308]]
**Week 10 Slide 1 – Embedded Machine Learning**

*Notes:*
*   This is a title slide for Week 10. It indicates the topic is "Embedded Machine Learning" within the course "02226 Networked Embedded Systems".
*   The presenter is Riccardo Miccini from the Technical University of Denmark.
*   The date (November 13, 2025) suggests this is a recent or future-dated lecture, but for your exam, the content is what matters.
*   **Exam Relevance:** This sets the scope. "Embedded" is key—it means we're focusing on running machine learning on resource-constrained devices that are part of a networked system (e.g., sensors, microcontrollers), not on powerful cloud servers.

![[All_slides_nes.pdf#page=310]]
**Week 10 Slide 3 – Structure**

*Notes:*
*   This slide outlines the **five-part structure** of the lecture. Understanding this roadmap is crucial as it defines the key areas you need to know for the exam.
*   The structure is:
    1.  **ML Primer**: Foundational concepts of Machine Learning (ML) and Deep Learning (DL).
    2.  **Wetware I**: The human motivations and application areas for embedded ML.
    3.  **Hardware**: The computing platforms used, from cloud to edge devices.
    4.  **Software**: The practical pipeline from data to deploying a model on a device.
    5.  **Wetware II**: The ethical and responsible development of embedded AI systems.
*   The lecturer notes the slides are dense and some references are missing. For your exam, focus on the core concepts explained in the slides themselves.
*   **Exam Relevance:** This is your study guide. Expect questions covering motivation (Why embedded ML?), hardware trade-offs, software techniques (like model compression), and societal implications. The terms "Wetware I/II" are metaphors for the human element (needs and responsibilities).

![[All_slides_nes.pdf#page=311]]
**Week 10 Slide 4 – Learning Objectives**

*Notes:*
*   This slide lists the **specific learning objectives** for the lecture. These are essentially the exam goals. You should be able to do each of these things.
*   **Explain the motivation**: You must be able to argue *why* we run ML on embedded devices instead of just in the cloud (think: latency, bandwidth, privacy, cost, reliability).
*   **Compare HW platforms**: You need to know the differences between CPUs, MCUs, GPUs, and NPUs, and their suitability for embedded ML tasks.
*   **Describe model compression and deployment**: Key exam topics. Know techniques like pruning and quantization, and the steps to get a model onto a device.
*   **Evaluate systems**: You should be able to discuss trade-offs in efficiency (e.g., energy use), scalability, and societal impact (e.g., privacy concerns).
*   **Critically assess trends**: Be prepared to discuss emerging topics (like neuromorphic computing) and argue for responsible development practices.
*   **Exam Relevance:** Treat this as a checklist. If you can fulfill these objectives, you are well-prepared for the exam. The verbs (Explain, Compare, Describe, Evaluate, Assess) indicate the depth of understanding required.

![[All_slides_nes.pdf#page=312]]
**Week 10 Slide 5 – Outline**

*Notes:*
*   This slide provides a more detailed **topic outline**, breaking down the five main sections from the "Structure" slide.
*   It's useful for mapping the flow of concepts:
    1.  **Quick intro to ML**: Covers basic definitions (AI, ML, DL) and how neural networks work.
    2.  **Wetware I**: Focuses on *applications* (e.g., healthcare, agriculture) and the core *reasons* for embedding ML (BLERP acronym).
    3.  **Hardware**: Covers the computing continuum (cloud/fog/edge), specific platforms (CPU, MCU, GPU, NPU), how NPUs accelerate NNs, and niche topics (e.g., neuromorphic).
    4.  **Software**: Covers the pipeline (collect, train, compress, convert, deploy), details of compression techniques (pruning, quantization, NAS), deployment tools, and niche topics (e.g., federated learning).
    5.  **Wetware II**: Focuses on ethics, responsibility, and a case study (Flock Safety).
*   **Exam Relevance:** This is your chapter list. Questions can come from any of these areas. Pay special attention to the "Latest and niche topics" as they can be used for deeper, critical assessment questions.

![[All_slides_nes.pdf#page=313]]
**Week 10 Slide 6 – Quick introduction to ML**

*Notes:*
*   This slide is a section header, marking the start of the foundational Machine Learning (ML) concepts.
*   No technical content is presented here. The actual introduction begins on the next slide.
*   For exam purposes, this signals that the following slides will cover basic ML/DL theory necessary to understand the embedded-specific challenges later.

![[All_slides_nes.pdf#page=314]]
**Week 10 Slide 7 – What is even ML/AI/DL?**

*Notes:*
*   This slide clarifies the often-confused hierarchy of key buzzwords.
*   **Definitions:**
    *   **Artificial Intelligence (AI)**: The broad goal of making machines perform tasks that seem intelligent.
    *   **Machine Learning (ML)**: A subset of AI. Instead of programming explicit rules, the system *learns* patterns from data.
    *   **Deep Learning (DL)**: A subset of ML that uses **deep neural networks** (many layers). Most modern AI breakthroughs are due to DL.
*   **Exam Relevance:** You should know this hierarchy. While the terms are often used interchangeably, for embedded systems, we are almost always dealing with **DL models** (neural networks) that need to be made efficient. The slide states the focus is mostly on DL.

![[All_slides_nes.pdf#page=315]]
**Week 10 Slide 8 – Other buzzwords I should know?**

*Notes:*
*   This slide defines key terms related to running ML on devices, crucial for the networked embedded systems context.
*   **Edge AI**: Running ML models *on the device* where data is generated (e.g., smartphone, IoT sensor), not in a remote cloud.
*   **TinyML**: A sub-field focused on running models on **extremely resource-constrained** devices (microcontrollers with limited memory, compute, and power). This is the core focus of the lecture.
*   Other aliases include AIoT (AI + IoT), edge computing, and embedded/resource-constrained ML.
*   The diagram shows TinyML as the intersection of Machine Learning and Embedded Systems.
*   **Exam Relevance:** You must know the distinction between **Edge AI** (broader) and **TinyML** (more extreme constraints). TinyML is the key challenge in our domain. Be prepared to explain what makes a device "resource-constrained" (low power, small memory, slow CPU).

![[All_slides_nes.pdf#page=316]]
**Week 10 Slide 9 – The artificial neuron**

*Notes:*
*   This slide explains the basic building block of neural networks: the **artificial neuron** (or perceptron).
*   **Function:** It computes a **weighted sum** of its inputs, adds a **bias**, and then applies a **non-linear activation function** (e.g., sigmoid, ReLU).
    *   *Inputs ($x_1...x_m$)*: Data features (e.g., pixel values, sensor readings).
    *   *Weights ($w_1...w_m$)*: Parameters learned during training. They represent the importance of each input.
    *   *Bias ($b$)*: An adjustable offset that allows the neuron to shift its activation threshold.
    *   *Activation function ($\phi$)*: Introduces non-linearity (e.g., a threshold), allowing the network to learn complex patterns.
*   The slide notes a single neuron is not useful, but stacking many layers of them creates a powerful model.
*   **Exam Relevance:** Understand the role of each component (weights, bias, activation). The core computation is the **multiply-accumulate (MAC)** operation (weighted sum), which is highly relevant for hardware acceleration (NPUs optimize for this).

![[All_slides_nes.pdf#page=317]]
**Week 10 Slide 10 – Deep neural networks**

*Notes:*
*   This slide introduces the **Deep Neural Network (DNN)**, specifically a **Multilayer Perceptron (MLP)**, which is created by stacking layers of artificial neurons.
*   **Structure:**
    *   **Input Layer:** Receives the raw data (e.g., vector of pixel values).
    *   **Hidden Layers:** Multiple layers of neurons that transform the data through successive weighted sums and activations. "Deep" refers to having many hidden layers.
    *   **Output Layer:** Produces the final prediction (e.g., "cat" or "not cat").
*   **Key Property:** A DNN with enough neurons can **approximate any continuous function**. This is called the *universal approximation theorem*.
*   **Application Example:** The complex function of recognizing a cat in an image can be learned by a DNN.
*   **Exam Relevance:** Know what makes a network "deep" (multiple hidden layers). Understand that this powerful flexibility (approximating any function) is why we use DNNs, but it also makes them computationally heavy—hence the need for compression and efficient hardware for embedded use. The example connects the abstract concept to a concrete embedded ML task (computer vision).

![[All_slides_nes.pdf#page=318]]
**Week 10 Slide 11 – Deep learning**

*Notes:*
*   This slide describes the **training process** for a Deep Neural Network (DNN).
*   **Process Steps:**
    1.  Start with a model with **random weights** (initially useless).
    2.  **Feed data** (e.g., labeled images) to get a prediction.
    3.  Compute a **loss function** (e.g., cross-entropy) to measure the error (how wrong the prediction was).
    4.  Adjust the model's **weights** to reduce this error. The primary method is **backpropagation** combined with **gradient descent**.
        *   *Backpropagation* calculates how much each weight contributed to the error.
        *   *Gradient Descent* updates the weights in the direction that reduces the error.
*   With enough data and iterations, the model "learns" the task by converging on a good set of weights.
*   **Exam Relevance:** You don't need to know the math of backpropagation in detail, but you must understand the *concept* of training: starting random, measuring error, and iteratively adjusting weights. Contrast this with **inference** (using the trained model), which is what happens on the embedded device. The heavy computation of *training* is typically done in the cloud, while *inference* is deployed to the edge.

![[All_slides_nes.pdf#page=319]]
**Week 10 Slide 12 – Is it really that simple?**

*Notes:*
*   This slide presents a balanced view of Deep Learning (DL), discussing its successes and challenges.
*   **Why "Yes" (It's simple):**
    *   DL is empirically successful for many tasks (vision, speech, etc.).
    *   Success often comes from scaling: **larger models + more data + more compute** (referencing Sutton's "Bitter Lesson" and neural scaling laws).
*   **Why "No" (It's not simple):**
    *   **Data labeling** is manual, expensive, and time-consuming.
    *   **Training** large models is computationally very expensive (requires powerful GPUs/cloud).
*   **Beyond MLPs:**
    *   Different data types (images, text, audio) require specialized **model architectures**.
    *   Examples: **Convolutional Neural Networks (CNNs)** for images, **Recurrent Neural Networks (RNNs)** for sequences, **Transformers** for language.
    *   You cannot just treat an image as a flat vector of pixels for good performance.
*   **Exam Relevance:**
    *   Understand the **practical challenges** (data, compute cost) of DL.
    *   Know that **different architectures exist** for different data modalities. For embedded vision, CNNs are most common.
    *   The "Bitter Lesson" concept implies that for embedded systems, we often can't rely on brute-force scaling—we need efficiency techniques (compression, specialized hardware).

![[All_slides_nes.pdf#page=320]]
**Week 10 Slide 13 – Wetware I**

*Notes:*
*   This is a section header slide introducing **Wetware I**, which covers the human-centric motivations and application areas for embedded machine learning.
*   "Wetware" is a metaphor for the human element (the brain). This section answers *why* we bother with embedded ML.
*   The next slides will cover real-world needs, challenges, and concrete examples.
*   **Exam Relevance:** This context is crucial. You may be asked to justify the use of embedded ML or identify suitable application areas based on given constraints.

![[All_slides_nes.pdf#page=321]]
**Week 10 Slide 14 – Human needs**

*Notes:*
*   This slide frames the motivation for embedded ML within the context of global **Sustainable Development Goals (SDGs)** set by the United Nations.
*   The icons represent broad human needs and challenges where technology can help, such as:
    *   Good Health and Well-being
    *   Quality Education
    *   Clean Water and Sanitation
    *   Affordable and Clean Energy
    *   Sustainable Cities and Communities
    *   Climate Action
*   **Exam Relevance:** This provides the "big picture" justification. Embedded ML isn't just a technical exercise; it's a tool to address grand societal challenges. You might be asked to propose how embedded ML could be applied to a specific goal (e.g., using sensor networks for climate monitoring or wearable devices for healthcare). It connects the technical course to broader engineering responsibility.

![[All_slides_nes.pdf#page=322]]
**Week 10 Slide 15 – Current challenges**

*Notes:*
*   This slide highlights specific **global trends and challenges** that increase the need for smart, efficient systems like embedded ML.
*   **Key Projections for 2050:**
    *   Global population: **9.7 billion**
    *   Population over 60: **22%**
    *   Population in urban areas: **68%**
*   These trends create pressure in areas like:
    *   **Food Security**: Need for efficient, high-yield agriculture.
    *   **Preventative Healthcare**: Managing care for an aging population.
    *   **Efficient Resource Management**: Managing energy, water, and waste in dense cities.
*   **Exam Relevance:** Understand that these demographic and urban trends are **drivers** for embedded ML. They create problems where decentralized, intelligent, and real-time decision-making is valuable. For example, precision farming (embedded ML on tractors/drones) addresses food security, while health monitors for the elderly address preventative healthcare.

![[All_slides_nes.pdf#page=323]]
**Week 10 Slide 16 – Where can embedded ML help?**

*Notes:*
*   This slide lists concrete **application domains** for embedded machine learning. These are practical examples of where the technology is deployed.
*   **Domains and Examples:**
    *   **Manufacturing & Industrial**: Fault detection in machinery, predictive maintenance (avoiding downtime).
    *   **Automotive & Transportation**: Autonomous driving assistance, traffic flow management.
    *   **Agriculture & Food Production**: Precision farming (targeted water/fertilizer), pest detection, predicting crop yield.
    *   **Healthcare**: Wearable monitors (heart rate, glucose), AI-assisted diagnostics (portable ultrasound).
    *   **Smart Cities & Infrastructure**: Managing smart grids, water networks, waste collection.
    *   **Environmental Monitoring**: Real-time detection of wildfires, floods, or illegal poaching using sensor networks.
*   **Exam Relevance:** You should be able to recognize and suggest applications. A common exam question could be: "Given a scenario (e.g., a factory), propose an embedded ML solution and justify it." The key is that the ML inference happens *on or near* the sensor/device in these applications.


![[All_slides_nes.pdf#page=324]]
**Week 10 Slide 17 – BLERP! [3]**

*Notes:*
*   This slide provides the core technical **motivations** for doing ML on embedded devices instead of in the cloud. Remember the acronym **BLERP**.
*   **B - Bandwidth**: Transmitting raw data (e.g., continuous video) from thousands of devices would overwhelm network infrastructure.
*   **L - Latency**: Local processing enables **real-time** responses (e.g., a robot arm avoiding an obstacle, wake-word detection), which is critical for many applications.
*   **E - Economics**: It's cheaper to process data locally than to pay for constant cloud data transmission and cloud compute cycles.
*   **R - Reliability**: Systems are more fault-tolerant and robust if they don't depend on a constant, high-quality cloud connection.
*   **P - Privacy**: Sensitive data (e.g., audio from your home, health metrics) stays on the device, reducing opportunities for breaches or misuse.
*   **Exam Relevance:** **This is extremely exam-relevant.** You must be able to list and explain these motivations. BLERP is a perfect framework for justifying an edge/embedded ML approach in any scenario. Contrast these points with the cloud's advantages (unlimited compute, easy updates).

![[All_slides_nes.pdf#page=325]]
**Week 10 Slide 18 – Some real-world examples**

*Notes:*
*   This slide presents two detailed case studies of deployed embedded ML systems, showing how the BLERP motivations play out in practice.

| Example | Hardware & Task | Why Embedded? (BLERP) |
| :--- | :--- | :--- |
| **Early Wildfire Detection [4]** | Gas sensors (Bosch BME688) on trees. On-device ML model detects fire-related gases. Alerts sent via LoRaWAN mesh. | **Low Power/Battery**: Always-on, ultra-low-power. <br> **Bandwidth**: Only sends alerts, not raw gas data. <br> **Latency**: Faster local detection than sending data for cloud analysis. <br> **Reliability**: Works in forests with poor connectivity. |
| **Traffic Monitoring [5]** | Camera-based devices on roads. On-device vision models estimate traffic demand to control lights. | **Latency**: Real-time light control is critical. <br> **Bandwidth**: Sends aggregated traffic data, not continuous video streams. <br> **Privacy**: Possibly avoids transmitting identifiable video. |

*   **Exam Relevance:** These are perfect examples to cite in an exam answer. They demonstrate **TinyML** (low-power sensors) and **Edge AI** (more capable camera devices). They show a hybrid approach: simple sensing with ML at the extreme edge (wildfire) and more complex vision processing at the roadside (traffic).

![[All_slides_nes.pdf#page=326]]
**Week 10 Slide 19 – Hardware**

*Notes:*
*   This is a section header slide, marking the start of the **Hardware** part of the lecture.
*   This section will cover the different computing platforms and paradigms used for embedded ML, moving from the cloud to the edge device.
*   The first topic is "The Computing Continuum," which explains the hierarchy of where computation can happen in a networked system.
*   **Exam Relevance:** Understanding the hardware landscape is critical for making design choices (e.g., which chip to use for a given task). This section directly addresses the learning objective to "Compare HW platforms."


![[All_slides_nes.pdf#page=327]]
**Week 10 Slide 20 – The computing continuum**

*Notes:*
*   This slide introduces the **computing continuum**, a model describing where processing happens in a distributed system, from the centralized cloud to the far edge.
*   **Three Key Levels:**
    *   **Cloud**: Centralized data centers. **High throughput**, virtually unlimited compute/storage, but **high latency**. Used for heavy training, batch processing, and complex analytics.
    *   **Fog**: Intermediate nodes (gateways, local servers). Act as a bridge. Perform pre-processing, caching, data aggregation/filtering. Reduce load on cloud and network.
    *   **Edge**: The end devices themselves (IoT sensors, cameras, wearables). **Low latency**, **resource-constrained**, operate on **streaming data** in **real-time**.
*   **Real-world Example - Smart Speaker:**
    *   **Edge**: Always-listening microphone runs a tiny ML model for *wake-word detection* ("Hey Google").
    *   **Cloud**: Once awake, the full audio is sent to the cloud for *speech recognition* and complex query handling.
*   **Exam Relevance:** You must understand the roles and trade-offs of each level. Many embedded ML solutions use a **hybrid approach** (like the smart speaker). You should be able to decide which parts of an ML pipeline belong at which level based on latency, privacy, and resource needs.

![[All_slides_nes.pdf#page=328]]
**Week 10 Slide 21 – What makes embedded ML different?**

*Notes:*
*   This slide directly contrasts the design and operation environments of **Cloud ML** versus **Edge/Embedded ML**. These are fundamental constraints for the rest of the lecture.

| Aspect | Cloud ML | Embedded/Edge ML |
| :--- | :--- | :--- |
| **Resources** | Virtually **unlimited** (compute, memory, storage). | **Severely constrained** by cost, size, and **battery life**. |
| **Latency** | Less sensitive; can process data in **batches**. | Must be **always-on** and provide **real-time**, streaming responses. |
| **Model Updates** | Can be retrained and **deployed instantly**. | Updating firmware/models after deployment is **difficult or impossible**. |
| **Hardware** | **General-purpose** (CPU/GPU clusters); can run any model. | **Application-specific** hardware with **limited flexibility** and library support. |
| **Model Design** | Can use large, complex models for maximum accuracy. | Models must be **tailored** to the specific hardware (or HW chosen for the model). |

*   **Exam Relevance:** This comparison is **extremely exam-relevant**. It summarizes the core challenges of embedded ML. You will need to apply these constraints when evaluating design choices (e.g., "Why can't we just use the cloud model on this sensor?"). The key takeaway: **Edge is about constrained, real-time, and fixed-function operation.**

![[All_slides_nes.pdf#page=330]]
**Week 10 Slide 23 – Overview of hardware platforms**

*Notes:*
*   This slide provides a high-level comparison of the main processing platforms used in embedded ML. Understanding their roles is key.

| Platform | Characteristics | Typical Applications | Examples |
| :--- | :--- | :--- | :--- |
| **Microprocessor (CPU/MPU)** | High frequency, multi-core, sophisticated cache/instructions. General-purpose control. | Robotics, automotive infotainment, advanced IoT gateways, smartphones. | x86, ARM Cortex-A series. |
| **Microcontroller (MCU)** | **Low frequency, low power**, built-in memory & peripherals. The heart of **TinyML**. | Wearables, simple IoT sensors, industrial automation, personal devices. | ARM Cortex-M, RISC-V, ESP32. |
| **Graphics Processing Unit (GPU)** | Massively parallel (SIMD), high throughput & bandwidth. | Heavy parallel workloads, computer vision, **smartphone AI acceleration**. | NVIDIA Jetson, Qualcomm Adreno. |
| **Neural Processing Unit (NPU)** | Specialized for NNs. Low-precision math, optimized data flow, static graph execution. | **Accelerating neural network inference** on edge devices. | ARM Ethos, Google Edge TPU, Intel Movidius. |

*   **Key Points:**
    *   **MCUs** are the core of **resource-constrained TinyML**.
    *   **NPUs** are **domain-specific accelerators** for NN inference, not general-purpose.
    *   Real-world solutions often **combine platforms** (e.g., an MCU for control + an NPU for acceleration).
*   **Exam Relevance:** You must be able to match a platform to an application given constraints (power, cost, performance need). Know that NPUs exist specifically to make NN inference efficient on edge devices.

![[All_slides_nes.pdf#page=331]]
**Week 10 Slide 24 – Other platforms and terms**

*Notes:*
*   This slide introduces other important hardware components and terms in the embedded/computing landscape.
*   **DSP (Digital Signal Processor):**
    *   **Optimized** for mathematical processing of signal data (audio, radar, images).
    *   Features like **SIMD** (Single Instruction, Multiple Data) and **fixed-point math** are common.
*   **FPGA (Field-Programmable Gate Array):**
    *   **Reconfigurable** hardware logic.
    *   Used for **prototyping** or **low-volume, domain-specific** acceleration where flexibility is key.
*   **SoC (System-on-Chip):**
    *   Integrates **multiple components** (CPU, memory, storage, I/O, sometimes NPU/GPU) onto a single chip.
    *   Provides a balance of performance and integration, common in smartphones and complex IoT devices.
*   **ASIC (Application-Specific Integrated Circuit):**
    *   A **custom chip** designed for one specific task (e.g., video encoding, Bitcoin mining).
    *   **Highest efficiency** but **high design cost**; only economical for very high volumes (like smartphone NPUs).
*   **Exam Relevance:** Understand that **FPGAs** offer flexibility post-manufacturing, while **ASICs** offer peak efficiency for fixed tasks. **SoC** is a common architectural approach. **DSPs** are often found in sensor fusion or audio processing pipelines.

![[All_slides_nes.pdf#page=332]]
**Week 10 Slide 25 – What changes in practice?**

*Notes:*
*   This slide explains the **architectural differences** between CPU, GPU, and NPU, which lead to their different performance characteristics.
*   **Core Design Philosophy:**
    *   **CPU**: Few, complex cores optimized for **sequential control flow** and diverse tasks (branch prediction, out-of-order execution). **General-purpose**.
    *   **GPU**: Many, simpler cores executing the **same instruction** on multiple data streams (SIMT). Optimized for **parallel data processing** (like graphics or matrix math).
    *   **NPU**: **Fixed-function hardware** (e.g., MAC arrays, activation units) arranged for **dataflow** execution. Optimized for the **predictable, parallel patterns** of neural networks.
*   **Diagram Key:**
    *   CPU has complex control logic (branch prediction).
    *   GPU has many Streaming Multiprocessors (SMs) with shared memory.
    *   NPU has dedicated units for MAC operations, activation/pooling, and weight decompression.
*   **Exam Relevance:** You should understand *why* an NPU is more energy-efficient than a CPU for NN inference: it eliminates general-purpose overhead and is a **domain-specific accelerator**. The CPU is good for control logic, the GPU for parallel data tasks, and the NPU for fixed NN graphs.

![[All_slides_nes.pdf#page=333]]
**Week 10 Slide 26 – Real-world examples**

*Notes:*
*   This slide shows two real-world products that exemplify the **hybrid use of hardware platforms** and the **computing continuum**.

| Example | Hardware (SoC) | Processing Distribution |
| :--- | :--- | :--- |
| **Reolink RLC-810A Surveillance Camera** | Novatek NT9852x: **2x Cortex-A9 CPUs + NPU** | **Edge (On-device)**: Motion detection, object recognition (person/vehicle/animal). <br> **Fog (Hub)**: Local storage, video captioning. <br> **Cloud**: Remote storage, natural language queries. |
| **Butterfly Network iQ3 Ultrasound Probe** | Microchip MPFS250T: **4x RISC-V CPUs + FPGA** | **Edge (On-probe)**: Image acquisition & preprocessing. <br> **Edge (Smartphone)**: Runs diagnostic ML models. <br> **Cloud**: Data storage, model marketplace. |

*   **Key Takeaways:**
    1.  **SoCs combine different processor types** (CPU+NPU, CPU+FPGA) to balance control and acceleration.
    2.  Tasks are distributed across the **computing continuum** (edge/fog/cloud) based on latency, privacy, and complexity needs.
    3.  The **edge device often handles sensitive, real-time inference** (object recognition, image preprocessing), pushing only results or summaries to the next level.
*   **Exam Relevance:** These are excellent examples of *applied embedded ML*. You may be asked to analyze a product and identify the role of its hardware components or explain its data flow across the computing continuum.


![[All_slides_nes.pdf#page=334]]
**Week 10 Slide 27 – Hardware**

*Notes:*
*   This is a sub-section header for **"Neural network acceleration."**
*   The following slides will dive deeper into *why* and *how* specialized hardware like NPUs accelerate neural network inference, which is a core topic for efficient embedded ML.
*   **Exam Relevance:** Understanding acceleration principles is key to justifying the use of NPUs over general-purpose CPUs for deployed models.


![[All_slides_nes.pdf#page=335]]
**Week 10 Slide 28 – Why do we need custom accelerators?**

*Notes:*
*   This slide explains the unique **computational properties of neural networks** that make them suitable for specialized hardware acceleration (NPUs).
*   **NN Characteristics Enabling Acceleration:**
    1.  **Static Computational Graphs**: The sequence of operations is fixed after training (no unpredictable branching). This allows for **efficient scheduling and pipelining**.
    2.  **Data Reuse**: Model weights are used repeatedly across many inputs. This allows them to be kept in **fast, local memory** (caches/SRAM) to avoid costly trips to main memory.
    3.  **Dominance of MAC Operations**: The core math is **Multiply-Accumulate (MAC)**. Hardware can be optimized almost entirely for this.
    4.  **Low-Precision Arithmetic**: Networks can often run with **INT8 or lower precision** with minimal accuracy loss, drastically reducing memory and compute needs.
*   **NPU Design Priorities:** (Different from CPUs)
    *   **Energy efficiency** over flexibility.
    *   **Minimal data movement** (the "memory wall" is a major bottleneck).
    *   **High compute utilization** (keeping the MAC units busy).
    *   Maximize **throughput per Watt**.
*   **Exam Relevance:** You must be able to list these properties and explain how they lead to efficient hardware. This is the rationale behind NPUs. Contrast this with the needs of a general-purpose CPU (which must handle unpredictable branches and diverse instructions).



![[All_slides_nes.pdf#page=336]]
**Week 10 Slide 29 – Architecture overview**

*Notes:*
*   This slide dissects the architecture of a typical microNPU, using **ARM Ethos-U55** as a case study. It shows how an NPU integrates with an MCU system.
*   **System Components:**
    *   **Host MCU** (e.g., Cortex-M): The main processor. It **controls the NPU**, initiating inference jobs and handling other system tasks.
    *   **System Memory (FLASH/SRAM)**: Stores the model weights, input/output data, and application code.
*   **NPU Internal Blocks:**
    *   **DMA (Direct Memory Access) Controller**: Efficiently moves data between system memory and the NPU's **local memory** without CPU intervention.
    *   **Control Unit**: Parses commands from the host and **orchestrates** the dataflow and computation.
    *   **MAC Engine**: The core compute unit, accelerates **dot products** (matrix multiplications).
    *   **Elementwise Engine**: Handles parallel operations like **activation functions**, pooling, and normalization.
    *   **Local Memory**: Holds **weights for the current layer** and **partial results**, minimizing access to slower main memory.
    *   **Weight Decoder**: Decompresses weights if a compression format is used.
*   **Exam Relevance:** Understand the **dataflow**: Host MCU sets up job → DMA fetches weights/inputs → Control unit manages computation in MAC/Elementwise engines using local memory → DMA writes back results. The separation of compute units and use of local memory are key to efficiency.


![[All_slides_nes.pdf#page=337]]
**Week 10 Slide 30 – Systolic arrays**

*Notes:*
*   This slide introduces the **systolic array**, a key hardware architecture used in many NPUs and TPUs to achieve high throughput for matrix operations.
*   **How it works:**
    *   **Weights are pre-loaded** into each processing element (PE) in the array.
    *   **Input data** flows horizontally through the array (left to right).
    *   **Partial results** (accumulations) flow vertically through the array (top to bottom).
    *   Each PE performs a **Multiply-Accumulate (MAC)** operation on the passing data and its stored weight, adding the result to the incoming partial sum.
*   **Advantages for NN Acceleration:**
    *   **Data Reuse**: Each input and weight is used multiple times as it propagates, maximizing compute per memory fetch.
    *   **Local Data Movement**: Communication is only with neighboring PEs, reducing energy cost.
    *   **Minimal Overhead**: Simple, regular control structure.
    *   **High Throughput**: Produces one output per cycle in a pipelined fashion.
*   **Exam Relevance:** The systolic array is a classic example of hardware optimized for the **MAC-dominated, data-reuse** pattern of NNs. You should understand its basic operation and why it's efficient (minimizes data movement, high utilization). It's a concrete example of NPU design priorities in action.


![[All_slides_nes.pdf#page=339]]
**Week 10 Slide 32 – Compute-in-memory**

*Notes:*
*   This slide introduces **Compute-in-Memory (CiM)** as a paradigm shift to address the **"memory wall"** bottleneck.
*   **The Problem (Memory Wall):** In traditional systems (von Neumann architecture), the CPU fetches data from memory, computes, and writes back. Data movement between memory and processor is **slow and energy-intensive**, becoming the main bottleneck for data-heavy workloads like ML.
*   **The CiM Solution:** Performs **computation directly inside the memory array** (or very close to it), drastically reducing the need to move data.
*   **Key Idea:** Make computing architectures **data-centric** rather than compute-centric.
*   **Exam Relevance:** Understand CiM as a response to the fundamental von Neumann bottleneck. Its promise is **radically improved energy efficiency** for ML workloads by minimizing data movement. It's an emerging research area that could enable next-generation ultra-low-power ML chips.

![[All_slides_nes.pdf#page=340]]
**Week 10 Slide 33 – In/near-sensor computing**

*Notes:*
*   This slide presents **in-sensor** and **near-sensor computing** as techniques to reduce the cost of data movement from the *sensor itself* to the processor.
*   **The Problem:** Moving raw analog sensor data (e.g., high-resolution video) to a central processor for conversion and analysis consumes significant **power and bandwidth**.
*   **The Solutions:**
    *   **Near-Sensor Computing**: Place **specialized processing units** very close to the sensor (on the same chip or package) to pre-process data *before* sending it to the main CPU.
    *   **In-Sensor Computing**: Integrate **simple computation directly into the sensor's pixel/circuit** during the analog-to-digital conversion.
*   **Examples:**
    *   **IMU**: On-sensor step counting or gesture recognition.
    *   **Microphone**: On-sensor voice activity detection or keyword spotting.
    *   **Camera**: Extracting only a region of interest (ROI) instead of the full frame.
*   **Exam Relevance:** This is a logical extension of the "minimize data movement" principle. It's highly relevant for **battery-powered sensor nodes**. You should understand the concept and be able to give an example. It pushes intelligence to the absolute furthest edge of the network.


![[All_slides_nes.pdf#page=341]]
**Week 10 Slide 34 – Neuromorphic computing**

*Notes:*
*   This slide introduces **neuromorphic computing**, a biologically-inspired approach that differs fundamentally from conventional deep learning.
*   **Conventional NNs vs. Neuromorphic Systems:**

| Aspect | Conventional NNs | Neuromorphic Systems |
| :--- | :--- | :--- |
| **Operation** | Clock-driven, synchronous. | **Event-driven, asynchronous**. |
| **Computation** | Dense matrix operations every cycle. | **Sparse computations** only when an "event" (spike) occurs. |
| **Neuron Model** | Continuous activations (e.g., ReLU). | **Spiking neurons** that fire binary pulses. |
| **Motivation** | Mathematical efficiency. | **Biological plausibility** and energy efficiency. |

*   **Key Technologies:**
    *   **Spiking Neural Networks (SNNs)**: The software model that uses spikes.
    *   **Neuromorphic Hardware**: Mixed-signal or digital chips designed to efficiently simulate SNNs.
    *   **Event-based Sensors**: e.g., "event cameras" that only output pixels when brightness changes.
*   **Advantages:**
    *   **Ultra-low power** due to sparsity and event-driven nature.
    *   Potential for **continual learning** (adapting to new data on the fly).
*   **Exam Relevance:** Know that neuromorphic computing is a **different paradigm** (spiking, event-driven) promising extreme efficiency. It's a niche but emerging topic. The diagram shows a spiking neuron's membrane potential integrating inputs until it fires a spike.
![[All_slides_nes.pdf#page=342]]
**Week 10 Slide 35 – Software**

*Notes:*
*   This is a major section header, marking the start of the **Software** part of the lecture.
*   This section covers the practical workflow and tools needed to take a machine learning model from concept to a running application on an embedded device.
*   The first topic is "The embedded ML pipeline," which outlines the end-to-end process.
*   **Exam Relevance:** This is a core part of the "Describe model compression techniques and deployment steps" learning objective. You need to know this pipeline.


![[All_slides_nes.pdf#page=343]]
**Week 10 Slide 36 – The embedded ML pipeline**

*Notes:*
*   This slide outlines the standard **pipeline for developing and deploying an embedded ML model**. It's a cycle, indicating continuous improvement.
*   **Pipeline Stages:**
    1.  **Collect Data**: Acquire and label sensor/data relevant to the task.
    2.  **Train**: Design and train the model (typically on powerful GPUs/cloud).
    3.  **Compress**: Apply techniques (pruning, quantization) to reduce the model's size and computational needs for the target hardware.
    4.  **Convert**: Export the compressed model to a hardware-compatible intermediate format (e.g., TFLite, ONNX).
    5.  **Deploy**: Compile the model into executable code and integrate it into the device's firmware.
    6.  **Monitor/Evaluate**: In production, check if the model performs well on real-world data; this can feed back into data collection.
*   **Exam Relevance:** **Memorize this pipeline.** You will likely need to list and describe the stages. A key insight is that **training is done in the cloud, inference is done on the edge**. The "Compress" stage is critical for embedded deployment and is covered in detail next.


![[All_slides_nes.pdf#page=344]]
**Week 10 Slide 37 – Evaluate/monitor what, exactly?**

*Notes:*
*   This slide details the **specific metrics** used to evaluate embedded ML models, which go beyond just accuracy.
*   **Standard ML Metric:** **Task performance** (e.g., accuracy, mean squared error) – checked after compression and in production.
*   **Embedded-Specific Metrics (Resource Constraints):**
    *   **Model Size** (kB/MB): Affects storage (Flash memory). Driven by # of parameters and their **precision** (e.g., INT8 vs. FP32).
    *   **Operations** (#FLOPs, #MACs): Measures computational complexity. Related to model architecture and size.
    *   **Inference Time** (µs/ms): Latency for a single prediction. Critical for real-time systems.
    *   **Throughput** (FPS - Frames Per Second): How much data can be processed continuously.
    *   **Memory Footprint** (kB/MB): Working memory (RAM) needed during inference. Includes model parameters *and* intermediate activations.
    *   **Energy Consumption** (µJ per inference): Directly impacts battery life. Perhaps the most important metric for TinyML.
*   **Exam Relevance:** You **must** know these metrics and what they measure. Exam questions may ask you to evaluate a model or choose a compression technique based on optimizing a specific metric (e.g., "Which technique best reduces memory footprint?"). They define the "efficiency" in "resource-efficient ML."


![[All_slides_nes.pdf#page=346]]
**Week 10 Slide 39 – Model compression: what and why**

*Notes:*
*   This slide introduces the fundamental purpose of **model compression**.
*   **Goal:** To **reduce a model's resource requirements** (size, computations, memory) while **maintaining its performance** (accuracy) as much as possible.
*   **Why it's possible/needed:** Deep learning models are often **overparameterized** (have more weights than strictly necessary) and contain **redundancy**. Compression finds and removes this redundancy.
*   **Core Idea:** We want a smaller, faster, more efficient model that is "good enough" for the task, not necessarily the most accurate one possible.
*   **Exam Relevance:** Understand the motivation. On embedded devices, we *must* compress models due to hardware constraints. The trade-off is typically a small loss in accuracy for a large gain in efficiency.


![[All_slides_nes.pdf#page=347]]
**Week 10 Slide 40 – Model compression: taxonomy**

*Notes:*
*   This slide presents a **taxonomy (classification tree)** of model compression techniques. It's a map of the field.
*   **Three Main Branches:**
    1.  **Reduce Resolution** (bits per number):
        *   **Quantization** (e.g., FP32 → INT8)
            *   **Post-Training Quantization (PTQ)**
            *   **Quantization-Aware Training (QAT)**
        *   **Binarization** (extreme quantization to 1 bit)
    2.  **Reduce Complexity** (# of operations):
        *   **Pruning** (removing weights)
            *   **Unstructured**
            *   **Structured**
        *   **Low-Rank Approximation** (factorizing weight matrices)
    3.  **Change Topology** (model architecture):
        *   **Knowledge Distillation** (train a small "student" model to mimic a large "teacher")
        *   **Neural Architecture Search (NAS)** (automatically design a small, efficient model)
*   **Exam Relevance:** This is a crucial overview. You should be able to name the three main categories and list techniques within them. This taxonomy helps you understand how different techniques achieve compression.


![[All_slides_nes.pdf#page=348]]
**Week 10 Slide 41 – Model compression: classification of techniques**

*Notes:*
*   This slide provides clear, concise definitions for the three main categories of compression from the taxonomy.
*   **Quantization (incl. Binarization):** Reduces the **numerical precision** (number of bits) used to represent model parameters and activations. Example: Converting from 32-bit floating point (FP32) to 8-bit integers (INT8). **Directly reduces model size and memory bandwidth needs.**
*   **Pruning & Low-Rank Approximation:** Reduce the **computational complexity** by reducing the number of arithmetic operations. They do this by removing parameters (pruning) or approximating weight matrices with smaller ones (low-rank). **Directly reduces the number of MACs.**
*   **Knowledge Distillation & Neural Architecture Search (NAS):** Alter the **model topology/architecture** itself. They result in a fundamentally different, smaller, or more efficient network design. **Affects both size and complexity.**
*   **Exam Relevance:** Be able to define each category and give an example. A common question is to categorize a described technique or to explain the primary effect of a technique (e.g., "Quantization primarily reduces memory footprint").


![[All_slides_nes.pdf#page=349]]
**Week 10 Slide 42 – Model compression: pruning (1)**

*Notes:*
*   This slide introduces **pruning**, a technique to remove redundant or less important parameters (weights) from a neural network.
*   **Biological Analogy:** The graphic compares neural network pruning to **synaptic pruning** in the human brain, where unused connections are eliminated over time to increase efficiency.
*   **Principle:** Not all weights in a trained network are equally important. Many have very small magnitudes and contribute little to the output. Pruning removes these, creating a **sparse network**.
*   **Benefits:** Reduces **model size** (fewer parameters to store) and **computations** (fewer MACs).
*   **Exam Relevance:** Understand the core idea of removing unimportant weights. The analogy to biology is a nice way to remember it. Pruning is a primary method for reducing *computational complexity*.


![[All_slides_nes.pdf#page=350]]
**Week 10 Slide 43 – Model compression: pruning (2)**

*Notes:*
*   This slide details the **granularity** of pruning – *what unit* of the model do we remove?
*   **Unstructured Pruning:** Removes **individual weights** anywhere in the network. Results in **irregular sparsity** (random zeroes in weight matrices).
    *   **Pro:** High compression ratio.
    *   **Con:** Requires **specialized hardware/software** to exploit sparsity; doesn't speed up standard CPUs/GPUs.
*   **Structured Pruning:** Removes **entire groups** of weights (e.g., a whole filter in a CNN, a channel, a neuron).
    *   **Pro:** Results in a **smaller, denser network** that runs efficiently on **general-purpose hardware**.
    *   **Con:** Lower compression ratio for same accuracy drop.
*   **Semi-structured Pruning:** A middle ground (e.g., removing blocks or specific patterns of weights). Aims for better hardware acceleration than unstructured.
*   **Exam Relevance:** You **must** know the difference between unstructured and structured pruning, especially their hardware implications. Structured pruning is more practical for common edge hardware (MCUs, CPUs). The diagram shows the spectrum from fine-grained (unstructured) to coarse-grained (structured).


![[All_slides_nes.pdf#page=351]]
**Week 10 Slide 44 – Model compression: pruning (3)**

*Notes:*
*   This slide covers **pruning criteria** (how to choose what to remove) and other practical aspects.
*   **Pruning Criteria (What to remove?):**
    *   **Weight Magnitude**: Simplest method. Remove weights with the smallest absolute values.
    *   **$\ell_1$ / $\ell_2$ Norm**: For structured pruning, remove groups (e.g., filters) with the smallest norm of their weights.
    *   **Sensitivity/Saliency**: Estimate how much removing a weight would increase the training loss.
    *   **BatchNorm Scaling Factors**: In CNNs, use the scaling factors ($\gamma$) from BatchNorm layers as a measure of channel importance.
*   **Practical Considerations:**
    *   **When?** Can be done *after* training, *during* training, or *iteratively* (prune a bit, re-train/finetune, repeat).
    *   **How much?** The **pruning ratio** (percentage of parameters removed). Can be set globally or per-layer.
*   **Key Insight from Graph:** **Iterative Pruning and Finetuning** (the blue line) maintains accuracy much better than one-shot pruning, even at high pruning ratios. **Finetuning after pruning is essential** to recover accuracy.
*   **Exam Relevance:** Know common criteria, especially magnitude-based. Understand that pruning is usually followed by finetuning. The iterative approach is a best practice.


![[All_slides_nes.pdf#page=352]]
**Week 10 Slide 45 – Model compression: quantization (1)**

*Notes:*
*   This slide introduces **quantization**, the process of mapping model weights and activations from high precision (e.g., 32-bit floating point) to lower precision (e.g., 8-bit integers).
*   **Visual:** Shows floating-point numbers being mapped to a smaller set of integer levels.
*   **Core Benefit:**
    *   **Reduces model size** (e.g., INT8 is 4x smaller than FP32).
    *   Allows models to run on hardware that **lacks floating-point units** (FPUs), such as many low-cost MCUs.
    *   Integer operations are **faster and more energy-efficient** than floating-point on most hardware.
*   **Uniform Quantization:** The most common method, which uses a **linear mapping** between integer values and floating-point ranges.
*   **Exam Relevance:** Quantization is **extremely important**. Know that it reduces memory footprint and enables deployment on MCUs. The primary trade-off is a potential, usually small, loss in accuracy.


	![[All_slides_nes.pdf#page=353]]
**Week 10 Slide 46 – Model compression: quantization (2)**

*Notes:*
*   This slide explains the **mathematics of uniform quantization**.
*   **Quantization Formula:** $r = S \cdot (q - Z)$
    *   $r$: Real (floating-point) value.
    *   $q$: Quantized (integer) value.
    *   $S$: **Scale factor** (the distance between quantization levels).
    *   $Z$: **Zero-point** (the integer value that maps to the real zero).
*   **Parameters:**
    *   **Scale ($S$)**: $S = \frac{r_{\max} - r_{\min}}{q_{\max} - q_{\min}}$
    *   **Zero-Point ($Z$)**: $Z = q_{\min} - \frac{r_{\min}}{S}$ (ensures zero is quantized without error)
    *   **Real Range**: $[r_{\min}, r_{\max}]$ (min/max of values to quantize).
    *   **Quantized Range**: $[q_{\min}, q_{\max}]$ (e.g., [-128, 127] for INT8).
*   **Exam Relevance:** You don't need to memorize the formulas for the exam, but you **must understand what the scale (S) and zero-point (Z) represent**. They are the key parameters that define the linear mapping between float and int. This is the foundation of how quantization works.


![[All_slides_nes.pdf#page=354]]
**Week 10 Slide 47 – Model compression: quantization (3)**

*Notes:*
*   This slide compares the two main **methodologies** for quantization and introduces key design choices.
*   **Post-Training Quantization (PTQ):**
    *   **Process:** Take a pre-trained FP32 model and quantize it.
    *   **Pros:** Simple, fast, **doesn't require labeled data or retraining**.
    *   **Cons:** Less accurate, especially at very low bit-widths (e.g., INT4).
*   **Quantization-Aware Training (QAT):**
    *   **Process:** Simulate quantization effects **during training**. The model learns weights that are robust to quantization.
    *   **Pros:** Much better accuracy at low bit-widths.
    *   **Cons:** More complex, requires a training pipeline and labeled data.
*   **Design Choices:**
    *   **Symmetric vs. Asymmetric:** Symmetric ($Z=0$) is simpler, often used for **weights**. Asymmetric is more accurate, often used for **activations**.
    *   **Per-Tensor vs. Per-Channel:** Using one $(S, Z)$ for an entire tensor (layer) vs. per output channel. Per-channel is more accurate.
*   **Exam Relevance:** Know the **key difference between PTQ and QAT** (when the quantization is applied) and their trade-offs (simplicity vs. accuracy). Know that QAT is needed for aggressive quantization. Be aware of symmetric/asymmetric as a concept.

![[All_slides_nes.pdf#page=355]]
**Week 10 Slide 48 – Model compression: neural architecture search (1)**

*Notes:*
*   This slide introduces **Neural Architecture Search (NAS)**, an automated method for designing efficient neural network architectures.
*   **NAS Process Loop:**
    1.  **Search Space (A)**: The set of all possible model architectures to consider.
    2.  **Search Strategy**: The algorithm that picks which architecture to try next (e.g., random, reinforcement learning).
    3.  **Performance Estimation**: How to quickly evaluate the chosen architecture's quality (accuracy, latency, size).
*   **Key Advantages for Embedded ML:**
    *   Can **optimize for multiple objectives** simultaneously (e.g., maximize accuracy **and** minimize latency).
    *   Can be **hardware-aware**, searching for architectures that run fast on a specific chip (e.g., a particular MCU).
    *   Can even **co-design hardware and software**.
*   **Exam Relevance:** Understand NAS as an **automated design tool** for finding efficient models. Its main benefit is **multi-objective optimization** tailored to hardware constraints. Contrast it with manual model design.


![[All_slides_nes.pdf#page=356]]
**Week 10 Slide 49 – Model compression: neural architecture search (2)**

*Notes:*
*   This slide focuses on the **Search Space** component of NAS.
*   **Search Space Definition:** The set of all possible neural network architectures that the NAS algorithm is allowed to explore.
*   **What it Includes:** Defined by architectural choices such as:
    *   Number of layers.
    *   Number of units/filters per layer.
    *   Type of operations in each layer (e.g., convolution type, kernel size).
    *   How layers/nodes are connected (e.g., skip connections).
*   **Trade-offs in Design:**
    *   **Larger, more flexible space**: More chance to find a great model, but **vastly more expensive** to search.
    *   **Smaller, constrained space**: Faster search, but limited by human designer's insight into what might work well.
*   **Exam Relevance:** Know that the search space is a critical design choice in NAS. It represents the "universe" of possible solutions. The fundamental challenge is balancing search cost with finding a good architecture.


![[All_slides_nes.pdf#page=357]]
**Week 10 Slide 50 – Model compression: neural architecture search (3)**

*Notes:*
*   This slide details **Search Strategies** and **Performance Estimation** methods in NAS.
*   **Search Strategies (How to explore the space?):**
    *   **Random Search**: Baseline. Randomly sample architectures.
    *   **Reinforcement Learning (RL)**: A "controller" network generates architectures, receives a "reward" (e.g., accuracy), and learns to generate better ones.
    *   **Genetic Algorithms (Evolutionary)**: Maintain a population of architectures, "mate" and "mutate" the best ones over generations.
    *   **Bayesian Optimization**: Builds a probabilistic model of architecture-performance relationship to intelligently pick promising ones to evaluate.
*   **Performance Estimation (The bottleneck):**
    *   **Problem:** Fully training and evaluating each candidate architecture is **prohibitively expensive**.
    *   **Efficient Alternatives:**
        *   **Learning Curve Extrapolation**: Predict final performance from early training epochs.
        *   **Weight Inheritance / Network Morphism**: Reuse weights from a parent network to speed up training.
        *   **Zero-Cost Proxies**: Use very cheap-to-compute metrics (e.g., gradient norms) that correlate with final performance.
*   **Exam Relevance:** You should know the names of common search strategies (RL, Evolutionary, Bayesian). The key takeaway is that **performance estimation is the major challenge**, leading to various clever approximations. NAS is computationally expensive but can produce state-of-the-art efficient models.


![[All_slides_nes.pdf#page=359]]
**Week 10 Slide 52 – Deployment tools**

*Notes:*
*   This slide frames the core **problem and solution** in the deployment tooling landscape.
*   **The Problem:** There is a huge variety of **heterogeneous hardware targets** (different MCUs, NPUs, SoCs, FPGAs), each requiring specialized code and optimization.
*   **The "Solution":** A fragmented ecosystem with:
    *   A few **model exchange formats** that act as common intermediaries (e.g., **ONNX**, **TensorFlow Lite (TFLite)**, NNEF). These are the "output" of the training/compression stage.
    *   **Many application-specific tools** provided by hardware vendors, chipmakers, and open-source projects that take these formats and compile/run them on specific hardware.
*   **Exam Relevance:** Understand that **no single tool works everywhere**. The workflow is typically: Train → Export to ONNX/TFLite → Use target-specific toolchain to compile for your hardware (e.g., STM32CubeAI for STM32 MCUs, Vela for Arm NPUs). This complexity is a practical challenge in embedded ML.


![[All_slides_nes.pdf#page=360]]
**Week 10 Slide 53 – Overview of tools**

*Notes:*
*   This slide categorizes the two main **approaches** that deployment tools take.
*   **1. Inference Engines (Runtimes):**
    *   **How they work:** Convert the model into an internal representation and provide a **runtime library** that gets integrated into the firmware. The runtime interprets the model graph during execution.
    *   **Pros:** Flexible, often easier to update the model without recompiling the whole firmware.
    *   **Examples:** **TensorFlow Lite for Microcontrollers (TFLM)**, ExecuTorch, ONNX Runtime.
*   **2. Compilers & Code Generators:**
    *   **How they work:** **Ahead-of-time (AOT) compilation** of the model into highly optimized, target-specific machine code (or C/C++ code). The result is a standalone function/library.
    *   **Pros:** Can achieve higher performance via aggressive optimization; often has a smaller memory footprint.
    *   **Examples:** **TVM**, XLA, IREE/MLIR.
*   **Many tools are a hybrid** of both approaches.
*   **Exam Relevance:** Know the conceptual difference between a **runtime interpreter** and an **AOT compiler**. TFLM (runtime) and TVM (compiler) are key examples. The choice affects performance, memory footprint, and flexibility.


![[All_slides_nes.pdf#page=361]]
**Week 10 Slide 54 – Vendor-specific tools**

*Notes:*
*   This slide presents a non-exhaustive table of **vendor-specific deployment tools**, highlighting the fragmented ecosystem.
*   **Key Takeaway:** Almost every major semiconductor vendor provides their own toolchain to deploy models to their hardware (MCUs, NPUs, SoCs). This is because they can apply deep hardware-specific optimizations.
*   **Patterns in the Table:**
    *   **MCU Vendors** (ST, NXP, Microchip, Renesas): Offer end-to-end solutions or plugins to convert and run models on their microcontrollers.
    *   **NPU / Accelerator Vendors** (Arm, Google, Hailo, BrainChip): Provide compilers and runtimes specifically to map NN graphs to their custom hardware.
    *   **SoC Vendors** (Qualcomm, MediaTek, Texas Instruments): Offer comprehensive SDKs for their application processors, which may include CPUs, GPUs, and NPUs.
*   **Examples to Note:** **Edge Impulse** is highlighted as a notable **multi-vendor, end-to-end platform** (web UI) that abstracts away some of this complexity.
*   **Exam Relevance:** You are **not expected to memorize this list**. However, you should understand that **vendor tools are the norm** for production deployment. The existence of this table illustrates the practical reality of embedded ML tooling. Knowing *that* tools like STM32CubeAI or Arm Vela exist is more important than their specific features.


![[All_slides_nes.pdf#page=363]]
**Week 10 Slide 56 – Continual learning**

*Notes:*
*   This slide introduces **Continual Learning (CL)**, also known as lifelong learning, which aims to allow models to **learn from new data after deployment**.
*   **Motivation:**
    *   **Concept Drift:** Real-world data distributions change over time (e.g., a camera's view changes with seasons).
    *   Retraining in the cloud and redeploying new models is often **infeasible** due to cost, bandwidth, or privacy constraints (e.g., medical devices).
*   **Core Challenge: Catastrophic Forgetting** – When learning new tasks, the model completely forgets how to perform old ones.
*   **Approaches:**
    *   **Progressive Networks:** Allocate *new parameters* for new tasks (avoids forgetting but grows model size).
    *   **Regularization:** Penalize changes to weights important for previous tasks (e.g., Elastic Weight Consolidation).
    *   **Memory-based:** Keep a small replay buffer of old data or generate synthetic samples to retrain on.
*   **Exam Relevance:** Understand the goal (on-device adaptation) and the main challenge (catastrophic forgetting). It's a key research area for making embedded ML systems more robust and long-lived.


![[All_slides_nes.pdf#page=364]]
**Week 10 Slide 57 – Federated learning**

*Notes:*
*   This slide explains **Federated Learning (FL)**, a distributed training paradigm designed for privacy and efficiency.
*   **Core Idea:** Train a shared global model **without centralizing raw user data**. Data remains on the local devices (clients).
*   **Process (Federated Averaging):**
    1.  Server sends the current global model to a subset of clients.
    2.  **Clients train the model locally** on their own data.
    3.  Clients send only the **model updates** (gradients or new weights) back to the server.
    4.  Server **aggregates** the updates (e.g., averages them) to improve the global model.
    5.  The new global model is broadcast back to clients.
*   **Advantages for Embedded/Edge ML:**
    *   **Enhanced Privacy:** Sensitive data (health, habits) never leaves the device.
    *   **Data Ownership:** Users/companies retain control.
    *   **Reduced Bandwidth:** Sending model updates is smaller than sending raw data.
    *   **Personalization & Collaboration:** Enables models that learn from many users' experiences without seeing their data.
*   **Exam Relevance:** Know the basic workflow and its **key advantages (privacy, bandwidth)**. It's a perfect solution for scenarios where data cannot be centralized (e.g., smartphone keyboard prediction, wearable health monitoring). Contrast with traditional cloud-based training.

![[All_slides_nes.pdf#page=365]]
**Week 10 Slide 58 – Dynamic inference**

*Notes:*
*   This slide introduces **Dynamic Neural Networks (DynNNs)**, which adapt their computation *during inference* based on the specific input.
*   **Problem with Static Networks:** They use the **same fixed amount of computation** for every input, whether it's easy (e.g., classifying a clear cat photo) or hard (a blurry dog). This is inefficient.
*   **Goal of DynNNs:** Achieve a **dynamic trade-off** between accuracy and efficiency (e.g., use more compute for hard samples, less for easy ones).
*   **Examples of Dynamic Inference Techniques:**
    *   **Early-Exiting:** Place "exit branches" at intermediate layers. Easy samples can be classified and exit early, skipping later layers.
    *   **Mixture-of-Experts (MoE):** The network has many "expert" sub-networks. A gating network chooses which few experts to activate for a given input.
    *   **Slimming:** Dynamically skip certain neurons, channels, or filters based on the input.
*   **Exam Relevance:** Understand the core concept: **adaptive computation based on input difficulty**. It's an advanced technique to improve average efficiency. Early-exiting is a classic and intuitive example. This represents a shift from static to conditional computation graphs.

![[All_slides_nes.pdf#page=367]]
**Week 10 Slide 60 – Responsible embedded ML**

*Notes:*
*   This slide presents a wheel diagram outlining the key pillars of **Responsible Embedded ML**.
*   **Core Principles:**
    1.  **Privacy & Data Protection**: Ensuring personal/sensitive data is handled securely, often by keeping it on-device.
    2.  **Fairness & Bias Mitigation**: Ensuring models do not discriminate against individuals or groups (e.g., based on race, gender).
    3.  **Transparency & Accountability**: Being able to explain how a system works and who is responsible for its decisions/errors.
    4.  **Sustainability**: Considering the environmental impact of manufacturing, operating, and disposing of devices.
    5.  **Monitoring & Reporting**: Continuously auditing system performance and impact in the real world.
    6.  **Compliance & Regulation**: Adhering to laws like GDPR (data privacy) and upcoming AI regulations.
    7.  **Public Engagement**: Involving communities affected by the technology in the decision-making process.
*   **Exam Relevance:** You should be familiar with these principles. They provide a framework for critically assessing an embedded ML application. An exam question might ask you to identify potential responsible AI issues in a given scenario.


![[All_slides_nes.pdf#page=369]]
**Week 10 Slide 62 – Flock Safety**

*Notes:*
*   This slide introduces **Flock Safety** as a prominent real-world example of embedded ML deployment and poses a critical question.
*   **What Flock Safety Does:**
    *   Deploys **camera-based Automated License Plate Readers (ALPR)**.
    *   Uses **on-device embedded ML** for license plate recognition and creating a "vehicle fingerprint" (make, model, color, etc.).
    *   **Scale:** ~90,000 devices across 6,000 clients, including ~5,000 police departments.
*   **Claimed Impact:** Solves **10% of US crimes** (700,000 cases/year). This is a powerful argument for its utility.
*   **Business Success:** $300M sales (2024), $7.5B valuation – indicating widespread adoption.
*   **The Central Question:** Is this an **"Embedded ML success story?"**
*   **Exam Relevance:** This is your case study. You need to know the facts: on-device ALPR, massive scale, used by law enforcement. The question frames the ethical dilemma: technological success vs. potential societal harm. The next slide provides the critical analysis.

![[All_slides_nes.pdf#page=370]]
**Week 10 Slide 63 – Some concerning aspects [16]**

*Notes:*
*   This slide critically analyzes Flock Safety against the **Responsible Embedded ML** principles, listing multiple serious concerns.
*   **Concerns Mapped to Principles:**

| Responsible ML Principle | Flock Safety Concern |
| :--- | :--- |
| **Privacy & Data Protection** | No opt-out; data shared with 3rd parties; reports of **hacked devices & leaked credentials**. |
| **Fairness & Bias Mitigation** | **Disproportionate deployment in marginalized communities**, potentially exacerbating over-policing. |
| **Transparency & Accountability** | **No public data on accuracy/error rates**; lack of oversight on data use. |
| **Public Engagement** | Deployed **without consulting local communities**. |
| **Monitoring & Reporting** | Official impact studies and crime-solving figures are **widely disputed**. |
| **Compliance & Regulation** | Devices installed without permits; long-term surveillance may violate the **4th Amendment** (unreasonable search). |

*   **Real-World Consequences:** The news headlines show concrete harms: a **nationwide search for a woman who had an abortion** and **immigration enforcement use**.
*   **Exam Relevance:** **This analysis is extremely exam-relevant.** You must be able to identify the ethical issues in a case study like this. Use the framework from Slide 60. The key takeaway is that **technical success (efficient on-device ML) does not equate to responsible or ethical success.** Embedded ML, especially in sensitive areas like surveillance, requires careful consideration of its societal impact.


![[All_slides_nes.pdf#page=371]]
**Week 10 Slide 64 – Additional resources**

*Notes:*
*   This slide lists **external resources** for further learning. It is provided for your reference.
*   **Online Courses:** Includes offerings from Harvard (TinyML), MIT, Edge Impulse, and Stanford. The "MEAD" course in Feb 2026 is noted as paid.
*   **Conferences & Events:** Edge AI/TinyML Summit, workshops at CVPR, ACACES Summer School.
*   **Curated Lists:** "Awesome" lists for Edge AI and TinyML on GitHub (community-maintained repositories of tools, papers, etc.).
*   **Exam Relevance:** These resources are **not part of the examinable material**. They are suggestions if you wish to explore topics in more depth. Your primary study source for the exam should be the content of these lecture slides.




WEEK 11 NOTES


![[All_slides_nes.pdf#page=377]] Week 11 slide 4 – Performance Objectives  
This slide outlines three major categories that define how “good” an embedded system is:

**Speed** refers to how fast the system reacts or processes work.

- _Short response time_ means the system should react quickly to inputs or events.
    
- _High throughput/bandwidth_ means it should handle many operations or large amounts of data per unit time.
    

**Efficiency** focuses on using minimal resources.

- _Low utilisation of computing resources_ means the system should not waste CPU or memory.
    
- _Low power_ is important for battery-powered or green systems.
    
- _Low cost_ refers to choosing hardware/software solutions that achieve the required functionality without unnecessary expense.
    

**Dependability** is about how trustworthy the system is over time.

- _Availability_ means the system should be ready to operate when needed (no downtime, no empty battery).
    
- _Reliability_ means it provides correct service with minimal failures.
    
- _Maintainability_ means it is easy to repair or update.
    
- _Security_ ensures confidentiality and integrity of data.
    

A helpful comparison:

|Objective Category|What It Ensures|Why It Matters in Embedded Systems|
|---|---|---|
|Speed|Fast reactions and high processing/data rates|Real-time constraints, user experience|
|Efficiency|Minimal power, resource use, and cost|Battery life, small form factor, affordability|
|Dependability|System works correctly, safely, and securely|Safety-critical applications, long deployments|

![[All_slides_nes.pdf#page=378]] Week 11 slide 5 – Performance Metrics  
This slide introduces three key metrics used to evaluate embedded system performance and explains what “good” means for each:

**Reliability**

- Defined as the _probability that an operation succeeds_.
    
- Higher reliability indicates fewer failures.
    
- Used for judging how trustworthy hardware, software, or communication links are.
    

**Delay (Latency)**

- The _time required to complete an operation_.
    
- Lower delay means the system responds or transmits information faster.
    
- Critical in real-time systems, networking, and control loops.
    

**Energy Consumption**

- The _energy required to complete an operation_.
    
- Lower energy consumption extends battery life and reduces operating cost.
    
- Particularly important for IoT and mobile systems.
    

A comparison of the metrics:

|Metric|What It Measures|“Better” Means|Typical Importance|
|---|---|---|---|
|Reliability|Success probability|Closer to 1|Safety, correctness|
|Delay|Time per operation|Lower|Real-time response|
|Energy Consumption|Energy used|Lower|Battery/green systems|

Each metric can conflict with others—for example, improving reliability with retries may increase delay and energy usage.

![[All_slides_nes.pdf#page=379]] Week 11 slide 6 – Reliability  
This slide explains what reliability means in different parts of an embedded system:

**Overall Meaning**

- Reliability is the _probability that something works correctly over time_.
    
- The opposite is the _probability of failure_.
    

**Types of Reliability**

- **Hardware reliability:** probability that physical components do not fail.
    
- **Software reliability:** probability that software runs without bugs causing incorrect behavior.
    
- **Network reliability:** ratio of successfully delivered packets to total packets sent.
    
- **Accuracy:** for predictive systems, reliability is reflected in prediction success rate.
    

These categories highlight that reliability is multi-layered: hardware, software, and communication channels all contribute to whether the system behaves correctly.

![[All_slides_nes.pdf#page=380]] Week 11 slide 7 – Measuring Reliability  
This slide describes how reliability is practically measured and why it can be challenging:

**How to Measure Reliability**

- Run the same operation many times and count how often it fails.
    
- The resulting value is between 0 and 1 (e.g., 0.99 means 99% success).
    

**Safety-Critical Systems**

- Even extremely small failure rates can be unacceptable if failures cause catastrophic outcomes.
    
- Example: 0.999 reliability sounds high, but it would imply 1 failure per 1000 operations—unacceptable for aviation.
    

**Reliability in Orders of Magnitude**

- High-reliability systems are often expressed using “nines”:
    
    - _Five nines_: 0.99999 → error probability < 10⁻⁵.
        

**Main Challenge**

- Achieving accurate reliability estimates requires very large numbers of measurements, because rare failures require long observation periods to detect.
    

Table summary:

|Concept|Explanation|
|---|---|
|Basic measurement|Count successes vs. failures over many trials|
|Safety-critical requirement|Extremely low failure probability|
|Representation|Often in multiple “nines”|
|Challenge|Need huge sample sizes for accuracy|
![[All_slides_nes.pdf#page=381]] Week 11 slide 8 – Example: Fair Coins  
This slide uses coin tossing as an analogy for measuring reliability and comparing two nearly identical systems.

**Scenario**

- A fair coin should have probability _p = 0.5_ of landing heads.
    
- Two coins (blue and orange) are tested. Their true probabilities are expected to be close to ideal, e.g., 0.49 < pREAL < 0.51.
    

**Goal**

- Determine which coin is _more fair_ (i.e., has probability closer to 0.5).
    

**Experimental Method**

1. Toss each coin repeatedly.
    
2. Count how many times each coin lands heads.
    
3. Compute the _error_ = pREAL – 0.5 for each coin.
    
    - Perfect fairness → error = 0.
        
4. Repeat the experiment until there is enough confidence to decide which coin is closer to fairness.
    

**Main Question**

- How many tosses are required to confidently distinguish a 0.505 coin from a 0.51 coin?
    
    - This illustrates the difficulty of estimating reliability when probabilities are close together: detecting small differences requires large numbers of trials.
        

Table summary:

|Element|Interpretation in embedded systems|
|---|---|
|Coin toss|Repeating an operation|
|Probability of heads|Probability of success|
|Error|Deviation from ideal reliability|
|Number of tosses|Amount of data needed to estimate reliability|
![[All_slides_nes.pdf#page=382]] Week 11 slide 9 – Example: Fair Coins (2000 tosses)  
This slide visualises how the measured probabilities of the two coins behave after _2000 tosses each_.

**Key Idea**

- With 2000 samples, the measured probabilities still fluctuate noticeably around the ideal 0.5.
    
- The blue and orange coin curves do not clearly separate enough to confidently say which is closer to fairness.
    

**What the plot shows**

- Both estimated probabilities drift above and below 0.5.
    
- The difference between the two coins’ measured values is small relative to the noise caused by limited sample size.
    

**Concept Illustrated**

- Even 2000 trials may be insufficient to reliably distinguish between probabilities that differ only slightly (e.g., 0.505 vs 0.51).
    
- This mirrors reliability measurements in embedded systems:
    
    - Small reliability differences require _very large_ sample sizes to detect statistically.
        

Table summary:

|Toss Count|What Happens|Reason|
|---|---|---|
|2000|Results fluctuate; no clear separation|Statistical noise still significant|
|Ideal Needed|Many more tosses|To shrink confidence intervals enough to resolve tiny probability differences|
![[All_slides_nes.pdf#page=383]] Week 11 slide 10 – Example: Fair Coins (10000 tosses)  
This slide shows how the estimates improve when the number of tosses increases from 2000 to **10,000**.

**Measured Results**

- pBLUE ≈ 0.505
    
- pORANGE ≈ 0.51
    

**Meaning**

- With 10,000 tosses, the statistical noise decreases enough that the two coins’ probabilities become distinguishable.
    
- The measured curves stabilise closer to their true values, and the difference between them becomes visible.
    

**Concept Demonstrated**

- Increasing sample size narrows the estimation error.
    
- For very small probability differences, large numbers of trials are needed before you can confidently say which system (or coin) is more reliable.
    

Comparison with previous slide:

|Tosses|Outcome|Reason|
|---|---|---|
|2000|Curves overlap; unclear which coin is fairer|Variance still too high|
|10,000|Curves separate; orange coin clearly less fair|Larger dataset reduces noise|
![[All_slides_nes.pdf#page=384]] Week 11 slide 11 – Airplane  
This slide introduces a real-world example of **redundancy for reliability**.

**Key Points**

- Commercial airplanes have **two pilots** even though one can operate the aircraft alone.
    
- They also have **two engines**, even though one engine is sufficient to keep the plane flying.
    

**Reason**

- These redundancies exist purely for **safety**.
    
- If one pilot becomes incapacitated or one engine fails, the second one ensures the plane can still be controlled and landed safely.
    

**Concept Illustrated**

- Critical systems cannot rely on a single component.
    
- Redundancy increases reliability by providing backup paths when one part fails.
    

Table summary:

|System Element|Normal Requirement|What Is Provided|Why|
|---|---|---|---|
|Pilots|1|2|Human backup for safety|
|Engines|1|2|Safe operation despite engine failure|

![[All_slides_nes.pdf#page=385]]  
Week 11 slide 12 – Airplane (continued)

This slide extends the redundancy explanation from the previous one.

**Main Idea**

- Redundancy is intentionally added even when one component is technically enough.
    
- Two pilots and two engines ensure that if one fails (pilot unconscious, engine malfunction), the airplane can still be operated safely.
    

**Key Insight**

- Redundancy increases **fault tolerance**: the system continues to function despite individual failures.
    
- This is an example of _designing for extremely high reliability_ in safety-critical systems.
    

Table summary:

|Component|Failure Scenario|Redundant Element Ensures|
|---|---|---|
|Pilot|One pilot becomes unable to operate the aircraft|Aircraft still has a capable operator|
|Engine|One engine fails mid-flight|Plane can continue flying and land safely|
![[All_slides_nes.pdf#page=386]] Week 11 slide 13 – Reliability After Countermeasures  
This slide explains that real-world systems are often unreliable, so additional mechanisms are used to **improve effective reliability** as experienced by the user or application.

**Key Idea**

- There is a difference between _raw reliability_ of the environment and the _final reliability_ after applying protocol-level improvements.
    

**Example Scenario**

- A wireless link has **Packet Reception Rate (PRR) = 0.6**, meaning only 60% of transmitted packets arrive successfully.
    
- To improve this, a MAC protocol uses:
    
    - **ACKs** (acknowledgements)
        
    - **Retransmissions** if an ACK is not received.
        

**Goal**

- Compute the _Packet Delivery Rate (PDR)_, which is the improved reliability after retransmissions.
    

**Interpretation**

- Reliability as seen by the application can be much higher than the raw physical layer reliability because countermeasures increase success probability.
    

Table summary:

|Term|Meaning|
|---|---|
|PRR|Chance a packet is received successfully on a single try|
|Countermeasure|ACK + retransmissions|
|PDR|Final probability a packet is received after retries|

![[All_slides_nes.pdf#page=387]] Week 11 slide 14 – Reliability After Countermeasures (calculations)  
This slide shows how retransmissions mathematically improve reliability when each transmission attempt is assumed statistically independent.

**Given**

- Raw link reliability: **PRR = 0.6**
    
- Failure probability per attempt: **1 − PRR = 0.4**
    

**Key Calculations**

- If you allow **N retransmissions**, the only way to fail is if _all attempts fail_.
    
- Thus:  
    **PDR = 1 − (failure probability)ᴺ⁺¹**
    

Results shown:

|Number of Attempts|Failure Probability|Final PDR|
|---|---|---|
|N = 2 attempts total|(0.4)² = 0.16|**0.84**|
|N = 4 attempts total|(0.4)⁴ = 0.0256|**0.9744**|
|N = 8 attempts total|(0.4)⁸ ≈ 0.00066|**0.99934**|

**Interpretation**

- Retransmissions dramatically increase reliability, even when individual attempts succeed only 60% of the time.
    
- However, this assumes _independence_, which often does not hold—interference can cause multiple attempts to fail together.
    

Summary table:

|Raw PRR|Countermeasure|Final PDR|Notes|
|---|---|---|---|
|0.6|Retransmit on failure|Up to 0.99934|Depends on independence assumption|
![[All_slides_nes.pdf#page=388]] Week 11 slide 15 – Comparing Two Reliability Approaches  
This slide compares two strategies for improving reliability on a wireless link with **PRR = 0.6**.

**Approach #1: ACKs + Retransmissions**

- Send a packet.
    
- If no ACK is received, retransmit.
    
- Give up after 8 failed attempts.
    
- Total attempts: up to 8.
    

**Approach #2: Repetition**

- Send the same packet **8 times back-to-back**, no feedback.
    
- Receiver keeps the first correctly received copy.
    

**Key Point**

- Assuming independence, both methods give the **same PDR = 1 − 0.4⁸ = 0.99934**.
    

**Concept Illustrated**

- Raw reliability improvement may be identical, but _how_ you achieve it affects other performance aspects (energy, delay, bandwidth).
    

Table for clarity:

|Approach|Mechanism|Number of Attempts|Resulting PDR|
|---|---|---|---|
|ACK + Retransmissions|Try again only if needed|Up to 8|0.99934|
|Repetition|Always send 8 copies|Exactly 8|0.99934|

Both methods improve reliability, but not in the same way operationally.

![[All_slides_nes.pdf#page=388]] Week 11 slide 15 – Comparing Two Reliability Approaches  
This slide compares two strategies for improving reliability on a wireless link with **PRR = 0.6**.

**Approach #1: ACKs + Retransmissions**

- Send a packet.
    
- If no ACK is received, retransmit.
    
- Give up after 8 failed attempts.
    
- Total attempts: up to 8.
    

**Approach #2: Repetition**

- Send the same packet **8 times back-to-back**, no feedback.
    
- Receiver keeps the first correctly received copy.
    

**Key Point**

- Assuming independence, both methods give the **same PDR = 1 − 0.4⁸ = 0.99934**.
    

**Concept Illustrated**

- Raw reliability improvement may be identical, but _how_ you achieve it affects other performance aspects (energy, delay, bandwidth).
    

Table for clarity:

|Approach|Mechanism|Number of Attempts|Resulting PDR|
|---|---|---|---|
|ACK + Retransmissions|Try again only if needed|Up to 8|0.99934|
|Repetition|Always send 8 copies|Exactly 8|0.99934|

Both methods improve reliability, but not in the same way operationally.

![[All_slides_nes.pdf#page=389]] Week 11 slide 16 – Comparing Two Reliability Approaches (costs)  
This slide continues the comparison of the two reliability approaches by focusing on their **costs** in terms of other performance metrics.

**Recall**

- Both approaches (ACK + retransmissions, and always repeating 8 times) achieve the same PDR (≈ 0.99934) under the independence assumption.
    

**Now Comparing Their Costs**

- **Approach #1 – ACKs + Retransmissions**
    
    - Only retransmits when previous transmission failed.
        
    - On average, uses _fewer transmissions_ than sending 8 copies every time.
        
    - Therefore:
        
        - **Lower energy consumption** (radio used less)
            
        - **Lower bandwidth usage** (fewer packets on the channel)
            
- **Approach #2 – Repetition (always 8 copies)**
    
    - Always transmits 8 times, even if the first attempt was successful.
        
    - This wastes bandwidth and energy but has an advantage:
        
        - **Lower latency**, because there is no waiting for ACKs or protocol overhead between transmissions.
            

**Trade-off Summary**

|Approach|Reliability|Energy/Bandwidth|Latency|
|---|---|---|---|
|ACK + Retransmissions|High (same PDR)|More efficient (less usage)|Slightly higher (due to feedback and protocol steps)|
|Always Repeating 8 Times|High (same PDR)|Less efficient (fixed 8 TX)|Lower (no waiting for ACKs)|

The slide emphasises that improving reliability always comes with trade-offs across **efficiency** and **delay**.

![[All_slides_nes.pdf#page=390]] Week 11 slide 17 – Redundancy  
This slide defines **redundancy** and shows the different forms it can take to improve system reliability.

**Main Idea**  
Redundancy means intentionally duplicating hardware, software, time, or information so the system can tolerate faults that would otherwise cause failure.

**Why Redundancy Helps**

- In fault-free conditions, the duplicate components might seem unnecessary.
    
- But when something goes wrong, redundancy allows the system to continue operating correctly.
    
- This creates a trade-off: **higher reliability** at the cost of **lower efficiency** (more resources used).
    

**Types of Redundancy**

1. **Hardware Redundancy**
    
    - Multiple instances of critical components (e.g., backup sensors, extra processors).
        
2. **Information Redundancy**
    
    - Adding extra bits (like parity codes or error-correcting codes) that do not carry new information but enable error detection or correction.
        
3. **Time Redundancy**
    
    - Performing the same action multiple times (e.g., retransmissions, repeating sensor readings).
        
4. **Software Redundancy – N-Version Programming**
    
    - Independent teams develop multiple implementations of the same function.
        
    - Since they are independent, they are less likely to have the _same_ bug.
        
    - Used in safety-critical domains like trains, aviation, electronic voting.
        

**Summary Table**

|Redundancy Type|Example|Purpose|
|---|---|---|
|Hardware|Multiple sensors/processors|Tolerate component failure|
|Information|Error-correcting codes|Correct corrupted data|
|Time|Repeated transmissions|Overcome transient errors|
|Software|N-version programming|Reduce impact of software bugs|
![[All_slides_nes.pdf#page=391]]  
Week 11 slide 18 – Dissimilar Redundancy

This slide explains why simply duplicating the same component is sometimes **not enough**, and introduces the idea of _dissimilar redundancy_.

**Core Problem**

- If two replicas share the same weaknesses, a single fault source may cause _both_ to fail.
    
- Example: If the original and the backup have the same manufacturing defect, both may break the same way.
    

**Goal of Dissimilar Redundancy**

- Add redundancy **with uncorrelated failure modes**.
    
- Meaning: When one fails, the other is _unlikely_ to fail for the same reason.
    

**Examples Provided**

1. **Different Manufacturers**
    
    - Using two sensors from different companies reduces the chance that both suffer the same defect or failure pattern.
        
2. **Different Types of Sensors for the Same Phenomenon**
    
    - Cameras degrade in low light.
        
    - LIDAR suffers in rain or snow.
        
    - Microphones struggle in wind.
        
    - Combining them ensures at least one works in challenging conditions.
        

**Key Insight**

- Dissimilarity increases robustness because correlated failures are avoided.
    

**Summary Table**

|Standard Redundancy|Dissimilar Redundancy|
|---|---|
|Duplicate identical components|Use different components/technologies|
|Vulnerable to correlated failures|Resistant to correlated failures|
|Cheaper but less robust|More expensive but more reliable|
![[All_slides_nes.pdf#page=392]]  
Week 11 slide 19 – Diversity in (Wireless) Communications

This slide applies the concept of redundancy/dissimilarity specifically to **wired and wireless communication**, which are especially error-prone.

**Main Idea**

- Communication reliability can be greatly improved by introducing **diversity**, which is essentially _uncorrelated redundancy_ applied to communication channels.
    

**Types of Diversity**

1. **Time Diversity**
    
    - Transmit signals at different times.
        
    - Includes retransmissions, interleaving, and error-correction codes.
        
    - Helps when interference or noise is temporary.
        
2. **Frequency Diversity**
    
    - Send the same information on different frequency channels.
        
    - Examples: channel hopping, using multiple narrowband channels.
        
    - Helps when noise affects only certain frequencies.
        
3. **Space Diversity**
    
    - Use physically different paths or antennas.
        
    - Examples: multiple antennas (MIMO), separate cables, alternative links.
        
4. **Path Diversity**
    
    - Route messages through different network paths or nodes.
        
    - If one path fails or is congested, another may still work.
        
5. **Technology Diversity**
    
    - Send a message via different **wireless technologies**.
        
    - Example: transmit via both WiFi and cellular for higher reliability.
        

**Key Insight**

- Each diversity type protects against different kinds of failures (temporal, spectral, spatial, routing, or technological).
    
- Combining them can yield _very high_ communication reliability, especially useful in harsh environments.
    

**Summary Table**

|Diversity Type|What Changes|What It Protects Against|
|---|---|---|
|Time|When you transmit|Temporary interference|
|Frequency|Channel used|Frequency-selective fading/interference|
|Space|Antennas/links|Physical obstructions, multipath loss|
|Path|Route through network|Node/link failures|
|Technology|Communication technology|Technology-specific outages|
![[All_slides_nes.pdf#page=393]]  
Week 11 slide 20 – Delay (Latency)

This slide introduces the different forms of **delay** that occur in embedded and networked systems. Delay represents how long it takes for information to travel from creation to use.

**Types of Delay**

1. **Response Time**
    
    - Time between an input or event and the system’s reaction.
        
    - Relevant in interactive or real-time systems.
        
2. **Processing Delay (Execution Time)**
    
    - Time spent computing inside a processing block (e.g., running a function).
        
    - Depends on CPU speed, software complexity, and scheduling.
        
3. **Communication Delay**
    
    - Time between sending a message and it being received.
        
    - Affected by medium access, transmission, propagation, congestion, and retransmissions.
        
4. **Age of Information**
    
    - Time since the information was originally generated.
        
    - Age = sampling delay + system delay.
        
    - Important in systems where _freshness_ of data matters (monitoring, control).
        

**Key Idea**

- Delay is not just one thing—it is composed of multiple components that accumulate.
    
- Optimizing latency requires identifying which of these components dominates.
    

**Comparison Table**

|Delay Type|What It Measures|Typical Cause|
|---|---|---|
|Response Time|Reaction speed|Combined processing + communication|
|Processing Delay|Execution time|CPU speed, algorithm complexity|
|Communication Delay|Delivery time|Network behavior, retransmissions|
|Age of Information|Data freshness|Sampling interval + system delays|
![[All_slides_nes.pdf#page=394]]  
Week 11 slide 21 – Sources of Delay

This slide breaks down where delay comes from in a **networked embedded system**, dividing the causes into three main areas: _source_, _network_, and _destination_. Each contributes its own delays.

---

### **Source-Side Delays**

These delays occur _before_ the message leaves the device.

- **Data transfer inside the embedded system**  
    Moving data between memory, peripherals, buffers.
    
- **Operating system delays**  
    Scheduling, context switching, interrupt handling.
    
- **Application-related processing**  
    Any computation required before sending.
    
- **Message preparation**  
    Adding headers, encryption, routing info.
    
- **Queuing delays**  
    Waiting in queues if multiple messages compete for transmission.
    

---

### **Network Delays**

These delays happen while the message travels through the communication medium.

- **Transmission delay**  
    Time to push the bits onto the medium (size / data rate).
    
- **Propagation delay**  
    Time for the signal to physically travel through the medium.
    
- **Duty-cycle delays**  
    Waiting for radios to wake up (common in low-power networks).
    
- **Congestion or error recovery**  
    Retransmissions, backoff due to collisions, interference.
    
- **Multi-hop delays**  
    All the above repeated for each hop in the network.
    

---

### **Destination-Side Delays**

These mirror the source-side delays but happen _after_ the message arrives.

- Data transfer, processing, OS scheduling, queuing, etc.
    

---

### **Summary Table**

|Delay Source|Examples|Why It Matters|
|---|---|---|
|Source|Scheduling, preparing packets|Adds variable startup time|
|Network|Transmission, propagation, retransmissions|Often dominates in wireless systems|
|Destination|Processing incoming data|Affects end-to-end latency|

The slide emphasizes that total latency is the _sum_ of many small delays, and optimizing performance requires identifying the dominant contributors.

![[All_slides_nes.pdf#page=395]]  
Week 11 slide 22 – Measuring Processing Delay (Approach #1)

This slide explains how to measure processing time using a **microcontroller’s internal timer**.

---

### **Approach #1: Using Timer Ticks**

1. Read current timer value → **T1**
    
2. Run the processing function
    
3. Read timer again → **T2**
    
4. Compute delay:
    

$$  
D = ((T2 - T1) \bmod MAXTIMERVALUE)\ \times\ TICKTIME  
$$

Where:

- **TICKTIME** = duration of one timer tick.
    

---

### **Important Constraint: Timer Overflow**

The timer must **not overflow more than once** during the measurement window.

**Example:**

- Timer overflows every 10 seconds.
    
- You measure a duration of 2 seconds.
    
- Without constraints, you cannot know if the actual delay was:
    

|Possible Real Delay|
|---|
|2 s|
|12 s|
|22 s|
|32 s|

Multiple wraparounds would produce the same T1/T2 pattern.

---

### **Key Insight**

This method is simple and low overhead, but only reliable when the timer period is sufficiently long relative to the measured task.

---

### **Summary Table**

|Term|Meaning|
|---|---|
|T1, T2|Timer readings before/after processing|
|MAXTIMERVALUE|Timer’s wraparound threshold|
|TICKTIME|Time per tick|
|Constraint|At most one overflow during measurement|
![[All_slides_nes.pdf#page=396]]  
Week 11 slide 23 – Measuring Processing Delay (Approach #2)

This slide presents an external, hardware-based method for measuring execution time using a **GPIO pin** and an **oscilloscope**.

---

### **Approach #2: GPIO Trigger + Oscilloscope**

1. Set a GPIO pin **high** before the processing block:  
    `gpio_set(PIN1);`
    
2. Execute the processing function.
    
3. Set the GPIO pin **low** after the block:  
    `gpio_clear(PIN1);`
    
4. The oscilloscope measures the **time difference** between the rising and falling edges of the signal.
    

The width of the pulse corresponds exactly to the execution time.

---

### **Oscilloscope Tip**

- Oscilloscopes can be configured with a **trigger**, e.g.,  
    _start measuring when the GPIO voltage rises above a threshold_.
    
- This makes capturing timing measurements predictable and repeatable.
    

---

### **Advantages**

|Benefit|Explanation|
|---|---|
|Very accurate|Hardware timestamps at high sampling frequencies|
|Independent|No timer overflow issues|
|Visual|Pulse width directly shows execution time|

---

### **Key Insight**

This method is common in embedded development when precise timing is required or when internal timers are unavailable or unreliable due to system load.

![[All_slides_nes.pdf#page=397]]  
Week 11 slide 24 – Measuring Communication Delay

This slide introduces the _basic idea_ of calculating communication delay when sending data from one device to another.

---

### **Core Concept**

Communication delay is simply:

$$  
D = T_2 - T_1  
$$

Where:

- **T₁** = timestamp when the message is sent (source)
    
- **T₂** = timestamp when the message is received (destination)
    

---

### **Why This Seems Easy**

If both devices share the _same notion of time_, subtracting the timestamps gives the exact delay.

---

### **Implicit Assumption**

- The slide shows that this method **only works if the source and destination clocks are synchronized**.
    
- Without time synchronization, the timestamps come from different clocks, making the subtraction meaningless.
    

---

### **Key Insight**

Measuring communication delay directly is conceptually simple but practically difficult because **accurate time synchronization** between devices is required.

---

### **Summary Table**

|Requirement|Why It Matters|
|---|---|
|Shared time base (sync)|Ensures T₁ and T₂ are comparable|
|Accurate timestamps|Determines precision of delay measurement|
![[All_slides_nes.pdf#page=398]]  
Week 11 slide 25 – Measuring Communication Delay (Round-Trip Method)

This slide provides an alternative method to measure delay **without requiring time synchronization** between source and destination.

---

## **Round-Trip Delay Measurement**

Instead of trying to timestamp on both devices, we:

1. The source sends a **ping** at time $$T_1$$.
    
2. The destination receives it and immediately sends back a **pong**, adding minimal processing delay.
    
3. The source receives the pong at time $$T_4$$.
    
4. At the source, the time between ping and pong is measured.
    

To estimate _one-way_ delay, the formula is:

$$  
D = \frac{(T_4 - T_1) - (T_3 - T_2)}{2}  
$$

Where:

- $$T_2, T_3$$ are timestamps at the destination, but they reflect _processing delay only_ (not clock time).
    
- Only $$T_1$$ and $$T_4$$ need to come from the same clock (the source).
    
- $$T_3 - T_2$$ is made as small as possible.
    

---

### **Why This Works**

- No need for synchronized clocks between devices.
    
- The round-trip time (RTT) is measured using only the source’s clock.
    
- Subtracting the destination’s minimal processing delay and dividing by 2 approximates the one-way delay.
    

---

### **Practical Consideration**

- This method assumes the forward and backward paths have **similar delays**.
    
- In many wireless systems, this is a reasonable approximation.
    

---

### **Summary Table**

|Step|Meaning|
|---|---|
|Ping → Pong|Message exchange loop|
|Measure $$T_4 - T_1$$|Total round-trip time|
|Subtract $$T_3 - T_2$$|Remove destination’s internal delay|
|Divide by 2|Estimate one-way delay|
![[All_slides_nes.pdf#page=399]]  
Week 11 slide 26 – Taking Advantage of Existing Time Synchronisation

This slide shows how communication delay can be measured **without extra cost** when the network already provides time synchronization.

---

## **Example: TSCH (Time-Slotted Channel Hopping)**

TSCH is a synchronous protocol used in low-power wireless networks.

- All nodes share a synchronized counter called the  
    **Absolute Slot Number (ASN)**.
    
- Time is divided into discrete slots, each with a fixed duration.
    

Because all nodes agree on slot timing, you can measure delay using:

$$  
D = (ASN_2 - ASN_1) \times SLOTDURATION  
$$

Where:

- **ASN₁** = slot when the message was sent
    
- **ASN₂** = slot when the message was received
    
- **SLOTDURATION** ≈ 10–15 ms (typical TSCH slot length)
    

---

## **Why This Works**

- ASN acts as a _globally shared clock_.
    
- No additional synchronization packets or protocols are needed.
    
- Delay accuracy is limited only by slot granularity.
    

---

## **Key Insight**

If a network already maintains synchronization (like TSCH), you get delay measurements “for free” by reusing existing timing infrastructure.

---

### **Summary Table**

|Element|Meaning|
|---|---|
|ASN|Global slot counter shared by all nodes|
|Slot duration|Fixed, known length of each timeslot|
|Delay formula|Slot difference × slot duration|
|Cost|Zero overhead if sync already exists|
![[All_slides_nes.pdf#page=400]]  
Week 11 slide 27 – Using External Measurement Devices

This slide explains how to measure timing between events occurring on different embedded devices using **external hardware tools** such as oscilloscopes and logic analyzers.

---

## **Method**

1. Each device toggles a **GPIO pin** when a specific event happens  
    (e.g., “message sent” or “message received”).
    
2. These GPIO signals are fed into an **oscilloscope** or **logic analyzer**.
    
3. By observing the timing difference between signal transitions, you can measure delays such as:
    
    - communication delay
        
    - synchronization offset
        
    - processing delay between nodes
        

---

## **Advantages**

|Advantage|Why It Matters|
|---|---|
|Very accurate|External tools sample at high frequencies (MHz–GHz range)|
|Independent of devices|Does not rely on internal clocks or synchronization|
|Visual signal traces|Easy to inspect, debug, and verify event timing|

---

## **Disadvantage**

- Only practical when devices are **physically close** to each other.  
    External probes cannot be attached to distant or widespread deployments.
    

---

## **Key Insight**

External physical measurement is extremely accurate and avoids clock synchronization issues, but it does **not scale** to large or deployed systems.

![[All_slides_nes.pdf#page=401]]  
Week 11 slide 28 – Delay Variability

This slide explains that delay is **not constant**. It varies due to random factors in processing, network conditions, scheduling, and more. Because of this, we must measure delay **multiple times** and summarize its statistical properties.

---

## **Key Metrics for Delay Variability**

### **1. Average (Mean) Delay**

$$  
D_{AVG} = \frac{1}{N} \sum_{i=1}^{N} D_i  
$$

This represents the _typical_ delay experienced by the system.

---

### **2. Jitter (Standard Deviation)**

Measures how much delay fluctuates around the mean.

$$  
\sigma = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (D_i - D_{AVG})^2}  
$$

Higher jitter = less predictable system behavior.

---

### **3. Maximum Delay**

$$  
D_{MAX} = \max(D_1, D_2, \dots, D_N)  
$$

Important in real-time systems where worst-case delay matters more than average delay.

---

### **4. Box Plot Statistics**

A box plot can summarize delay distribution with:

- Minimum
    
- First quartile
    
- Median
    
- Third quartile
    
- Maximum
    

Useful for visualizing spread and outliers.

---

## **Key Insight**

Knowing only the _average_ delay is not enough.  
Real-time and networking systems require understanding the **distribution** of delays, especially jitter and worst-case delays.

---

### **Summary Table**

|Metric|Meaning|Why It Matters|
|---|---|---|
|$$D_{AVG}$$|Mean delay|Typical performance|
|$$\sigma$$|Jitter|Predictability|
|$$D_{MAX}$$|Worst-case delay|Safety-critical systems|
|Box Plot|Distribution shape|Identifies variability & outliers|
![[All_slides_nes.pdf#page=402]]  
Week 11 slide 29 – Determinism (Predictability)

This slide introduces **deterministic networking**, where delay and reliability are controlled tightly to guarantee predictable system behavior.

---

## **Deterministic Networking (DetNet)**

Developed by the IETF DetNet Working Group.

### **Key Goals**

1. **Extremely low data loss:**
    

- Wired links:  
    $$< 10^{-9}$$ loss rate
    
- Wireless links:  
    $$< 10^{-5}$$ loss rate
    

2. **Extremely low delay variability (jitter)**  
    Predictable communication timing.
    
3. **Bounded latency**  
    A guaranteed **maximum delay** that packets will _never exceed_.
    

---

## **Applications**

These properties are needed in systems where timing and correctness are critical:

- **Audio/Video streaming**  
    Smooth playback, no glitches.
    
- **Industrial automation**  
    Machinery control requires precise coordination.
    
- **Vehicle control**  
    Autonomous and connected vehicles must react within strict timing limits.
    

---

## **Key Insight**

Deterministic networks aim not just for good _average_ performance, but for strict **predictability**, ensuring systems behave reliably under all conditions.

---

### **Summary Table**

| Requirement     | Meaning                       |
| --------------- | ----------------------------- |
| Ultra-low loss  | Ensures reliability           |
| Low jitter      | Ensures timing consistency    |
| Bounded latency | Ensures worst-case guarantees |
![[All_slides_nes.pdf#page=403]]  
Week 11 slide 30 – Energy Efficiency

This slide introduces the topic of **energy efficiency** by asking two foundational questions:

---

## **1. When does energy efficiency matter?**

Energy efficiency becomes important in systems that:

- Run on **limited energy sources** (like batteries).
    
- Use **energy harvesting** (solar, vibration, thermal), where energy supply is unpredictable.
    
- Need to operate for **long periods without maintenance**.
    
- Must be **environmentally friendly** (reduced power usage → lower carbon footprint).
    

---

## **2. What affects energy consumption?**

Energy usage depends on both:

### **Hardware Factors**

- Power states (active, idle, sleep).
    
- Efficiency of components (CPU, radio, sensors).
    
- Faults or inefficiencies like leakage currents.
    

### **Software Factors**

- Duty cycling (how often hardware is awake).
    
- Algorithm complexity (affects CPU time).
    
- Communication patterns (radio is expensive).
    
- Scheduling of tasks to minimize wake-ups.
    

---

## **Key Insight**

Energy consumption is not just a hardware issue.  
Software design plays a major role in determining how long an embedded device can operate on its available energy.

---

### **Summary Table**

|Factor Type|Examples|Impact|
|---|---|---|
|Hardware|Power states, leakage|Sets physical limits on power usage|
|Software|Duty cycling, algorithms|Determines how often power-hungry components run|
![[All_slides_nes.pdf#page=404]]  
Week 11 slide 31 – Energy Efficiency (continued)

This slide gives a more structured view of _when_ energy efficiency matters and _what_ determines energy consumption.

---

## **When Energy Efficiency Matters**

### **1. Energy-Constrained Embedded Systems**

Devices powered by:

- Batteries
    
- Energy harvesters
    

For these systems, energy efficiency is directly tied to **availability**:  
if energy runs out, the system simply cannot operate.

### **2. Green Embedded Systems**

Systems designed to reduce environmental impact by lowering energy consumption.  
This is important for:

- Large-scale IoT deployments
    
- High-volume consumer electronics
    
- Sustainability-driven design requirements
    

---

## **What Affects Energy Consumption?**

### **Hardware Effects**

- Active / idle / sleep power levels
    
- Hardware faults
    
- Efficiency of radios, sensors, memory, CPU
    
- Internal leakage currents
    

### **Software Effects**

- **Duty cycling** (how long components stay active) is one of the strongest factors.
    
- Algorithm complexity → CPU time → energy.
    
- Communication frequency and packet size → radio energy.
    
- Scheduling choices → wake-up frequency.
    

---

## **Key Insight**

Energy consumption results from a combination of hardware limitations and software decisions.  
Software often has _more influence_ because it controls how long hardware stays in high-power states.

---

### **Summary Table**

|Category|Examples|Impact|
|---|---|---|
|Energy-Constrained Systems|Battery-powered, energy harvesting|Energy = lifetime|
|Green Systems|Eco-focused design|Lower carbon footprint|
|Hardware Factors|Power states, leakage, device efficiency|Baseline power usage|
|Software Factors|Duty cycling, algorithms|Controls active-time energy|
![[All_slides_nes.pdf#page=405]]  
Week 11 slide 32 – Energy Consumption Basics

This slide introduces the fundamental relationship between **power**, **energy**, and **time**.

---

## **Key Formula**

Energy is the time-integral of power:

$$  
E = P \times T  
$$

Where:

- **E** = energy (Joules)
    
- **P** = power (Watts)
    
- **T** = time (seconds)
    

---

## **Meaning**

- Power tells you **how fast** energy is being consumed.
    
- Energy tells you **how much total** was consumed over a period.
    

Example interpretations:

- A device using 1 W for 10 seconds consumes:  
    $$E = 1 \times 10 = 10\ \text{Joules}$$
    
- A device using 100 mW for 1 hour consumes:  
    $$E = 0.1\ \text{W} \times 3600\ \text{s} = 360\ \text{Joules}$$
    

---

## **Key Insight**

Understanding energy consumption always starts with this relationship.  
Even complex measurements (like varying power levels over time) ultimately rely on integrating this same equation.

---

### **Summary Table**

|Concept|Meaning|
|---|---|
|Power (P)|Rate of energy consumption|
|Time (T)|Duration of operation|
|Energy (E)|Total consumed over time → $$E = P \cdot T$$|

![[All_slides_nes.pdf#page=406]]  
Week 11 slide 33 – Variable Consumption

This slide explains that energy consumption is not always constant—systems often switch between different power states, and energy must be computed by integrating power over time.

---

## **Key Idea: Power Changes With System State**

Example:  
A LED that blinks every second.

- When the LED is **on**, power is higher.
    
- When the LED is **off**, power is near zero.
    
- Total energy use depends on how long the system stays in each state.
    

---

## **Energy as a Time Integral**

Even when power varies, energy is still computed as:

$$  
E = \int P(t), dt  
$$

This means:

- You accumulate power consumption over time.
    
- The more time spent in high-power states, the greater the total energy.
    

---

## **Why This Matters**

Many embedded systems:

- Sleep most of the time
    
- Wake briefly to perform short actions
    
- Use radios that have huge differences between sleep and active power
    

Therefore, understanding **power vs. time** is essential for predicting battery life.

---

### **Summary Table**

|Concept|Meaning|
|---|---|
|Variable power|Power changes based on state (LED on/off, radio on/off)|
|Energy integral|$$E = \int P(t), dt$$|
|Insight|Time spent in high-power states dominates total energy|

![[All_slides_nes.pdf#page=407]]  
Week 11 slide 34 – Quiz (Energy Efficiency Comparison)

This slide presents a question comparing the energy efficiency of **two embedded systems** that perform the same functionality but have very different power characteristics.

---

## **Given**

### **System A**

- Idle power: **1 µW**
    
- Active power: **100 mW**
    

### **System B**

- Idle power: **100 µW**
    
- Active power: **10 mW**
    

---

## **Question**

**Which system is more energy efficient?**

At this point, the slide does **not** give the answer—it sets up the idea that efficiency depends on how long the system spends in each state.

---

## **Key Insight**

You _cannot_ say which system is more efficient without knowing the **duty cycle** (how much time is spent active vs idle).

- If the system is active **very rarely**, idle power dominates → System A (1 µW idle) looks better.
    
- If the system is active **very often**, active power dominates → System B (10 mW active) looks better.
    

This prepares for the next slide.

---

### **Summary Table**

|System|Idle Power|Active Power|Better When…|
|---|---|---|---|
|A|1 µW|100 mW|Low duty cycle (mostly idle)|
|B|100 µW|10 mW|High duty cycle (often active)|

![[All_slides_nes.pdf#page=408]]  
Week 11 slide 35 – Quiz (Answer)

This slide provides the conclusion to the energy efficiency question from the previous slide.

---

## **Answer: It Depends on the Duty Cycle**

Neither system (A or B) is universally more energy efficient.

### **Why?**

Energy consumption over time depends on how long the system stays in active vs. idle mode.

- If the system is **active rarely** → idle power dominates
    
    - System **A** is better because it has extremely low idle power (1 µW).
        
- If the system is **active frequently** → active power dominates
    
    - System **B** is better because its active power (10 mW) is much lower than A’s (100 mW).
        

---

## **Key Insight**

Energy efficiency is not determined by power levels alone but by:

$$  
\text{How long the device spends in each power state}  
$$

This leads directly into the next topic: long-term average power.

---

### **Summary Table**

|Condition|More Efficient System|Reason|
|---|---|---|
|Low duty cycle (mostly idle)|**A**|Lower idle power|
|High duty cycle (mostly active)|**B**|Lower active power|
![[All_slides_nes.pdf#page=409]]  
Week 11 slide 36 – Long-Term Average Power Consumption

This slide introduces a formula for computing **average power** over long periods when a system alternates between active and idle states.

---

## **Duty Cycle (DC)**

Duty cycle represents the **fraction of time** the system spends in active mode.

Example:  
A 1% duty cycle means:

- 1% of the time → **active**
    
- 99% of the time → **idle**
    

---

## **Average Power Formula**

If:

- $$P_{ON}$$ = power in active mode
    
- $$P_{IDLE}$$ = power in idle mode
    
- $$DC$$ = duty cycle (between 0 and 1)
    

Then average power is:

$$  
P_{AVG} = P_{ON} \cdot DC + P_{IDLE} \cdot (1 - DC)  
$$

---

## **Interpretation**

- When **DC is high**, active power dominates → high $$P_{AVG}$$
    
- When **DC is low**, idle power dominates → $$P_{AVG}$$ depends mostly on $$P_{IDLE}$$
    

This explains why a device that rarely wakes up benefits more from low idle power than low active power.

---

### **Graph (from slide)**

The plot visualizes how $$P_{AVG}$$ transitions from being dominated by $$P_{IDLE}$$ at low duty cycles to being dominated by $$P_{ON}$$ at high duty cycles.

---

## **Summary Table**

|Duty Cycle|Dominant Power Term|Meaning|
|---|---|---|
|Low DC|$$P_{IDLE}$$|Device mostly sleeps|
|High DC|$$P_{ON}$$|Device often active|
![[All_slides_nes.pdf#page=410]]  
Week 11 slide 37 – How to Measure Energy Consumption?

This slide explains how to measure the **actual energy usage** of an embedded system by measuring its **current draw over time**.

---

## **Key Electrical Relationships**

1. Power:  
    $$  
    P = V \times I  
    $$
    
2. Energy over time:  
    $$  
    E = V \times I \times T  
    $$
    

Assumption:

- The supply voltage **V** is constant (e.g., battery voltage).
    

---

## **How to Measure Current**

To find energy, you need the current as a function of time:

$$  
I(t)  
$$

To get this, you measure the voltage drop across a **shunt resistor** using an oscilloscope.

---

## **Measurement Setup**

1. Place a small resistor **in series** with the device.
    
2. Measure the voltage across it:
    

$$  
V_R(t)  
$$

3. Compute current as:
    

$$  
I(t) = \frac{V_R(t)}{R}  
$$

4. Integrate over time to get energy:
    

$$  
E = V_S \int I(t), dt  
$$

where $$V_S$$ is the supply voltage.

---

## **Key Insight**

To measure energy accurately, you need:

- A resistor
    
- An oscilloscope
    
- Knowledge of the resistor value
    
- The assumption (or measurement) of supply voltage
    

---

### **Summary Table**

|Quantity|Symbol|How It’s Obtained|
|---|---|---|
|Supply voltage|$$V_S$$|Battery or power supply|
|Voltage over resistor|$$V_R(t)$$|Oscilloscope|
|Current|$$I(t) = V_R(t)/R$$|Computed|
|Energy|$$E = V_S \int I(t), dt$$|Integration over time|

![[All_slides_nes.pdf#page=411]]  
Week 11 slide 38 – High-Side Shunt Resistor

This slide explains the **high-side shunt** method for measuring current by placing a resistor in series with the supply line.

---

## **Core Principle**

A resistor is placed in series with the power supply.  
You measure the voltage drop across it:

$$  
I(t) = \frac{V_R(t)}{R}  
$$

Where:

- $$V_R(t)$$ is the measured voltage across the resistor
    
- $$R$$ is the resistor value
    

---

## **Question: How large should R be?**

The slide sets up this question but does not yet answer it (the next slide does).  
Choosing R is a trade-off:

- If **R is too large**, the resistor drops too much voltage → the device may not get enough supply voltage.
    
- If **R is too small**, the voltage drop is tiny → difficult to measure accurately, especially for small currents.
    

---

## **Measurement Context**

This method is “high-side” because the resistor sits on the **positive supply rail**, meaning:

- The measurement does _not_ disturb ground reference.
    
- But it requires differential measurement if the tool shares ground with the device.
    

---

## **Key Insight**

The accuracy and safety of current measurement depend heavily on choosing an appropriate resistor value.

---

### **Summary Table**

|Quantity|Meaning|
|---|---|
|$$V_R(t)$$|Voltage across shunt resistor|
|$$R$$|Shunt resistor value|
|$$I(t)$$|Current computed as $$V_R(t)/R$$|
|Design trade-off|Large R → big voltage drop; small R → hard to measure|

![[All_slides_nes.pdf#page=412]]  
Week 11 slide 39 – High-Side Shunt Resistor (Choosing R)

This slide continues the previous one and explains **how to choose the correct shunt resistor value** using a concrete example.

---

## **Given Example**

- Supply voltage:  
    $$V_S = 3.3\ \text{V}$$
    
- The IC requires:  
    $$V_{IN} = 3\text{–}5\ \text{V}$$  
    (so the voltage drop across the resistor must stay small)
    
- Current draw ranges:
    
    - Idle: $$10\ \mu\text{A}$$
        
    - Active: $$10\ \text{mA}$$
        

---

## **Case 1: Resistor Too Large (R = 100 Ω)**

Maximum voltage drop:

$$  
V_R = 10\ \text{mA} \times 100\ \Omega = 1\ \text{V}  
$$

This reduces the input voltage:

$$  
V_{IN} = 3.3\ \text{V} - 1\ \text{V} = 2.3\ \text{V}  
$$

**Problem:**  
2.3 V is _below_ the required 3–5 V → the circuit may fail.

---

## **Case 2: Resistor Too Small (R = 1 Ω)**

- Max voltage drop at 10 mA:
    

$$  
V_R = 10\ \text{mA} \times 1\ \Omega = 10\ \text{mV}  
$$

- This yields:
    

$$  
V_{IN} = 3.29\ \text{V}  
$$

→ **Safe**, the device still gets enough voltage.

- Minimum voltage drop at 10 µA:
    

$$  
V_R = 10\ \mu\text{A} \times 1\ \Omega = 10\ \mu\text{V}  
$$

**Problem:**  
Very small voltage → hard to measure accurately.

---

## **Key Insight**

Choosing R is a balancing act:

- **Large R** → large, easy-to-measure voltage drop, but risks disrupting the circuit.
    
- **Small R** → safe for the circuit, but the voltage drop may be below measurement resolution.
    

---

### **Summary Table**

|R Value|Pros|Cons|
|---|---|---|
|Large R|Easy to measure voltage drop|Voltage drop may break the system|
|Small R|Safe for circuit operation|Very small voltages → hard to measure|
![[All_slides_nes.pdf#page=413]]  
Week 11 slide 40 – Resistor Tolerance

This slide explains how **resistor tolerance** affects current measurement accuracy when using a shunt resistor.

---

## **Formula Reminder**

Current is computed as:

$$  
I(t) = \frac{V_R(t)}{R}  
$$

But this only works correctly if you know **R** precisely.

---

## **What Is Resistor Tolerance?**

Tolerance specifies how much the **actual** resistance may deviate from the **nominal** value.

Example:  
A 10 Ω resistor with:

- **10% tolerance** → actual value between 9 Ω and 11 Ω
    
- **1% tolerance** → actual value between 9.9 Ω and 10.1 Ω
    

---

## **Impact on Current Measurement**

### **Example Using 10 mV Voltage Drop (V_R = 10 mV)**

### **Case 1: 10 Ω Resistor, 10% Tolerance**

Actual R is between 9 and 11 Ω.

Current estimates:

- Minimum current:
    

$$  
I_{\min} = \frac{10\ \text{mV}}{11\ \Omega} \approx 0.91\ \text{mA}  
$$

- Maximum current:
    

$$  
I_{\max} = \frac{10\ \text{mV}}{9\ \Omega} \approx 1.11\ \text{mA}  
$$

→ **Large uncertainty** (± ~10%).

---

### **Case 2: 10 Ω Resistor, 1% Tolerance**

Actual R between 9.9 and 10.1 Ω.

- Minimum current:
    

$$  
\frac{10\ \text{mV}}{10.1\ \Omega} \approx 0.99\ \text{mA}  
$$

- Maximum current:
    

$$  
\frac{10\ \text{mV}}{9.9\ \Omega} \approx 1.01\ \text{mA}  
$$

→ **Much smaller error** (± ~1%).

---

## **Key Insight**

To obtain accurate current measurements:

- Use **low-tolerance resistors**  
    **or**
    
- Measure the actual resistance with a precise meter
    

Otherwise, current calculation error can be large.

---

### **Summary Table**

|Tolerance|Possible R Range|Measurement Accuracy|
|---|---|---|
|10%|9–11 Ω|Large current error|
|1%|9.9–10.1 Ω|Small current error|
![[All_slides_nes.pdf#page=414]]  
Week 11 slide 41 – Calculating the Energy

This slide explains how an oscilloscope converts continuous current measurements into a **digital approximation** of the energy consumed.

---

## **Sampling Process**

An oscilloscope samples the signal at a fixed frequency:

$$  
f = \frac{1}{\tau}  
$$

where:

- $$f$$ = sampling frequency
    
- $$\tau$$ = time between samples
    

---

## **Energy Approximation**

Energy is computed by summing the energy of many small rectangles:

$$  
E \approx V_S \sum_{i=0}^{n} \frac{V_{R,i}}{R} \cdot \tau  
$$

Where:

- $$V_S$$ = supply voltage
    
- $$V_{R,i}$$ = measured shunt resistor voltage at sample _i_
    
- $$R$$ = shunt resistor value
    
- $$\tau$$ = sampling period
    
- $$\frac{V_{R,i}}{R}$$ = current at sample _i_
    

This is a discrete approximation of the integral:

$$  
E = V_S \int I(t), dt  
$$

---

## **Interpretation**

The oscilloscope:

1. Measures voltage across the resistor at many time points.
    
2. Converts each measurement into a current.
    
3. Multiplies by the sampling interval.
    
4. Sums all contributions to obtain total energy.
    

More samples ⇒ more accurate energy estimation.

---

### **Summary Table**

|Symbol|Meaning|
|---|---|
|$$f$$|Sampling frequency|
|$$\tau$$|Sampling interval|
|$$V_{R,i}$$|Voltage sample across resistor|
|$$\frac{V_{R,i}}{R}$$|Current sample|
|$$E$$|Sum of all $$I \cdot V_S \cdot \tau$$|
![[All_slides_nes.pdf#page=415]]  
Week 11 slide 42 – Low-Side Shunt Resistor

This slide compares **high-side** and **low-side** current measurement and explains why low-side measurement is often simpler.

---

## **High-Side Measurement (recap)**

- Resistor placed on the **positive (Vcc) side** of the circuit.
    
- Requires **differential measurement**, because the oscilloscope must measure voltage between two non-ground points.
    
- Some oscilloscopes share ground with the DUT, which can cause short circuits.
    

---

## **Low-Side Shunt Measurement**

### **Setup**

- The shunt resistor is placed between the **device ground** and the **actual ground**.
    
- Voltage is measured _relative to ground_, so a **single-ended probe** can be used.
    

### **Advantages**

- Much simpler measurement: only one oscilloscope channel needed.
    
- No risk of shorting the device’s supply through the measurement tool.
    
- Works with inexpensive equipment.
    

### **Caveats**

- Can introduce a small offset in device ground (ground lift).
    
- Usually acceptable but must be considered in sensitive analog circuits.
    

---

## **Key Insight**

Low-side shunt measurement is **easier and safer**, especially when using standard oscilloscopes that reference ground internally.

---

### **Summary Table**

|Method|Resistor Placement|Pros|Cons|
|---|---|---|---|
|High-side|On Vcc line|Does not disturb ground reference|Requires differential probes|
|Low-side|On ground line|Simple, safe, single-ended measurement|Slight ground lift| 
![[All_slides_nes.pdf#page=416]]  
Week 11 slide 43 – Measuring the Supply Voltage

This slide explains why assuming a **constant supply voltage** can cause errors in energy measurements, and how to correct for it.

---

## **Why Supply Voltage Is _Not_ Actually Constant**

Even though many analyses assume:

$$  
V_S = \text{constant}  
$$

in reality the voltage varies because of:

1. **Battery internal resistance**
    
    - As current increases, voltage drops temporarily.
        
2. **Power supply noise**
    
    - AC→DC conversion introduces ripple.
        
3. **Voltage drop across the shunt resistor**
    
    - Measuring current changes the actual supply seen by the device.
        

All these variations affect **accuracy** if you assume a fixed voltage.

---

## **How to Measure Accurately**

To compute energy more precisely, measure:

- The instantaneous supply voltage: $$V_{IN,i}$$
    
- The shunt voltage drop: $$V_{R,i}$$
    
- The resistor value: $$R$$
    

Then energy becomes:

$$  
E = \sum_{i=0}^{n} \frac{V_{IN,i}, V_{R,i}}{R} \cdot \tau  
$$

Where:

- $$\tau$$ is the sampling interval
    
- $$\frac{V_{R,i}}{R}$$ is the current at sample _i_
    

This captures variations in both voltage and current.

---

## **Why Synchronization Matters**

- Measurements of $$V_{IN}$$ and $$V_R$$ must be **time-aligned**.
    
- Otherwise, current samples might be multiplied by the _wrong_ voltage samples, producing incorrect energy estimates.
    

---

### **Summary Table**

|Issue|Effect|
|---|---|
|Battery resistance|Voltage sag under load|
|Noise|Rapid fluctuations in supply|
|Shunt voltage drop|Reduces actual device voltage|
|Fix|Measure both $$V_{IN}$$ and $$V_R$$ synchronously|
![[All_slides_nes.pdf#page=417]]  
Week 11 slide 44 – Power Measurement Instruments

This slide describes professional instruments used for **precise power and energy measurements** in embedded systems.

---

## **Why Use Specialized Instruments?**

Compared to shunt + oscilloscope setups, these instruments offer:

- **Higher accuracy**
    
- **Greater dynamic range** (can measure tiny µA currents and large mA spikes)
    
- **Cleaner signals**
    
- **Automated data collection**
    

---

## **Types of Power Measurement Instruments**

### **1. Power Analyzers**

- Measure **voltage and current simultaneously**.
    
- Can automatically **switch measurement ranges** to handle both low and high currents.
    
- Ideal for detailed consumption profiling.
    

---

### **2. Source and Measurement Units (SMUs)**

- Provide power _and_ measure it at the same time.
    
- Very clean, low-noise power supply.
    
- Excellent for characterizing devices under controlled power conditions.
    

---

### **3. Current Probes**

- Non-invasive: they **clamp around a wire** rather than inserting a resistor.
    
- Measure the **magnetic field** generated by current.
    
- Allow measurement without modifying the circuit.
    

---

## **Key Insight**

These instruments are powerful but expensive.  
They are ideal for lab environments where precision matters but often impractical for large-scale or field deployments.

---

### **Summary Table**

|Instrument|Strengths|Typical Use|
|---|---|---|
|Power Analyzer|High precision, wide range, simultaneous V/I|Lab profiling|
|SMU|Clean power + measurement|Device characterization|
|Current Probe|Non-invasive, easy to attach|Quick diagnostics|

![[All_slides_nes.pdf#page=418]]  
Week 11 slide 45 – Power Measurements in the Wild

This slide highlights the **practical challenges** of performing power measurements outside of a controlled laboratory environment.

---

## **Why Lab Instruments Don’t Scale**

Professional measurement tools (power analyzers, SMUs, scopes):

- Are **too expensive** to deploy on many devices
    
- Are **too bulky** to attach to embedded systems in real-world scenarios
    
- Are **too invasive**, requiring wires or probes inserted into the power path
    
- Consume significant power and storage themselves, making them unsuitable for long-term remote operation
    

---

## **Real-World Measurement Challenges**

The slide poses several key questions:

1. **How can we measure a distributed system of 100 devices?**
    
    - Lab tools cannot be attached to all devices simultaneously.
        
2. **How can we measure devices deployed in public spaces?**
    
    - Physical access is limited, and bulky tools cannot be installed outdoors.
        
3. **How can we measure moving systems (e.g., smart vehicles)?**
    
    - Measurement tools cannot follow mobile devices seamlessly.
        
4. **How can we measure devices over long durations (e.g., 1 year)?**
    
    - Lab tools require stable power, maintenance, and generate huge data volumes.
        

---

## **Key Insight**

There is a major gap between **high-accuracy lab measurements** and the need for **scalable, long-term, low-overhead measurements in the field**.

This motivates the need for **software-based energy estimation**, which is introduced in the following slides.

---

### **Summary Table**

|Challenge|Why It’s a Problem|
|---|---|
|Cost|Instruments too expensive for large deployments|
|Size|Too bulky for embedded devices|
|Invasiveness|Require wiring changes, not possible in the field|
|Mobility|Cannot follow moving systems|
|Long-term measurement|Instruments not designed for months/years of operation|
![[All_slides_nes.pdf#page=419]]  
Week 11 slide 46 – Software-Based Estimation

This slide introduces a **scalable but less accurate** method for estimating energy consumption using software instrumentation instead of external measurement tools.

---

## **Key Idea**

Instead of measuring current with hardware, the MCU **counts how many timer ticks it spends in each power state**.

This works because:

- Each state has a **known, constant current draw**, either from measurements or the datasheet.
    
- Energy can be estimated by multiplying **time spent in each state** by **current of that state**.
    

---

## **Assumptions**

1. **Supply voltage is constant**  
    Used for simplifying energy calculation.
    
2. **Each MCU/peripheral state has a constant current**  
    Example states:
    
    - MCU Active
        
    - MCU Idle
        
    - MCU Standby
        
    - Radio TX
        
    - Radio RX
        

---

## **Procedure**

1. MCU counts clock ticks in each state during a reporting period.
    
2. It logs the tick counts periodically.
    
3. Energy is computed later using known current values.
    

---

## **Example Table from Slide**

Period log (simplified):

|Period|MCU Active|MCU Idle|MCU Standby|Radio TX|Radio RX|
|---|---|---|---|---|---|
|1|1966080|32768|294912|1638400|540|
|2|1966080|31232|296405|1638443|654|
|3|1966080|34440|293106|1638534|434|

Each row corresponds to one measurement interval.

---

## **Key Insight**

This approach scales to:

- Large deployments
    
- Remote or inaccessible devices
    
- Long-term energy monitoring
    

It trades **accuracy** for **practicality and scalability**.

---

### **Summary Table**

|Property|Hardware Measurement|Software Estimation|
|---|---|---|
|Accuracy|High|Medium/Low|
|Scalability|Low|High|
|Invasiveness|High|None|
|Long-term use|Difficult|Easy|

![[All_slides_nes.pdf#page=420]]  
Week 11 slide 47 – Software-Based Estimation (Energy Formula)

This slide explains **how to convert tick counts into actual energy estimates** using known current values for each state.

---

## **Energy Calculation per Reporting Period**

Each state _i_ has:

- Time spent in the state (in ticks): $$t_i$$
    
- Current drawn in the state: $$I_i$$
    
- Supply voltage: $$V_S$$
    

To convert ticks into seconds:

$$  
\text{Time in seconds} = \frac{t_i}{t_s}  
$$

where:

- $$t_s$$ = number of ticks per second (timer frequency)
    

---

## **Energy Formula**

Total energy in period _k_ is:

$$  
E_k = \sum_{i=0}^{n} \frac{t_i}{t_s} , I_i , V_S  
$$

This computes the energy consumed across all states.

---

## **Average Power**

Power over the reporting period is simply:

$$  
P_{AVG} = \frac{E_k}{\text{Period Duration}}  
$$

Since the period duration is known, average power can be derived directly from the energy estimate.

---

## **Key Insight**

The MCU does not measure current dynamically—it only reports _how long it stayed in each state_.

Energy is obtained by:

1. Converting ticks → time
    
2. Multiplying time × known current × supply voltage
    
3. Summing across all states
    

This provides a **scalable** and **lightweight** method for estimating energy in large deployments.

---

### **Summary Table**

|Variable|Meaning|
|---|---|
|$$t_i$$|Tick count spent in state _i_|
|$$t_s$$|Ticks per second|
|$$I_i$$|Current draw of state _i_|
|$$V_S$$|Supply voltage|
|$$E_k$$|Estimated energy in reporting period|
|$$P_{AVG}$$|Average power during the period|


---
---
---
Here are 5 multiple-choice questions based on the full slide set, **without answers**:

---

### **MCQ 1 — Reliability Measurement**

When measuring reliability of a wireless link with PRR = 0.6 and allowing N retransmissions, the Packet Delivery Rate (PDR) depends on:  
A. The number of successful transmissions only  
B. The probability that at least one of the attempts succeeds  
C. The average number of packets sent per second  
D. The size of each transmitted packet

---

### **MCQ 2 — Delay Components**

Which of the following is **not** a source of delay in network communication?  
A. Propagation delay  
B. Transmission delay  
C. Temperature drift  
D. Duty-cycle related waiting time

---

### **MCQ 3 — Energy Measurement**

In a shunt-resistor measurement setup, choosing a resistor value that is too large primarily risks:  
A. Producing too much noise for the oscilloscope  
B. Lowering the supply voltage below what the device requires  
C. Increasing the sampling frequency  
D. Making the resistor heat up and break immediately

---

### **MCQ 4 — Software-Based Energy Estimation**

Software-based energy estimation relies on the assumption that:  
A. The supply voltage and current vary unpredictably  
B. All MCU states draw constant, known currents  
C. RTC timers are always perfectly synchronized  
D. The radio is always active

---

### **MCQ 5 — Redundancy**

Dissimilar redundancy is primarily used to:  
A. Reduce hardware cost  
B. Protect against correlated failures  
C. Improve processing speed  
D. Increase packet size for more accuracy

---

Let me know when you're ready for the answers.

Here are the answers:

---

### **MCQ 1 — Reliability Measurement**

**Answer: B** — The probability that at least one of the attempts succeeds.

---

### **MCQ 2 — Delay Components**

**Answer: C** — Temperature drift.

---

### **MCQ 3 — Energy Measurement**

**Answer: B** — Lowering the supply voltage below what the device requires.

---

### **MCQ 4 — Software-Based Energy Estimation**

**Answer: B** — All MCU states draw constant, known currents.

---

### **MCQ 5 — Redundancy**

**Answer: B** — Protect against correlated failures.

---

If you want, I can generate more questions or a mixed quiz.



WEEK 12 NOTES


![[All_slides_nes.pdf#page=425]]
**Week 12 Slide 2 – Requirements of (Industrial) Networked Embedded Systems**

*   **Key Performance Metrics for NES:** These are the measurable goals or "non-functional requirements" of a network. In industrial settings, they define what makes a network suitable for critical tasks.
*   **List of Requirements:**
    *   **Scalability:** The ability of the network to support a growing number of embedded devices (nodes).
    *   **Throughput:** The network's data-carrying capacity, measured in bytes received per second.
    *   **Reliability (Packet Delivery Ratio - PDR):** The success rate of transmissions, calculated as (Packets Received / Packets Sent). High PDR (e.g., 99.9%+) is essential for control systems.
    *   **Latency/Delay:** The total time from when a packet is sent until it is received. Low latency is critical for real-time control.
    *   **Jitter:** The variation or inconsistency in latency (e.g., one packet takes 10ms, the next takes 50ms). Predictable (low) jitter is needed for determinism.
    *   **Time-sensitivity / Determinism:** The property of having **predictable and bounded** latency and jitter. This allows systems to be designed with guaranteed timing behavior.
    *   **Energy Efficiency:** The power consumed by network devices. Important for battery-powered nodes; all the above features require energy to achieve.
*   **Critical Insight – Trade-offs:** It is **impossible** to optimize all these requirements simultaneously in a single network design. You must prioritize based on the application. For industrial networks, **reliability and determinism** are typically prioritized over raw throughput and sometimes energy efficiency.

![[All_slides_nes.pdf#page=426]]
**Week 12 Slide 3 – Industrial Embedded Networks**

*   **Industrial Network Priority:** They carry vital, often safety-critical data (e.g., factory robot control, sensor readings for automated processes). Therefore, they tend to **prioritize reliability and determinism** over high throughput and maximum energy efficiency.
*   **Data Coexistence:** These networks can also carry non-critical **best-effort data** (e.g., entertainment in a vehicle, diagnostic logs) alongside time-critical traffic, but the critical data gets priority.
*   **Common Technical Features** (used to achieve reliability/determinism):
    *   **Schedule-based communication:** Uses a pre-defined timetable (schedule) for transmissions to **avoid collisions**, unlike contention-based protocols like Wi-Fi (CSMA/CA).
    *   **Time synchronisation:** All devices in the network share a highly accurate common notion of time.
    *   **Traffic prioritisation:** More important data packets are scheduled for transmission before less important ones.
    *   **Redundancy:** Having backup paths or components to maintain operation if a primary element fails.
    *   **Interference mitigation:** Techniques like channel hopping to avoid persistent wireless interference.
*   **Key Examples:**
    *   **TSCH (Time-Slotted Channel Hopping):** A **wireless** standard (IEEE 802.15.4e).
    *   **TSN (Time-Sensitive Networking):** A set of **wired** Ethernet standards (IEEE 802.1).

| **Aspect** | **Industrial Networks (e.g., TSCH)** | **General-Purpose Networks (e.g., Wi-Fi)** |
| :--- | :--- | :--- |
| **Main Goal** | Predictability, Reliability | High Speed, Convenience |
| **Access Method** | Scheduled (TDMA) | Contention-based (CSMA/CA) |
| **Critical Metrics** | Latency, Jitter, PDR | Throughput |
| **Typical Use Case** | Factory automation, process control | Internet access, file sharing |
![[All_slides_nes.pdf#page=427]]
**Week 12 Slide 4 – Industrial Wireless Networks (The 6TiSCH protocol stack)**

*   **6TiSCH:** A complete **protocol stack** that combines existing IETF (Internet) and IEEE (networking) standards to create reliable, deterministic **industrial wireless networks**.
*   **Goal:** To provide IPv6 connectivity over low-power wireless links with **high reliability and bounded delay/jitter**.
*   **Stack Components (Bottom to Top in the diagram):**
    *   **IEEE 802.15.4:** The **Physical Layer (PHY)**, defining the radio hardware (frequencies, modulation).
    *   **IEEE 802.15.4e TSCH:** The **Medium Access Control (MAC)** layer protocol. This is the core innovation, providing time-slotted, channel-hopping communication.
    *   **6top (6TiSCH Operation Sublayer):** A sublayer that sits between TSCH and the network layer to manage the TSCH schedule (adding/deleting communication slots).
    *   **6LoWPAN (HC):** An adaptation layer that compresses IPv6 headers to fit efficiently into the small 127-byte frames of IEEE 802.15.4.
    *   **IPv6:** The network layer protocol, enabling each device to have a unique internet address.
    *   **RPL (Routing Protocol for Low-Power and Lossy Networks):** The routing protocol that builds and maintains paths in the mesh network.
    *   **Transport/Application Layers (UDP, CoAP, etc.):** Standard Internet protocols used for data transport and application communication.
*   **Key Takeaway:** 6TiSCH is not a single new protocol, but a carefully selected **integration** of standards, with **TSCH at its heart**, to meet industrial requirements.

![[All_slides_nes.pdf#page=428]]
**Week 12 Slide 5 – IEEE 802.15.4 PHY**

*   **What it is:** The **Physical Layer (PHY)** standard for **Low-Rate Wireless Personal Area Networks (LR-WPANs)**. It defines the "radio hardware" characteristics like frequency, data rate, and modulation.
*   **Key Specifications:**
    *   **Frequency Bands:** Operates in **2.4 GHz** (global) and **sub-GHz** (regional, e.g., 868 MHz in Europe, 915 MHz in US) ISM bands.
    *   **Data Rate:** **250 kbps** in the 2.4 GHz band (lower rates in sub-GHz).
    *   **Packet Size:** Maximum **127 bytes** per frame.
    *   **Channels:** **16 channels** in the 2.4 GHz band (numbered 11-26), each 5 MHz apart, coexisting with Wi-Fi channels 1, 6, and 11.
    *   **Security:** Supports built-in **encryption and authentication** (AES-128).
*   **Common Applications:**
    *   **Smart Home/City:** Used by protocols like **Zigbee** and **Thread**.
    *   **Industrial Wireless:** Serves as the foundational radio layer for the **6TiSCH** stack.
*   **Visual (Frequency Chart):** The chart shows how the 16 IEEE 802.15.4 channels (vertical bars) are spaced within the 2.4 GHz band, sitting between and overlapping with common Wi-Fi channels. This highlights the potential for **interference**, a key challenge that TSCH's channel hopping aims to solve.

![[All_slides_nes.pdf#page=429]]
**Week 12 Slide 6 – IEEE 802.15.4 MAC**

*   **MAC Layer Role:** Manages **how devices access the shared wireless medium**. It sits above the PHY layer.
*   **Traditional MAC (802.15.4-2011):**
    *   **Device Types (Asymmetric):**
        *   **FFD (Full-Function Device):** Can act as a network **coordinator** or **router**. Has more resources.
        *   **RFD (Reduced-Function Device):** A simple, low-power **end device** (e.g., a sensor). Can only talk to an FFD.
    *   **Access Methods:**
        *   **Contention-based (CSMA/CA):** Devices "listen before talk," competing for the channel. Can lead to **unpredictable delays and collisions**.
        *   **Contention-free (GTS - Guaranteed Time Slots):** A coordinator can allocate dedicated time slots to specific devices. More deterministic but limited in scale.
*   **Enhanced MAC for Industry (802.15.4e):** Introduced new modes to better support industrial applications.
    *   **DSME:** Deterministic and Synchronous Multi-channel Extension. Enhances reliability using multiple channels.
    *   **LLDN:** Low Latency Deterministic Network. For very fast, star-topology networks.
    *   **TSCH (Time Slotted Channel Hopping):** The main focus. Combines **time-slotted access** (like a strict timetable) with **channel hopping** (changing frequencies) to provide high reliability and determinism for mesh networks.
![[All_slides_nes.pdf#page=430]]
**Week 12 Slide 7 – IEEE 802.15.4 TSCH**

*   **TSCH (Time-Slotted Channel Hopping):** A **MAC protocol** from the IEEE 802.15.4e standard, specifically designed for **industrial-grade wireless sensor networks**.
*   **What it supports:**
    *   **Network Topologies:** **Multi-hop** networks, including line, tree, and mesh topologies.
    *   **Radio Duty Cycling:** All devices (not just RFDs) can turn their radios off according to a schedule to **save energy**.
*   **What it provides (Key Benefits):**
    *   **Very High Reliability:** Can achieve **>99.99% Packet Delivery Ratio (PDR)**.
    *   **Interference Avoidance:** Uses channel hopping to escape persistent interference on a single frequency.
    *   **Predictable Performance:** Offers **bounded latency, jitter, and energy consumption** because everything operates on a known schedule.
    *   **Time Synchronisation:** Keeps all devices in the network tightly synchronized (within ~**10 ms**), which is the foundation of its operation.

| **Feature** | **Benefit for Industrial Networks** |
| :--- | :--- |
| **Time-Slotted** | Eliminates collisions, provides predictable channel access. |
| **Channel Hopping** | Mitigates multi-path fading and external interference (e.g., from Wi-Fi). |
| **Synchronization** | Enables precise scheduling and coordination across the entire network. |
| **Duty Cycling** | Allows for long battery life even in always-on industrial networks. |
![[All_slides_nes.pdf#page=431]]
**Week 12 Slide 8 – TSCH Mechanics**

*   **Core Technology:** TSCH is a combination of two classic multiple access techniques:
    *   **TDMA (Time Division Multiple Access):** Time is divided into discrete **slots**. Only one scheduled transmission happens per slot on a given channel.
    *   **FDMA (Frequency Division Multiple Access):** The available radio spectrum is divided into multiple **frequency channels**.
*   **How it works:**
    1.  **Time-Slotted:** Communication happens in a synchronized, repeating **schedule**. This makes channel access **predictable and collision-free** (for dedicated slots).
    2.  **Channel Hopping:** Devices change (**hop**) the frequency channel they use for each timeslot according to a pre-defined pattern. This provides **resilience to interference** (if one channel is noisy, the next transmission might be on a clean one).
*   **Historical Roots:** TSCH concepts come from earlier, often proprietary, industrial wireless standards:
    *   **TSMP (2006):** Time Synchronized Mesh Protocol by Dust Networks.
    *   **WirelessHART (2007):** First open wireless standard for process automation.
    *   **ISA100.11a (2009):** A competing standard for general industrial automation.
*   **Key Takeaway:** TSCH **standardizes** and combines these proven, deterministic techniques (TDMA + FDMA hopping) into an open protocol for reliable industrial wireless networking.

![[All_slides_nes.pdf#page=432]]
**Week 12 Slide 9 – TSCH: Timeslots and Time Synchronisation**

*   **Foundation:** Two core, interdependent concepts in TSCH.
*   **1. Network-wide Time Synchronisation:**
    *   **Requirement:** **All devices** in a TSCH network must be tightly synchronized to a common clock.
    *   **Method:** Uses **implicit synchronisation**. Devices adjust their clocks based on the timing of received data frames or acknowledgements from their neighbors.
*   **2. Timeslots:**
    *   Time is divided into fixed-length **timeslots**. Each slot is a potential opportunity for a single frame transmission and its acknowledgement.
    *   **Slot Duration:** **Not fixed by the standard**, but designed to be long enough for:
        *   **Tx Data:** Transmit a max-size frame (~4 ms).
        *   **Rx ACK:** Receive an acknowledgement (~0.35 ms).
        *   **Guard Time:** A buffer period (~2 ms) to account for tiny clock drifts between devices.
        *   **Radio Turnaround:** Time for the radio to switch from transmit (Tx) to receive (Rx) mode, and for encryption/decryption.
    *   **Typical Size:** **10 ms** is common. Some slower radios may require **15 ms** slots.
*   **Visual (A, B, C timeline):** Shows devices A, B, and C operating on the same repeating timeline of slots, demonstrating synchronized slot boundaries.
![[All_slides_nes.pdf#page=433]]
**Week 12 Slide 10 – TSCH: Timeslot**

*   **Timeslot Purpose:** Defines a scheduled **transmission opportunity** for a specific link (sender-receiver pair). *Note: A transmission may not occur if the sender has no data.*
*   **Detailed Slot Timeline:**
    1.  **Start of Slot:** Both sender and receiver are synchronized.
    2.  **TxOffset:** The **sender** begins its frame transmission at a precise, small delay after the slot start.
    3.  **Guard Time Window:** The **receiver** wakes up and listens for a preamble during this window, which is centered around the expected arrival time.
        *   If a preamble is detected **within** the guard time, the receiver stays awake to get the full frame.
        *   If **nothing** is detected, the receiver goes **back to sleep**, saving energy.
    4.  **Mode Swap:** After the data frame is sent, the sender and receiver **swap roles** (Tx ↔ Rx) for the acknowledgement (ACK) transmission.
*   **Key Concept:** The **guard time** allows the system to tolerate small synchronization errors without missing transmissions, which is crucial for maintaining reliability while keeping devices synchronized.

![[All_slides_nes.pdf#page=434]]
**Week 12 Slide 11 – TSCH: Guard Time**

*   **Purpose of Guard Time:** A buffer period within a timeslot that **absorbs synchronization errors** between devices. It ensures the receiver is listening even if the sender's clock is slightly fast or slow.
*   **Guard Time Trade-offs:**
    *   **Longer Guard Time:**
        *   **Pros:** More robust to clock drift, allows for **less frequent** resynchronization.
        *   **Cons:** More **idle listening** (radio on but not receiving data), leading to **higher energy consumption**. It also makes slots longer, reducing the total number of slots per second and thus **network capacity**.
    *   **Shorter Guard Time:**
        *   **Pros:** Less idle listening, **better energy efficiency**, more slots per second (**higher capacity**).
        *   **Cons:** Requires **more precise, frequent synchronisation**.
*   **Design Goal:** The guard time should be **as short as possible**, but just long enough to maintain robust synchronization given the clock drift of the devices.
*   **Graph Explanation:** The graph shows the relationship between clock **Drift Amplitude** (in ppm - parts per million) and the maximum allowed time between resynchronizations. **Longer guard times (τ)** allow for much longer periods between sync messages for the same level of clock drift.

![[All_slides_nes.pdf#page=435]]
**Week 12 Slide 12 – TSCH: Frame-Based and ACK-Based Synchronisation**

*   **Implicit Synchronisation:** TSCH devices **do not** send separate time sync packets. Instead, they synchronize **using every single data/ACK frame exchange**.
*   **Two Methods:**
    1.  **Frame-Based:** The **receiver** calculates the difference between the expected and actual arrival time of the data frame. It then adjusts **its own clock** to match the sender's.
    2.  **ACK-Based:** The **receiver** calculates the same time offset but **includes it in the ACK frame** it sends back. The original **sender** then uses this information to adjust **its clock** to match the receiver's.
*   **The "Keep-Alive" Problem:** If a device has **no data to send for a long time**, it stops exchanging frames and loses synchronization. To prevent this, it must periodically send empty **"Keep-Alive" frames** just to resync.
    *   **Overhead:** This creates significant **energy and bandwidth overhead** in applications with very infrequent data (e.g., smart meters sending once per hour).
*   **Diagram:** Illustrates the TxOffset, data transmission, guard time, and the swap for the ACK, showing where timing measurements are taken for synchronization.

![[All_slides_nes.pdf#page=436]]
**Week 12 Slide 13 – TSCH: Absolute Slot Number (ASN)**

*   **What is ASN?** An **Absolute Slot Number** that counts every timeslot since the network was formed. It is a **globally shared, monotonically increasing counter**.
    *   **Size:** 5 bytes (40 bits), large enough to run for **hundreds of years** without wrapping around.
*   **ASN Synchronisation:**
    *   The device that starts the network initializes ASN = 0.
    *   When a new device joins, it learns the current ASN value.
    *   Because all devices are time-synchronized, **every device knows the current ASN at all times**.
*   **Purpose:** The ASN is the **master clock** for the entire network. It is used to:
    1.  Determine the exact **slot position** in the repeating schedule.
    2.  Calculate the **frequency channel** to use for any given slot (via the Channel Hopping Sequence).

**Visual:** Shows a timeline where ASN increments with every slot (0, 1, 2...). Devices A and B's slots are aligned under the same ASN values, demonstrating they share the same global timeline.

![[All_slides_nes.pdf#page=437]]
**Week 12 Slide 14 – TSCH: Slot frame and Schedule**

*   **Slot Frame:** Timeslots are organized into a repeating cycle called a **slot frame**. It's like a weekly timetable that repeats continuously.
    *   **Slot Frame Size:** The number of slots in one cycle. This is **not defined by the standard** and is tailored to the application's needs.
    *   **Slot Offset:** A device's position within the current frame. Calculated as:  
        `Slot Offset = ASN mod Slot Frame Size`.
*   **Schedule:** A **communication plan** that defines what happens in each slot offset for each device (Transmit, Receive, or Sleep). It is typically a table mapping Slot Offsets to actions.
*   **Example (from slide):**
    *   Slot Frame Size = 7 slots.
    *   Schedule rule: "Device B transmits to Device A in Slot Offset 1."
    *   This means every time `ASN mod 7 = 1`, that specific communication occurs.

**Visual:** The timeline shows ASN increasing. A slot frame of size 7 is highlighted, repeating every 7 slots. The schedule (e.g., "B→A") is applied to specific slot offsets within each frame.

![[All_slides_nes.pdf#page=438]]
**Week 12 Slide 15 – TSCH: The Schedule Controls Several Performance Metrics**

*   **Central Idea:** The **schedule directly determines** the key performance characteristics of the network. By designing the schedule, you trade off between capacity, latency, and energy.
*   **Example Calculation** (assuming 10ms timeslot & slotframe size of 7):
    *   **Link Capacity (Throughput):**  
        `100 slots/sec / 7 slots/frame ≈ 14.28 packets/sec`  
        This is the **maximum** rate a link can achieve if it gets 1 slot per frame.
    *   **Energy Consumption (Duty Cycle):**  
        `1 slot active / 7 total slots ≈ 14.28%` radio duty cycle.  
        The radio is asleep for the remaining 85.72% of the time.
    *   **Worst-Case Latency:**  
        `7 slots/frame * 10 ms/slot = 70 ms`.  
        If data arrives just after its designated slot, it must wait almost a full frame to be sent.
*   **Design Trade-off:** A **shorter** slotframe (e.g., size 3) increases capacity and reduces latency but **worsens energy efficiency** (higher duty cycle) because each device is active a larger fraction of the time.

![[All_slides_nes.pdf#page=439]]
**Week 12 Slide 16 – TSCH: Slot Frame Size**

*   **Core Impact:** The slot frame size defines the **ratio of active slots to idle slots** in the repeating schedule. It is a primary knob for tuning network performance.
*   **Shorter Slot Frame Size (e.g., 3 slots):**
    *   **Advantages:**
        *   **Higher Capacity:** More transmission opportunities per second for each link.
        *   **Higher Reliability:** More chances for retransmissions within a given time period.
        *   **Lower Latency:** Shorter wait between a device's scheduled slots.
    *   **Disadvantages:**
        *   **Worse Energy Efficiency:** Devices have a **higher radio duty cycle** (active more often).
        *   **Worse Scalability:** Fewer total slots to distribute among many devices/links.
*   **Longer Slot Frame Size (e.g., 100 slots):**
    *   Has the opposite effects: better energy efficiency and scalability, but lower per-link capacity, potentially lower reliability, and higher latency.

**Visual:** The timeline shows a short slotframe. Device A is active (tx) in 2 out of every 3 slots, resulting in a high 66% duty cycle but high capacity.


![[All_slides_nes.pdf#page=440]]
**Week 12 Slide 17 – TSCH Schedule: Dedicated Slots**

*   **Slot Types:** In any given slot, a device can be scheduled to **Transmit (Tx)**, **Receive (Rx)**, or be idle (**Sleep**).
*   **Dedicated Slots (Contention-Free):**
    *   A slot dedicated to a **single, specific communication link** (e.g., "Device B -> Device A").
    *   **Key Property:** Only **one device is the assigned transmitter** in that slot. This **eliminates collisions** completely.
    *   **Example:** In a slot scheduled as `B > A`:
        *   Device B's role = **Tx** (Transmit).
        *   Device A's role = **Rx** (Receive).
        *   All other devices (C, D) = **Sleep**.

**Visual (Schedule Table):** The table shows a schedule over 13 slot offsets (0-12). It marks specific slots (e.g., offset 3, 10) as dedicated for links like `D > C` or `B > A`, assigning Tx/Rx roles only to the involved devices.

![[All_slides_nes.pdf#page=441]]
**Week 12 Slide 18 – TSCH Schedule: How many slots?**

*   **Question:** How do you decide **how many dedicated slots** to allocate to a specific link (e.g., why 2 slots for C→A in the example)?
*   **Answer:** The slot allocation must provide enough capacity to handle the **total traffic** that needs to flow over that link.
*   **Traffic on a link consists of:**
    1.  **Packets generated locally** by the transmitter (its own sensor data).
    2.  **Packets forwarded** from its child nodes in the network (relay traffic).
*   **Critical Factor – Retransmissions:** You must also allocate extra slots to account for **packet losses**. The number of needed slots is multiplied by the **Expected Transmission Count (ETX)**.
    *   **ETX Formula:** `ETX = 1 / p`, where `p` is the probability of a packet being successfully received (PDR).
    *   **Example:** If the link quality `p = 0.2` (20% PDR), then `ETX = 5`. You need to schedule **5 transmission opportunities** on average to successfully deliver one packet.

**Conclusion:** Total slots needed for a link ≈ (Local + Forwarded traffic rate) * ETX.


![[All_slides_nes.pdf#page=442]]
**Week 12 Slide 19 – TSCH Schedule: Broadcast Slots**

*   **Broadcast Slot:** A special slot where **all nodes in the network are active** (listening).
*   **Rules of Operation:**
    *   If a device **has a broadcast message** to send (e.g., routing info), it transmits.
    *   If a device **has nothing to broadcast**, it listens (receives).
    *   **Typically** the **first slot** (Slot Offset 0) of the slotframe.
*   **Characteristics:**
    *   **Collisions Possible:** Since multiple devices may decide to broadcast, their transmissions can collide. This makes broadcasts **less reliable** than dedicated slots.
    *   **Transmitter Deafness:** A node that is transmitting a broadcast **cannot simultaneously receive** broadcasts from others.
*   **Purpose:** Used for network management traffic that needs to reach all nodes, such as routing advertisements or network-wide commands.

**Visual:** The schedule table shows "BC" (Broadcast) in Slot Offset 0. All devices (A, B, C, D) are shown as active (not sleeping) in that slot.

![[All_slides_nes.pdf#page=443]]
**Week 12 Slide 20 – TSCH: Slots Are Limited**

*   **Fundamental Limitation:** Time is a finite resource. With a typical 10ms timeslot, there are a maximum of **100 slots available per second** in the entire network.
*   **Implication:** This places a hard upper limit on the **total network capacity** (max 100 packets/sec, ignoring retransmissions).
*   **Design Challenge:** What do you do when you need to support:
    *   **More devices?**
    *   **More traffic?**
    *   **More retransmissions** (due to poor link quality)?
*   **Answer:** You must use the available slots **more efficiently**. The next slides introduce two key techniques to overcome this limitation: **Shared Slots** and **Multiple Channels**.

![[All_slides_nes.pdf#page=444]]
**Week 12 Slide 21 – TSCH Schedule: Shared Slots**

*   **Shared Slot (Contention-Based):** A slot assigned to **multiple potential transmitters**.
*   **How it works:** Unlike a dedicated slot, multiple devices are scheduled to *possibly* transmit in the same slot offset. To avoid constant collisions, they use **CSMA/CA** (Carrier Sense Multiple Access with Collision Avoidance) – they "listen before talking."
*   **Characteristics:**
    *   **Efficiency:** Allows more devices to share a smaller number of slots, improving **scalability**.
    *   **Trade-off:** Introduces **unpredictability**. Collisions can still occur, and latency is **not bounded** because a device may have to back off and wait.
    *   **Use Case:** Suitable for **best-effort, non-critical traffic** where determinism is not required.

**Visual:** The schedule table shows a shared slot (e.g., at offset 2) where potentially both A and C could transmit (`A>A` implies A to another, C likely similar). They must contend for the channel using CSMA/CA.


![[All_slides_nes.pdf#page=445]]
**Week 12 Slide 22 – TSCH Schedule: Multiple Channels**

*   **Key Concept for Capacity:** TSCH can use **multiple radio frequency channels in parallel** (FDMA). This is the primary method to **increase network capacity** beyond the 100 packets/sec limit of a single channel.
*   **Mechanics:** The schedule is extended into a **2D table**:
    *   **Rows:** Represent **Channel Offsets (CHO)**.
    *   **Columns:** Represent **Slot Offsets (SO)**.
*   **Rule:** A transmitter-receiver pair must be tuned to the **same specific channel** for a scheduled communication to happen.
*   **Benefit:** **Parallel transmissions** can occur simultaneously in the same slot offset, as long as they are on **different channels**. This multiplies the network's capacity.

**Visual:** The schedule shows two channels (CH0 and CH1) operating in parallel. In Slot Offset 1, transmission `C > A` happens on CH0, while `D > C` happens **simultaneously** on CH1. This doubles the capacity compared to using one channel.

![[All_slides_nes.pdf#page=446]]
**Week 12 Slide 23 – Some Channels are better than others**

*   **Problem:** Wireless channels are not equally good. They suffer from:
    *   **Interference:** From other networks (e.g., Wi-Fi).
    *   **Fading:** Signal weakening due to environment.
*   **Key Observation:** These errors are **correlated in time** but **often uncorrelated across frequencies**.
    *   **Time Correlation:** If a channel is bad now, it's likely to be bad for the next several seconds.
    *   **Frequency Independence:** The interference source (e.g., a Wi-Fi router) typically affects only a portion of the spectrum. If channel 15 is bad, channel 20 might be perfect.
*   **TSCH's Smart Solution:** **Channel Hopping.**
    *   Instead of retransmitting a failed packet on the same (likely still bad) channel, TSCH **changes the channel for each retransmission attempt**.
    *   This spreads the risk across multiple frequencies, dramatically **increasing the probability of successful delivery** and thus **enhancing reliability**.

![[All_slides_nes.pdf#page=447]]
**Week 12 Slide 24 – TSCH: Channel Hopping**

*   **Channel Hopping Sequence (CHS):** A pre-agreed, pseudo-random list of channels that all nodes in the network know (e.g., `[10, 11, 12, 14, 15]`).
*   **How it works:** The channel to use for any given timeslot is **not fixed**. It is determined by:
    1.  The **Absolute Slot Number (ASN)**.
    2.  The **Channel Hopping Sequence (CHS)**.
*   **Formula:**  
    `Channel = CHS[ Index ]`  
    where `Index = ASN mod length(CHS)`.
*   **Example:** If `CHS = [10, 11, 12]` and `ASN = 7`, then:  
    `Index = 7 mod 3 = 1`  
    `Channel = CHS[1] = 11`.
*   **Outcome:** The network **hops through the CHS in sync**, using a different channel for each successive ASN. This provides frequency diversity and interference resilience.

![[All_slides_nes.pdf#page=448]]
**Week 12 Slide 25 – Slot Frame Size vs Channel Hopping Sequence Size**

*   **Critical Rule:** The **Slot Frame Size** and the **Channel Hopping Sequence (CHS) Size** must be **relatively prime** (their Greatest Common Divisor must be 1).
*   **Why?** To ensure **true channel hopping** and avoid getting stuck on a subset of channels.
*   **Bad Example (from slide):** If Slot Frame Size = 6 and CHS Size = 3:
    *   GCD(6, 3) = 3 (not relatively prime).
    *   The pattern repeats every 6 slots, but the channel cycle is 3. This means the same (Slot Offset, Channel) pair repeats every **2 slotframes**, reducing frequency diversity.
    *   **Result:** A link scheduled in a specific slot offset would **always use the same channel**, losing the benefit of hopping.
*   **Good Design:** Choose sizes like 7 and 4 (GCD=1) to ensure all channel-sequence combinations are used before the pattern repeats, maximizing diversity.

![[All_slides_nes.pdf#page=449]]
**Week 12 Slide 26 – The TSCH Schedule**

*   **The Complete Schedule:** A **2-dimensional table** that defines communication for every Slot Offset and Channel Offset.
    *   **N (Columns):** Slot Frame Size (number of Slot Offsets, SO).
    *   **M (Rows):** Number of used Channel Offsets (CHO), often equal to the Channel Hopping Sequence (CHS) size.
*   **Cell Contents:** Each cell `(CHO, SO)` can be empty or contain a link (e.g., `C > A`).
*   **Channel Calculation (The Key Formula):**  
    The actual radio frequency channel for a cell is determined dynamically by:
    `Channel = CHS[ Index ]`  
    where `Index = (ASN + CHO) mod length(CHS)`.
*   **Implication:** For a given link in cell `(CHO, SO)`, the **physical channel changes every slotframe** because the ASN increases. This is **channel hopping**.

**Example Table:** The slide shows a 3x7 schedule (3 CHOs, 7 SOs). A link like `C > A` in cell `(0,2)` will hop through the CHS based on the formula above.

![[All_slides_nes.pdf#page=450]]
**Week 12 Slide 27 – Channel Selection**

*   **Problem:** Not all channels in the hopping sequence are equally good. Some may have persistent interference.
*   **Static vs. Adaptive Selection:**
    *   **Static:** Use a fixed, pre-defined Channel Hopping Sequence (CHS).
    *   **Adaptive:** **Dynamically measure** channel quality and **update the CHS** to use the best available channels.
*   **Adaptive Channel Selection Process:**
    1.  **Measure:** Nodes listen to and assess the quality (e.g., noise level, packet success rate) of candidate channels.
    2.  **Update:** Maintain statistics/metrics for each channel.
    3.  **Select:** Create a **whitelist** (good channels) or **blacklist** (bad channels).
    4.  **Distribute:** Propagate the updated channel list (new CHS) to all nodes in the network.
*   **Benefit:** The network can **avoid chronically bad channels** and adapt to changing interference patterns, maintaining high reliability.

**Diagram Flow:** Shows the cycle: Wireless Medium → Measurement → Channel Assessment → Quality Metrics → Channel Selection → Updated Hopping Sequence.

![[All_slides_nes.pdf#page=451]]
**Week 12 Slide 28 – TSCH Scheduler**

*   **Scheduler:** The **"brain"** or algorithm that **creates and manages** the TSCH schedule (the 2D table of who transmits when and on which channel).
*   **Important:** The scheduler is **not defined** by the IEEE 802.15.4 TSCH standard. This **flexibility** allows it to be optimized for different use cases.
*   **Types of TSCH Scheduling:**
    1.  **Static Scheduling:** Schedule is fixed and hardcoded.
    2.  **Dynamic Scheduling:** Schedule changes at runtime. This has three sub-types:
        *   **Centralised Scheduling:** A central controller (e.g., root node) makes all scheduling decisions.
        *   **Distributed Scheduling:** Nodes negotiate schedules with their neighbors.
        *   **Autonomous Scheduling:** Each node independently determines its own schedule based on local rules.

![[All_slides_nes.pdf#page=452]]
**Week 12 Slide 29 – Static Scheduling**

*   **How it works:** The complete communication schedule is **pre-defined and hardcoded** into the firmware of every device before deployment.
*   **Creation:** The schedule can be **handcrafted by a human** or **calculated by an algorithm** for a specific known network.
*   **When it makes sense:** Only in **static, unchanging networks** where the following are known and fixed in advance:
    *   Number of devices.
    *   Network topology (who talks to whom).
    *   Traffic patterns (data rates).
    *   Link quality (expected retransmissions).
*   **Pros & Cons:**
    *   **Pro:** Simple, no scheduling overhead during operation.
    *   **Con:** **Inflexible.** Cannot adapt to node failures, new nodes joining, or changes in traffic/links.

**Example Table:** Shows a static schedule table hardcoded into the network.

![[All_slides_nes.pdf#page=453]]
**Week 12 Slide 30 – Dynamic Scheduling**

*   **Core Idea:** Start with a minimal, basic schedule and then **dynamically add/remove dedicated slots** as needed during network operation.
*   **Two Main Approaches:**
    1.  **Centralised Scheduling:**
        *   A **central controller** (usually the root/gateway node) collects information (topology, traffic, link quality) from all nodes.
        *   With this global view, it computes an optimal schedule and **instructs nodes** to add/remove specific slots.
        *   Can use advanced techniques like **Machine Learning or Reinforcement Learning** for optimization.
    2.  **Distributed Scheduling:**
        *   **No central controller.** Neighboring nodes **exchange messages** to negotiate and agree on which slots to use for their communication links.
        *   More scalable and robust to single-point failure, but can be harder to optimize globally.
*   **Initial Schedule:** Both approaches typically begin with a network-wide **shared slot** (or a set of them) used for the control traffic needed to organize the dedicated slots.

![[All_slides_nes.pdf#page=454]]
**Week 12 Slide 31 – IETF Minimal Schedule and 6top**

*   **Minimal Schedule (IETF Standard):** A default, simple schedule defined so that devices from different manufacturers can initially communicate.
    *   **Contains:** A single **broadcast slot** in cell `(0,0)` – the first slot offset on the first channel offset.
    *   **Undefined:** Slotframe size and channel sequence size are not specified, allowing flexibility.
*   **6top Protocol (6TiSCH Operation Sublayer):** The **standardized protocol** used for **distributed scheduling**.
    *   **Function:** Allows two neighbor nodes to exchange messages to **add, delete, or relocate** dedicated slots between them.
    *   **Key Commands (6P):**
        *   **ADD (1):** Add one or more cells (slots) to our link.
        *   **DELETE (2):** Remove cells.
        *   **RELOCATE (3):** Move a cell to a different (slot, channel) offset (e.g., to resolve a schedule collision).
        *   **COUNT (4), LIST (5):** Query the current schedule.
        *   **CLEAR (7):** Remove all cells between neighbors (reset).

**Table:** Lists the 6P commands with their codes and descriptions.

![[All_slides_nes.pdf#page=455]]
**Week 12 Slide 32 – Autonomous Scheduling**

*   **Concept:** Each node **independently calculates** its own transmission/receive schedule **without negotiating** with neighbors (no 6P-like message exchange).
*   **How it works:**
    1.  **Shared Slots for Routing:** A few shared slots are used to run the routing protocol (e.g., RPL), which determines parent-child relationships.
    2.  **Deterministic Slot Calculation:** A node uses a **hash function** on unique identifiers (e.g., its own MAC address, its parent's MAC address) **modulo the slotframe size** to determine its dedicated slot(s).
*   **Example - Orchestra Scheduler:** A widely used, non-standard autonomous scheduler.
    *   A node has a **receive slot** determined by hashing its own MAC address.
    *   It has a **transmit slot** determined by hashing its parent's MAC address.
*   **Pros & Cons:**
    *   **Pro:** Very low control overhead, simple, and inherently collision-free if hashing works well.
    *   **Con:** Can be inefficient if traffic patterns don't match the hash-based allocation; less adaptable than dynamic scheduling.

![[All_slides_nes.pdf#page=456]]
**Week 12 Slide 33 – Joining a TSCH Network**

*   **Challenge for a New Device:** A device wanting to join has **no knowledge** of the network's:
    1.  Schedule (when to listen).
    2.  Current ASN (what time it is).
    3.  Time synchronization (when slots begin).
*   **Solution: Enhanced Beacon (EB)**
    *   **What it is:** A special packet **periodically broadcast** by devices already in the network.
    *   **Contents:** Includes the **current ASN** and (at least part of) the **schedule**.
    *   **Purpose:** To **advertise** the network and provide the information needed to join.
*   **Joining Process:** The new device must **scan** for an EB without knowing when or where it will be sent.

![[All_slides_nes.pdf#page=457]]
**Week 12 Slide 34 – Searching for an EB packet**

*   **The Joining Scan Process:**
    1.  **Sequential Channel Scan:** The joining device turns on its radio and listens on one channel at a time, cycling through all channels (or a known subset).
    2.  **First EB Received:** When it hears its first EB, it has found a potential **parent** node and acquires initial sync and schedule info.
    3.  **Optional: Parent Selection:** It may continue scanning for a short time to find other EBs and choose the best parent (e.g., with strongest signal).
*   **Characteristics:**
    *   **Slow & Energy-Inefficient:** Scanning all 16 channels sequentially is a **notoriously slow and power-hungry** process.
    *   **Acceptable Trade-off:** This inefficiency is often considered acceptable because joining is (ideally) a **one-time event** in static industrial networks. After joining, the node operates on the efficient TSCH schedule.

![[All_slides_nes.pdf#page=458]]
**Week 12 Slide 35 – Industrial Wired Networks**

*   **Context:** Not all industrial networks are wireless. **Wired networks** (Ethernet) are also enhanced for determinism.
*   **IEEE 802.1Q (VLAN):** The base standard that adds **Virtual LAN (VLAN) tagging** to Ethernet frames.
    *   **Key Feature:** An 802.1Q header includes a 3-bit **Priority Code Point (PCP)** field, defining **8 priority classes** (0-7) for traffic.
*   **Time-Sensitive Networking (TSN):** A **suite of standards** (IEEE 802.1) that **extends** IEEE 802.1Q to provide **deterministic performance** over standard Ethernet.
    *   **Analogy:** TSN is to wired Ethernet what **TSCH** is to wireless IEEE 802.15.4. Both add timing guarantees to a best-effort base standard.

![[All_slides_nes.pdf#page=459]]
**Week 12 Slide 36 – Time Sensitive Networking (TSN)**

*   **TSN Goal:** Provide **bounded low latency and low jitter** for time-critical traffic on standard Ethernet.
*   **Key TSN Standards:**
    *   **IEEE 802.1AS (Timing & Synchronization):** Provides **microsecond-level precision time sync** across the network using a profile of PTP (Precision Time Protocol).
    *   **IEEE 802.1Qbv (Time-Aware Shaper - TAS):** The core scheduling mechanism.
*   **Time-Aware Shaper (TAS) Operation:**
    *   Time is divided into repeating **cycles**.
    *   Each cycle is split into **time slices (windows)**.
    *   Each time slice is **exclusively allocated** to a specific VLAN priority (or set of priorities).
    *   **Example (from diagram):** A dedicated slice is reserved for **VLAN priority 3** (time-critical traffic). All other priorities (7,6,5,4,2,0) must wait and are transmitted in a **separate "best-effort" window**.
*   **Result:** Time-critical traffic gets **guaranteed, collision-free access** at scheduled times, ensuring deterministic latency, just like TSCH's dedicated slots.


END OF WEEK 12
