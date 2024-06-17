### GitHub README: Implementing People Counting with Raspberry Pi and Wi-Fi Sensing

Welcome to our project! This repository contains the code and documentation for our ambitious project on people counting using Raspberry Pi and Wi-Fi sensing technology. Our goal is to leverage cutting-edge open-source tools, apply advanced machine learning algorithms, and follow a rigorous classification process to develop a program that accurately recognizes the number of people in a given environment. This README provides a comprehensive guide to understand, set up, and contribute to this project.

---

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

---

### Project Overview

#### Main Goal
The primary objective of this project is to identify and count the number of people in an indoor environment using Wi-Fi sensing technology. Unlike traditional systems that detect human behavior, this project focuses on classifying the number of people present. By doing so, we aim to create a low-cost, low-power, and highly efficient system suitable for various applications, including smart buildings, security, and occupancy monitoring.

#### Requirements
- **Affordability and Low-Power Consumption:** The system must be cost-effective and energy-efficient to facilitate widespread adoption.
- **Support for Various Operating Systems:** The system should be versatile and compatible with different programming environments and operating systems.
- **Accurate Classification:** The ability to accurately classify activities and count the number of people is crucial for the system's success.

### Technical Background

Wi-Fi sensing technology utilizes existing 802.11-based protocols to detect environmental changes. This approach is advantageous because it does not require additional sensors or devices, making it privacy-friendly and cost-effective. Channel State Information (CSI) is the cornerstone of this technology, allowing us to analyze how signals propagate through space to estimate the location and movement of objects and people.

#### Advantages of Wi-Fi Sensing:
- **Device-Free:** No need for additional hardware.
- **Extra Sensor-Free:** Utilizes existing Wi-Fi infrastructure.
- **Privacy-Friendly:** Non-intrusive sensing method.

### Setup and Installation

#### Prerequisites
Before you begin, ensure you have the following:
- **Hardware:** Raspberry Pi 3 or 4, compatible Wi-Fi adapter.
- **Software:** Raspberry Pi OS, Nexmon CSI tools.
- **Skills:** Basic knowledge of Linux commands, Git, and machine learning.

#### Installation Steps

1. **Download and Install Raspberry Pi OS**:
   - Use the [Raspberry Pi Imager](https://www.raspberrypi.com/software/) to write the OS image to your SD card.
   - Our recommended version: `2022-01-28-raspios-bullseye-armhf.img`.

2. **Install Nexmon and Nexmon CSI**:
   - Clone the repositories and install the tools:
     ```bash
     git clone https://github.com/seemoo-lab/nexmon
     git clone https://github.com/seemoo-lab/nexmon_csi
     cd nexmon
     make
     cd ../nexmon_csi
     makecsiparams -h
     ```
   
3. **Configure Wi-Fi Access Point and Monitor Mode**:
   - Follow detailed instructions to set one Raspberry Pi as an Access Point (AP) and another in monitor mode.
   - Reference: [Raspberry Pi AP Mode Setup](https://limjunho.github.io/2020/08/25/Raspberry-Pi-AP%EB%A7%8C%EB%93%A4%EA%B8%B0.html).

### Data Collection

#### Extracting CSI
1. **Set Device to Monitor Mode**:
   - Extract CSI using the following commands:
     ```bash
     makecsiparams -c 40/20/ -C 1 -N 1 -m 88:36:6c:c7:95:fe
     tcpdump -i wlan0 dst port 5500 -vv -w output.pcap -c 1000
     ```

2. **Convert PCAP Files to CSV**:
   - Use tools like [Gigasheet](https://www.gigasheet.com/) or the [PCAP to CSV Converter](https://github.com/cheeseBG/pcap-to-csv) to convert the captured data into a CSV format for easier analysis.

### Model Training and Testing

#### Train the Model
1. **Feature Extraction**:
   - Extract relevant features from the CSV files for model training.
   - Common features include signal strength, variance, and other statistical measures.

2. **Model Selection**:
   - Choose an appropriate machine learning algorithm (e.g., Random Forest, SVM, or a Neural Network).
   - Train the model using the extracted features.

3. **Training**:
   - Split the data into training and validation sets.
   - Train the model and fine-tune hyperparameters for optimal performance.

#### Test the Model
1. **Validation**:
   - Evaluate the model using validation data to ensure it generalizes well.
   
2. **Testing**:
   - Test the model on unseen data to measure its accuracy and robustness.

### Results and Visualization

#### Visualize CSI Data
1. **Visualization Tools**:
   - Utilize visualization tools to interpret CSI data and the model’s performance.
   - Example tool: [CSI Visualization Tool](https://github.com/cheeseBG/csi-visualization).

2. **Performance Metrics**:
   - Use metrics such as accuracy, precision, recall, and F1-score to evaluate the model’s performance.

### Troubleshooting

#### Common Issues and Solutions
1. **Wi-Fi Connection Problems**:
   - Ensure the Wi-Fi adapter is compatible and properly configured.
   - Reboot and reconfigure if the connection drops.

2. **CSI Extraction Issues**:
   - Verify that all dependencies are installed correctly.
   - Refer to the [Nexmon CSI Installation Guide](https://pio-ji.notion.site/Nexmon-CSI-2653217c26644723a5f91e45f37b8a5a) for troubleshooting steps.

### Future Work

#### Enhancements and Extensions
1. **Real-Time People Counting**:
   - Implement real-time data processing and visualization to enhance the system’s responsiveness.

2. **Advanced Activity Recognition**:
   - Expand the system to classify specific activities in addition to counting people.

3. **Scalability**:
   - Explore methods to scale the system for larger environments or more complex scenarios.

### References

- **Nexmon CSI**: [Nexmon CSI GitHub](https://github.com/seemoo-lab/nexmon_csi)
- **Nexmon Install Manual**: [Nexmon Installation Guide](https://pio-ji.notion.site/Wi-Fi-Sensing-3c03bfbaa99c4cb8a7a40333278efff3)
- **Raspberry Pi AP Mode**: [Setup Guide](https://limjunho.github.io/2020/08/25/Raspberry-Pi-AP%EB%A7%8C%EB%93%A4%EA%B8%B0.html)
- **What is Nexmon**: [Nexmon Overview](https://github.com/seemoo-lab/bcm-rpi3)
- **What is Raspberry Pi**: [Raspberry Pi Resource](https://opensource.com/resources/raspberry-pi)
- **Gigasheet, Convert PCAP to CSV**: [Gigasheet Converter](https://www.gigasheet.com/popular-tools/convert-pcap-to-csv)
- **Convert PCAP to CSV**: [PCAP to CSV GitHub](https://github.com/cheeseBG/pcap-to-csv)
- **CSI Real Time Visualization**: [CSI Visualization GitHub](https://github.com/cheeseBG/csi-visualization)
- **People Counting Model**: [Wi-Fi Sensing GitHub](https://github.com/cheeseBG/wifi-sensing)
- **Insomnia News Articles**: [Chosun News](https://biz.chosun.com/it-science/ict/2022/01/07/YV7CA77GXRHGFHVW4VVCG2V5SQ/) and [Medigate News](https://medigatenews.com/news/2161288985)
- **About Insomnia Wi-Fi Sensing**: [Brunch Article](https://brunch.co.kr/@8d2b9087f2a94bd/61)

---

Thank you for your interest in our project! We welcome any feedback or contributions. Please feel free to open an issue or submit a pull request. Together, we can make this project even better. Happy coding!
