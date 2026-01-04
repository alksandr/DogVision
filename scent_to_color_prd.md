# 🐶 Product Requirements Document (PRD)
## Dog Vision — Spatial Scent-to-Color Visualization System

**Product Name:** Dog Vision  
**Version:** 1.1  
**Status:** Draft  
**Owner:** Aleksandr Surguy
**Last Updated:** 1/4/2026

---

## 1. Overview

### 1.1 Purpose
Dog Vision is a hardware + software system that allows humans to **see smell** by converting spatial scent intensity into a visual map on a monitor. A rod-mounted sensor array scans the environment, collects smell data over space, and renders it as a **blue-intensity heatmap**, providing a visual analogue of how dogs perceive scent landscapes.

---

## 2. Problem Statement

Humans lack the ability to perceive spatial scent information directly, while animals like dogs rely heavily on smell for navigation, detection, and understanding of their environment. There is no consumer or research-grade tool that provides a **real-time spatial visualization of smell**.

Dog Vision solves this by:
- Digitizing ambient odors,
- Mapping them into spatial data,
- Visualizing them as color on a screen.

---

## 3. Goals

- Enable real-time spatial mapping of scent intensity.
- Convert scent intensity into a blue color channel on a display.
- Provide a simple and intuitive visual representation of smell distribution.
- Enable research, education, accessibility, and artistic applications.

---

## 4. Target Users

### Primary
- Researchers (olfaction, robotics, animal behavior)
- Developers and engineers
- Accessibility technology developers

### Secondary
- Artists and installation designers
- Educators
- Science museums / exhibits

---

## 5. Key Use Case

**Dog Vision Mode:**  
A user moves a sensor rod through an environment. The system collects smell data at different positions and renders a live 2D color map on a screen, where:

- X/Y = physical scan position  
- Blue intensity = scent strength  

Result: A visual "smell landscape".

---

## 6. Functional Requirements

### 6.1 Sensing
- The system shall include a rod-mounted electronic nose (multi-sensor VOC array).
- The system shall sample scent at ≥ 5 Hz per sensor.
- The system shall timestamp and spatially index each reading.

---

### 6.2 Data Processing
- Raw sensor values must be normalized into a 0–255 range.
- The system must support smoothing and filtering to reduce noise.
- The system must support calibration for baseline ambient smell.

---

### 6.3 Spatial Mapping
- Each sensor reading shall be associated with a spatial coordinate.
- The system shall build a 2D or 3D scent intensity grid.
- The system shall interpolate between points for continuous maps.

---

### 6.4 Visualization
- The system shall display a real-time heatmap on a monitor.
- Blue channel intensity shall represent scent intensity.
- The display shall update within 500 ms of new data.
- The system shall support playback of recorded scans.

---

### 6.5 Calibration
- The system shall provide a calibration workflow for:
  - Baseline air
  - Known scent references
  - Sensor drift correction

---

## 7. Non-Functional Requirements

| Category | Requirement |
|----------|-------------|
| Latency | ≤ 500 ms end-to-end |
| Stability | No crashes during 8-hour operation |
| Accuracy | ±5% repeatability under same conditions |
| Portability | Rod weight ≤ 1 kg |
| Extensibility | Modular sensors and visualization |

---

## 8. Technical Architecture

### Hardware
- Multi-sensor VOC / gas sensor array
- Microcontroller or SBC (ESP32 / Raspberry Pi)
- Position tracking (IMU or external tracker)
- Power source (battery or USB)

### Software
- Firmware for sensor acquisition
- Processing pipeline for normalization + smoothing
- Visualization client (web, desktop, or Unity)

### Communication
- USB, Wi-Fi, or Bluetooth

---

## 9. Data Flow

Sensor Rod → Microcontroller → Normalize → Map to Spatial Grid → Render on Screen

yaml
Copy code

---

## 10. Risks & Mitigations

| Risk | Mitigation |
|------|------------|
| Sensor noise | Filtering + averaging |
| Sensor drift | Scheduled recalibration |
| Environmental variability | Temperature/humidity compensation |
| Slow response | Reduce smoothing window |

---

## 11. Milestones

| Phase | Duration | Outcome |
|-------|----------|----------|
| Requirements | 1 week | Approved PRD |
| Hardware Prototype | 3 weeks | Functional rod |
| Firmware | 2 weeks | Stable sensor pipeline |
| Visualization | 3 weeks | Real-time heatmap |
| Testing | 2 weeks | Validated system |
| Documentation | 1 week | Public release |

---

## 12. Success Criteria

- User can scan an environment and observe a coherent smell heatmap.
- The blue channel changes consistently with scent presence.
- The system runs reliably for extended sessions.

---

## 13. Glossary

- **VOC:** Volatile Organic Compound  
- **Electronic Nose:** Multi-sensor smell detection system  
- **Smell Heatmap:** Visual spatial representation of scent intensity  
- **Blue Channel:** The B component of RGB used for scent mapping  

---
