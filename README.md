# Low-Power Miniaturized Coded Continuous Wave (CCW) Vertical Ionosonde Based on SDR
(Software Defined Radio Ionosonde)

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.xxxxxxx.svg)](https://doi.org/10.5281/zenodo.20844580)

## Project Overview

We propose and develop a low-power, miniaturized Coded Continuous Wave (CCW) vertical ionospheric sounding system based on the Software-Defined Radio (SDR) architecture. This system relies on the core digital signal processing architecture of the open-source project ([jvierine/ionosonde](https://github.com/jvierine/ionosonde)) and is optimized and developed for mid-latitude ionospheric sounding requirements.

The system utilizes long-code Pseudo-Random Noise (PRN) sequences for phase modulation combined with pulse compression technology to achieve high processing gain, which significantly improves the detection capability of weak signals. The system supports both vertical and oblique sounding and can be easily scaled into a multi-static ionospheric sounding network.

## Directory Structure

To keep the project structure clean and maintainable, this repository is organized as follows:

- `src/`: Core Python source code and execution scripts (TX/RX control and signal analysis).
- `docs/`: Detailed documentation of the overall system architecture, software logic, and hardware implementation.
- `hardware/`: Contains the system's Bill of Materials (BOM) and hardware connection block diagrams.
- `figures/`: Stores experimental results and sample ionograms.
- `config/`: Various runtime configuration files for the system.

## Hardware & BOM

This system utilizes independent transmit (TX) and receive (RX) chains, incorporating a bidirectional coupler to achieve safe VSWR monitoring. 
For a detailed description of the system architecture, please refer to: [docs/system_implementation.md](docs/system_implementation.md)

**For the core Hardware Bill of Materials (BOM), please refer to:** [hardware/BOM.md](hardware/BOM.md)

## System Requirements

The SDR control framework is built on Linux and standard scientific computing stacks. 

- **Operating System**: Linux-based OS (Ubuntu 24.04 or later is recommended).
- **RF Driver**: Ettus Research UHD (USRP Hardware Driver) version 4.x.
- **Python Environment**: Python 3.10+ with standard scientific libraries (`numpy`, `scipy`, `matplotlib`, etc.).

## Deployment & Configuration Guidelines

To successfully run the SDR ionosonde, please ensure the following system-level configurations are met:

1. **Network Configuration**: Ensure the host computer and the USRP device are directly connected via a Gigabit Ethernet interface. Configure the host computer with a compatible static IP subnet corresponding to your USRP default address.
2. **Buffer Optimization**: To support high-rate continuous data streams and prevent buffer overflow/underrun errors (such as `O` or `U` errors), it is highly recommended to increase the kernel network buffer sizes (e.g., tuning `net.core.rmem_max` and `net.core.wmem_max`).
3. **Dependencies Installation**: Ensure all required core libraries and Python dependencies (such as `numpy`, `scipy`, `matplotlib`, `h5py`, `psutil`, and the `uhd` Python API) are installed via your system's package manager (e.g., `apt`) or `pip`.

## Citation & License

This software is released under the **GNU General Public License v3.0 (GPL-3.0)**. 
Original framework attribution: (c) 2012-2025 Juha Vierinen, Markus Floer, Mikko Syrjäsuo, Peje Nilsson.

If you use this software or hardware architecture design in your research, please cite the Zenodo DOI of this project. You can also refer to the `CITATION.cff` file for the exact citation format.
