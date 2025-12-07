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