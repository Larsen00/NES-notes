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