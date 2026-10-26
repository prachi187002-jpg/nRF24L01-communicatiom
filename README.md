# nRF24L01-communication

A simple wireless communication project using **two Arduino UNO boards** and **two nRF24L01 wireless transceiver modules**.

## Introduction

The **nRF24L01** is a 2.4 GHz wireless transceiver module that can transmit and receive data wirelessly.

In this project, two nRF24L01 modules communicate with each other through two Arduino UNO boards. The transmitter sends the message **"Hello World"** to the receiver, which displays the received message in the Serial Monitor.

## Project Objective

- Establish wireless communication between two Arduino UNO boards.
- Transmit the message **"Hello World"** wirelessly.
- Receive and display the message on the receiver's Serial Monitor.

## Hardware Requirements

| Component | Quantity |
|---|---:|
| Arduino UNO | 2 |
| nRF24L01 Wireless Transceiver Module | 2 |
| USB cables for programming and powering | As required |

**Note:** No batteries or additional electronic components are used in this project. Both Arduino UNO boards can be powered through USB cables.

## Pin Connections

The following connections are identical for both the transmitter and receiver.

| nRF24L01 Pin | Arduino UNO Pin |
|---|---|
| CE | Digital Pin 5 |
| CSN (CS) | Digital Pin 10 |
| SCK / SCLK | Digital Pin 13 |
| MOSI | Digital Pin 11 |
| MISO | Digital Pin 12 |
| VCC | 3.3V |
| GND | GND |

> ** Important:** The nRF24L01 operates at 3.3V. Connect its VCC pin to the Arduino UNO's **3.3V pin**, never to 5V.

## System Architecture

```text
       TRANSMITTER                         RECEIVER
   ┌─────────────────┐                ┌─────────────────┐
   │   Arduino UNO   │                │   Arduino UNO   │
   │        │        │                │        ▲        │
   │    nRF24L01     │  ~~~~~~~~~~~   │    nRF24L01     │
   │        │        │  Wireless      │        │        │
   │ Send "Hello     │  Communication │ Receive Message │
   │     World"      │                │        │        │
   └─────────────────┘                └────────┬────────┘
                                               │
                                               ▼
                                        Serial Monitor
                                        Hello World
```

The transmitter sends the message through the nRF24L01 module. The receiver module receives the wireless data and passes it to the second Arduino UNO, which displays it in the Serial Monitor.

## Repository Structure

```text
nRF24L01-communication/
│
├── README.md
│
├── Transmitter-Code/
│   └── Transmitter-Code.ino
│
└── Receiver-Code/
    └── Receiver-Code.ino
```

### Files Description

- **`README.md`** — Contains the project introduction, wiring details, and instructions.
- **`Transmitter-Code.ino`** — Arduino program responsible for transmitting the message "Hello World".
- **`Receiver-Code.ino`** — Arduino program responsible for receiving and displaying the message.

## Software Requirements

- **Arduino IDE** — To write and upload the Arduino programs.
- **RF24 Library by TMRh20** — To control the nRF24L01 modules.

### Installing the RF24 Library

1. Open the Arduino IDE.
2. Navigate to **Sketch → Include Library → Manage Libraries**.
3. Search for **RF24**.
4. Install the RF24 library by TMRh20.

## How to Run the Project

1. Connect the first nRF24L01 module to the first Arduino UNO using the pin connections listed above.
2. Connect the second nRF24L01 module to the second Arduino UNO in the same way.
3. Open `Transmitter-Code.ino` in the Arduino IDE.
4. Select **Arduino UNO** and the correct port, then upload the transmitter program.
5. Open `Receiver-Code.ino`, select the second Arduino's port, and upload the receiver program.
6. Power both Arduino boards using USB cables.
7. Open the Serial Monitor for the receiver Arduino.
8. Select the baud rate specified in the receiver code.
9. Observe the received message.

**Expected Output:**

```text
Hello World
```

The message may appear repeatedly if the transmitter program sends it continuously.

## Working Principle

1. The transmitter Arduino initializes its nRF24L01 module.
2. The transmitter prepares the message `"Hello World"`.
3. The nRF24L01 transmits the message over a 2.4 GHz wireless link.
4. The receiver's nRF24L01 listens for incoming data using matching radio settings.
5. The receiver Arduino reads the received message.
6. The message is displayed in the receiver's Serial Monitor.

## Troubleshooting

| Problem | Possible Solution |
|---|---|
| No message received | Check wiring, power, and whether both programs are uploaded. |
| Radio initialization fails | Recheck CE, CSN, SCK, MOSI, MISO, VCC, and GND. |
| Communication fails | Ensure both programs use matching radio addresses, channels, and data rates. |
| Unstable communication | Keep wires short and ensure a stable 3.3V supply. |
| No Serial Monitor output | Check the selected port and baud rate. |

## Important Notes

- The nRF24L01 must be powered using **3.3V**, not 5V.
- The Arduino UNO communicates with the nRF24L01 through the **SPI interface**.
- The two Arduino boards do not require a direct signal connection to each other.
- USB cables provide power and are used for uploading programs.
- Both modules must use compatible radio settings to communicate successfully.
- This setup assumes standard nRF24L01 modules. Different module variants may have different power requirements.

## Project Summary

| Parameter | Details |
|---|---|
| Project Name | nRF24L01 Communication |
| Microcontroller | Arduino UNO |
| Wireless Module | nRF24L01 |
| Operating Frequency | 2.4 GHz band |
| Communication Type | Wireless |
| Transmitter | 1 Arduino UNO + 1 nRF24L01 |
| Receiver | 1 Arduino UNO + 1 nRF24L01 |
| Message | Hello World |

---

**Developed using Arduino UNO and nRF24L01 wireless transceiver modules.**
