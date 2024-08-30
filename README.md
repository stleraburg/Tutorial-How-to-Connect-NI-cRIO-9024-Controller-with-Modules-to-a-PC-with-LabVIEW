# Tutorial:How to Connect NI-cRIO 9024 Controller with Modules to a PC with LabVIEW
How to choose approptiate drivers and software version to meet compatibitlity between the hardware and software.

The NI cRIO-9024 embedded real-time controller is part of the high-performance NI CompactRIO programmable automation controller (PAC) platform. It features an industrial 800
MHz real-time Freescale processor for deterministic, reliable real-time applications and contains 512 MB of DDR2 RAM and 4 GB of nonvolatile storage for holding programs and
logging data. For more details, see the **datasheet** and user **manual**. 

The CompactRIO real-time controller connects to any four- or eight-slot CompactRIO reconfigurable chassis. In our, case it is NI cRIO-9113 CompactRIO 4-Slot Chassis. The user-defined FPGA circuitry in the chassis controls each I/O
module and passes data to the controller through a local PCI bus using built-in communication functions.

NI C Series I/O modules are self-contained measurement modules. All circuitry required for measurement is contained in the module itself. All A/D and D/A conversion occur in the module before
the data reaches the chassis. Each I/O module contains built-in signal conditioning and screw terminal, BNC, or D-Sub connectors. A variety of I/O types is available, including ±80 mV thermocouple inputs, ±10 V simultaneous-sampling analog inputs/outputs, 24 V industrial digital I/O with up to 1 A current drive, differential/TTL digital inputs with 5 V regulated supply output for encoders, and 250 Vrms universal digital inputs.
We use **NI-9262**, a simultaneously updating analog output module (16-bit, 1MS/s/ch) and **NI-9231**, sound and vibration input module (24-bit, 51.2 kS/s/ch). 

## Software Requirements (latest)
CompactRIO is programmed using NI LabVIEW. Because CompactRIO is a distributed real-time system, it also uses the LabVIEW Real-Time Module and the LabVIEW FPGA Module. CompactRIO also requires the NI-RIO driver to be installed
on your development PC to support real-time controllers, reconfigurable chassis, and C Series modules. 

1. Windows 10 OS
2. LabVIEW 2019 development system
3. NI-RIO driver
4. LabVIEW Real-Time Module (19.0)
5. LabVIEW FPGA Module (19.0)

You can install the modules from the NI Package Manager, ensure that you choose the appropriate version. 

## Hardware Connection
I assume that the controller has been already connected to the chassis. If this is not the case, please refer to the user manual. 

### Installing C Series Modules
1. Make sure that no I/O-side power is connected to the module. Because C Series modules are hot swappable, if the system is in a nonhazardous location, the chassis power can be on when you install modules.
2. Squeeze the latches and insert the module into the module slot.
3. Press firmly on the connector side of the C Series module until the latches lock the module into place.

### Connecting Ethernet and Power
CompactRIO systems use Ethernet for almost all configuration and other communication with the development or host PC. Before connecting power, ensure that all controller DIP switches are in the OFF position. 

![image](https://github.com/user-attachments/assets/a74fc951-ccdc-45f4-9e5b-61ae1e90414c)

Open Measurement & Automation Explorer (MAX) from the Windows Start menu. Expand *Remote Systems*. You should see your CompactRIO system under Remote Systems. Make sure that the IPv4 address is static and coincides with the IPv4 address of you PC. You are advices to have a router to which you connect the PC and the cRIO system so that you will have the Internet access.
- if you see an error *Inconsistent IP Settigns*, review the first step.

### Adding a CompactRIO System to a New Project
1. Open a blank LabVIEW project. Right-click the project name and select **New>>Targets and Devices…**
2. On the Add Targets and Devices... dialog box that appears, find the cRIO-9024 under RealTime CompactRIO and click **OK**.
3. Choose the option to use the LabVIEW FPGA Interface programming mode.

















