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