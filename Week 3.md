![[All_slides_nes.pdf#page=76]]  
**Week 3 Slide 3 – Digital Logic**  

**Notes:**

- Digital systems interpret two voltage levels as binary values.
    
- High voltage → logical **1**; low voltage → logical **0**.
    
- Real-world signals are noisy, but thresholds (e.g., above (V_S/2) = ‘1’) allow correct interpretation.
    
- Noise near the threshold can cause unstable readings, motivating later concepts such as **hysteresis**.

![[All_slides_nes.pdf#page=77]]  
**Week 3 Slide 4 – General Purpose Input/Output (GPIO)**  

**Notes**

- A **GPIO** pin is fully controlled by software.
    
- It can:
    
    - **Drive output high** (‘1’)
        
    - **Drive output low** (‘0’)
        
    - **Read** the logic level present on the pin
        
- Example: the **nRF52832** MCU provides **32 GPIOs**, labelled **P0.00–P0.31** (shown in the diagram).
    
- These pins serve as the MCU’s basic interface to the external world—sensors, LEDs, switches, communication lines, etc.

![[All_slides_nes.pdf#page=78]]  
**Week 3 Slide 5 – GPIO Output: Push-Pull Mode**  

**Notes (with deeper explanation)**

- In **push-pull mode**, the MCU actively drives the pin **both high and low** using internal transistor switches.
    
    - When output = ‘1’, the MCU **pushes** the pin up to (V_S).
        
    - When output = ‘0’, the MCU **pulls** the pin down to ground.
        
- Because the MCU is actively forcing the voltage, the pin behaves like a **strong, low-impedance source**—it can reliably drive LEDs, digital inputs on other chips, etc.
    
- This is the **default output mode** in most MCUs because it offers:
    
    - **Fast transitions** between logic levels
        
    - **Clear, well-defined voltage states**
        
    - **Ability to source or sink modest current**
        
- Key idea for understanding:
    
    - Push-pull mode gives you **full control**.
        
    - But because you actively drive both high and low, you **must not connect two push-pull outputs together**, or they might drive in opposite directions and cause a short circuit.
        

**Concept clarity**

- Think of the pin as a _muscle_ that can push upward and pull downward.
    
- Since it is always actively doing something, conflicts are dangerous if multiple devices try to drive the same line.

![[All_slides_nes.pdf#page=79]]  
**Week 3 Slide 6 – GPIO Output: Push-Pull Mode (MOSFET Implementation)**  

**Notes**

- Push-pull is implemented using **two MOSFETs** arranged so only one conducts at a time.
    
- When the control input = ‘1’:
    
    - The **upper MOSFET** connects the pin to (V_S).
        
    - The **lower MOSFET** disconnects from ground.
        
- When the control input = ‘0’:
    
    - The **upper MOSFET** disconnects from (V_S).
        
    - The **lower MOSFET** connects the pin to ground.
        
- Internally, this ensures:
    
    - A strong, clean logic level
        
    - Fast switching
        
    - No undefined voltage region (the pin is _always_ driven)
        

**What you should know for the exam**

- Be able to explain **how push-pull works** conceptually and electrically (two transistors, one sourcing, one sinking).
    
- Understand **why only one device may drive a push-pull output line** (otherwise shorts).
    
- Know that push-pull **actively drives both high and low**, unlike open-drain.

![[All_slides_nes.pdf#page=80]]  
**Week 3 Slide 7 – GPIO as a Current Source**  

**Notes**

- Besides carrying logic signals, a GPIO can **source current** to power small external components (e.g., an LED, a sensor enable pin).
    
- The GPIO acts like a small **on/off switch** controlled by software.
    
- However, GPIO pins have **strict current limits**: typically **2–12 mA**, sometimes up to **40 mA** for special “high-drive” pins.
    
- Exceeding this limit can **damage the pin or the MCU**.
    
- High-power components (motors, relays, power LEDs) must be powered directly from the supply and controlled indirectly via **transistors, MOSFETs, or driver circuits**.
    

**What you should know for the exam**

- Understand that GPIOs are **not general power outputs**—they can only supply small currents.
    
- Know the difference between **logic signalling** (very low current) and **current sourcing** (limited but finite).
    
- Be able to explain when to use a **driver circuit** instead of powering a component directly from a GPIO.

![[All_slides_nes.pdf#page=81]]  
**Week 3 Slide 8 – GPIO as a Current Sink**  

**Notes**

- A GPIO can also **sink current**, meaning current flows _into_ the pin toward ground.
    
- This is the opposite of current sourcing: instead of providing current, the pin completes the circuit by pulling the line to ground.
    
- When configured as a sink:
    
    - Writing **‘0’** → the pin connects to ground → current flows → an LED **turns on**.
        
    - Writing **‘1’** → the pin becomes high (no current flow) → LED **turns off**.
        
- This reverses the intuitive logic: **0 = ON**, **1 = OFF**.
    
- Sink current is also **limited**, just like source current.
    

**Comparison Table: Source vs Sink**

|Concept|Current Source|Current Sink|
|---|---|---|
|Direction of current|Out of GPIO pin|Into GPIO pin|
|LED wiring|LED → GND|Vcc → LED|
|LED ON when|Output = ‘1’|Output = ‘0’|
|Risk|Exceeding source limit|Exceeding sink limit|

**What you should know for the exam**

- Be able to explain the difference between **sourcing** and **sinking** current.
    
- Understand why an LED may be wired differently depending on whether the MCU **sources** or **sinks** current.
    
- Remember that **logic inversion** occurs in sink configurations (0 turns things on).

![[All_slides_nes.pdf#page=82]]  
**Week 3 Slide 9 – Two MCUs**  

**Notes**

- The slide introduces the problem of **multiple devices sharing the same output line**.
    
- If two MCUs are connected to the same line and both are configured as **outputs**, they may try to drive **different logic levels** at the same time.
    
- This sets up the concept of **output conflicts**, which can damage hardware.
    

**Concept clarity**

- Think of the shared line as a “tug-of-war”:
    
    - If both MCUs try to push/pull the line in opposite directions, they effectively short **Vcc → GND** through their output drivers.
        
- The slide sets the stage for why we need more than just ‘0’ and ‘1’ output states.
    

**What you should know for the exam**

- Understand _why_ two push-pull outputs must **never** drive the same line simultaneously.
    
- Be able to describe the risk: **short circuit due to opposing drive levels**.
    
- Recognize that this motivates the need for a **third state** (Hi-Z), introduced in the next slides.

![[All_slides_nes.pdf#page=83]]  
**Week 3 Slide 10 – Two MCUs (Short Circuit Problem)**  

**Notes**

- When two devices share the same output line, the danger becomes clear:
    
    - If one MCU outputs **‘1’** (pushes the line to (V_S))
        
    - And the other outputs **‘0’** (pulls the line to ground)  
        → This forms a **direct short circuit** through the two output drivers.
        
- Because push-pull outputs are _actively_ driven, neither side “lets go,” so current spikes can occur that may:
    
    - Overheat pins
        
    - Damage MOSFETs inside the MCU
        
    - Corrupt signals or reset devices
        
- The key limitation:
    
    - With only two output states (‘0’ and ‘1’), there is **no safe way** to share a line between multiple drivers.
        
    - We need a way for devices to **disconnect** themselves → the motivation for **tri-state logic / Hi-Z**.
        

**What you should know for the exam**

- Be able to explain **exactly why** output conflicts cause shorts.
    
- Recognize that the problem arises because push-pull outputs **actively drive both high and low**.
    
- Understand that this leads to the requirement for a third state (**Hi-Z**) to enable safe bus sharing.


![[All_slides_nes.pdf#page=84]]  
**Week 3 Slide 11 – Tri-State Logic**  

**Notes**

- Tri-state logic introduces a **third output state** beyond ‘0’ and ‘1’:
    
    - **‘0’** → actively driven low
        
    - **‘1’** → actively driven high
        
    - **Hi-Z** (high impedance) → **disconnected**, behaving like an open circuit
        
- In Hi-Z, the output driver’s MOSFETs are **both off**, making the pin effectively invisible to the circuit.
    
- Because Hi-Z presents extremely high resistance, **no current flows**, so multiple devices can be connected to the same line **as long as only one drives it at a time**.
    
- This enables shared-bus communication systems (e.g., memory buses, some digital protocols).
    
- The tri-state buffer uses MOSFET switches controlled by an **enable signal**:
    
    - EN = 1 → output is active (‘0’ or ‘1’)
        
    - EN = 0 → output is Hi-Z
        

**Comparison Table: Push-Pull vs Tri-State**

|Feature|Push-Pull|Tri-State|
|---|---|---|
|Possible states|‘0’, ‘1’|‘0’, ‘1’, **Hi-Z**|
|Can share line with others|❌ No|✅ Yes (if only one enabled)|
|Risk of short|High if multiple drivers|Avoided via Hi-Z|
|Use case|Simple GPIO output|Shared buses, multi-device lines|

**What you should know for the exam**

- Know the **definition** of the Hi-Z state and why it is essential.
    
- Understand the **MOSFET-based mechanism** that disconnects the pin.
    
- Be able to explain how tri-state logic **prevents short circuits** when multiple devices share a line.

![[All_slides_nes.pdf#page=85]]  
**Week 3 Slide 12 – GPIO Output States**  

**Notes**

- A GPIO’s output behavior is controlled by two internal signals:
    
    - **A** → the output value (‘0’ or ‘1’)
        
    - **EN** → the enable signal that determines whether the output driver is active
        
- This produces **three possible states**:
    
    1. **EN = 1, A = 1 → actively driven high**
        
    2. **EN = 1, A = 0 → actively driven low**
        
    3. **EN = 0 → Hi-Z (output disconnected)**
        
- This is how MCUs implement **tri-state functionality** on GPIO pins.
    
- When in Hi-Z, the pin does not affect the line; it can instead be **read** by the MCU or left floating unless external pull resistors set a default level.
    

**Concept clarity**

- EN acts like a _master switch_:
    
    - When EN is off, A no longer matters.
        
    - This is crucial for shared lines or when temporarily giving control to another device.
        

**What you should know for the exam**

- Understand the relationship between **A** and **EN** and how these two signals produce the three GPIO states.
    
- Be able to explain why Hi-Z is necessary for **safe multi-device connections**.
    
- Know that EN = 0 allows the pin to be used as an **input** or left floating for external circuitry to control.
![[All_slides_nes.pdf#page=86]]  
**Week 3 Slide 13 – GPIO Input and Input Hysteresis**  

**Notes**

- A GPIO input uses a **comparator**: it compares the pin voltage to a threshold to decide whether the input is ‘0’ or ‘1’.
    
- Typically, the threshold is around **(V_S/2)**.
    
- Problem: if the input voltage hovers near the threshold, **noise** can cause rapid switching between ‘0’ and ‘1’.
    
- Solution: **input hysteresis**, which introduces **two thresholds**:
    
    - To switch from **0 → 1**, voltage must exceed ((V_S/2) + V_H).
        
    - To switch from **1 → 0**, voltage must fall below ((V_S/2) - V_H).
        
- This creates a “dead band” where small fluctuations **do not** change the digital reading.
    
- Hysteresis dramatically improves stability for noisy or slowly changing signals (e.g., long wires, mechanical buttons without debouncing).
    

**Concept clarity**

- This is similar to how a thermostat avoids rapid on/off cycling by having separate temperature thresholds for heating and cooling.
    
- The input becomes immune to minor, fast disturbances.
    

**What you should know for the exam**

- Be able to **define hysteresis** and explain why it prevents spurious toggling.
    
- Know the meaning of the two thresholds and why they differ.
    
- Understand that hysteresis makes GPIO inputs **more robust to noise** and is common in real MCUs.

![[All_slides_nes.pdf#page=87]]  
**Week 3 Slide 14 – GPIO Input Mode**  

**Notes**

- This slide shows how the GPIO circuitry behaves when used as an **input** rather than an output.
    
- Key rule: **When EN = 1, the internal input signal (IN) simply equals A**, the logic level present on the pin.
    
    - In input mode, the MCU is _not_ driving the pin; instead, it is **sampling** the voltage on it.
        
- The diagram highlights that the pin’s logic level is determined by external circuitry (e.g., sensors, switches).
    
- No internal push-pull driving occurs in input mode; the pin must be given a valid high or low level externally or via pull resistors.
    

**Concept clarity**

- Think of EN as choosing whether the pin is “talking” (output) or “listening” (input).
    
- When listening, the pin must receive a clean signal from outside; otherwise, noise or floating behavior may occur (addressed in later slides).
    

**What you should know for the exam**

- Understand that **input mode disables the output driver**, allowing the pin voltage to be controlled externally.
    
- Know that the MCU reads the pin through an internal **comparator**.
    
- Recognize why floating inputs are problematic and require **pull resistors** (explained in upcoming slides).

![[All_slides_nes.pdf#page=88]]  
**Week 3 Slide 15 – Hardwired Input**  

**Notes**

- A **hardwired input** is a pin permanently tied to a fixed logic level (‘0’ or ‘1’) in the circuit.
    
- This input is **not meant to change** during operation.
    
- Typical uses:
    
    - **Permanent configuration** (e.g., selecting modes or enabling features).
        
    - **Device identification**:
        
        - Two MCUs may run the same firmware, but if one has Pin3 wired to ‘0’ and the other to ‘1’, the software can read the pin and know which board it is running on.
            
- This method avoids needing different code versions for different hardware variants.
    

**Concept clarity**

- Hardwired inputs act like **hardware constants**.
    
- They let the software adapt dynamically to the board’s wiring without needing external components or extra memory.
    

**What you should know for the exam**

- Know the purpose of a **hardwired input** and why it is used.
    
- Be able to explain how hardwired pins help with **board identification** or **permanent configuration settings**.
    
- Recognize that these inputs do **not change at runtime** and require no external driver circuitry.

![[All_slides_nes.pdf#page=89]]  
**Week 3 Slide 16 – Reading a Hi-Z Output**  

**Notes**

- A Hi-Z (high-impedance) output is **electrically disconnected** from the circuit.
    
- When you try to **read** a pin that is in Hi-Z, the voltage on the line is **not defined** because nothing is driving it.
    
- The pin can randomly register as ‘0’ or ‘1’ due to:
    
    - Ambient electrical noise
        
    - Capacitive coupling from nearby signals
        
    - Leakage currents
        
- This behavior is called a **floating input**.
    
- Floating inputs are **unreliable** and must be avoided when a stable digital value is required.
    

**Concept clarity**

- A Hi-Z pin behaves like a tiny **antenna**, easily picking up noise.
    
- Without a defined driving source or pull resistor, the voltage can wander unpredictably.
    

**What you should know for the exam**

- Be able to explain what happens when reading a **floating (Hi-Z) input**.
    
- Understand why a Hi-Z line provides **no guaranteed logic level**.
    
- Know that this issue motivates the use of **pull-up or pull-down resistors**, introduced next.

![[All_slides_nes.pdf#page=90]]  
**Week 3 Slide 17 – Reading a Hi-Z Output (Floating Input Explained)**  

**Notes**

- When the output is **disabled (Hi-Z)** and you attempt to read it, the input value is **undefined**.
    
- Because no circuit drives the line, the voltage can:
    
    - Drift to random levels
        
    - Flip between ‘0’ and ‘1’ unpredictably
        
    - Respond to tiny external electrical influences
        
- This is why a Hi-Z pin is described as **floating**.
    
- Floating inputs lead to **unstable behavior**, such as false triggers, random toggling, or noisy readings.
    

**Concept clarity**

- A floating pin has **no reference**—it tries to settle somewhere but even slight environmental interference changes its state.
    
- Reliable digital logic requires **defined voltage levels**, not arbitrary noise-influenced values.
    

**What you should know for the exam**

- Know the definition of a **floating input** and why it is unstable.
    
- Understand that **Hi-Z does not imply a known logic level**.
    
- Recognize that this problem is solved using **pull-up or pull-down resistors**, which set a default logic value.

![[All_slides_nes.pdf#page=91]]  
**Week 3 Slide 18 – Pullup and Pulldown Resistors**  

**Notes**

- Pull resistors give a **default logic level** when no device is actively driving the line.
    
- **Pullup resistor**:
    
    - Connects the line weakly to **‘1’**.
        
    - If nothing drives the line, it reads as **1**.
        
    - If an external device actively pulls the line low, that wins, because the pullup is weak.
        
- **Pulldown resistor**:
    
    - Connects the line weakly to **‘0’**.
        
    - If nothing drives the line, it reads as **0**.
        
- Key behavior of a pullup:
    
    - If the line is actively driven to ‘1’ → **no current flows** (both sides are at the same voltage).
        
    - If the line is actively driven to ‘0’ → **current flows through the resistor**, allowing the driven ‘0’ to dominate.
        
- MCUs often provide **internal pullups/pulldowns**, eliminating the need for external resistors in many designs.
    

**Concept clarity**

- Pull resistors ensure that a pin **never floats**.
    
- They are “weak” on purpose so that a real driver can easily override them.
    

**Comparison Table**

|Feature|Pullup|Pulldown|
|---|---|---|
|Default state|‘1’|‘0’|
|Connection|Line → Vcc through resistor|Line → GND through resistor|
|Overridden by|Driving ‘0’|Driving ‘1’|

**What you should know for the exam**

- Be able to explain why floating inputs are bad and how pull resistors fix the problem.
    
- Know the behavior of pullups vs pulldowns and how they interact with actively driven signals.
    
- Understand that pull resistors provide a **stable default** but do **not** act like strong drivers.

![[All_slides_nes.pdf#page=92]]  
**Week 3 Slide 19 – GPIO Output with Pullup**  

**Notes**

- When a GPIO has an **internal pullup resistor** and:
    
    - **EN = 0 (Hi-Z)** → the pullup sets the input level to **‘1’**.
        
    - **EN = 1 (output enabled)** → the output driver takes over and the input simply equals **A** (either 0 or 1).
        
- This allows a single pin to behave predictably even when the MCU is **not driving** it.
    
- Useful when the pin must:
    
    - Be read during startup before the MCU configures its direction
        
    - Avoid floating during tri-state phases
        
    - Cooperate with open-drain systems that rely on pullups
        

**Concept clarity**

- When EN=0, the pullup provides a **weak default**.
    
- When EN=1, the MCU provides a **strong drive**, overriding the pullup easily.
    

**What you should know for the exam**

- Understand how the pullup defines a default input when the pin is disabled.
    
- Know that when EN=1, the output driver has priority over the pull resistor.
    
- Be able to explain why pullups are essential in shared-line and open-drain configurations.
![[All_slides_nes.pdf#page=93]]  
**Week 3 Slide 20 – Multiple MCUs**  

**Notes**

- When multiple MCUs share the same physical line, it is **only safe if exactly one device drives the line at a time**.
    
- Even with pull resistors present, **push-pull outputs can still cause short circuits** if two devices accidentally drive opposite values simultaneously.
    
- The slide asks: _Is this safe enough?_
    
    - The answer is **no**—push-pull GPIOs remain risky in multi-device scenarios.
        
- This is why communication buses (I²C, 1-Wire, open-collector logic, etc.) use **open-drain** instead of push-pull:
    
    - Open-drain avoids direct conflicts because devices can only pull the line **low**, never drive it **high**.
        

**Concept clarity**

- A shared line must have a guaranteed rule that prevents two drivers from ever forcing conflicting voltages.
    
- Push-pull cannot guarantee this → open-drain is the safe alternative.
    

**What you should know for the exam**

- Know why **push-pull outputs are unsafe** on shared lines.
    
- Understand that even with pull resistors, **two push-pull drivers can still short the line**.
    
- Recognize that this leads directly to the need for **open-drain** outputs, covered in the next slide.

![[All_slides_nes.pdf#page=94]]  
**Week 3 Slide 21 – GPIO Output: Open-Drain Mode**  

**Notes**

- **Open-drain** (or open-collector) outputs have **only two states**:
    
    1. **Drive low (‘0’) — actively pull the line to ground**
        
    2. **Hi-Z — disconnect and let a pullup resistor bring the line high (‘1’)**
        
- Importantly, the MCU **never actively drives the line high**.
    
- A pullup resistor (internal or external) creates the ‘1’ state by default; devices only **pull the line low** when needed.
    
- Because no device ever drives the line high, **multiple devices can share the same line without risking a short circuit**:
    
    - If two devices pull low → line stays low (no conflict).
        
    - If one pulls low and others are Hi-Z → still safe.
        
- This is why open-drain is used for multi-device buses (e.g., **I²C SDA/SCL**, interrupt lines, wired-OR logic).
    

**Concept clarity**

- Open-drain = “I can pull low, but I never push high.”
    
- This guarantees that a conflict can _never_ create a Vcc–GND short.
    

**Comparison Table**

|Feature|Push-Pull|Open-Drain|
|---|---|---|
|Drives high?|Yes|No (pullup needed)|
|Drives low?|Yes|Yes|
|Hi-Z possible?|Yes (tri-state)|Yes|
|Safe for shared lines?|No|**Yes**|
|Risk of short?|High if multiple active drivers|**None** when pulling low|

**What you should know for the exam**

- Be able to clearly define **open-drain** and how its two states work.
    
- Understand why open-drain enables **safe multi-device communication**.
    
- Know the role of the **pullup resistor** in generating the high level.

![[All_slides_nes.pdf#page=95]]  
**Week 3 Slide 22 – Analog-to-Digital Converter (ADC)**  

**Notes**

- An **ADC** converts a continuously varying **analog voltage** into a **digital number** the MCU can process.
    
- The ADC measures the input voltage and maps it into one of **(2^M)** discrete values, where **M = bit resolution**.
    
    - Example: a **12-bit ADC** outputs values from **0 to 4095**.
        
- The image shows the ADC sampling the input voltage and outputting a digit that corresponds to the voltage level.
    
- ADCs are essential for sensors (temperature, light, pressure, microphones, etc.) because most real-world measurements are **analog**.
    

**Concept clarity**

- The ADC does **not** give exact voltages—only the nearest discrete step allowed by its resolution.
    
- Higher resolution → **more precise representation** of small voltage differences.
    
- Lower resolution → larger quantization steps → “rougher” measurements.
    

**What you should know for the exam**

- Know what an ADC does: **maps analog voltages to digital numbers**.
    
- Understand the meaning of **bit resolution** and how it sets the range of possible output values.
    
- Be able to explain why higher resolution gives **finer voltage detail**.
    
- Recognize why ADCs are required when interfacing with **analog sensors**.

![[All_slides_nes.pdf#page=96]]  
**Week 3 Slide 23 – Single-Ended ADC**  

### **What a Single-Ended ADC Does**

Measures the input voltage relative to ground:

$$  
V_{\text{measured}} = V_{in}  
$$

Valid input range:

$$  
0 \le V_{in} \le V_{ref}  
$$

Digital output range:

$$  
D_{out} \in [0,; 2^M - 1]  
$$

Saturation occurs when:

$$  
V_{in} > V_{ref}  
\quad\Rightarrow\quad  
D_{out} = 2^M - 1  
$$

---

### **Example: 12-bit ADC with (V_{ref} = 5,\text{V})**

|Input Voltage (V_{in})|Digital Output (D_{out})|
|---|---|
|$$0,\text{V}$$|$$0$$|
|$$2.5,\text{V}$$|$$2048$$|
|$$5,\text{V}$$|$$4095$$|
|$$6,\text{V}$$|$$4095 ;(\text{saturation})$$|

---

### **Key Idea**

The ADC divides the voltage range into discrete steps.  
Example resolution step size:

$$  
Q = \frac{V_{ref}}{2^M}  
$$

---

### **What you should know for the exam**

- Single-ended ADC measures **relative to ground**.
    
- Understand saturation when:  
    $$  
    V_{in} > V_{ref}  
    $$
    
- Know how the ADC maps voltages to:  
    $$  
    D_{out} = \frac{V_{in}}{V_{ref}}(2^M - 1)  
    $$
    
- Understand how choosing (V_{ref}) affects measurement detail.
    


![[All_slides_nes.pdf#page=97]]  
**Week 3 Slide 24 – Single-Ended ADC: Quantisation Error & Resolution**  

---

### **Core Concepts**

#### **Quantisation**

An ADC converts a continuous voltage into discrete steps.  
This introduces **quantisation error** because real voltages rarely align perfectly with step boundaries.

#### **Voltage Resolution (Q)**

The size of each voltage step is:

$$  
Q = \frac{V_{ref}}{2^M}  
$$

This means the ADC can only represent voltages in increments of (Q).  
Smaller (Q) → finer resolution.

---

### **Examples**

(Using the formula (Q = \frac{V_{ref}}{2^M}))

|Bit Resolution (M)|(V_{ref})|Resolution (Q)|
|---|---|---|
|12-bit|$$5,\text{V}$$|$$1.22,\text{mV}$$|
|12-bit|$$2.5,\text{V}$$|$$0.61,\text{mV}$$|
|8-bit|$$5,\text{V}$$|$$19.5,\text{mV}$$|
|8-bit|$$2.5,\text{V}$$|$$9.7,\text{mV}$$|

---

### **Trade-Off: Range vs Resolution**

Lower (V_{ref}):

- Smaller steps
    
- Better resolution
    
- But smaller measurable range
    

Higher (V_{ref}):

- Larger steps
    
- Worse resolution
    
- Larger measurable range
    

---

### **What you should know for the exam**

- Be able to compute resolution using:  
    $$  
    Q = \frac{V_{ref}}{2^M}  
    $$
    
- Understand why quantisation error occurs.
    
- Recognize the **trade-off** between measurement range and resolution.

![[All_slides_nes.pdf#page=98]]  
**Week 3 Slide 25 – ADC: Range vs Resolution**  

---

### **Problem Setup**

We have an **8-bit ADC** with:

$$  
2^8 = 256 \text{ levels}  
$$

and supply voltage:

$$  
V_{ref} = 5,\text{V}  
$$

Resolution:

$$  
Q = \frac{5}{256} = 19.5,\text{mV}  
$$

---

### **Case 1 — Measuring a signal in ([0,5],\text{V})**

This works normally:

- Entire ADC range is used
    
- Resolution is:
    

$$  
Q = 19.5,\text{mV}  
$$

---

### **Case 2 — Measuring a signal in ([0,1],\text{V})**

With the same (V_{ref} = 5,\text{V}), the ADC cannot represent small voltage differences well:

- Only values:  
    $$  
    D_{out} \in [0,; 52]  
    $$  
    are used, since:  
    $$  
    \frac{1\text{V}}{19.5\text{mV}} \approx 52  
    $$
    

Most of the ADC’s range is **wasted**.  
Resolution is too coarse.

---

### **Fix: Lower the reference voltage**

If we set:

$$  
V_{ref} = 1,\text{V}  
$$

Then:

$$  
Q = \frac{1}{256} = 3.9,\text{mV}  
$$

- Entire ADC range (0 \rightarrow 255) is used
    
- Much finer measurement resolution
    

---

### **What you should know for the exam**

- Resolution depends on both **bit depth** and **(V_{ref})**:  
    $$  
    Q = \frac{V_{ref}}{2^M}  
    $$
    
- Lowering (V_{ref}) **improves resolution** but reduces maximum measurable voltage.
    
- High range → worse resolution; low range → better resolution.

![[All_slides_nes.pdf#page=99]]  
**Week 3 Slide 26 – ADC: Range vs Resolution (Reflecting on the Slide Question)**  

---

### **Slide question:**

**“How can I measure a signal in ([4,5],\text{V}) with resolution (3.9,\text{mV})?”**

---

### **Direct answer (no repetition, just the reasoning the slide implies)**

To achieve a resolution of:

$$  
Q = 3.9,\text{mV}  
$$

you need:

$$  
V_{ref} = 1,\text{V} \quad (\text{for an 8-bit ADC})  
$$

because:

$$  
Q = \frac{1}{256} = 3.9,\text{mV}  
$$

**But:**  
With (V_{ref} = 1,\text{V}), you can only measure:

$$  
0 \le V_{in} \le 1,\text{V}  
$$

so the range ([4,5],\text{V}) is **not directly measurable**.

---

### **The insight the slide wants you to reach**

To measure only the **small variation** inside the 4–5 V window with high resolution, you must:

1. **Remove the 4–5 V DC offset**,
    
2. So that the ADC only sees a small ±0.5 V signal.
    

This turns the desired range:

$$  
[4,;5],\text{V}  
$$

into a centered, narrow range:

$$  
[-0.5,;+0.5],\text{V}  
$$

Then you can set:

$$  
V_{ref} = 0.5,\text{V}  
$$

and achieve:

$$  
Q = \frac{0.5}{256} \approx 2,\text{mV}  
$$

which meets the target resolution.

---

### **What enables this?**

A **differential ADC** (next slide).  
It lets you measure:

$$  
V_{diff} = V_{in} - V_{offset}  
$$

so you can “zoom in” on the small range you care about.

---

### **What you should know for the exam**

- To get high resolution over a small portion of a large voltage range, you must **subtract an offset** so the ADC only processes the small window.
    
- This offset-removal technique is fundamental to using **differential ADC inputs**.
    
- You cannot simply lower (V_{ref}) unless the signal itself is shifted into that smaller measurement window.

![[All_slides_nes.pdf#page=100]]  
**Week 3 Slide 27 – Differential ADC**  

---

### **Core Idea**

A **differential ADC** measures the voltage difference:

$$  
V_{diff} = V_A - V_B  
$$

This difference can be **positive or negative**.

---

### **Measurement Range**

A differential ADC with reference (V_{ref}) measures:

$$

- V_{ref} ;\le; V_{diff} ;\le; +V_{ref}  
    $$
    

Digital output range is:

$$  
D_{out} \in [-2^{M-1},; 2^{M-1}-1]  
$$

---

### **Saturation**

If:

$$  
V_A - V_B > V_{ref}  
$$

then:

$$  
D_{out} = 2^{M-1}-1  
$$

If:

$$  
V_A - V_B < -V_{ref}  
$$

then:

$$  
D_{out} = -2^{M-1}  
$$

---

### **Why differential is useful**

- It naturally removes **common-mode noise** (noise present on both inputs).
    
- It allows you to **subtract an offset voltage**, enabling high-resolution measurement of a small window inside a large voltage range.
    
- This answers the previous slide’s question: a differential ADC can isolate tiny variations by subtracting a fixed reference input.
    

---

### **Examples from the slide**

- $$V_A = 0,, V_B = 5 ;\Rightarrow; V_{diff} = -5 ;\Rightarrow; D_{out} = -2048$$
    
- $$V_A = 5,, V_B = 0 ;\Rightarrow; V_{diff} = +5 ;\Rightarrow; D_{out} = 2047$$
    
- $$V_A = 5,, V_B = 5 ;\Rightarrow; V_{diff} = 0 ;\Rightarrow; D_{out} = 0$$
    
- $$V_A = 3,, V_B = 2 ;\Rightarrow; V_{diff} = 1 ;\Rightarrow; D_{out} = 410$$
    

---

### **What you should know for the exam**

- Differential ADC measures **voltage differences**, not absolute voltages.
    
- Output range includes **positive and negative digital values**.
    
- Differential inputs allow **offset removal** and **noise rejection**.
    
- Understand how saturation works for both positive and negative extremes.

![[All_slides_nes.pdf#page=101]]  
**Week 3 Slide 28 – ADC: Removing a DC Offset**  

---

### **Goal**

Measure a signal in:

$$  
[4,\text{V},;5,\text{V}]  
$$

with high resolution:

$$  
Q = 3.9,\text{mV}  
$$

---

### **Problem**

Using an 8-bit ADC, obtaining (Q = 3.9,\text{mV}) requires:

$$  
V_{ref} = 1,\text{V}  
$$

But then the ADC can only measure:

$$  
0 \le V_{in} \le 1,\text{V}  
$$

so the range 4–5 V is **outside** the measurable window.

---

### **Solution: Subtract a DC Offset**

Apply a fixed offset voltage to the _negative_ ADC input:

$$  
V_B = 4.5,\text{V}  
$$

The differential ADC then measures:

$$  
V_{diff} = V_{in} - 4.5,\text{V}  
$$

This transforms the original range:

- If (V_{in} = 4,\text{V}):  
    $$  
    V_{diff} = -0.5,\text{V}  
    $$
    
- If (V_{in} = 5,\text{V}):  
    $$  
    V_{diff} = +0.5,\text{V}  
    $$
    

So the ADC now only needs to measure:

$$  
[-0.5,\text{V},;+0.5,\text{V}]  
$$

---

### **Choose a New Reference Voltage**

Set:

$$  
V_{ref} = 0.5,\text{V}  
$$

Resolution becomes:

$$  
Q = \frac{0.5}{256} = 1.95,\text{mV}  
$$

(which satisfies the needed precision).

---

### **Concept clarity**

- The ADC is not measuring the _absolute_ voltage anymore.
    
- It is measuring only the **small variations** around 4.5 V.
    
- This is exactly what differential ADCs are designed for.
    

---

### **What you should know for the exam**

- High-resolution measurement of a small voltage window requires **offset removal**.
    
- Differential ADCs allow measuring:  
    $$  
    V_{diff} = V_A - V_B  
    $$
    
- By choosing (V_B) as a fixed offset, the ADC “zooms in” on the small range of interest.
    
- Lowering (V_{ref}) is only useful if the signal is first shifted into the accessible measurement range.


![[All_slides_nes.pdf#page=102]]  
**Week 3 Slide 29 – ADC Channels**  

---

### **Core Idea**

Most MCUs include an internal ADC whose input can be connected to **multiple external pins**, called **ADC channels**.

Only **one channel** can be sampled at a time, even though many channels exist.

---

### **How it works**

- The MCU contains a **single ADC module**.
    
- A **multiplexer (MUX)** selects which external pin is routed to the ADC input.
    
- Example from the slide:
    
    - The nRF52832 has  
        $$  
        \text{AIN0, AIN1, ..., AIN7}  
        $$  
        meaning 8 possible analog inputs.
        
- The MCU switches between them in software, choosing the pin to read.
    

---

### **Why this matters**

- You can measure many analog signals with just **one ADC**.
    
- But because only one channel is active at a time, simultaneous measurements require **fast switching** or **scan mode** (later slide).
    
- Each channel must obey:  
    $$  
    0 \le V_{in} \le V_{ref}  
    $$  
    (or the differential rules if differential mode is supported).
    

---

### **What you should know for the exam**

- An MCU may have multiple **ADC channels**, but usually only **one physical ADC**.
    
- A **multiplexer** selects which channel is read.
    
- Understand that channels do **not** measure simultaneously unless explicitly supported by the architecture.
    
- Know that each channel corresponds to a physical pin that can be connected to external analog signals.

![[All_slides_nes.pdf#page=103]]  
**Week 3 Slide 30 – ADC Modes of Operation**  

---

### **One-Shot Mode**

Takes a **single sample** and stops.

$$  
\text{One measurement} \rightarrow \text{Done}  
$$

Used for slow-changing signals (battery voltage, temperature, configuration inputs).

---

### **Continuous Mode**

ADC samples **repeatedly** at a fixed sampling frequency:

$$  
f_s = \text{samples per second}  
$$

To avoid distortion, sampling must follow **Nyquist’s theorem**:

$$  
f_s \ge 2 f_{\text{max}}  
$$

where (f_{\text{max}}) is the highest frequency component in the input signal.

---

### **Oversampling Mode**

ADC samples **faster** than Nyquist and then averages:

- Reduces noise
    
- Improves effective resolution
    
- Smooths the signal
    

Mathematically, oversampling reduces quantisation noise roughly proportional to:

$$  
\sqrt{N}  
$$

where (N) is the number of samples averaged.

---

### **Scan Mode**

The ADC automatically cycles through multiple channels:

$$  
\text{AIN0} \rightarrow \text{AIN1} \rightarrow \ldots  
$$

This provides **multi-channel monitoring**, though still not simultaneous, just sequential and automatic.

---

### **What you should know for the exam**

- Definitions and use cases of **one-shot**, **continuous**, **oversampling**, and **scan** modes.
    
- Nyquist condition:  
    $$  
    f_s \ge 2 f_{\text{max}}  
    $$
    
- Why oversampling improves signal quality.
    
- Scan mode = automated sampling across multiple ADC channels in sequence.

![[All_slides_nes.pdf#page=104]]  
**Week 3 Slide 31 – Digital-to-Analog Converter (DAC)**  

---

### **Core Idea**

A **DAC** performs the opposite function of an ADC:

$$  
D_{in} ;\longrightarrow; V_{out}  
$$

It converts digital numbers into a **continuous analog voltage**.

---

### **What the DAC actually does**

Given a digital input value (D_{in}) in:

$$  
[0,;2^M - 1]  
$$

the DAC outputs a corresponding voltage:

$$  
V_{out} = \frac{D_{in}}{2^M - 1} , V_{ref}  
$$

This produces a smooth (or stepped) analog signal.

---

### **Applications**

- Audio output (speakers, headphones)
    
- Video generation
    
- Wireless communications (waveform synthesis)
    
- Motor control
    
- Digitally controlled potentiometers
    

Any system where the MCU must **generate a voltage level**, not just read one.

---

### **Concept clarity**

A DAC allows the MCU to produce signals such as ramps, sine waves, control voltages, or adjustable reference levels — things not possible with GPIO alone.

---

### **What you should know for the exam**

- DAC converts **digital → analog**.
    
- Know the output formula:  
    $$  
    V_{out} = \frac{D_{in}}{2^M - 1} , V_{ref}  
    $$
    
- Understand why DACs are essential for producing realistic analog signals.

![[All_slides_nes.pdf#page=105]]  
**Week 3 Slide 32 – Power Control**  

---

### **Core Idea**

We compare how **R1** affects the power delivered to **R2 (the load)** when placed in series.

---

### **Obsidian-Friendly Table Format**

| Case                | Relationship            | Effect on Current (I)              | Effect on Power in R1                   | Effect on Power in R2 (Load)           | Key Insight                    |
| ------------------- | ----------------------- | ---------------------------------- | --------------------------------------- | -------------------------------------- | ------------------------------ |
| **1. R- << R2**     | R1 much smaller than R2 | $$I \approx \frac{V}{R_2}$$        | Very small: $$P_1 = I^2 R_1 \approx 0$$ | Nearly full power delivered            | R1 barely affects the system   |
| **2. (R_1 >> R_2)** | R1 much larger than R2  | $$I \approx \frac{V}{R_1}$$ (tiny) | Very small (low current)                | Very small (load gets almost no power) | R1 blocks almost all power     |
| **3. (R_1 = R_2)**  | Equal resistances       | $$I = \frac{V}{2R_2}$$             | $$P_1 = I^2 R_1$$                       | $$P_2 = I^2 R_2$$                      | Half the power is wasted in R1 |

---

### **Concept clarity**

- Using resistors for power control wastes energy because R1 **converts power into heat**.
    
- Case 3 is especially bad because **the resistor wastes exactly as much power as the load receives**.
    
- This is why MCUs prefer **PWM**, which controls power **without** dissipating wasted energy.
    

---

### **What you should know for the exam**

- The three operating cases and their effects on current and power.
    
- Why resistor-based power control is **inefficient**.
    
- That this inefficiency motivates **PWM** for motor and LED control.

![[All_slides_nes.pdf#page=106]]  
**Week 3 Slide 33 – Dimming an LED**  

---

### **Notes**

- The LED is turned **on and off rapidly** at a frequency high enough that the human eye cannot detect the switching.
    
- The human visual system has **persistence** (a built-in low-pass filter), so it perceives the _average_ brightness rather than the instantaneous on/off state.
    
- By adjusting the **ratio of ON time to OFF time**, we control how bright the LED _appears_, even though the electrical signal is only ever fully ON or fully OFF.
    
- This principle is the foundation for **PWM dimming**.
    

---

### **Obsidian-Friendly Concept Summary**

|Idea|Explanation|
|---|---|
|Human eye filtering|Acts like a low-pass filter, blending fast changes into a smooth perception.|
|LED drive method|LED is not driven with analog voltage—just rapid on/off switching.|
|Perceived brightness|Determined by the fraction of time the LED is ON within each cycle.|

---

### **What you should know for the exam**

- Dimming is achieved through **fast toggling**, not lowering voltage.
    
- The human eye’s **low-pass filtering** makes PWM dimming appear smooth.
    
- The concept prepares for PWM parameters: **frequency** and **duty cycle** (next slide).

![[All_slides_nes.pdf#page=107]]  
**Week 3 Slide 34 – Pulse Width Modulation (PWM)**  

---

### **Notes**

PWM is an **on/off digital signal** defined by two parameters:

#### **1. Frequency**

How many times per second the full ON–OFF cycle repeats:

$$  
f = \frac{1}{T}  
$$

where (T) is the period of one full cycle.

#### **2. Duty Cycle**

The fraction of the period where the signal is **ON**:

$$  
\text{Duty cycle} = \frac{t_{\text{on}}}{T}  
$$

- A higher duty cycle → more average power delivered
    
- A lower duty cycle → less average power
    

The signal itself is always **fully ON (V_S)** or **fully OFF (0 V)**.  
The perceived or effective output is based on the **average** due to low-pass behavior (like the LED dimming from the previous slide).

---

### **Obsidian-Friendly Summary Table**

|Parameter|Meaning|Effect|
|---|---|---|
|**Frequency**|$$f = 1/T$$|Must be high enough to avoid visible flicker or motor chatter|
|**Duty Cycle**|$$DC = t_{on}/T$$|Controls _average_ power delivered|
|**Signal shape**|Digital on/off|Hardware stays efficient (no wasted heat like resistors)|

---

### **What you should know for the exam**

- PWM uses digital switching but achieves **analog-like control** of power.
    
- Frequency sets _how fast_ cycles repeat; duty cycle sets _how strong_ the average output is.
    
- MCU GPIOs can generate PWM directly.
    
- PWM avoids resistor-power waste by using efficient switching rather than voltage reduction.

![[All_slides_nes.pdf#page=108]]  
**Week 3 Slide 35 – PWM Motor Control**  

---

### **Notes**

- The **PWM duty cycle** controls how much **average power** is delivered to the motor.
    
- Motors are **inductive loads**, meaning they do **not** respond instantly to changes in current.
    
    - Instead of following the rapid ON/OFF switching, the motor’s current **smooths out** due to inductance.
        
    - This makes PWM ideal for motor control because the motor experiences a **steady average current**, not choppy pulses.
        

---

### **Why PWM Instead of a Variable Resistor?**

|Method|Problem / Behavior|
|---|---|
|**Variable resistor in series**|Wastes energy as heat; reduces efficiency; limits available power to the motor|
|**PWM**|Nearly zero wasted energy; motor receives the full supply voltage during ON phases; simple to generate with an MCU|

Electrical transistors (e.g., MOSFETs or drivers like DRV8835) act as **switches**, not as analog resistors, making PWM extremely efficient.

---

### **Concept clarity**

- A motor doesn’t care about instantaneous voltage—it reacts to **average current**, which PWM controls elegantly.
    
- PWM allows both **speed control** and **power efficiency**; the motor “filters” the high-frequency switching naturally.
    

---

### **What you should know for the exam**

- Motors are **inductive**, so they average PWM into a smooth current.
    
- PWM avoids the inefficiency of resistor-based control.
    
- Duty cycle directly controls motor speed because it controls **average delivered power**.

---
---
---


Here are **5 multiple-choice questions** covering the full Week 3 slide set.  
(As requested: **no answers provided yet**.)

---

### **Question 1 — GPIO Output Modes**

Which statement about **push-pull vs open-drain** outputs is correct?

A. Push-pull outputs can safely share a line with multiple devices without risk of short circuits.  
B. Open-drain outputs require a pullup resistor to generate a logical ‘1’.  
C. Open-drain outputs actively drive both ‘0’ and ‘1’.  
D. Push-pull outputs can only drive a ‘0’, not a ‘1’.

---

### **Question 2 — ADC Resolution**

A 12-bit ADC with (V_{ref} = 3.3,\text{V}) has a voltage resolution:

A. (Q = \frac{3.3}{4096})  
B. (Q = \frac{3.3}{256})  
C. Always (1,\text{mV}), regardless of (V_{ref})  
D. Equal to the quantisation error of a differential ADC only

---

### **Question 3 — Floating Inputs**

A GPIO pin configured as an input with **no pull resistor** and **no external driver** will:

A. Always read as ‘0’  
B. Always read as ‘1’  
C. Produce undefined readings influenced by noise  
D. Remain in a safe, stable Hi-Z state with a known voltage

---

### **Question 4 — Differential ADC**

A differential ADC measures:

A. The absolute voltage of each input separately  
B. (V_A - V_B), allowing both positive and negative values  
C. Only voltages above (V_{ref})  
D. Only voltages below ground

---

### **Question 5 — PWM**

Which statement about PWM is true?

A. PWM varies the analog voltage level directly using a DAC.  
B. PWM uses resistor networks to control average power efficiently.  
C. Duty cycle determines the average delivered power.  
D. Increasing frequency increases the output voltage amplitude.

---

When you're ready, say **“give answers”** and I will provide the correct choices with explanations.