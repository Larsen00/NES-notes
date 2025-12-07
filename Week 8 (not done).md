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
