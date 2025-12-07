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


