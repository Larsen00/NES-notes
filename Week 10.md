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



