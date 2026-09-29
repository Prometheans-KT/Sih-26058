# Prometheans

## Software defined sonar transmitter
SIH26058  --- An ESP32-Based Adaptive Sonar System that Continuously Monitors Environmental Conditions, Dynamically Adjusts Sonar Parameters, Measures Echo Response, Optimizes Transmission Power, and Provides Real-Time Feedback for Autonomous Underwater Vehicles

## 📑 Table of Contents

- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Proposed Solution](#proposed-solution)
- [System Architecture](#system-architecture)
- [Hardware Components](#hardware-components)
- [Software & Technologies](#software-technologies)
- [Working Principle](#working-principle)
- [Implementation](#implementation)
- [Results](#results)
- [Uniqueness](#Uniqueness)
- [Future Scope](#future-scope)
- [Conclusion](#conclusion)

## Project Overview 
Prometheans creates intelligent underwater sensing system by combining:
- Real-time environmental sensing like Salinity monitoring , Water temperature monitoring , Depth monitoring and Turbidity monitoring
- Adaptive sonar parameter selection like sonar frequency, bandwidth, pulse duration, waveform, and transmission power.
- Software-defined waveform generation
- Echo detection and target range estimation
- Adaptive sonar transmission
- SNR and signal-quality analysis
- Low-power and duty-cycle optimization
- Wired underwater-to-surface communication
- Real-time monitoring dashboard
- Continuous feedback and adaptation
- Designed for integration with an AUV
##  System Workflow


```text
Environmental Sensing
        ↓
   Data Processing
        ↓
 Adaptive Decision
        ↓
Sonar Waveform Generation
        ↓
 Underwater Transmission
        ↓
    Echo Reception
        ↓
 Signal Processing
        ↓
Range / SNR / Target Detection
        ↓
 Feedback & Adaptation
```

The system continuously senses underwater environmental conditions, processes the collected data, adapts sonar parameters, transmits and receives acoustic signals, detects targets, and uses feedback to continuously improve sonar operation.
## Problem Statement
### Development of a Low-Power, Real-Time Adaptive Software-Defined Sonar Transmitter Payload for Autonomous Underwater Vehicles (AUVs)

Autonomous Underwater Vehicles (AUVs) are used for underwater exploration, mapping and monitoring. Sonar is an important part of these systems because it allows the vehicle to sense objects and the underwater surroundings. However, underwater conditions are not always the same. Changes in temperature, salinity, turbidity and depth can affect how sound travels through water.

Most conventional sonar systems work with predefined transmission settings. This means that when the underwater environment changes, the sonar may continue using the same frequency, pulse duration or transmission power even when those settings are no longer suitable. This can affect the quality of the received signal and may also waste the limited battery power of an AUV.

Our team, Prometheans, aims to address this problem by developing a compact and low-power software-defined sonar transmitter that can respond to changing underwater conditions in real time. The system will collect environmental data, process it using an embedded platform, and adjust important sonar parameters such as frequency, bandwidth, pulse duration and transmission power.

The goal is to make the sonar more flexible and energy-efficient, while keeping the system suitable for integration with a small AUV.

## Proposed Solution
Our proposed system is a compact, low-power and real-time adaptive sonar payload designed for an Autonomous Underwater Vehicle (AUV). Instead of keeping the sonar settings fixed throughout the mission, the system continuously monitors the underwater environment and adjusts the sonar parameters according to the conditions.

```text
Environmental Sensing
(Temperature • Salinity • Turbidity • Depth)
                ↓
        Data Collection
                ↓
        Data Processing
      (Filter & Validate)
                ↓
       Adaptive Decision
                ↓
    Select Sonar Parameters
(Frequency • Bandwidth • Pulse
 Duration • Waveform • TX Power)
                ↓
Software-Defined Waveform Generation
             (ESP32 + DAC)
                ↓
       Signal Conditioning
        (Filter + Amplifier)
                ↓
     Underwater Transmission
          (TX Transducer)
                ↓
        Echo Reception
           (Hydrophone)
                ↓
        Signal Processing
        (FFT / Filtering)
                ↓
    Range / SNR / Target
          Detection
                ↓
       Feedback Analysis
                ↓
    Update Sonar Parameters
                ↓
          Repeat Cycle
```
The main idea is to create a closed-loop system. Environmental conditions and received signal quality are continuously used to decide how the sonar should operate. This allows the system to adjust its transmission parameters instead of using one fixed setting throughout the mission.
## System Architecture


```text
                 UNDERWATER AUV SYSTEM
                         │
        ┌────────────────┴────────────────┐
        │                                 │
        ▼                                 ▼
 Environmental Sensors              Power System
        │                         (Battery + PMU)
        │                                 │
        └──────────────┬──────────────────┘
                       ▼
                 ESP32 Controller
                       │
        ┌──────────────┼──────────────┐
        │              │              │
        ▼              ▼              ▼
 Adaptive Algorithm  Data Logging   Communication
        │                             │
        ▼                             ▼
 Sonar Parameter                  Surface Gateway
 Selection                        / Dashboard
        │
        ▼
 Software-Defined
 Waveform Generation
        │
        ▼
     DAC / PWM
        │
        ▼
 Filter + Power Amplifier
        │
        ▼
 Underwater TX Transducer
        │
        ▼
     Acoustic Signal
        │
        ▼
       Target
        │
        ▼
   Echo / Reflected Signal
        │
        ▼
     Hydrophone
        │
        ▼
 Receiver Amplifier + Filter
        │
        ▼
       ADC
        │
        ▼
   ESP32 Signal Processing
        │
        ▼
 Range / SNR / Detection
        │
        └──────────► Feedback
                     │
                     ▼
              Adaptive Algorithm
```


## Hardware Components

The proposed system uses the following hardware components:

| Component | Purpose |
|---|---|
| **ESP32** | Main controller for sensor reading, adaptive decision-making, communication and signal processing |
| **Temperature Sensor (DS18B20)** | Measures underwater temperature |
| **Salinity / Conductivity Sensor** | Measures electrical conductivity to estimate salinity |
| **Turbidity Sensor** | Measures the clarity of water |
| **Pressure / Depth Sensor** | Measures underwater pressure and estimates depth |
| **DAC / Waveform Generator** | Converts the digitally generated sonar waveform into an analog signal |
| **Signal Filter** | Removes unwanted frequency components and improves signal quality |
| **Power Amplifier** | Increases the signal level before transmission |
| **Underwater TX Transducer** | Converts the electrical sonar signal into acoustic waves |
| **Hydrophone / RX Transducer** | Receives the reflected acoustic signal |
| **Receiver Amplifier / LNA** | Amplifies the weak received echo signal |
| **ADC** | Converts the received analog signal into digital data for processing |
| **Battery** | Provides power to the AUV system |
| **Power Management Unit (PMU)** | Regulates and distributes power to different components |
| **Communication Interface** | Transfers monitoring and mission data between the AUV and surface system |
| **Waterproof Enclosure** | Protects the electronics from water during underwater operation |

The design also focuses on low-power operation by controlling transmission power and pulse activity according to the requirements of the current environment.

By combining environmental sensing, adaptive decision-making, software-defined waveform generation, signal processing, and feedback, the proposed system aims to make underwater sensing more flexible, efficient, and suitable for small AUV platforms.
## Software & Technologies

Our system combines embedded programming, signal processing, and a web-based monitoring interface to control and monitor the adaptive sonar.

| Technology | Purpose |
|---|---|
| **ESP32** | Main controller for reading sensors, running the adaptive logic and controlling the sonar system |
| **Embedded C/C++** | Programming the ESP32 and handling sensors, control logic and hardware communication |
| **Signal Processing** | Processing the received sonar signal and extracting useful information such as SNR and target range |
| **FFT / Digital Filtering** | Used for analyzing the received signal and reducing unwanted noise |
| **DAC / PWM** | Used to generate the required sonar waveform |
| **Web Dashboard** | Displays sensor values, sonar parameters, signal quality and system status in real time |
| **Serial / Wired Communication** | Transfers data between the underwater system and the surface monitoring unit |
| **Data Logging** | Stores sensor and sonar data for testing, comparison and further analysis |
## Working principle
## ⚙️ Working Principle

The **Adaptive Software-Defined Sonar AUV** works as a closed-loop system. It continuously monitors underwater conditions and adjusts the sonar settings instead of using fixed parameters throughout the mission.

```text
Environmental Sensing
        ↓
Data Processing
        ↓
Adaptive Decision
        ↓
Sonar Parameter Selection
        ↓
Waveform Generation
        ↓
Underwater Transmission
        ↓
Echo Reception
        ↓
Signal Processing
        ↓
Range / SNR / Target Detection
        ↓
Feedback & Adaptation
        ↓
Update Sonar Parameters
        ↓
      Repeat
```
The ESP32 processes temperature, salinity, turbidity, and depth data to select suitable sonar parameters such as frequency, bandwidth, pulse duration, waveform, and transmission power. The transmitted signal is reflected by underwater targets and the returned echo is processed to estimate range and signal quality.

The system uses this information as feedback to continuously adapt its sonar operation while controlling transmission power and pulse activity for low-power operation.
## Uniqueness

Existing sonar systems and our proposed system both aim to improve underwater sensing, but our approach focuses on making the sonar more adaptive, compact, and suitable for a small AUV platform.

| Existing Approach | Our Approach – Prometheans |
|---|---|
| Sonar parameters may be predefined for a particular mission or operating condition | Parameters are adjusted based on changing environmental conditions and signal quality |
| Adaptation may require dedicated or higher-end hardware | We aim to implement the adaptive logic on a compact embedded platform |
| Systems can involve complex and expensive hardware | Focus on a low-cost and compact prototype |
| High transmission power may be used when conditions require it | Transmission power and pulse activity are adjusted to support low-power operation |
| Environmental data and sonar operation may be handled as separate functions | Environmental sensing is directly connected to the sonar adaptation process |
| Sonar configuration can be hardware-dependent | Software-defined waveform generation allows the waveform parameters to be changed through software |
| Monitoring may be provided separately from the sonar system | A monitoring dashboard can display environmental conditions, sonar parameters and system status |
| Large or specialized systems can be difficult to adapt for small AUVs | Designed with small-AUV integration and compact implementation in mind |

## Future scope

As Team Prometheans, we see this project as a starting point that can be further developed into a more capable underwater sensing system. Some of our planned improvements are:

Improve adaptive algorithms to make sonar parameter selection more accurate for different underwater conditions.
Extend the operating range by improving the transmitter, receiver, and signal-processing stages.
Add advanced target classification to distinguish between different types of underwater objects.
Improve energy management to increase the AUV's operating time.
Develop a compact and robust underwater enclosure suitable for longer underwater operation.
Add real-time surface monitoring for environmental data, sonar status, target information, and system health.

## Conclusion


As Team Prometheans, our aim is to develop a sonar system that can adapt to changing underwater conditions instead of depending on fixed settings. By combining environmental sensors, an ESP32-based controller, adaptive decision-making, and sonar signal processing, we want to make underwater sensing more flexible and reduce unnecessary power consumption.

The main idea behind our project is that the sonar should not continue working in the same way when the surrounding conditions change. It should use the available environmental data and feedback from received echoes to adjust its operating parameters whenever required. This can help improve signal quality while making better use of the limited battery power available in an Autonomous Underwater Vehicle (AUV).

Through this project, we are exploring how embedded systems and software-defined technology can be used to solve a real-world underwater engineering problem. We also understand that building a reliable underwater sonar system requires careful hardware selection, testing, and improvement. Our next step is to validate the design under different water conditions and improve its performance through practical experiments.

Our goal is to develop a compact, low-power, and affordable adaptive sonar prototype that can eventually support underwater exploration, monitoring, and mapping using small AUVs.

