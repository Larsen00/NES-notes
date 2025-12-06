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