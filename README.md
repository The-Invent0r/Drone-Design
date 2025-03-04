# Custom Drone flight controller PCB and radio controller + all software.

## Overview
This is a custom flight controller I designed and built for a brushed DC motor drone, powered by an ATmega328p microcontroller, nRF24l01 radio, and MPU6050 IMU. I wanted a hands-on challenge to merge my skills in PCB design, microcontrollers, and motor control—after a year of troubleshooting, it flies stable and takes wireless commands.

## Features
- Real-time stabilization using MPU6050 gyro and accelerometer data.  
- Wireless control via nRF24l01 at 2.4GHz.  
- Drives four brushed DC motors with custom MOSFET-based drivers.  
- Lightweight 4-layer PCB with EMI shielding and efficient power distribution.

## Design & Build
- **Hardware**:  
  - *ATmega328p*: Familiar, handles PWM, I2C, and SPI for motors, IMU, and radio. Runs at 3.7V (LiPo)—tested stable at 16MHz, no boost converter needed.  
  - *MPU6050*: 3-axis gyro and accelerometer for flight dynamics.  
  - *nRF24l01*: 2.4GHz radio for ground station comms.  
  - *IRLML2502 MOSFETs*: Low Rds, fast-switching drivers for four motors, with Schottky flyback diodes.  
  - *1S 90C LiPo*: Powers it all; ditched regulators after testing.  
- **PCB**: Started with a 2-layer board, but motor EMI kept resetting the MCU. Switched to a 4-layer design—motor drivers on bottom, sensitive components on top, ground/power planes in between for shielding, I also tried a 6-layer board which worked just as well as the 4-layer board.
- **Tools**: KiCAD for schematics and PCB layout, soldering iron and heat gun for assembly, Multiwii open-source software for fast firmware.  
- **Challenges**:  
  - EMI from motors crashed the MCU. Tried a 5V boost converter—didn’t help. Went 3.7V direct from LiPo, still issues.  
  - 4-layer and 6-layer PCB rethink separated high-current and signal paths—killed the resets.

## Results
Breadboard tests nailed stable motor control; bench sims proved IMU-driven stabilization. It’s rough but works—tweaking PWM is next for smoother flight.

## Media
4-layer board

![image](https://github.com/user-attachments/assets/d88bf149-84f7-420c-809c-81aa0fa1bbaf)
![image](https://github.com/user-attachments/assets/115f4bf0-53b1-4fdd-89e0-b8ffd9f7069a)
![go2-2u-r](https://github.com/user-attachments/assets/d0571c33-b2d1-43d1-99dc-565f38e9ddb6)
![JmDARRze](https://github.com/user-attachments/assets/2ff8e556-3ad8-4ba5-b72a-0245a0ebaf45)

6-layer board

![5ym9NuEH](https://github.com/user-attachments/assets/7f3cefb1-ce35-4c12-bbce-2ebd1d3c56c4)
![L8ePkmEb](https://github.com/user-attachments/assets/67bf9971-dce2-4924-9e1d-46b63fd47b17)


