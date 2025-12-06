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