# **UART TX Block Diagram**

## **📌 Overview**
The **UART Transmitter (uart_tx_8n1)** follows a structured architecture to convert **parallel data (8-bit)** into a **serial UART format**. The block diagram below represents the key functional blocks of this module.
## UART TX Block Diagram

![UART TX Block Diagram](block_diagram.png)

## **📌 Description of Each Block**

### **1️⃣ FSM Controller (State Machine)**
- Controls the **state transitions** for UART transmission.
- Moves through states: **IDLE → STARTTX → TXING → TXDONE → IDLE**.
- Ensures **correct bit timing and sequence**.

### **2️⃣ Shift Register (Data Buffer)**
- **Stores `txbyte` before transmission**.
- **Shifts out bits one-by-one**, sending **LSB first**.
- Updates `txbit` for UART transmission.

### **3️⃣ Bit Counter**
- **Tracks how many bits have been transmitted (`bits_sent`)**.
- Ensures exactly **8 data bits are transmitted** before moving to stop bit.

### **4️⃣ TX Output Logic**
- **Drives `txbit`** to generate a **serial UART signal**.
- Sends **Start Bit (`0`), 8 Data Bits (LSB First), Stop Bit (`1`)**.
- Connects directly to the **UART TX pin (`tx`)**.

## **📌 Data Flow Explanation**
1. The **FSM Controller** starts transmission when `senddata = 1`.
2. The **Shift Register** loads `txbyte` and begins shifting bits.
3. The **Bit Counter** keeps track of bits sent, ensuring **8 bits are transmitted**.
4. The **TX Output Logic** sends **start bit → data bits → stop bit** in **serial format**.
