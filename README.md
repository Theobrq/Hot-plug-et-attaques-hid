# Hot-Plug and HID Attacks

A school demonstration project showcasing HID (Human Interface Device) attack vectors using a microcontroller (e.g. Teensy) to execute arbitrary commands by pretending to be a keyboard, bypassing security, and opening a reverse shell connection to a listener server (using Villain).

## Authors
- TheoOrigin
- School Project Team (3A)

---

## Attack Flow

1. **Microcontroller Payload (Victim Side)**:
   - Connect the configured Teensy/Arduino microcontroller to the target machine.
   - The device automatically initializes keyboard emulation.
   - It runs the custom bypass payload sequence: opens Windows Defender settings, navigates via keys, and temporarily turns off real-time protection.
   - Launches PowerShell with elevated privileges (Run as Administrator) using Ctrl+Shift+Enter.
   - Downloads/types the base64-encoded reverse shell payload, creating a persistent startup script.

2. **Control Server (Attacker Side)**:
   - Setup a reverse shell listener using the Villain framework:
     ```sh
     git clone https://github.com/t3l3machus/Villain
     cd Villain
     pip3 install -r requirements.txt
     python3 Villain.py
     ```
   - Manage incoming connections:
     ```sh
     # List active sessions
     sessions
     # Open interactive shell on a target session
     shell [ID]
     ```

---

## Technical Details

The Arduino sketch code is located in the **[payload/payload.ino](file:///C:/Users/theob/Desktop/Project/Hot-plug-and-hidden-attacks-School-Project-3A/payload/payload.ino)** file.

> [!WARNING]
> This repository is created strictly for educational purposes and authorized penetration testing demonstrations. Unauthorized use of these techniques is illegal.
