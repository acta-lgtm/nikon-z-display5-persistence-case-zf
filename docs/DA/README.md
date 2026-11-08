# Phase 1: Definition A (Coarse-grained Analysis)

This directory contains the "coarse-grained" state definitions used at the onset of observing the Nikon Z f, along with the corresponding analysis results.

## 1. State Definitions
To maintain objectivity, each state is defined by a combination of LCD physical position, LCD display content, and EVF status.

- State S0 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  EVF off

- State S1 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Live View displayed on the LCD monitor \
  EVF off

- State S2 \
  LCD monitor docked \
  Menu displayed on the LCD monitor \
  EVF off

- State S3 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Menu displayed on the LCD monitor \
  EVF off

- State S4 \
  LCD monitor docked \
  Info display with [i] menu overlay on the LCD monitor \
  EVF off

- State S5 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Info display with [i] menu overlay on the LCD monitor \
  EVF off

- State S6 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Info displayed on the LCD monitor \
  EVF off

- State S7 \
  LCD monitor docked \
  Info displayed on the LCD monitor \
  EVF off

- State S8 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View displayed in the EVF

- State S9 \
  LCD monitor opened to the selfie position (180 degrees) \
  Live View (Selfie mode) displayed on the LCD monitor \
  EVF off

- State S10 \
  LCD monitor docked \
  Images stored on the memory card displayed on the LCD monitor \
  EVF off

- State S11 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Images stored on the memory card displayed on the LCD monitor \
  EVF off

- State S12 \
  LCD monitor docked \
  White balance adjustment displayed on the LCD monitor \
  EVF off

- State S13 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  White balance adjustment displayed on the LCD monitor \
  EVF off

- State S14 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Nothing displayed on the LCD monitor \
  EVF off

- State S15 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Live View with the WB adjustment overlay displayed on the LCD monitor \
  EVF off

- State S16 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with the WB adjustment overlay displayed in the EVF

- State S17 \
  LCD monitor docked \
  Live View displayed on the LCD monitor \
  EVF off

---

## 2. Analyzed Cases

Detailed transition diagrams and transition tables are provided for the following two cases.

### [Case A1: Schrödinger's Sisyphean Loop](./Case_A1_Schrodinger.md)

Observation of the initial entry into the loop, subsequent escape attempts in which the Info display persistently remains on the LCD, and cases where visually identical states exhibit different operational behaviors.

### [Case A2: Deterministic Loop: Immediate Transition from Default Settings](./Case_A2_Deterministic.md)

Observation of immediate Info-display persistence triggered by a minimal operation after initialization. Furthermore, depending on subsequent configurations, user customization may unintentionally restrict or eliminate immediate escape routes without warning.

---

## 3. Methodology
- **Visualization Tool:** Graphviz (dot)
- **Recording Method:** State transition tables generated from logs of altered operation sequences and settings.

