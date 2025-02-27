# VTesting and Output 

## Clone & Setup Repository
```bash
git clone https://github.com/Skandakm29/VsdSquadron_mini_fpga_uart_loopback.git
cd VsdSquadron_mini_fpga_uart_loopback
⚡ Build & Flash FPGA Bitstream
🛠️ 1️⃣ Build the Bitstream
bash
Copy
Edit
make build
✅ Generates top.bin for the FPGA.

🔥 2️⃣ Flash to FPGA
bash
Copy
Edit
sudo make flash
✅ Uploads the bitstream to the FPGA.

📡 UART Loopback Testing
1️⃣ Open Serial Terminal
bash
Copy
Edit
sudo picocom -b 9600 /dev/ttyUSB0 --echo
2️⃣ Send Data & Verify Output
bash
Copy
Edit
# Expected Output:

Sent Data (TX)   | Received Data (RX)
-----------------|------------------
A               | A
hello           | hello
12345           | 12345
3️⃣ Exit Terminal
bash
Copy
Edit
CTRL + A, then CTRL + X
🖼️ Circuit Diagram
markdown
Copy
Edit
![Circuit Diagram](images/circuit_diagram.png)
❗ Debugging Tips
bash
Copy
Edit
# If no output appears:
1. Check FPGA pin connections.
2. Ensure baud rate is set to 9600.
3. Verify FTDI cable is properly connected.