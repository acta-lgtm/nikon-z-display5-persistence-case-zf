# Case A2: Deterministic Loop: Immediate Transition from Default Settings (Firmware Ver. 3.01)

## Revision History
| Rev. | Date | Description |
| :--- | :--- | :--- |
| 1.0 | 2026-05-04 | Initial report. |
| 1.1 | 2026-05-05 | Added Thought experiment. |
| 1.2 | 2026-05-06 | Added states. Refined the title to more accurately reflect the inevitable progression from factory settings to the inescapable state. |
| 1.3 | 2026-05-14 | Refined operational assessment criteria (E/N/M) and added display-control context definitions to distinguish user-observable behavior from inferred display-control consistency. 
| 1.4 | 2026-05-31 | Introduced structured display-control context notation:`Context <MonitorMode>(<AutoSwitch>; DP1-4=<enabled displays>; DP5=<ON/OFF>)`.<br> The change was made to better describe later observations involving Display 5 persistence, Live View display-index retention, and context-dependent recovery behavior.<br> Concurrently updated the relevant tables.|

---

## 1. Core Observation

* **Phenomenon:**
    Immediate Info-display persistence can be triggered by a minimal operation immediately after initialization. Furthermore, depending on subsequent configurations, user customization may unintentionally restrict or eliminate immediate escape routes without warning.

* **Core Issue:**
    A minimal operation can transition the system from a factory-default state into a persistent Info-display loop. Furthermore, it was verified that this persistent state can degrade into an effectively inescapable loop even under configuration profiles different from those observed in Case A1.

### Figure 

![Figure A2-1](../../figures/Case_A2_Figure1.svg)

Source: [`Case_A2_Figure1.dot`](../../figures/Case_A2_Figure1.dot)

This figure focuses on the first half of Case A2, where Info-display persistence is entered immediately from the factory-default display configuration. Later observations involving Monitor only mode and restricted recovery paths are described in the transition table rather than in this simplified diagram.

---

## 2. Preparation and Settings

1. Begin with the LCD monitor docked (folded into the body) with the screen facing you.
2. Initialize all camera settings.
3. Attach a native Z-mount lens, an F-mount lens via FTZ, or a non-CPU manual focus lens, and remove the lens cap, as no lens-specific variations were observed in my scope of testing.
4. In [CUSTOM SETTINGS MENU] > [c3 Power off delay], set each item to the maximum duration.
5. To avoid interference with the verification process, adjust the shutter speed as necessary so that it remains faster than approximately 1/60 s.
6. Power off.

---

## 3. Experimental Contexts

### Display Control Context Notation

Contexts are written in the following form:

`Context <MonitorMode>(<AutoSwitch>; DP1-4=<enabled displays>; DP5=<ON/OFF>)`

> MonitorMode
 
>- `PV` = Prioritize viewfinder (1 or 2)
>- `AS` = Automatic display switch
>- `MO` = Monitor only

> AutoSwitch

>- `O` = Automatic monitor display switch: On
>- `OD` = Automatic monitor display switch: On (when monitor docked)
>- `-` = Not applicable or not changed in this context

> DP1-4, DP5

>- `DP1-4=1,2,3,4` means Display 1 through Display 4 are enabled in [d19 Custom monitor shooting display].
>- `DP1-4=1` means only Display 1 is enabled.
>- `DP1-4=none` means none of Display 1 through Display 4 is enabled.
>- `DP5=ON/OFF` indicates whether Display 5 (“Info”) is enabled.


Example: `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`


### Assessment Codes
> For details on the evaluation ratings (E / N / M), please refer to the [Assessment Codes](../../README.md#assessment-codes) in the main README.
---

## 4. State Transition Table (Definition A)


> [!NOTE]
> Some states defined in this document are visually indistinguishable
> from one another, yet exhibit different operational behavior
> depending on prior display-routing history and monitor context.

### Operational Notes

- Unless otherwise specified, “Open LCD monitor” refers to opening the monitor to at least 20° but less than 140° (to avoid entering self-portrait mode), while keeping the LCD active and allowing viewfinder status checks without triggering the eye sensor.

- Unless otherwise specified, keep your eye and other objects away from the viewfinder to prevent eye sensor activation.

- Unless otherwise specified, perform each operation with an interval of at least three seconds between actions.

- Throughout this table, “closing the LCD” refers to returning the monitor to the docked position with the screen facing the user, as defined in the initial setup.

- WB = White balance.



| Step | Current State | Operation                                                     | Next State | LCD Status                                  | EVF Status | My Assessment | Your Assessment             |
| :--- | :------------ | :------------------------------------------------------------ | :--------- | :------------------------------------------ | :------------------ | :----- | :-------- |
| ▼ |  **Context** | **AS (O; DP1-4=1,2,3,4; DP5=ON)**                                    |            |                                                                                               |                   |                                              |                   |
| 1    | S0            | Power on                                                      | S17        | Live View display                           | Off                 |   E   | E / N / M |
| 2    | S17           | Press DISP button repeatedly until Info display is shown      | S7         | Info display                                | Off                 |   E   | E / N / M |
| 3    | S7            | Power off, then on                                            | S7         | Info display                                | Off                 | **N** | E / N / M |
| 4    | S7            | Half-press shutter button                                     | S7         | Info display                                | Off                 | **N** | E / N / M |
| 5    | S7            | Look into the EVF                                             | S8         | Nothing display                             | Live View display   |   E   | E / N / M |
| 6    | S8            | Move eye away from EVF                                        | S7         | Info display                                | Off                 | **N** | E / N / M |
| 7    | S7            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N** | E / N / M |
| 8    | S6            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N** | E / N / M |
| 9    | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N** | E / N / M |
| 10   | S7            | Press the DISP button                                         | S17        | Live View display                           | Off                 |   E   | E / N / M |
| 11   | S17           | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E   | E / N / M |
| 12   | S1            | Close LCD monitor                                             | S17        | Live View display                           | Off                 |   E   | E / N / M |
| 13   | S17           | Power off, then on                                            | S17        | Live View display                           | Off                 |   E   | E / N / M |
| 14   | S17           | Press DISP button repeatedly until Info display is shown      | S7         | Info display                                | Off                 |   E   | E / N / M |
| 15   | S7            | Power off, then on                                            | S7         | Info display                                | Off                 | **N** | E / N / M |
| ▼ |  **Context** | **MO (-; DP1-4=1,2,3,4; DP5=ON)**                                    |            |                                                                                               |                   |                                              |                   |
| 16   | S7            | In [SETUP MENU] > [Limit monitor mode selection], <br>select ONLY "Monitor only", then exit | S7 | Info display                                | Off                 | **N** | E / N / M |
| 17   | S7            | In [CUSTOM SETTINGS MENU] > [f2 Custom controls (shooting)], <br>set DISP button  to "OFF None", then exit| S7 | Info display                                | Off                 | **N** | E / N / M |
| 18   | S7            | Power off, then on                                            | S7         | Info display                                | Off                 | **N** | E / N / M |
| 19   | S7            | Half-press shutter button                                     | S7         | Info display                                | Off                 | **N** | E / N / M |
| 20   | S7            | Look into the EVF                                             | S7         | Info display                                | Off                 |   E   | E / N / M |
| 21   | S7            | Move eye away from EVF                                        | S7         | Info display                                | Off                 | **N** | E / N / M |
| 22   | S7            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N** | E / N / M |
| 23   | S6            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N** | E / N / M |
| 24   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N** | E / N / M |
| 25   | S7            | Press the DISP button                                         | S7         | Info display                                | Off                 | **M** | E / N / M |
| 26   | S7            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N** | E / N / M |
| 27   | S6            | Press the DISP button                                         | S6         | Info display                                | Off                 | **M** | E / N / M |
| 28   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N** | E / N / M |
| 29   | S7            | Press and hold the Fn button                                  | S12        | WB adjustment displayed          | Off                 |   E   | E / N / M |
| 30   | S12           | Release the Fn button                                         | S7         | Info display                                | Off                 | **N** | E / N / M |
| 31   | S7            | Power off, then on                                            | S7         | Info display                                | Off                 | **N** | E / N / M |
| 32   | S7            | Half-press shutter button                                     | S7         | Info display                                | Off                 | **N** | E / N / M |
| 33   | S7            | Power off, then on                                            | S7         | Info display                                | Off                 | **N** | E / N / M |
| 34   | S7            | Half-press shutter button                                     | S7         | Info display                                | Off                 | **N** | E / N / M |
| 35   | S7            | Power off -> battery removal -> wait 10 min -> reinstall      | S0         | Nothing display                             | Off                 |   E   | E / N / M |
| 36   | S0            | Power on                                                      | S7         | Info display                                | Off                 | **N** | E / N / M |
| 37   | S7            | Power off                                                     | S0         | Nothing display                             | Off                 |   E   | E / N / M |

---
### Observational Notes

#### Steps 1–15

These steps observe the transition into persistent fixation and subsequent recovery under the factory-default display configuration:

`Context AS(O; DP1-4=1,2,3,4; DP5=ON)`

The observations indicate that, immediately after power-on, operating the DISP button while the LCD monitor is docked can lead to persistent Info fixation (Steps 3, 4, and 6).

Unlike Case A1, recovery by pressing the DISP button was possible even while the LCD monitor remained docked (Step 10).

It should be noted that, under this context, when the eye is away from the EVF, the LCD monitor is normally expected to remain in an active shooting-display state.

#### Steps 16–37

These steps continue from the fixation state observed in Step 15. The camera was then switched to:

`Context MO(-; DP1-4=1,2,3,4; DP5=ON)`

In addition, the DISP button function was disabled. Under this context, the EVF is unavailable.

Several recovery attempts were then tested, but none successfully restored a usable Live View shooting display:

* shutter-button half-press (Steps 19 and 23)
* moving the eye away from the EVF (Step 21)
* DISP button operation (Steps 25 and 27)
* Fn button operation (Step 30)
* power cycling (Step 31)
* battery removal for 10 minutes (Step 36)

Because the DISP button function had been disabled in this context, a quick and reliable recovery from the fixation state would likely be extremely difficult in practical shooting situations.



---

### Observed Recovery Paths

The following operations were observed to terminate,
bypass, or prevent persistent Info-display states
under at least some tested conditions:

- Pressing DISP while the LCD monitor remained active
- Reassigning the "DISP Cycle view info display" function
  to a custom button and then pressing it
  (not to be confused with "Live view info display off")
- Disabling "Display 5" in:
  [CUSTOM SETTINGS MENU] >
  [d19 Custom monitor shooting display]
- Initializing camera settings




