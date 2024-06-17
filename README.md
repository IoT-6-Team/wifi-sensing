### GitHub README: Implementing People Counting with Raspberry Pi and Wi-Fi Sensing

Welcome to our project! This repository contains the code and documentation for our project on people counting using Raspberry Pi and Wi-Fi sensing technology. The goal of this project is to leverage open-source tools, apply machine learning algorithms, and follow a systematic classification process to develop a program that recognizes the number of people in a given environment.

#### Table of Contents
1. [Project Overview](#project-overview)
2. [Technical Background](#technical-background)
3. [Setup and Installation](#setup-and-installation)
4. [Data Collection](#data-collection)
5. [Model Training and Testing](#model-training-and-testing)
6. [Results and Visualization](#results-and-visualization)
7. [Troubleshooting](#troubleshooting)
8. [Future Work](#future-work)
9. [References](#references)

### Project Overview

#### Main Goal
The primary objective of this project is to identify and count the number of people in an indoor environment using Wi-Fi sensing technology. Unlike traditional systems that detect human behavior, this project focuses on classifying the number of people present.

#### Requirements
- Affordable and low-power consumption
- Support for various operating systems and programming languages
- Ability to classify activities and count people accurately

### Technical Background

Wi-Fi sensing uses existing 802.11-based protocols to detect changes in the environment. It is device-free, sensor-free, and privacy-friendly. We utilize Channel State Information (CSI) to estimate the location and movement of Wi-Fi devices, which helps in counting people.

### Setup and Installation

#### Prerequisites
- Raspberry Pi 3 or 4
- SD card with Raspberry Pi OS
- Wi-Fi adapter compatible with Nexmon CSI
- Basic knowledge of Linux commands and Git

#### Steps
1. **Download Raspberry Pi OS**:
   - Use the Raspberry Pi Imager to write the OS image to your SD card.
   - [Raspberry Pi OS Download](https://downloads.raspberrypi.com/)
   
2. **Install Nexmon and Nexmon CSI**:
   ```bash
   git clone https://github.com/seemoo-lab/nexmon
   git clone https://github.com/seemoo-lab/nexmon_csi
   cd nexmon
   make
   cd ../nexmon_csi
   makecsiparams -h
   ```
   
3. **Set Up Wi-Fi Access Point and Monitor Mode**:
   - Follow the instructions to set one Raspberry Pi as an Access Point (AP) and another in monitor mode.
   - [Raspberry Pi AP Mode Setup](https://limjunho.github.io/2020/08/25/Raspberry-Pi-AP%EB%A7%8C%EB%93%A4%EA%B8%B0.html)

### Data Collection

#### Extracting CSI
1. Set the device to monitor mode and extract CSI using:
   ```bash
   makecsiparams -c 40/20/ -C 1 -N 1 -m 88:36:6c:c7:95:fe
   tcpdump -i wlan0 dst port 5500 -vv -w output.pcap -c 1000
   ```
2. Convert the `pcap` files to `CSV` for easier analysis:
   - [Gigasheet](https://www.gigasheet.com/)
   - [PCAP to CSV Converter](https://github.com/cheeseBG/pcap-to-csv)

### Model Training and Testing

1. **Train the Model**:
   - Use machine learning algorithms to train the model on collected data.
   - Example: Random Forest, SVM, or a Neural Network.
   
2. **Test the Model**:
   - Validate the model using test data and evaluate its performance.

### Results and Visualization

1. **Visualize CSI Data**:
   - Use visualization tools to interpret CSI data and the model’s performance.
   - [CSI Visualization Tool](https://github.com/cheeseBG/csi-visualization)

2. **Evaluate Accuracy**:
   - Compare the predicted count of people against the actual count to measure accuracy.

### Troubleshooting

1. **Wi-Fi Connection Issues**:
   - Ensure the Wi-Fi adapter is compatible and properly configured.
   - Reboot and reconfigure if the connection drops.

2. **CSI Extraction Problems**:
   - Check dependencies and ensure all necessary drivers are installed.
   - Refer to the detailed Nexmon installation guide: [Nexmon CSI Guide](https://pio-ji.notion.site/Nexmon-CSI-2653217c26644723a5f91e45f37b8a5a)

### Future Work

- **Real-Time People Counting**:
  - Implement real-time data processing and visualization.
  
- **Advanced Activity Recognition**:
  - Expand the system to classify specific activities in addition to counting people.

### References

- Nexmon CSI: [Nexmon CSI GitHub](https://github.com/seemoo-lab/nexmon_csi)
- Raspberry Pi AP Mode Setup: [Setup Guide](https://limjunho.github.io/2020/08/25/Raspberry-Pi-AP%EB%A7%8C%EB%93%A4%EA%B8%B0.html)
- PCAP to CSV: [Converter](https://github.com/cheeseBG/pcap-to-csv)
- CSI Visualization: [Visualization Tool](https://github.com/cheeseBG/csi-visualization)

Thank you for your interest in our project. We welcome any feedback or contributions. Please feel free to open an issue or submit a pull request. Happy coding!
