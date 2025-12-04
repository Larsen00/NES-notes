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