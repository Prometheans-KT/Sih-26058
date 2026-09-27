# Prometheans

## Software defined sonar transmitter
SIH26058  --- An ESP32-Based Adaptive Sonar System that Continuously Monitors Environmental Conditions, Dynamically Adjusts Sonar Parameters, Measures Echo Response, Optimizes Transmission Power, and Provides Real-Time Feedback for Autonomous Underwater Vehicles

## 📑 Table of Contents

- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Proposed Solution](#proposed-solution)
- [System Architecture](#system-architecture)
- [Hardware Components](#hardware-components)
- [Working Principle](#working-principle)
- [Implementation](#implementation)
- [Results](#results)
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

##
