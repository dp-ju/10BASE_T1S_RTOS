![Microchip logo](https://raw.githubusercontent.com/wiki/Microchip-MPLAB-Harmony/Microchip-MPLAB-Harmony.github.io/images/microchip_logo.png)

# lwIP TCP/IP example on SAM E54 Curiosity Ultra using the LAN865x 10BASE-T1S Ethernet MAC-PHY

This project demonstrates how to build a SOME/IP-based client to access the LAN866X endpoint product from Microchip.
 It provides a guide on configuring and utilizing the LAN866X in a network environment.

## Building The Application
The parent folder for all the MPLAB X IDE projects for this application is given below:

**Application Path** : \app\firmware

To build the application, refer to the table below and open the appropriate project file
in MPLABX IDE.

| Project Name              | Description                                                                |
| ---                       | ---                                                                        |
| \app\firmware\demo.X      | Main project implementing all needed layers to remote access the LAN866X.  |

## Hardware setup

![Setup](images/setup.jpg)

* Hardware used
    * [SAM E54 Curiosity Ultra Development Board](https://www.microchip.com/en-us/development-tool/DM320210)
    * [SPI to 10BASE-T1S interface card](https://www.mikroe.com/two-wire-eth-click)
* Hardware setup
    * Connect the DEBUG USB port on the board to the computer using a micro USB cable
    * Connect the SPI to 10BASE-T1S interface card to one or multiple LAN866X Endpoints.

## Settings for LAN865x

Configuration is done via #defines in the "\app\firmware\src\task_network.c".

**MAC-PHY Settings**

    #define T1S_PLCA_ENABLE             (true)
    #define T1S_PLCA_NODE_ID            (0)
    #define T1S_PLCA_NODE_COUNT         (8)
    #define T1S_PLCA_BURST_COUNT        (0)
    #define T1S_PLCA_BURST_TIMER        (0x80)
    #define MAC_PROMISCUOUS_MODE        (false)
    #define MAC_TX_CUT_THROUGH          (true)
    #define MAC_RX_CUT_THROUGH          (false)

**PLCA Settings**

10BASE-T1S can be used in PLCA or CSMA/CD mode.
When using PLCA, the parameters for _Local Node ID_, _Node Count_,
_Max Burst Count_ and _Burst Timer_ must be configured.
These settings are stored in a subsection inside the MAC-PHY settings.

## Running the Application

1. Open a Terminal application (e.g. Tera term) on the computer
2. Connect to the Virtual COM port and configure the serial settings as follows:
    * Baud : 115200
    * Data : 8 Bits
    * Parity : None
    * Stop : 1 Bit
    * Flow Control : None
3. Build and Program the application using the MPLAB X IDE
    For optimum results, select "Release" Mode as build target, this requires fee-based XC32 compiler license.
