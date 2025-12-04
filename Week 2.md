![[All_slides_nes.pdf#page=39]]  
**Week 2 Slide 3 – A Wearable Embedded System**  

---

### **Notes**

**Purpose of the slide:**  
This slide shows a **real wearable embedded system** and its **full electronic schematic**, introducing how complex embedded hardware looks in practice.

---

### **Key Points**

#### **1. What a Wearable Embedded System Contains**

- A wearable device is a **self-contained electronic system** designed to be worn on the body.
    
- It typically includes:
    
    - **Sensors** (e.g., accelerometers — visible here as ADXL362 chips)
        
    - **Microcontroller (MCU)** (main brain — CC2650 in this schematic)
        
    - **Power management** (LDOs, DC/DC converters)
        
    - **Wireless communication** (RF antenna + matching network)
        
    - **Memory storage** (flash)
        
    - **User interface parts** (LED, button)
        
    - **Battery and charging circuit** (Qi wireless charging chip shown)
        

This slide provides the **complete schematic** of such a system.

---

### **3. Why This Matters for Exam**

You should understand:

- Embedded systems combine **many different circuit blocks**.
    
- Each block plays a specific role (sensing, computing, power, RF).
    
- Real schematics look complicated, but they follow modular principles.
    

---

### **4. Main Components Identified in the Schematic**

(You do not need to memorize the specific part numbers, but know the categories.)

|Component Type|Example on Schematic|Function|
|---|---|---|
|**MCU**|CC2650|Runs firmware, processes data, handles wireless (BLE)|
|**Sensors**|ADXL362|Measure motion/acceleration|
|**Power Management**|TPS62746, TPS78318|Create stable voltages for components|
|**Charging Circuit**|bq51050b|Wireless charging receiver|
|**Memory**|GD5F1GQ4UAY|Stores firmware/data|
|**RF Section**|Antenna + inductors/capacitors|Enables wireless communication|
|**Passive components**|Capacitors, resistors|Filtering, decoupling, biasing|
|**LED + Button**|D1, S1|User interface|

---

### **5. Important Concept Introduced**

RF = **Radio Frequency**

- These parts handle wireless communication at high frequencies.
    
- They require **special components** (inductors/capacitors) for tuning.
    


![[All_slides_nes.pdf#page=40]]  
**Week 2 Slide 4 – Schematic (or Circuit Diagram)**  

---

### **Notes**

### **1. What a Schematic Is**

- A **schematic** is a _model_ of an electronic circuit.
    
- It uses symbols to represent components and lines to represent electrical connections.
    
- It is **not** a physical layout — it is a **logical diagram**.
    

---

### **2. What an Electronic Circuit Is**

- A circuit is made of **electronic components interconnected in a closed loop**.
    
- A closed loop means current has a complete path to flow.
    

---

### **3. Why Schematics Make Life Easier**

Schematics **abstract** away messy physical details.

They:

- Show each component as a **simple symbol**, reducing visual clutter.
    
- Make the system **easier to read** than a real circuit on a PCB.
    
- Help engineers understand and debug electronic designs.
    
- Provide a clean reference that can be directly translated into PCB layout later.
    

---

### **4. Visual Reference (Image on the Slide)**

The slide includes:

- A physical LED glove circuit.
    
- Its corresponding schematic diagram.
    

This demonstrates how a **complex-looking real circuit** becomes much easier to understand once abstracted into a schematic.

---

### **5. Exam-Relevant Understanding**

You should recognize that:

- Schematic diagrams are fundamental design tools.
    
- They tell you _what connects to what_, not _where it physically is_.
    
- They use **standardized symbols** that all engineers understand.
    

This forms the basis for all circuit analysis and PCB design later in the lecture.

![[All_slides_nes.pdf#page=41]]  
**Week 2 Slide 5 – Basic Concepts**  

---

### **Notes**

### **1. Core Electrical Quantities**

|Quantity|Symbol|Unit|Meaning|
|---|---|---|---|
|**Voltage**|V|Volts (V)|Electric potential difference between two points|
|**Current**|I|Amperes (A)|Flow of electric charge (electrons) through a conductor|
|**Resistance**|R|Ohms (Ω)|How much a component resists the flow of current|

---

### **2. Ohm’s Law**

- **Formula:**                      **I = V / R**
    
- Describes the relationship between:
    
    - **I**: Current
        
    - **V**: Voltage
        
    - **R**: Resistance
        

This law is foundational for all circuit calculations:

- Increase voltage → current increases
    
- Increase resistance → current decreases
    

---

### **3. How This Applies to Circuits**

- Every resistor, wire, or component affects current flow based on its resistance.
    
- Designers use Ohm’s Law to:
    
    - Size resistors properly
        
    - Ensure components receive the correct amount of current
        
    - Diagnose issues like short circuits or power drops
        

---

### **4. Key Insight for Exam**

Expect questions that require:

- Using Ohm’s Law to solve for unknown values.
    
- Understanding how changing V or R affects current.
    
- Interpreting units and relationships between these quantities.

![[All_slides_nes.pdf#page=42]]  
**Week 2 Slide 6 – Electric Power Source**  

---

### **Notes**

### **1. Two Types of Electric Power Sources**

#### **Direct Current (DC)**

- Current flows in **one direction only**.
    
- Example: **Battery**.
    
- Most **embedded systems** require DC because digital electronics need a stable, one-way voltage.
    

#### **Alternating Current (AC)**

- Current **reverses direction periodically**.
    
- Example: **mains electricity** (wall outlet).
    
- AC is good for long-distance distribution but **must be converted** before electronics can use it.
    

---

### **2. Rectifier**

- A rectifier converts **AC → DC**.
    
- Needed when an embedded system is powered from AC mains.
    
- Often found in power adapters and chargers.
    

---

### **3. Key Concept for Embedded Systems**

Embedded devices (microcontrollers, sensors, wireless chips, etc.) cannot run on AC.  
They always need a **DC supply**, typically in the range of:

- 1.8V
    
- 3.3V
    
- 5V
    

So AC from the wall must go through:

1. Transformer + rectifier → produces DC
    
2. Regulators → stabilize the voltage
    

---

### **4. Exam-Relevant Points**

You should know:

- Recognize the difference between **AC** and **DC**.
    
- Understand why embedded systems **cannot** use AC directly.
    
- Understand **rectification** as the process that enables AC-powered devices to run digital circuits

![[All_slides_nes.pdf#page=43]]  
**Week 2 Slide 7 – Voltage Sources**  

---

### **Notes**

### **1. DC Voltage Sources**

- Can come from **batteries** directly.
    
- Or from **AC mains** after rectification (AC → DC).
    

---

### **2. Voltage as a Potential Difference**

- Voltage is always measured **between two points**.
    
- But in practice, we almost always measure it relative to a **common reference** called **ground (GND)**.
    

---

### **3. Ground (GND)**

- A shared reference point for _all_ voltage measurements in the circuit.
    
- Sometimes physically connected to Earth, sometimes not (in battery devices, it usually isn’t).
    
- Allows designers to say “this node is at 3.3V” meaning “3.3V above ground”.
    

---

### **4. Using Labels in Schematics**

As circuits grow more complex:

- Instead of drawing wires everywhere, designers use **labels** such as:
    
    - **Vsource**, **VDD**, **3V3**, **GND**, etc.
        
- Any points with the **same label** are assumed to be **electrically connected**, even if no physical wire is shown on that page.
    

This keeps schematics readable.

---

### **5. Visuals on the Slide**

- Examples of circuits showing voltage sources, resistors, and LEDs.
    
- The diagrams illustrate:
    
    - Voltage measured with respect to ground.
        
    - The convenience of using labels rather than long wires.
        

---

### **6. Exam-Relevant Concepts**

You should be comfortable with:

- What “ground” actually means.
    
- Interpreting voltage labels on schematics.
    
- Understanding that voltage is always relative to something — usually GND.

![[All_slides_nes.pdf#page=44]]  
**Week 2 Slide 8 – Electric Load (Power Consumers)**  

---

### **Notes**

### **1. What Is an Electric Load?**

An **electric load** is _anything in a circuit that consumes electrical energy_.

Examples:

- LEDs (convert electricity → light)
    
- Motors (convert electricity → motion)
    
- Heaters (convert electricity → heat)
    
- Microcontrollers and sensors (convert → internal processing work)
    

---

### **2. Electric Power (P)**

- Defines **how fast** electrical energy is being consumed.
    
- Formula:  
    **P = V × I**
    
    - V = voltage across load
        
    - I = current through load
        
- Units: **Watt (W)**
    

Higher power means:

- More energy used per second.
    
- More heat generated.
    

---

### **3. Electric Energy (E)**

- Total consumed energy over time.
    
- Formula:  
    **E = P × t = V × I × t**
    
- Units: **Joules (J)**  
    (or Watt-hours, Wh, in battery contexts)
    

---

### **4. Why This Matters for Embedded Systems**

- Power consumption determines **battery life**.
    
- Designers must calculate:
    
    - How much current each component draws.
        
    - How long the system can run before the battery drains.
        
    - Whether components need heat dissipation (usually minimal in low-power systems).
        

---

### **5. Exam-Relevant Concepts**

You should be able to:

- Calculate power using P = VI.
    
- Use E = VIt to estimate energy usage.
    
- Recognize examples of electric loads in a circuit.

![[All_slides_nes.pdf#page=45]]  
**Week 2 Slide 9 – Everything Has Resistance**  

---

### **Notes**

### **1. Resistance Exists Everywhere**

Even though schematics simplify things, **all real materials have resistance**.

#### **Fixed Resistors**

- Have a set value (e.g., 1 kΩ, 10 Ω, 1 MΩ).
    
- Available from **0 Ω** (practically a wire) to **hundreds of GΩ** (huge resistance).
    

---

### **2. Insulators**

- Ideal insulators are assumed to have **infinite resistance**.
    
- Reality: insulators like **air** have _very high_ resistance, not infinite.
    
- Extremely tiny currents can still leak through high resistance paths.
    

---

### **3. Conductors**

- Ideal wires are assumed to have **zero resistance**.
    
- Reality: metals like copper still have a **very small resistance**.
    
    - Small enough to ignore in many circuits.
        
    - But not zero → becomes important in high-current or precision designs.
        

---

### **4. Why This Matters**

Understanding real vs. ideal resistance helps you reason about:

- **Voltage drops** on wires.
    
- **Power losses** due to resistance.
    
- Why short circuits produce large currents (wires still have small resistance).
    
- Why insulators can sometimes break down at high voltages.
    

---

### **5. Exam-Relevant Understanding**

Expect to reason about:

- Differences between **ideal** and **real** components.
    
- Why wires are treated as 0 Ω in diagrams.
    
- Why insulators are treated as infinite Ω in diagrams.
    
- But also why, physically, neither is perfectly true.

![[All_slides_nes.pdf#page=46]]  
**Week 2 Slide 10 – Quiz (Current Through Different Resistors)**  

---

### **Notes**

### **1. Purpose of the Slide**

This is a conceptual quiz to test your understanding of **Ohm’s Law** and how **slight resistance differences** affect current.

---

### **2. The Setup**

Two resistor paths:

- **Left:** 1 kΩ
    
- **Right:** 1 kΩ + 0.1% or 1% or 10% more (depending on the example)
    

You apply the **same voltage** across both.

---

### **3. The Key Question**

**Which path draws more current? And how much more?**

Using Ohm’s Law:

- **I = V / R**
    

Smaller resistance → larger current.

So the path with the **lower resistance** always has slightly **higher current**.

---

### **5. Practical Meaning**

In many circuits:

- Small differences in resistance (like from manufacturing tolerance) cause **tiny, often irrelevant** changes in current.
    
- This is why the concept of “**path of least resistance**” doesn’t mean current dramatically prefers one branch—it just shifts slightly.
    

This prepares you for the next slide, which goes deeper into this example.

![[All_slides_nes.pdf#page=47]]  
**Week 2 Slide 11 – “Path of Least Resistance”**  

---
### **1. Purpose of the Slide**

Clarifies a common misconception:  
Current does **not** exclusively choose the lowest-resistance path — it divides **proportionally** based on resistance.

---

### **2. The Setup**

We apply:

- Supply voltage: **1 V**
    
- **Left branch:**  
    $$R_L = 1000\ \Omega$$
    
- **Right branch:** two resistors in parallel:  
    $$R_1 = 1000\ \Omega,\qquad R_2 = 1,000,000\ \Omega$$
    

---

### **3. Equivalent Resistance of the Right Branch**

Parallel resistance formula:

$$  
R_{\text{eq}}=\frac{R_1 R_2}{R_1 + R_2}  
$$

Plugging in:

$$  
R_{\text{eq}}=\frac{1000 \times 1,000,000}{1000 + 1,000,000}  
\approx 999\ \Omega  
$$

---

### **4. Currents Through Each Branch**

Using Ohm’s Law:

Left branch:

$$  
I_L = \frac{V}{R_L} = \frac{1}{1000} = 1.000\ \text{mA}  
$$

Right branch:

$$  
I_R = \frac{V}{R_{\text{eq}}} = \frac{1}{999} \approx 1.001\ \text{mA}  
$$

---

### **5. Interpretation**

- Resistance difference:  
    $$1000\ \Omega \quad \text{vs.} \quad 999\ \Omega$$
    
- Current difference:  
    About **0.1%**
    

So:

- Both branches carry _almost exactly_ the same current.
    
- Current does **not** strongly favor one branch unless resistance differences are large.
    

---

### **6. Exam-Relevant Points**

You should understand:

- How to compute **parallel resistances** using  
    $$R_{\text{eq}}=\frac{R_1 R_2}{R_1+R_2}$$
    
- How current splits based on resistance.
    
- Why “path of least resistance” is an **oversimplification** — the correct concept is **current division**.

![[All_slides_nes.pdf#page=48]]  
**Week 2 Slide 12 – Short Circuit (or short)**  

---
### **1. What Is a Short Circuit?**

A **short circuit** is an (often accidental) connection of **very low or nearly zero resistance** between:

- A **high-voltage node**, and
    
- **Ground** (or a lower-voltage node)
    

This creates an unintended path where current can rush through almost freely.

---

### **2. Theoretical Model**

A perfect short means:

$$  
R_{\text{short}} = 0\ \Omega  
$$

Using Ohm’s Law:

$$  
I = \frac{V}{R}  
$$

Substituting:

$$  
I = \frac{V}{0} \rightarrow \infty  
$$

So mathematically, the current would be **infinite**.

---

### **3. Real-World Reality**

In practice, nothing has truly zero resistance:

- Wires have very small resistance (milliohms).
    
- Batteries have **internal resistance**:
    
    $$R_I > 0$$
    

Therefore:

$$  
I = \frac{V}{R_{\text{short}} + R_I}  
$$

The current is **very large**, but not infinite.  
The limiting factor is usually the **battery or power supply**.

---

### **4. Why Shorts Are Dangerous**

A large current can:

- Burn or damage components
    
- Overheat wires
    
- Destroy ICs (chips)
    
- In high-power systems: start fires or be lethal
    
- In low-power systems: still enough to ruin delicate electronics
    

Even tiny wearable devices can be damaged by a small short.

---

### **5. Key Concept for Embedded Systems**

Short circuits usually occur because of:

- Solder bridges
    
- Miswiring
    
- Damaged insulation
    
- Conductive debris (e.g., metal shavings)
    

Detecting and preventing shorts is a **critical skill** when building prototypes.

---

### **6. Exam-Relevant Understanding**

You must understand:

- Why shorts cause huge currents.
    
- Mathematical ideal vs. real-world behavior.
    
- Role of **internal resistance** of the power source.
    
- Practical consequences of a short in low-power electronics.

![[All_slides_nes.pdf#page=49]]  
**Week 2 Slide 13 – Resistance Can Be Variable**  

---

### **1. Not All Resistance Is Fixed**

Many components have **resistance that changes** depending on:

- Mechanical movement
    
- Temperature
    
- Light level
    
- Frequency
    
- Electrical control signals
    

This makes them extremely useful for sensing and control.

---

### **2. Types of Variable Resistors Introduced**

#### **Potentiometer (mechanically controlled)**

- A knob or slider that changes resistance by moving a **wiper**.
    
- Used for:
    
    - Volume control
        
    - User input
        
    - Adjustable tuning
        

#### **Thermistor (temperature-dependent)**

- Resistance changes with temperature.
    
- Two types:
    
    - **NTC:** resistance ↓ when temperature ↑
        
    - **PTC:** resistance ↑ when temperature ↑
        
- Used in temperature sensing, protection circuits.
    

#### **Photoresistor (light-dependent)**

- Resistance decreases when exposed to more light.
    
- Used to detect ambient light levels.
    

---

### **3. Frequency-Dependent Resistors**

Capacitors and inductors **act like resistors only for AC signals**, where their resistance depends on **frequency**.

This is called **reactance**:

- Capacitive reactance:  
    $$X_C = \frac{1}{2\pi f C}$$  
    (↓ with increasing frequency)
    
- Inductive reactance:  
    $$X_L = 2\pi f L$$  
    (↑ with increasing frequency)
    

These formulas help determine how AC signals behave through these components.

---

### **4. Transistor (electrically controlled resistor)**

A MOSFET’s resistance between its **drain** and **source** terminals:

- Becomes **very small** when gate voltage is high → behaves like a closed switch
    
- Becomes **very large** when gate voltage is low → behaves like an open switch
    

So in many circuits a transistor is essentially a **resistance you can turn on/off with voltage**.

---

### **5. Why This Matters for Embedded Systems**

Variable resistors allow embedded systems to measure or control physical quantities:

- Temperature
    
- Light
    
- Position
    
- User inputs
    
- Signal levels
    

They are the foundation of analog sensing.

---

### **6. Exam-Relevant Points**

You should know:

- Examples of variable resistors.
    
- Their behaviors (mechanical, thermal, optical, AC, electrical control).
    
- Basic formulas for **reactance** (as above).
    
- That these components convert physical changes → electrical resistance changes.

![[All_slides_nes.pdf#page=50]]  
**Week 2 Slide 14 – Voltage Divider**  

---

### **1. What a Voltage Divider Does**

A **voltage divider** takes an input voltage and outputs a **fraction** of it.

It is built using **two resistors in series**.

---

### **2. Voltage Divider Formula**

Given two resistors:

- Top resistor:  
    $$R_1$$
    
- Bottom resistor:  
    $$R_2$$
    

Input voltage at the top:  
$$V_{\text{in}}$$

Output voltage between the two resistors:  
$$V_{\text{out}}$$

The formula is:

$$  
V_{\text{out}}  
= V_{\text{in}} \cdot \frac{R_2}{R_1 + R_2}  
$$

---

### **3. Understanding Attenuation** (dæmpning)

#### **If (R_1 \ll R_2):** R1 << R2

- Very small attenuation
    
- Most of the input voltage “gets through”
    
- Output is close to **Vin**
    

#### **If (R_1 \gg R_2):** R1 >> R2

- Large attenuation
    
- Only a small portion of Vin becomes Vout
    
- Output is much **smaller**
    

---

### **4. Where Voltage Dividers Are Used**

- Adjust a signal to a lower voltage that another device can safely read
    
- Convert larger voltage ranges to smaller ranges for ADCs
    
- Create reference voltages
    
- Light sensing (photoresistor circuits)
    
- Temperature sensing (thermistor circuits)
    

---

### **5. Important Limitations**

Voltage dividers **do not work well** when the output is loaded heavily.  
If a device connected to Vout draws current, the formula changes.

This is why voltage dividers are good for **signals**, but not for powering loads.

---

### **6. Exam-Relevant Concepts**

Understand:

- The formula
    
- When a divider attenuates a lot vs. a little
    
- Typical use cases
    
- Why loading affects accuracy

![[All_slides_nes.pdf#page=51]]  
**Week 2 Slide 15 – Level Shifter**  

---

### **1. Purpose of a Level Shifter**

A **level shifter** safely connects two digital devices that use **different logic voltage levels**.

Example scenario:

- Device A outputs logic “1” as **5 V**
    
- Device B expects a maximum of **3.3 V** on its inputs
    

Direct connection would **damage** the 3.3 V device.

A level shifter solves this by **reducing the voltage** of the signal before it reaches the lower-voltage device.

---

### **2. Why This Is Necessary in Embedded Systems**

Different components operate at different supply voltages:

- Microcontroller at 3.3 V
    
- Sensor module at 1.8 V
    
- Legacy device at 5 V
    

Without voltage shifting:

- Inputs can be destroyed
    
- Chips can latch up or behave unpredictably
    
- Communication becomes unreliable
    

---

### **3. How a Level Shifter Typically Works**

Common approaches:

- **Resistive voltage divider** (simple but only works in one direction and slows signals)
    
- **MOSFET-based bidirectional level shifter** (common for I²C, UART)
    
- **Dedicated IC level shifters** (fast, reliable, multi-channel)
    

The slide shows a resistive divider example:  
**Two resistors reduce a 5 V high level to a safe 3.3 V.**

---

### **4. Key Requirement**

The receiving device must **never** see a voltage higher than its supply voltage.  
Exceeding this often destroys input protection diodes or internal transistors.

---

### **5. Exam-Relevant Understanding**

You should know:

- What problem a level shifter solves
    
- What happens if you don’t use one
    
- Common ways to implement it (resistors, MOSFETs, ICs)
    
- That logic “1” has different meanings depending on the voltage domain

![[All_slides_nes.pdf#page=52]]  
**Week 2 Slide 16 – Volume Control (Potentiometer as Variable Attenuator)**  

---

### **1. How a Potentiometer Works**

A **potentiometer (pot)** is a mechanically adjustable resistor with:

- Two end terminals (full resistor)
    
- One **wiper** terminal that moves along the resistive track
    

By turning the knob, you change the ratio between the two parts of the resistor.

---

### **2. Using It as a Volume Control**

When wired as a **voltage divider**:

- Input audio signal goes across the full resistor
    
- The wiper outputs a fraction of that signal
    
- Turning the knob changes attenuation of the signal → **volume up/down**
    

This is exactly the same principle as the earlier voltage divider slide, but now **continuously adjustable**.

---

### **3. Using It for User Input**

If the wiper is connected to an ADC (Analog-to-Digital Converter):

- ADC reads a voltage proportional to the wiper position
    
- Software interprets this as a number
    
- Effectively gives the user an analog input control (e.g., sliders, knobs)
    

The output voltage is:

$$  
V_{\text{out}}  
= V_{\text{in}} \cdot \frac{R_{\text{bottom}}}{R_{\text{top}} + R_{\text{bottom}}}  
$$

where the ratio changes as the knob is turned.

---

### **4. Key Concept**

A potentiometer splits a resistor into two parts:

- **Top section:**  
    $$R_{\text{top}}$$
    
- **Bottom section:**  
    $$R_{\text{bottom}}$$
    

and the ratio is determined by mechanical movement.

---

### **5. Why This Matters in Embedded Systems**

Potentiometers are extremely common in:

- User interfaces
    
- Trimming/adjustments of analog circuits
    
- Sensor calibration
    
- Volume, contrast, brightness controls
    

They provide a **simple, intuitive** way for a user to set a variable level without digital complexity.

---

### **6. Exam-Relevant Understanding**

You should know:

- Potentiometer structure (two fixed ends + wiper)
    
- How it forms a variable voltage divider
    
- How ADCs read analog positions
    
- Use cases in both audio and general embedded input systems

![[All_slides_nes.pdf#page=53]]  
**Week 2 Slide 17 – Temperature Sensor (Thermistor-Based Measurement)**  

---

### **1. Embedded Systems Measure Voltage, Not Resistance**

A microcontroller cannot directly read “resistance.”  
It can only measure **voltage** using an ADC.

Therefore, to read a thermistor (whose resistance changes with temperature), we place it in a **voltage divider** so the changing resistance creates a changing **voltage**.

---

### **2. What the Slide Shows**

The figure displays:

- A **fixed resistor** at the top (labeled R₁)
    
- A **thermistor** at the bottom (labeled R₂)
    
- The output voltage taken between them
    
- A supply voltage feeding the divider
    

This is the standard thermistor measurement circuit.

---

### **3. How the Circuit Works**

- R₂ is the **thermistor**, whose resistance changes with temperature.
    
- R₁ is a **fixed resistor**, chosen to match the expected range of the thermistor.
    

As temperature changes:

- R₂ changes
    
- That changes the ratio between R₁ and R₂
    
- And that changes the output voltage the ADC reads
    


---

### **4. Behavior of an NTC Thermistor**

Most thermistors used in embedded systems are **NTC** (Negative Temperature Coefficient):

- When temperature **increases** → resistance **decreases**
    
- When temperature **decreases** → resistance **increases**
    

The voltage divider converts these resistance shifts into voltage shifts.

---

### **5. Why This Works in Practice**

The ADC reads the output voltage and converts it into a number.  
Software then maps that number to a temperature using:

- A lookup table, or
    
- A curve-fit equation (e.g., Steinhart–Hart)
    

This is how simple, low-cost temperature sensing is done.

---

### **6. Exam-Relevant Understanding**

Be sure you understand:

- Why a thermistor must be placed in a voltage divider
    
- That the _voltage_ (not resistance) is what the ADC measures
    
- The relationship between temperature and resistance for an NTC thermistor
    
- How the divider outputs a temperature-dependent voltage

![[All_slides_nes.pdf#page=54]]  
**Week 2 Slide 18 – Capacitors**  

---

### **1. What Capacitors Do**

A capacitor **stores electrical energy** in an electric field between two conductive plates separated by an insulator.

Key behaviors:

- Can **store and release** energy → acts like a tiny temporary power source.
    
- Acts differently for **DC** and **AC** signals.
    

---

### **2. Capacitors and DC**

- Capacitors **block DC** once fully charged.  
    After charging, no current flows through (in steady state).
    
- This makes them useful for:
    
    - Filtering out DC components
        
    - Coupling AC signals between stages
        

---

### **3. Capacitors and AC**

Capacitors **allow AC** to pass, and the ease with which AC flows depends on the signal frequency.

Important idea on the slide:

- High-frequency signals “see” the capacitor as having **low impedance** → pass through easier
    
- Low-frequency signals “see” **high impedance** → are attenuated
    

This property is why capacitors behave like **frequency-dependent resistors**.

---

### **4. RC Low-Pass Filter (Shown in the Figure)**

The slide shows a classic **RC low-pass filter**:

- A resistor in series
    
- A capacitor to ground
    

How it works:

- High frequencies: strongly attenuated (the capacitor shunts them to ground)
    
- Low frequencies: mostly passed through
    

This is used everywhere in embedded systems to smooth signals, remove noise, or stabilize sensor readings.

---

### **5. Practical Uses in Embedded Systems**

Capacitors are used for:

- Power supply smoothing (removing noise)
    
- Decoupling high-frequency spikes
    
- Signal filtering
    
- Timing circuits (RC delays)
    
- AC coupling between stages
    

You will see them constantly around microcontrollers, power regulators, and sensor inputs.

---

### **6. Exam-Relevant Understanding**

You should know:

- Capacitors block DC but allow AC
    
- Their “resistance” depends on frequency (called **impedance**)
    
- High frequencies pass more easily
    
- Basics of the RC low-pass filter and why it attenuates high-frequency signals


![[All_slides_nes.pdf#page=55]]  
**Week 2 Slide 19 – Batteries Are Imperfect Power Sources**  

---

### **1. Real Batteries Have Internal Resistance**

The slide shows a battery modeled as:

- An ideal voltage source **V**
    
- A small internal resistor **Rᵢ** in series
    

This resistor is not shown on physical batteries, but it **always exists**.

As a battery ages or discharges:

- **Rᵢ increases**
    
- This makes the battery perform worse under load
    

---

### **2. Voltage Drop Caused by Internal Resistance**

Whenever the system draws current **I**, the internal resistance creates its own voltage drop:

- Voltage drop inside the battery:  
    $$ \text{(conceptually)} V_{\text{drop}} = I \cdot R_i $$
    

Because of this:

- The voltage that actually reaches the system (**Vₛ**) is **less** than the battery’s rated voltage.
    

The slide illustrates this using:

- **Low current → small voltage drop → OK**
    
- **High current → large voltage drop → problematic**
    

---

### **3. Why This Is Dangerous for Embedded Systems**

Embedded systems have a **minimum operating voltage**.  
If Vₛ (the voltage after Rᵢ) drops below that threshold:

- The microcontroller may reset
    
- The system may malfunction
    
- Memory operations may fail
    
- Sensors can behave unpredictably
    

Even a short burst of high current (e.g., radio transmission, LED flash, motor start) can temporarily pull the voltage down.

---

### **4. Real-World Example**

A wearable device might run fine until the radio transmits using a high-current spike.  
The internal resistance of the nearly depleted battery causes a big voltage drop → the MCU crashes.

This is extremely common in battery-powered systems.

---

### **5. Why Understanding This Matters**

Designers must:

- Account for high-current peaks
    
- Add **decoupling capacitors** (next slide covers this)
    
- Ensure the battery can supply the peak current
    
- Avoid operating the battery too close to its depletion point
    

---

### **6. Exam-Relevant Understanding**

Know:

- That batteries are modeled as “ideal voltage source + internal resistance”
    
- Higher current → larger internal voltage drop
    
- Why high current spikes can **reset or crash** embedded systems
    
- Why internal resistance increases as batteries age or discharge

![[All_slides_nes.pdf#page=56]]  
**Week 2 Slide 20 – Decoupling Capacitors**  

---

### **1. What Decoupling Capacitors Are**

Decoupling capacitors are **small capacitors placed physically very close** to IC (integrated circuit) power pins.

Their purpose:  
To act as a tiny **local energy reservoir** that smooths and stabilizes the supply voltage.

---

### **2. Why They Are Needed**

Embedded systems often have:

- Sudden current spikes
    
- Switching noise
    
- Fast digital transitions
    

These cause **momentary voltage drops** or **noise** on the supply line.

Without decoupling capacitors:

- Microcontrollers can reset
    
- Sensors can behave incorrectly
    
- Wireless modules can malfunction
    

---

### **3. How They Work (as shown in the figure)**

The slide illustrates:

- A battery with internal resistance
    
- An IC that draws fast-changing current
    
- A capacitor placed **in parallel**, right next to the IC
    

What happens:

- When voltage suddenly dips, the capacitor **discharges**, supplying current instantly
    
- When voltage suddenly rises, the capacitor **absorbs** the excess energy
    
- High-frequency noise is filtered out because capacitors pass high-frequency components to ground
    

This keeps the IC’s supply voltage stable.

---

### **4. Key Behavioral Points**

- Capacitors oppose rapid voltage changes.
    
- Closer placement = better performance (shorter trace → lower inductance).
    
- Often multiple values are placed together (e.g., 100 nF + 1 µF) to cover different frequency ranges.
    

---

### **5. Typical Use**

You will typically find:

- **One 100 nF capacitor per power pin** of a microcontroller
    
- Additional bulk capacitors (1–10 µF) for larger current dips
    

This is standard PCB design practice.

---

### **6. Exam-Relevant Understanding**

You should know:

- Why decoupling capacitors are used
    
- How they stabilize supply voltage during noise or current spikes
    
- Why they must be placed close to the IC
    
- That they act as a short-term local energy buffer

![[All_slides_nes.pdf#page=57]]  
**Week 2 Slide 21 – Switches and Buttons**  

---

### **1. What Switches and Buttons Do**

Both switches and buttons are **mechanical devices** that physically **open or close a circuit**.

Their purpose is to let a user control whether current can flow.

---

### **2. Difference Between a Switch and a Button**

|Device|Behavior|Example Use|
|---|---|---|
|**Switch**|Stays in its position (open or closed)|Power switch, mode selector|
|**Button**|Only closed **while pressed**|Reset button, user input|

The slide shows a simple push button symbol (momentary contact).

---

### **3. Electrical Behavior**

- **Open** → no current can flow (infinite resistance)
    
- **Closed** → current flows freely (near-zero resistance)
    

This is the most basic form of digital input to an embedded system.

---

### **4. Real-World Notes**

- Mechanical contacts can “bounce” (rapid open/close transitions) → software often needs **debouncing**.
    
- Buttons are extremely common for resets, configuration, and user input.
    

---

### **5. Exam-Relevant Understanding**

You should know:

- The conceptual difference between switches and buttons
    
- That they physically open/close the circuit
    
- Why buttons are momentary while switches are latching


![[All_slides_nes.pdf#page=58]]  
**Week 2 Slide 22 – Detecting When a Button Is Pushed**  

---

### **1. Embedded Systems Measure Voltage, Not “Pressed/Not Pressed”**

A microcontroller cannot directly sense whether a button is physically pressed.  
It can only sense a **voltage level** on an input pin.

So the button must be wired in a way that pressing it changes the voltage.

---

### **2. How the Circuit Works (as shown in the slide)**

The slide shows a simple pull-up configuration:

#### **When the button is _not pressed_:**

- The circuit is **open**, meaning no current flows.
    
- Since no current flows through the resistor, there is **no voltage drop** across it.
    
- Therefore, the output node is pulled up to the supply voltage (**Vₛ**).
    
- Microcontroller reads **logic HIGH**.
    

#### **When the button is _pressed_:**

- The button **closes the circuit** and creates a direct path to ground.
    
- Current flows through the resistor to ground.
    
- The output node is now connected to **0 V**.
    
- Microcontroller reads **logic LOW**.
    

This is known as a **pull-up resistor** configuration.

---

### **3. Why You Need the Resistor**

The resistor prevents a **short circuit** between Vₛ and ground when the button is pressed.

- Without it, pressing the button would connect Vₛ → GND directly → dangerous current spike.
    

---

### **4. Common Implementation**

This is one of the most common digital input circuits in all embedded systems:

- Microcontroller input pin
    
- Resistor to supply voltage (pull-up)
    
- Button to ground
    

Microcontrollers often include **internal pull-up resistors**, so the external resistor may not be needed.

---

### **5. Exam-Relevant Understanding**

You should know:

- Why the button must be combined with a resistor
    
- How pressing/releasing affects voltage at the MCU pin
    
- Difference between **pull-up** and **pull-down** configurations
    
- Why this method avoids undefined or floating input states
![[All_slides_nes.pdf#page=59]]  
**Week 2 Slide 23 – Transistor (MOSFET) as a Switch**  

---

### **1. Purpose of the Slide**

This slide introduces how a **MOSFET transistor** can act as an **electronically controlled switch**, replacing a mechanical button.

This is essential in embedded systems when you want the microcontroller to turn something **on or off** electronically.

---

### **2. How a MOSFET Works (Conceptually)**

A MOSFET has three terminals:

- **Gate (G)** – control input
    
- **Drain (D)** – one side of the controlled path
    
- **Source (S)** – the other side
    

The key idea:

- The **gate voltage** controls the **resistance** between drain and source.
    

---

### **3. Two Operating States (as shown in the slide)**

#### **1. Gate = Vₛ (high)**

- MOSFET turns **on**
    
- Drain–source resistance becomes **very small**
    
- Behaves like a **closed switch**
    
- Current flows through the load → the load receives power
    

#### **2. Gate = 0 V (low)**

- MOSFET turns **off**
    
- Drain–source resistance becomes **very large**
    
- Behaves like an **open switch**
    
- No current flows → the load receives **no power**
    

This is exactly how you switch LEDs, motors, sensors, radios, etc.

---

### **4. Why We Use MOSFETs Instead of Mechanical Switches**

- **No moving parts** → highly reliable
    
- **Controlled by logic voltage** from the microcontroller
    
- Can switch **large currents** safely
    
- Can be switched **thousands of times per second** (or more)
    

Microcontrollers use MOSFETs to control devices that require more current than a GPIO pin can supply.

---

### **5. Real-World Embedded Example**

A microcontroller sets a GPIO pin HIGH → MOSFET turns ON → powers a motor/LED/transmitter.  
Set GPIO LOW → MOSFET turns OFF → cuts power.

This is power gating.

---

### **6. Exam-Relevant Understanding**

You should know:

- MOSFET is an electrically controlled switch
    
- Gate voltage controls whether the load receives power
    
- High at gate = switch closed (load on)
    
- Low at gate = switch open (load off)
    
- Why MOSFETs are preferred for electronic switching

![[All_slides_nes.pdf#page=60]]  
**Week 2 Slide 24 – Diodes and LEDs**  

---

### **1. What a Diode Does**

A **diode** is a component that allows current to flow in **one direction only**.

Ideal behavior:

- **Forward direction:** zero resistance
    
- **Reverse direction:** infinite resistance
    

Real behavior:

- Still one-way, but with imperfections.
    

---

### **2. Forward Voltage Drop**

When current flows through a diode in the correct direction, it has a **voltage drop** across it.  
This drop depends on diode type:

- Silicon diode: ~0.7 V
    
- LED: typically 1.8–3.3 V depending on color
    

This is why diodes consume power when conducting.

---

### **3. LEDs Are Just Light-Emitting Diodes**

An LED behaves like a diode but:

- Emits **light** when forward-biased
    
- Has a specific forward voltage depending on color/material
    

Since LEDs allow current in only one direction, they must be oriented correctly.

---

### **4. Why You Need a Series Resistor**

LEDs are very sensitive to excessive current.  
A resistor is placed in series to limit the current to a safe value.

Without it:

- The LED would draw too much current
    
- It could be destroyed within milliseconds
    

This resistor ensures the current stays in the intended safe operating range.

---

### **5. What the Slide’s Diagram Shows**

- A diode symbol indicating directionality
    
- An LED with a resistor in series
    
- Demonstrates that the resistor sets the maximum current through the LED
    

---

### **6. Exam-Relevant Understanding**

You should know:

- Diodes conduct one way and block the other
    
- LEDs are diodes that emit light
    
- There is always a forward voltage drop
    
- A series resistor is required to protect LEDs from overcurrent
- 
![[All_slides_nes.pdf#page=61]]  
**Week 2 Slide 25 – Reverse Voltage Protection**  

---

### **1. Purpose of Reverse Voltage Protection**

If a user accidentally connects a battery **backwards**, the entire system could be damaged instantly.  
Reverse voltage protection prevents this by using a **diode** that only allows current to flow when the battery is connected correctly.

---

### **2. How the Circuit Works (as shown on the slide)**

#### **When the battery is connected correctly:**

- The diode is **forward-biased**.
    
- Current flows normally into the circuit.
    
- The system receives power and works as expected.
    

#### **When the battery is connected backwards:**

- The diode becomes **reverse-biased**.
    
- It blocks current completely.
    
- The system receives **no power**, but is **safe** from damage.
    

---

### **3. Why This Works**

Diodes inherently block current in the reverse direction.  
This simple behavior prevents:

- Overcurrent
    
- Component burnout
    
- Reverse polarity damage to ICs and regulators
    

Even a moment of reverse connection can destroy sensitive electronics, so this protection is very common.

---

### **4. Practical Considerations**

- The diode must handle the system’s maximum current.
    
- Because diodes have a forward voltage drop, they waste a small amount of power (typically ~0.2–0.7 V).
    
- To minimize this drop, designers often use **Schottky diodes** (lower forward drop).
    

More advanced designs sometimes use MOSFET-based ideal diodes to reduce the drop further.

---

### **5. Exam-Relevant Understanding**

You should know:

- What reverse polarity means
    
- Why a diode prevents damage
    
- How the diode’s orientation determines whether current can flow
    
- That this is a **common and simple protective technique** in embedded hardware

![[All_slides_nes.pdf#page=62]]  
**Week 2 Slide 26 – PCB Prototyping**  

---

### **1. Why Prototyping Is Important**

Before designing a full **Printed Circuit Board (PCB)**, it is often necessary to **prototype the circuit** or certain subsystems.  
This helps verify:

- That the circuit works as intended
    
- That component choices are correct
    
- That software/hardware interaction is stable
    

Prototyping avoids costly PCB redesigns.

---

### **2. Three Prototyping Tools Shown on the Slide**

#### **1. Breadboard**

- No soldering required
    
- Components and wires plug in easily
    
- Best for quick experiments and low-frequency circuits
    
- Not suitable for high-speed signals or RF
    

#### **2. Veroboard (Stripboard)**

- Copper strips on a board
    
- Requires soldering
    
- More permanent than a breadboard
    
- Good for small custom circuits or early prototypes
    

#### **3. Breakout Boards**

- Small PCBs that “break out” tiny IC pins into a usable pin header
    
- Essential for chips that are too small to be used on a breadboard
    
- Common for sensors, regulators, accelerometers, wireless modules
    

Breakout boards are extremely important because modern components are rarely available in breadboard-friendly packages.

---

### **3. Why This Matters for Embedded Systems**

Prototyping:

- Saves time
    
- Avoids manufacturing errors
    
- Enables testing before committing to a full PCB design
    
- Makes debugging much easier
    

---

### **4. Exam-Relevant Understanding**

You should know:

- The differences between breadboard, veroboard, and breakout boards
    
- Why breakout boards exist
    
- Why prototyping is done before PCB design
![[All_slides_nes.pdf#page=63]]  
**Week 2 Slide 27 – PCB Design**  

---

### **1. What a PCB Is**

A **Printed Circuit Board (PCB)** is a rigid board with **copper tracks** printed on its surface (or internal layers).  
These tracks replace wires and electrically connect components.

A PCB includes:

- **Copper traces** (electrical connections)
    
- **Pads** (where components are soldered)
    
- **Substrate material** (such as FR4 fiberglass)
    

---

### **2. Why PCBs Are Used**

Compared to hand-wired circuits:

- PCBs are **smaller**
    
- **More reliable**
    
- **Reproducible**
    
- Support **high-speed**, **low-noise**, and **dense** designs
    

All modern embedded systems use PCBs.

---

### **3. PCB Design Tools**

PCB design is done with specialized software called:

- **Electronic Design Automation (EDA)** or
    
- **Electronic Computer-Aided Design (ECAD)** tools
    

Examples commonly used in academia/industry:

- Altium Designer
    
- KiCad
    
- Eagle
    
- OrCAD
    
- EasyEDA
    

These tools handle schematics, component placement, routing, and manufacturing outputs.

---

### **4. What the Slide Shows**

Images illustrating:

- Copper traces on a PCB
    
- A PCB layout example with components and routing
    
- Demonstrating how physical design corresponds to schematic connections
    

---

### **5. Exam-Relevant Understanding**

You should know:

- What a PCB is
    
- Why PCBs are essential for embedded systems
    
- That ECAD tools are used to design them
    
- How PCB layout represents physical implementation of the schematic

![[All_slides_nes.pdf#page=64]]  
**Week 2 Slide 28 – PCB Design: Schematic**  

---

### **1. First Step of PCB Design: Build the Schematic**

Before laying out the physical board, you must create a **schematic diagram** of the entire circuit.

This step includes:

- Identifying **key components** (MCU, sensors, regulators, connectors, etc.)
    
- Identifying the **power source** and voltage levels
    
- Ensuring all components are **electrically compatible**
    

---

### **2. Using Reference Circuits**

Many components (especially ICs) provide:

- **Datasheet-recommended circuits**
    
- **Example applications**
    
- **Required passive components** (e.g., a 100 nF decoupling capacitor)
    

Designers often:

- Reuse values from reference designs
    
- Borrow circuits from **open hardware** examples  
    This reduces mistakes and speeds up development.
    

---

### **3. Creating a Schematic Symbol**

Every component must have a schematic symbol that matches:

- The **pin numbers**
    
- The **pin functions**
    

Example in the slide:

- A portion of the **ADXL362 accelerometer** datasheet
    
- Showing pinouts and how they translate into a schematic symbol
    

This ensures the PCB routing will match the real-world chip pin positions.

---

### **4. Why This Step Matters**

If the schematic is wrong:

- The PCB will be wrong
    
- The board may be unusable
    
- Redesigns cost time and money
    

The schematic is the **logical blueprint** of the circuit.

---

### **5. Exam-Relevant Understanding**

You should know:

- Why schematics come before layout
    
- Why datasheet pin information must match the schematic symbol
    
- Why passive components are often chosen based on reference designs
    
- The importance of identifying power sources and voltage levels early
Below is a clean table for all **ADXL362 pins shown in the slide’s figure** (Slide 28).  
This table maps **pin names → function/purpose**, based on the diagram in the slide.  

---

# **ADXL362 Pin Table (Slide Figure Breakdown)**

|**Pin Name**|**Type**|**Meaning / Function**|
|---|---|---|
|**VDDIO**|Power|I/O supply voltage (logic level power for digital pins)|
|**VS**|Power|Main analog/digital supply voltage for the sensor core|
|**GND**|Power|Ground reference (multiple GND pins for noise reduction)|
|**SCLK**|Digital Input|SPI clock input — driven by MCU|
|**MOSI**|Digital Input|SPI data input (Master Out, Slave In)|
|**MISO**|Digital Output|SPI data output (Master In, Slave Out)|
|**CS**|Digital Input|Chip Select for SPI (active low)|
|**INT1**|Digital Output|Interrupt output #1 — sensor event notification|
|**INT2**|Digital Output|Interrupt output #2 — programmable events/wakeup|
|**RSVD**|—|Reserved pins (must not be connected / follow datasheet)|
|**NC**|—|Not connected internally — leave floating|
|**DIO_XX**|Digital I/O|General-purpose digital I/O from main system (MCU connections)|
|**100 nF capacitor pins**|Passive|Decoupling capacitor for local power stability|

**Note:**  
The slide shows **two ADXL362 chips**, both using the same pin naming and functions.

---

# **Grouped Explanation (Easier for Exam Use)**

### **1. Power Pins**

|Pins|Purpose|
|---|---|
|VDDIO|Logic I/O voltage|
|VS|Core supply voltage|
|GND (multiple)|Ground reference|

Multiple grounds help reduce noise because accelerometers are sensitive analog devices.

---

### **2. SPI Communication Pins**

|Pin|Direction|Purpose|
|---|---|---|
|SCLK|Input|SPI clock|
|MOSI|Input|MCU → ADXL362 data|
|MISO|Output|ADXL362 → MCU data|
|CS|Input|Chip select to activate the device|

This is a standard **4-wire SPI interface**.

---

### **3. Interrupt Pins**

|Pin|Purpose|
|---|---|
|INT1|Programmable interrupt (motion detect, activity, etc.)|
|INT2|Second interrupt (activity, inactivity, FIFO events, etc.)|

These allow the sensor to wake the MCU from sleep to save power.

---

### **4. Reserved & NC Pins**

|Pin Type|Meaning|
|---|---|
|RSVD|Must follow datasheet — often used internally, not user-accessible|
|NC|Not connected — leave floating|

Important: **Never connect RSVD to other signals unless the datasheet says so.**

---

### **5. Related Passives**

|Component|Purpose|
|---|---|
|C13, C19 (100 nF caps)|Decoupling capacitors to stabilize power for each ADXL362|

![[All_slides_nes.pdf#page=65]]  
**Week 2 Slide 29 – PCB Design: Component Layout**  

---

### **1. Purpose of This Stage**

After drawing the schematic, the next PCB design step is creating the **physical footprint** for each component.  
A footprint defines:

- The pad shapes
    
- Pad spacing
    
- Component outline
    
- Orientation
    
- Exact physical dimensions
    

This ensures the component can be soldered correctly on the PCB.

---

### **2. What the Slide Shows**

#### **Top image: ADXL362 footprint diagram**

- Shows exact pad layout from the datasheet
    
- Dimensions are given in **millimeters**
    
- Includes top-down and side views
    
- Highlights that designers must match **pin numbers** to the correct pads
    

#### **Bottom image: Standard SMD resistor/capacitor packages**

- Shows common package sizes such as:
    
    - **0402** (0.04" × 0.02")
        
    - **0603**
        
    - **0805**
        
- Demonstrates the difference between **imperial** and **metric** sizing systems
    

This explains why physical size matters in PCB layout.

---

### **3. Critical Point: Top vs. Bottom Views**

The slide emphasizes:

- Datasheets often show the **bottom view**
    
- When placing a footprint on the PCB, the view is effectively **mirrored**
    
- Misinterpreting this leads to **reversed pin assignments**, which can destroy the board
    

This is a common beginner mistake.

---

### **4. Why Footprints Matter**

If the footprint is wrong:

- The component cannot be soldered
    
- Pads won't align with the real pins
    
- The board may be unusable
    
- Re-spinning the PCB costs time and money
    

Footprint accuracy is just as important as the schematic.

---

### **5. Importance of Standard Passive Sizes**

Typical SMD sizes:

- Smaller packages (0402, 0201) allow compact layouts but are harder to solder
    
- Larger packages (0603, 0805) are easier to hand-assemble
    
- Passive parts follow standardized dimensions, making layout faster
    

Knowing package sizes helps estimate:

- Space requirements
    
- Solderability
    
- PCB density
    

---

### **6. Exam-Relevant Understanding**

You should know:

- What a component footprint is
    
- Why datasheet dimensions must be matched exactly
    
- The meaning of package sizes like 0402 / 0603
    
- The issue of top vs. bottom views (mirroring)
    
- Why footprints are a critical step before routing the PCB

![[All_slides_nes.pdf#page=66]]  
**Week 2 Slide 30 – PCB Design: Board Layout**  

---

### **1. What Board Layout Is**

Board layout is the step where you:

- Place each component footprint on the actual PCB
    
- Draw copper traces to connect them
    
- Define how signals travel across layers
    

This is the **physical implementation** of your schematic.

---

### **2. Layers in a PCB (as shown in the slide)**

The slide mentions multiple copper layers:

#### **1. Top Layer**

- Components usually placed here
    
- Contains copper traces
    

#### **2. Bottom Layer**

- Also supports components and traces
    
- Often used for routing when top is crowded
    

#### **3. Internal Layers (for multi-layer PCBs)**

- Dedicated to power distribution (e.g., 3.3V plane)
    
- Dedicated to ground (ground plane)
    
- Used for routing high-density signals
    

More layers = more routing flexibility but higher cost.

---

### **3. Vias (Vertical Electrical Connections)**

The slide defines three types:

|Via Type|What It Connects|Use Case|
|---|---|---|
|**Through-hole via**|Top → bottom|Most common; cheapest|
|**Blind via**|Top → internal OR bottom → internal|Saves space; more complex|
|**Buried via**|Internal → internal|For dense PCBs; most expensive|

Vias are essential for connecting traces on different layers.

---

### **4. Ground Plane / Ground Layer**

A **ground plane** is a large copper area connected to ground.

Benefits:

- Reduces noise by providing a stable reference
    
- Improves electromagnetic interference (EMI) performance
    
- Helps with heat dissipation
    
- Simplifies routing by allowing easy grounding
    

Most embedded boards use a **continuous ground plane** for signal integrity.

---

### **5. What the Slide Images Represent**

- A 3D depiction of multi-layer PCB stack-up
    
- Examples of vias connecting different layers
    
- A real PCB showing traces, pads, and copper areas
    

These visuals help understand how signals move **inside** the PCB, not only on the surface.

---

### **6. Exam-Relevant Understanding**

You should know:

- Difference between top, bottom, and internal layers
    
- What vias do and the differences between via types
    
- Purpose of a ground plane
    
- That board layout is the step where schematic connections become real physical routing

![[All_slides_nes.pdf#page=67]]  
**Week 2 Slide 31 – PCB Design: Bill of Materials (BOM)**  

---

### **1. What a BOM Is**

A **Bill of Materials (BOM)** is essentially a **shopping list** for all the components required to build the PCB.

It includes:

- Part names / types
    
- Manufacturer part numbers
    
- Quantities
    
- Supplier information
    
- Cost (sometimes)
    

This document allows a manufacturer or assembly house to order exactly the correct parts.

---

### **2. What the Slide Shows**

The slide includes a typical spreadsheet-style BOM, with columns for:

- **Item number**
    
- **Description**
    
- **Manufacturer**
    
- **Part number**
    
- **Quantity**
    
- **Package type**
    
- **Comments / notes**
    

This is the standard format used in industry.

---

### **3. Why the BOM Matters**

Without a correct BOM:

- Manufacturers may order the wrong components
    
- Assemblies may fail or be incomplete
    
- Production delays become extremely costly
    

A BOM is as important as the schematic and layout.

---

### **4. Key Points for Embedded Designers**

A good BOM must:

- Match the components used in the schematic AND layout
    
- Specify exact part numbers (because many components look similar but behave differently)
    
- Indicate package sizes (e.g., 0402 vs 0603)
    
- Include alternatives if needed (optional but helpful)
    

Special attention must be given to:

- Voltage ratings of capacitors
    
- Power ratings of resistors
    
- Temperature ranges
    
- IC variants (package, speed grade, memory size, etc.)
    

---

### **5. Exam-Relevant Understanding**

You should know:

- What a BOM is used for
    
- Why component selection must be precise
    
- What typical information appears in a BOM
    
- How it connects the schematic → manufacturing process

![[All_slides_nes.pdf#page=68]]  
**Week 2 Slide 32 – PCB Design: Manufacturing and Assembly**  

---

### **1. Two Distinct Stages: Manufacturing vs. Assembly**

#### **PCB Manufacturing**

This stage produces the **empty PCB**, including:

- Copper layers (etched or plated)
    
- Drill holes and vias
    
- Solder mask
    
- Silkscreen text
    
- Multilayer stack-up
    

No components are attached yet.

#### **PCB Assembly**

This stage solders components onto the manufactured PCB, typically using:

- **Pick-and-place machines** (shown in the slide)
    
- Reflow ovens
    
- Automated inspection systems
    

---

### **2. Why These Steps Are Often Outsourced**

Modern PCBs and assemblies require:

- High precision
    
- Specialized machinery
    
- Controlled environments
    

Because of cost and complexity, companies rely on **PCB fabrication services** (“fabs”) and **assembly houses**.

---

### **3. Cost Factors (important understanding)**

Costs increase when:

- Components become **smaller**
    
- PCB requires **more layers**
    
- Tolerances are **tighter**
    
- Via types are advanced (e.g., blind/buried)
    
- Assembly volume is low (prototype runs)
    

The slide hints at this with the caption:  
**“The smaller, the costlier.”**

---

### **4. What the Slide Images Show**

- A pick-and-place machine holding a reel of components
    
- This automated tool places tiny components at high speed (thousands per minute)
    
- Demonstrates how precise and automated modern assembly is
    

This visual emphasizes why manual assembly is unrealistic for dense embedded systems.

---

### **5. Exam-Relevant Understanding**

You should know:

- Difference between **manufacturing** (making the PCB) and **assembly** (populating it)
    
- Why these steps require specialized equipment
    
- Why smaller components and high precision increase cost
    
- What a pick-and-place machine does (automated component placement)

![[All_slides_nes.pdf#page=69]]  
**Week 2 Slide 33 – PCB Design: Testing**  

---

### **1. Why Testing Is Required**

Just like software can have bugs, **hardware designs can also have errors**—either from the design itself or from manufacturing defects.  
Testing ensures the PCB works as intended and meets performance requirements.

---

### **2. Who Performs the Testing**

Two layers of testing usually occur:

#### **1. Manufacturer Testing**

- Ensures PCBs are manufactured correctly (correct traces, no shorts/opens)
    
- Uses automated tools like electrical test fixtures
    
- Checks assembly quality (solder joints, component orientation)
    

#### **2. Designer/Engineer Testing**

- Ensures the **design** itself works
    
- Validates functionality, signal performance, power consumption, etc.
    

---

### **3. Types of Testing (as listed on the slide)**

|Test Type|Purpose|
|---|---|
|**Functional testing**|Does the board actually work as intended?|
|**Performance / power testing**|Does it meet energy and speed requirements?|
|**Signal quality testing**|Are signals clean, or is noise/EMI a problem?|
|**Mechanical testing**|Does the board withstand stress, vibration, etc.?|
|**Thermal testing**|Does heat dissipation work correctly?|
|**Specification verification**|Does the board meet the design specs?|
|**Safety certification**|Required for commercial products sold legally|

These are especially important for embedded devices used in healthcare, consumer electronics, or critical systems.

---

### **4. Why Testing Is Essential**

Testing catches:

- Incorrect footprints
    
- Routing mistakes
    
- Voltage/power issues
    
- Timing and signal integrity problems
    
- Component failures
    
- Manufacturing defects (e.g., solder bridges)
    

Even a small mistake may require a full **hardware revision**, which is costly in both time and money.

---

### **5. Exam-Relevant Understanding**

You should know:

- The difference between manufacturing testing and design-stage testing
    
- The key types of tests performed
    
- Why PCB/hardware testing is as important as software testing
    
- The consequences of inadequate testing

![[All_slides_nes.pdf#page=70]]  
**Week 2 Slide 34 – Electronic Testing Instruments: Multimeter**  

---

### **1. What a Multimeter Is**

A **multimeter** (specifically a digital multimeter, DMM) is a versatile tool used to measure basic electrical parameters in circuits.

It is one of the most essential tools in electronics debugging and testing.

---

### **2. Main Measurement Modes (as shown on the slide)**

|Mode|What It Measures|Use Case|
|---|---|---|
|**Voltmeter (DC/AC)**|Voltage|Checking supply rails, reading sensor outputs|
|**Ammeter (DC/AC)**|Current|Measuring consumption of a device|
|**Ohmmeter**|Resistance|Checking components, detecting open/closed circuits|
|**Continuity Mode**|Very low resistance (beeps)|Detecting shorts or verifying two points are connected|

These are the most commonly used functions.

---

### **3. Measurement Ranges**

Multimeters operate in selectable ranges:

- Too high a range → less resolution
    
- Too low a range → overload / out of range
    

For precise readings, the correct range must be selected.

---

### **4. When Multimeters Are Useful**

They excel at measuring **steady-state** (non-changing) values:

- Checking if a board has 3.3 V or 5 V properly
    
- Verifying connections and resistors
    
- Measuring battery voltage
    
- Testing LEDs, switches, continuity
    
- Verifying power consumption in idle/active states
    

They are **not** ideal for rapidly changing signals—that requires an oscilloscope.

---

### **5. What the Slide Image Shows**

A typical digital multimeter:

- LCD display
    
- Rotary selection knob
    
- Input jacks for probes
    
- Common measurement symbols
    

This helps you identify and use the tool in a lab setting.

---

### **6. Exam-Relevant Understanding**

You should know:

- The four main functions of a DMM
    
- When to use a multimeter vs. an oscilloscope
    
- What continuity mode is and why it’s useful
    
- Why the correct range must be selected

![[All_slides_nes.pdf#page=71]]  
**Week 2 Slide 35 – Electronic Testing Instruments: DC Power Supply**  

---

### **1. Purpose of a DC Power Supply**

A **bench DC power supply** provides a stable, controllable voltage source for testing circuits.  
It replaces batteries during development because it is:

- Adjustable
    
- Stable
    
- Safe (current limiting)
    

This makes it ideal for powering prototypes.

---

### **2. Key Features (as shown on the slide)**

#### **Adjustable Output Voltage**

- You can set the exact voltage your circuit requires (e.g., 1.8 V, 3.3 V, 5 V).
    
- Supports fine resolution adjustments.
    

#### **Multiple Independent Outputs**

- Many supplies have 2–4 channels.
    
- Allows powering several parts of a circuit at different voltages.
    

#### **Current Limiting**

- You set a maximum current.
    
- If your circuit tries to draw more, the supply **limits** it.
    
- Prevents damage from shorts or wiring mistakes.
    

This is one of the biggest advantages over a battery.

---

### **3. Use Cases in Embedded Systems**

- Powering a prototype MCU board
    
- Testing current consumption
    
- Detecting shorts (supply goes into current limit mode)
    
- Simulating battery voltages at different charge levels
    
- Measuring power profiles
    

---

### **4. What the Slide Image Shows**

- A typical lab DC supply with:
    
    - Display for voltage and current
        
    - Output terminals
        
    - Mode indicators
        
    - Buttons/dials for adjusting settings
        

These devices are standard in electronics labs.

---

### **5. Exam-Relevant Understanding**

You should know:

- Why adjustable DC power supplies are used during development
    
- How current limiting prevents damage
    
- That bench supplies can replace batteries during testing
    
- Why having multiple channels is useful for multi-voltage systems

![[All_slides_nes.pdf#page=72]]  
**Week 2 Slide 36 – Electronic Testing Instruments: Oscilloscope**  

---

### **1. What an Oscilloscope Does**

An **oscilloscope** measures and displays **voltage over time**.  
This makes it essential for observing signals that **change quickly**, unlike a multimeter which only measures steady values.

Embedded systems rely heavily on timing, so oscilloscopes are a core debugging tool.

---

### **2. Key Capabilities (as listed on the slide)**

#### **Measure and display time-varying signals**

- View waveforms such as square waves, sensor outputs, clock signals, communication signals.
    

#### **Multiple channels**

- Compare two or more signals at once (e.g., input vs. output).
    

#### **Triggering**

- Set conditions so the oscilloscope captures the waveform only when a specific event occurs  
    (e.g., rising edge, specific voltage threshold).
    

#### **Statistics**

- Measure:
    
    - Minimum voltage
        
    - Maximum voltage
        
    - Frequency
        
    - Period / time duration
        
    - Rise/fall times
        

#### **Data extraction**

- Save signal data to a file for analysis.
    

---

### **3. When Oscilloscopes Are Used**

Oscilloscopes are used for:

- Debugging digital communication (SPI, I²C, UART)
    
- Checking PWM signals
    
- Measuring clock signals
    
- Observing noise or ripple on power supplies
    
- Verifying timing relationships between signals
    
- Viewing sensor waveforms
    

If something is not working but a multimeter says “looks fine,” the oscilloscope usually reveals the real problem.

---

### **4. What the Slide Image Shows**

A modern digital oscilloscope with:

- Large waveform display
    
- Control knobs for voltage, time, and triggering
    
- Multiple input channels
    
- Measurement indicators
    

This is the standard tool you’ll find in engineering labs.

---

### **5. Exam-Relevant Understanding**

You should know:

- Difference between multimeter and oscilloscope
    
- What signals look like on an oscilloscope
    
- The meaning of “triggering”
    
- When to use an oscilloscope in embedded debugging

![[All_slides_nes.pdf#page=73]]  
**Week 2 Slide 37 – Electronic Testing Instruments (Additional Tools)**  

---

### **1. Overview of Additional Electronic Test Instruments**

This slide introduces four more tools commonly used when debugging or characterizing embedded systems—particularly when working with **digital signals**, **RF**, or **precision measurements**.

These tools complement the multimeter and oscilloscope.

---

### **2. Logic Analyzer**

A logic analyzer captures **digital** voltage signals across many channels at once.

Used for:

- Debugging digital protocols (I²C, SPI, UART, I²S, etc.)
    
- Timing analysis (when do signals change?)
    
- Checking if communication lines are correct
    
- Recording long sequences of digital activity
    

Key point:  
A logic analyzer reads **digital 0s and 1s**, not analog voltages.

---

### **3. Spectrum Analyzer**

A spectrum analyzer shows how **signal power is distributed across frequency**.

Used for:

- RF design (Bluetooth, Wi-Fi, antennas)
    
- Measuring harmonic content
    
- Identifying interference sources
    
- Checking transmitter output power and frequency stability
    

Unlike an oscilloscope (time-domain), a spectrum analyzer shows the **frequency-domain** representation.

---

### **4. Signal/Function Generator**

A function generator **creates electrical signals** with selectable:

- Waveform shape (sine, square, triangle, pulse)
    
- Amplitude
    
- Frequency
    
- DC offset
    

Used for:

- Testing circuit response
    
- Injecting known signals into filters, amplifiers, ADC inputs
    
- Replacing a sensor temporarily with a predictable signal
    

This tool is often paired with an oscilloscope.

---

### **5. Source Measurement Unit (SMU)**

An SMU can **supply power** _and_ **measure voltage and current** with extreme precision at the same time.

Used for:

- Characterizing sensors
    
- Measuring battery behavior
    
- Testing ultra-low-power devices (microamp or nanoamp currents)
    
- IV curve tracing of components (LEDs, diodes, transistors)
    

SMUs are more advanced and expensive than typical lab tools.

---

### **6. Exam-Relevant Understanding**

You should know:

- Differences between oscilloscope vs. logic analyzer vs. spectrum analyzer
    
- Which tool is used for **digital timing**, **RF frequency**, or **stimulus generation**
    
- That an SMU provides highly accurate power + measurement simultaneously
    

These tools appear often in embedded system labs and exam contexts.



--- 
---
---

## **MCQ 1 — Basic Electrical Concepts**

Which of the following statements about **Ohm’s Law** is correct?

A. Current is inversely proportional to voltage  
B. Voltage equals resistance divided by current  
C. Current increases when resistance increases (at fixed voltage)  
D. Current equals voltage divided by resistance

---

## **MCQ 2 — Power and Batteries**

A battery has internal resistance. When the device suddenly draws a high current, what happens?

A. The supply voltage increases  
B. The internal resistance decreases to compensate  
C. The supply voltage drops below the battery’s nominal voltage  
D. The battery outputs AC instead of DC

---

## **MCQ 3 — Components and Circuits**

A **voltage divider** is typically used to:

A. Convert AC to DC  
B. Produce an output that is a fraction of an input voltage  
C. Store energy for later use  
D. Amplify small signals

---

## **MCQ 4 — PCB Design**

Which of the following best describes the purpose of a **ground plane** in a PCB?

A. To physically support the components  
B. To reduce noise and improve electromagnetic performance  
C. To convert digital signals into analog signals  
D. To increase the board’s overall resistance

---

## **MCQ 5 — Electronic Testing Instruments**

A **logic analyzer** is the best tool for:

A. Measuring high-frequency analog waveforms  
B. Capturing digital 0/1 transitions on multiple lines simultaneously  
C. Measuring power consumption at microamp levels  
D. Viewing frequency-domain RF spectra

---

**MCQ 1:** **D**  
(Current = Voltage / Resistance)

**MCQ 2:** **C**  
(High current through internal resistance causes a supply voltage drop)

**MCQ 3:** **B**  
(Voltage dividers output a fraction of the input voltage)

**MCQ 4:** **B**  
(Ground planes reduce noise and improve EMI performance)

**MCQ 5:** **B**  
(Logic analyzers capture digital transitions across multiple channels)