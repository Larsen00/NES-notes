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

