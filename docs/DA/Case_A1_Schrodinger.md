# Case A1: Schrödinger's Sisyphean Loop (Firmware Ver. 3.01)

## Revision History
| Rev. | Date | Description |
| :--- | :--- | :--- |
| 1.0  | 2026-04-20 | Initial report. 
| 1.1  | 2026-04-29 | Added verification that DISP button cannot restore the display while the LCD is closed (docked). 
| 1.2  | 2026-04-29 | Strictly distinguished between "[i] menu" and "Information display" in all test steps. Fixed inconsistency in Step 67. 
| 1.3  | 2026-04-30 | Clarified "Close" definition and removed redundant S0 reference in Setup to clarify state transitions. Changed the expression "Display [i] menu" to "Press [i] button". Added Steps 11 to 16. 
| 1.4  | 2026-05-01 | Title Update: Renamed the anomaly to "Schrödinger’s Sisyphean Loop".This better characterizes the non-deterministic nature of the UI: the return-path from the S3 (Menu) remains in a "superposition" of S1 (Live View) and S6 (Info-display), which collapses into an endless Sisyphean return to the Info-display once a setting is changed.
| 1.5  | 2026-05-04 | Added State S17, 18. Introduced the "Next State" column to all steps to better visualize unexpected state transitions and provide a more rigorous tracking of the Sisyphean loop. Refined the state definitions in the state transition table.
| 1.6  | 2026-05-14 |  Refined operational assessment criteria (E/N/M) and added display-control context definitions to distinguish user-observable behavior from inferred display-control consistency. 
| 1.7  | 2026-05-19 | Added Operational Notes. 
| 1.8  | 2026-05-20 | Partial correction of the table. 
| 1.9  | 2026-05-31 | Introduced structured display-control context notation:`Context <MonitorMode>(<AutoSwitch>; DP1-4=<enabled displays>; DP5=<ON/OFF>)`.<br> The change was made to better describe later observations involving Display 5 persistence, Live View display-index retention, and context-dependent recovery behavior.<br> Concurrently updated the relevant tables.|
| 2.0  | 2026-06-01 | Added Steps 157–176


---

## 1. Core Observation

*   **Phenomenon:** 
    - A shutter button half-press frequently fails to return the system to Live View, leaving the LCD locked on the Info screen.
    - The state persists across power cycles and long-term battery removal (10+ minutes).
*   **Core Issue:** 
    The Info screen appears to enter a “reject” state for standard operational inputs. Escape routes are limited and may be unintentionally disabled through user customization without warning.


### Figure 

![Figure A1-1: Persistent Info-Display Loop (Primary)](../../figures/Case_A1_Figure1.svg)
Source: [`Case_A1_Figure1.dot`](../../figures/Case_A1_Figure1.dot)

![Figure A1-2: Persistent Info-Display Loop (Primary)](../../figures/Case_A1_Figure2.svg)
Source: [`Case_A1_Figure2.dot`](../../figures/Case_A1_Figure2.dot)

---

## 2. Preparation and Settings

1. Start with a memory card that already contains saved images. If none are saved, take a picture to create and save image data.
2. Begin with the LCD monitor docked (folded into the body) with the screen facing you.
3. Initialize all camera settings. 
4. Attach a native Z-mount lens, an F-mount lens via FTZ, or a non-CPU manual focus lens, and remove the lens cap, as no lens-specific variations were observed in my scope of testing.
5. In [CUSTOM SETTINGS MENU] > [c3 Power off delay], set each item to the maximum duration.
6. In SETUP MENU > Limit monitor mode selection, select ONLY "Prioritize viewfinder (1 or 2)."
7. In SETUP MENU > Automatic monitor display switch, set it to "On (when monitor docked)."
8. Exit the menu so that nothing is displayed on the LCD monitor.
9. To avoid interference with the verification process, adjust the shutter speed as necessary so that it remains faster than approximately 1/60 s.
10. Power off, then on; wait 10 s.

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
| ▼ |  **Context** | **PV (OD; DP1-4=1,2,3,4; DP5=ON)**                                  |            |                                                                                               |                   |                                              |                   |
| 1    | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 2    | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 3    | S0            | Press [MENU] button                                           | S2         | Menu display                                | Off                 |   E    | E / N / M |
| 4    | S2            | Open LCD monitor                                              | S3         | Menu display                                | Off                 |   E    | E / N / M |
| 5    | S3            | Half-press shutter button                                     | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 6    | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 7    | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 8    | S4            | Open LCD monitor                                              | S5         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 9    | S5            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 10   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 11   | S7            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 12   | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 13   | S4            | Press [i] button                                              | S7         | Info display                                | Off                 |   E    | E / N / M |
| 14   | S7            | Open LCD monitor                                              | S6         | Info display                                | Off                 |   E    | E / N / M |
| 15   | S6            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 16   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 17   | S7            | Look into the EVF                                             | S8         | Nothing display                             | Live View display   |   E    | E / N / M |
| 18   | S8            | Move eye away from EVF                                        | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 19   | S0            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 20   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 21   | S7            | Half-press shutter button                                     | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 22   | S0            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 23   | S6            | Open LCD monitor to selfie position                           | S9         | Live View display (Selfie)                  | Off                 |   E    | E / N / M |
| 24   | S9            | Move LCD monitor back to less than 180 degrees                | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 25   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 26   | S7            | Press [MENU] button                                           | S2         | Menu display                                | Off                 |   E    | E / N / M |
| 27   | S2            | Open LCD monitor                                              | S3         | Menu display                                | Off                 |   E    | E / N / M |
| 28   | S3            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 29   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 30   | S7            | Power off; wait 10 s, then turn on and wait 10 s              | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 31   | S0            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 32   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 33   | S7            | Press playback button                                         | S10        | Images stored on the memory card displayed  | Off                 |   E    | E / N / M |
| 34   | S10           | Press playback button                                         | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 35   | S0            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 36   | S6            | Press playback button                                         | S11        | Images stored on the memory card displayed  | Off                 |   E    | E / N / M |
| 37   | S11           | Press playback button                                         | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 38   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 39   | S7            | Half-press shutter button                                     | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 40   | S0            | Press and hold the Fn button                                  | S12        | White balance adjustment displayed          | Off                 |   E    | E / N / M |
| 41   | S12           | Release the Fn button                                         | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 42   | S7            | Half-press shutter button                                     | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 43   | S0            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 44   | S6            | Press and hold the Fn button                                  | S13        | White balance adjustment displayed          | Off                 | **M**  | E / N / M |
| 45   | S13           | Release the Fn button                                         | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 46   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 47   | S7            | Power off -> battery removal -> wait 10 min -> reinstall -> Power on            | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 48   | S0            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 49   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 50   | S7            | Power off, then on; wait 10 s                                 | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 51   | S0            | Press and hold the Fn button                                  | S12        | White balance adjustment displayed          | Off                 |   E    | E / N / M |
| 52   | S12           | Release the Fn button                                         | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 53   | S7            | Half-press shutter button                                     | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 54   | S0            | Power off                                                     | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 55   | S0            | Open LCD monitor                                              | S14        | Nothing display                             | Off                 |   E    | E / N / M |
| 56   | S14           | Power on                                                      | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 57   | S6            | Press the DISP button                                         | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 58   | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 59   | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 60   | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 61   | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 62   | S4            | Open LCD monitor                                              | S5         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 63   | S5            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 64   | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 65   | S7            | Press the DISP button                                         | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 66   | S0            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 67   | S6            | Press the DISP button                                         | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 68   | S1            | Press and hold the Fn button                                  | S15        | Live View with the WB adjustment overlay    | Off                 |   E    | E / N / M |
| 69   | S15           | Release the Fn button                                         | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 70   | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 71   | S0            | Look into the EVF                                             | S8         | Nothing display                             | Live View display   |   E    | E / N / M |
| 72   | S8            | Press and hold the Fn button                                  | S16        | Nothing display                             | Live View display with the WB adjustment overlay |   E    | E / N / M |
| 73   | S16           | Release the Fn button                                         | S8         | Nothing display                             | Live View display   |   E    | E / N / M |
| 74   | S8            | Move eye away from EVF                                        | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 75   | S0            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 76   | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 77   | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 78   | S0            | Press [i] button; wait 1 s                                    | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 79   | S4            | Open LCD monitor; wait 1 s                                    | S5         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 80   | S5            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 81   | S6            | Press the DISP button                                         | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 82   | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 83   | S0            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 84   | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 85   | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 86   | S0            | Press [i] button; wait 10 s                                   | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 87   | S4            | Open LCD monitor; wait 10 s                                   | S5         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 88   | S5            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 89   | S6            | Press the DISP button                                         | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 90   | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 91   | S0            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 92   | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 93   | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 94   | S0            |In [CUSTOM SETTINGS MENU] > [c3 Power off delay], set Standby timer to 10 s, then exit | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 95   | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 96   | S4            | Open LCD monitor                                              | S5         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 97   | S5            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 98   | S6            | Wait until the standby timer activates and <br> the LCD goes dark , then wait another 1 s                     | S14        | Nothing display                             | Off                 |   E   | E / N / M |
| 99   | S14           | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 100  | S6            | Press the DISP button                                         | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 101  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 102  | S0            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 103  | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 104  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 105  | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 106  | S4            | Open LCD monitor                                              | S5         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 107  | S5            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 108  | S6            | Wait until the standby timer activates and <br> the LCD goes dark , then wait another 10 s                    | S14        | Nothing display                             | Off                 |   E    | E / N / M |
| 109   | S14          | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 110   | S6           | Press the DISP button                                         | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 111  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 112  | S0            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 113  | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 114  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 115  | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 116  | S4            | Open LCD monitor                                              | S5         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 117  | S5            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 118  | S6            | Wait until the standby timer activates and <br> the LCD goes dark , then wait another 30 s                     | S14        | Nothing display                             | Off                 |   E    | E / N / M |
| 119  | S14           | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 120  | S6            | Press the DISP button                                         | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 121  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 122  | S0            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 123  | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 124  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 125  | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 126  | S4            | Open LCD monitor                                              | S5         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 127  | S5            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 128  | S6            | Half-press the shutter button as soon as the LCD is fully dark| S6         | Info display                                | Off                 | **N**  | E / N / M |
| 129  | S6            | Press the DISP button                                         | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 130  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 131  | S0            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 132  | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 133  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 134  | S0            |In [CUSTOM SETTINGS MENU] > [c3 Power off delay], set Standby timer to No limit, then exit | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 135  | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 136  | S4            | Open LCD monitor                                              | S5         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 137  | S5            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 138  | S6            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 139  | S0            | Power off                                                     | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 140  | S0            | remove the memory card; no specific timing is required        | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 141  | S0            | Power on;wait 10 s                                            | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 142  | S0            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 143  | S6            | Press the DISP button                                         | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 144  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 145  | S0            | Power off                                                     | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 146  | S0            | Reinsert the memory card; no specific timing is required      | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 147  | S0            | Power on;wait 10 s                                            | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 148  | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 149  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 150  | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 151  | S4            | Open LCD monitor                                              | S5         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 152  | S5            | Half-press shutter button                                     | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 153  | S6            | Press the shutter button all the way down to capture an image; no specific timing is required  | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 154  | S6            | Press playback button                                         | S11        | Images stored on the memory card displayed  | Off                 |   E    | E / N / M |
| 155  | S11           | Press playback button                                         | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 156  | S6            | Close LCD monitor                                             | S7         | Info display                                | Off                 | **N**  | E / N / M |
| 157  | S7            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N**  | E / N / M |
| 158  | S6            | Press the DISP button                                         | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 159  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 160  | S0            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 161  | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 162  | S4            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 163  | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 164  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 165  | S0            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 166  | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 167  | S4            | Half-press shutter button                                     | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 168  | S0            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 169  | S0            | Open LCD monitor                                              | S1         | Live View display                           | Off                 |   E    | E / N / M |
| 170  | S1            | Close LCD monitor                                             | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 171  | S0            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 172  | S0            | Press [i] button                                              | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 173  | S4            | Open LCD monitor                                              | S5         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 174  | S5            | Close LCD monitor                                             | S4         | Info display with [i] menu overlay          | Off                 |   E    | E / N / M |
| 175  | S4            | Power off; wait 3 s, then turn on and wait 10 s               | S0         | Nothing display                             | Off                 |   E    | E / N / M |
| 176  | S0            | Open LCD monitor                                              | S6         | Info display                                | Off                 | **N**  | E / N / M |

---

### Observational Notes

#### Steps 1–6

These steps examine the behavior of the MENU screen when the LCD monitor is opened or closed.

The observed behavior is consistent with long-standing Nikon operational expectations: opening or closing the LCD monitor does not by itself dismiss the MENU screen. This suggests that preserving the MENU screen across LCD monitor movement is likely consistent with Nikon’s intended display behavior.

#### Steps 7–16 and Steps 160–176

These steps examine the phenomenon that originally motivated this repository: under certain conditions, the camera cannot exit the Info display on the LCD by shutter-button half-press, and Live View is not restored.

Comparison of Steps 9 and 15 with Steps 5 and 21 suggests that persistent fixation becomes visible after an LCD monitor displaying the Info screen while docked is opened and then followed by shutter-button half-press.

However, Step 176 suggests that shutter-button half-press may be only one trigger that reveals the fixation. The fixation condition may already have been established when the LCD monitor was opened while the Info display was present in the docked-LCD state.

Under `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`, opening the LCD monitor should normally activate the LCD shooting display and restore Live View. Instead, the Info display remains. This suggests that the transition from docked LCD to active LCD may be a critical point at which the Info display becomes persistently retained.

#### Steps 17–74 and Steps 135–146

These steps record multiple attempts to escape after the persistent Info state had appeared.

The following operations did not successfully restore normal Live View operation:

* moving the eye away from the EVF (Step 19)
* opening the LCD monitor into self-portrait position (Step 23)
* entering and exiting the MENU screen (Step 28)
* power cycling (Step 30)
* entering and exiting image playback from the memory card (Steps 35 and 37)
* operating the Fn button and releasing the WB adjustment display (e.g., Step 41)
* removing the battery for an extended period (Step 47)
* operating the DISP button while the LCD monitor was docked (Steps 65–66)
* removing the memory card (Step 142)

During these observations, the Fn button was also found to provide another route into an Info-related display state, because releasing the WB adjustment display could return the camera to the Info display.

The only successful recovery path observed in this sequence was pressing the DISP button while the LCD monitor was open (Steps 57–59).

This observation was made under `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`. In this context, an open LCD monitor normally corresponds to an active LCD shooting display. Therefore, pressing the DISP button while the LCD monitor is open can be interpreted as operating DISP while the LCD is in, or expected to be in, a shooting-display context.

By contrast, when the LCD monitor is docked, the LCD is not normally in an active shooting-display state. Instead, the camera is effectively waiting for EVF activation via the eye sensor. Therefore, pressing the DISP button while the LCD monitor is docked appears to operate in a different display-routing context.

Because this DISP operation with the LCD monitor open was the only reliable recovery method observed in this sequence, it is used several times later in the table to proceed to subsequent observations.

#### Steps 75–90

These steps examine whether the transition into persistent fixation depends on operation timing.

The results suggest that the observed fixation behavior is not merely a timing artifact. Changing the interval between operations did not appear to prevent the transition into the persistent Info state.

#### Steps 91–134

These steps examine whether standby / sleep behavior affects recovery from the persistent Info state.

The observations suggest that returning from standby does not by itself clear the persistent Info state. The fixation remains after sleep and wake sequences under several tested timings.

#### Notes on Steps 5, 28, 163, and 176

Steps 5 and 28 are especially important because they appear visually identical from the user’s perspective: in both cases, under the same settings, the LCD monitor is open and the MENU screen is displayed. However, shutter-button half-press produces different results.

Similarly, Steps 163 and 176 appear visually identical from the user’s perspective: in both cases, under the same settings, the camera has just been powered on. However, opening the LCD monitor produces different results.

These observations indicate that the visible display state alone is not sufficient to predict the next transition. Prior display-routing history affects subsequent behavior, even when the current visible state appears identical.


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






