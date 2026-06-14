# Case B3: Cornering the Shadow: A Trace from the Past (Firmware Ver. 3.01)

> Created: 2026-05-13 | Published: 2026-05-17 | Last Updated: 2026-06-14

---

### 1. Core Observation

### [Case B3: Cornering the Shadow: A Trace from the Past](./Case_B3_Cornering.md)
*   **Phenomenon:**
    - Based on the observations up to this point, it was hypothesized that grasping the behavior of the Info display—rather than the [i] menu overlay—holds the key to understanding the overall behavior of this camera.
    - Consequently, detailed observations were conducted, with a particular focus on the pathways leading to screen lockups and their relationship with the opening and closing of the LCD.
    - The results revealed that not only the physical state of opening or closing the LCD, but also the active monitor mode at that moment, serves as a crucial factor determining whether or not the Info display becomes locked.
*   **Core Issue:**
    The screen lockup on the Info display is governed not merely by the physical state of the LCD, but by a multi-layered interaction that includes the active software-driven monitor mode.


---

## 2. Preparation and Settings

1. Begin with the LCD monitor docked (folded into the body) with the screen facing you.
2. Initialize all camera settings. 
3. Attach a native Z-mount lens, an F-mount lens via FTZ, or a non-CPU manual focus lens, and remove the lens cap, as no lens-specific variations were observed in my scope of testing.
4. In **[CUSTOM SETTINGS MENU] > [d19 Custom monitor shooting display]**, check **Display 1 and Display 5** (leaving Display 2–4 unchecked), ensure Display 1 is selected, then exit.
5. In **[CUSTOM SETTINGS MENU] > [c3 Power off delay]**, set each item to the maximum duration.
6. In **[SETUP MENU] > [Automatic monitor display switch]**, set it to **"On (when monitor docked)"**,then exit the menu.
7. Use the Monitor mode button to set it to **"Prioritize viewfinder (1 or 2)"**.
8. To avoid interference with the verification process, adjust the shutter speed as necessary so that it remains faster than approximately 1/60 s.
9. Power off, then on; wait 10 seconds.



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

---

### Assessment Codes

> [!NOTE]
> For details on the evaluation ratings (E / N / M), please refer to the [Assessment Codes](../../README.md#assessment-codes) in the main README.

---

## 4. State Transition Table (Definition B)

> [!NOTE]
> Some states defined in this document are visually indistinguishable
> from one another, yet exhibit different operational behavior
> depending on prior display-routing history and monitor context.


> [!NOTE]
> In the following tables, display overlays are abbreviated as
> “DP1” through “DP5”, corresponding to the selectable display modes
> configured under [d19 Custom monitor shooting display].

> For example:

> - “Live View (with DP1)” indicates Live View with Display 1 overlay.


> [!NOTE]
> For detailed distinctions between visually similar Info states,
> see "Info-State Classification" in the DB README.


### Operational Notes

- Unless otherwise specified, “Open LCD monitor” refers to opening the monitor to at least 20° but less than 140° (to avoid entering self-portrait mode), while keeping the LCD active and allowing viewfinder status checks without triggering the eye sensor.

> [!NOTE]
 Throughout this document, “closing the LCD monitor” includes
returning the monitor to any angle below the LCD activation threshold,
even if the monitor is not fully docked.
Conversely, “opening the LCD monitor” refers to opening the monitor
beyond the threshold at which the LCD display becomes active.

- Unless otherwise specified, keep your eye and other objects away from the viewfinder to prevent eye sensor activation.

- Unless otherwise specified, perform each operation with an interval of at least three seconds between actions.

- Throughout this table, “closing the LCD” refers to returning the monitor to the docked position with the screen facing the user, as defined in the initial setup.

- WB = White balance.

- with [i] menu = with [i] menu overlay.




| Step | Current State | Operation                                                     | Next State | LCD Status                                  | EVF Status | My Assessment | Your Assessment             |
| :--- | :------------ | :------------------------------------------------------------ | :--------- | :------------------------------------------ | :------------------ | :----- | :-------- |
| ▼ |  **Context** | **PV (OD; DP1-4=1,2,3,4; DP5=ON)**                                    |            |                                                                                               |                   |                                              |                   |
| 1    | S0            | Open LCD monitor, then press DISP button                                                                                                     | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 2    | S22           | Half-press shutter button                                                                                                                    | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 3    | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 4    | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 5    | S22           | Press [i] button                                                                                                                             | S30        | Live View with [i] menu      | Off        |   E   | E / N / M |
| 6    | S30           | Half-press shutter button                                                                                                                    | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 7    | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 8    | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 9    | S22           | Press DISP button repeatedly until Display 5=Info is shown                                                                                   | S25        | Info display (explicit DP5 route; DP5 ON) | Off        |   E   | E / N / M |
| 10   | S25           | Close LCD monitor                                                                                                                            | S21        | Info display (explicit DP5 route; DP5 ON) | Off        |   E   | E / N / M |
| 11   | S21           | Open LCD monitor                                                                                                                             | S25        | Info display (explicit DP5 route; DP5 ON) | Off        |   E   | E / N / M |
| 12   | S25           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 13   | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 14   | S0            | Open LCD monitor, then press DISP button                                                                                                     | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 15   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 16   | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 17   | S22           | Press DISP button repeatedly until Display 5=Info is shown                                                                                   | S25        | Info display (explicit DP5 route; DP5 ON) | Off        |   E   | E / N / M |
| 18   | S25           | Half-press shutter button                                                                                                                    | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 19   | S38           | Close LCD monitor                                                                                                                            | S37        | Info display (persistent fixation)   | Off        | **M** | E / N / M |
| 20   | S37           | Open LCD monitor                                                                                                                             | S38        | Info display (persistent fixation)   | Off        | **M** | E / N / M |
| 21   | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 22   | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 23   | S0            | Open LCD monitor, then press DISP button                                                                                                     | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 24   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 25   | S0            | Press [i] button                                                                                                                             | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 26   | S4            | Press [i] button                                                                                                                             | S7         | Info display (non-DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 27   | S7            | Power off, then on; wait 10 s                                                                                                                | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 28   | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 29   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 30   | S0            | Press [i] button                                                                                                                             | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 31   | S4            | Power off, then on; wait 10 s                                                                                                                | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 32   | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 33   | S2            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 34   | S0            | Press DISP button                                                                                                                            | S7         | Info display (non-DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 35   | S7            | Power off, then on; wait 10 s                                                                                                                | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 36   | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 37   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 38   | S0            | Press [i] button                                                                                                                             | S4         | Info display with [i] menu   | Off        |   E   | E / N / M |
| 39   | S4            | Press [i] button                                                                                                                             | S7         | Info display (non-DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 40   | S7            | Open LCD monitor                                                                                                                             | S6         | Info display (non-DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 41   | S6            | Close LCD monitor                                                                                                                            | S7         | Info display (non-DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 42   | S7            | Power off, then on; wait 10 s                                                                                                                | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 43   | S0            | Open LCD monitor                                                                                                                             | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 44   | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 45   | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 46   | S0            | Open LCD monitor, then press DISP button                                                                                                     | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 47   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 48   | S0            | Press [i] button                                                                                                                             | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 49   | S4            | Open LCD monitor                                                                                                                             | S5         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 50   | S5            | Close LCD monitor                                                                                                                            | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 51   | S4            | Power off, then on; wait 10 s                                                                                                                | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 52   | S0            | Open LCD monitor                                                                                                                             | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 53   | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 54   | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 55   | S0            | Open LCD monitor, then press DISP button                                                                                                     | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 56   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 57   | S0            | Press DISP button                                                                                                                            | S7         | Info display (non-DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 58   | S7            | Open LCD monitor                                                                                                                             | S6         | Info display (non-DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 59   | S6            | Close LCD monitor                                                                                                                            | S7         | Info display (non-DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 60   | S7            | Power off, then on; wait 10 s                                                                                                                | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 61   | S0            | Open LCD monitor                                                                                                                             | S38        | Info display (persistent fixation)    | Off        | **N** | E / N / M |
| 62   | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 63   | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 64   | S0            | Open LCD monitor, then press DISP button                                                                                                     | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 65   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 66   | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 67   | S22           | Press [i] button                                                                                                                             | S30        | Live View with [i] menu      | Off        |   E   | E / N / M |
| 68   | S30           | Power off, then on; wait 10 s                                                                                                                | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 69   | S22           | Press DISP button repeatedly until Info display is shown                                                                                     | S25        | Info display (explicit DP5 route; DP5 ON)      | Off        |   E   | E / N / M |
| 70   | S25           | Power off, then on; wait 10 s                                                                                                                | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 71   | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 72   | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M 
| 73   | S0            | Power off, then on; wait 10 s                                                                                                                | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 74   | S0            | Open LCD monitor, then press DISP button                                                                                                     | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 75   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 76   | S0            | Press DISP button                                                                                                                            | S7         | Info display (non-DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 77   | S7            | Power off, then on; wait 10 s                                                                                                                | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 78   | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 79   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 80   | S0            | Press DISP button                                                                                                                            | S7         | Info display (non-DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 81   | S7            | Half-press shutter button, then unpress and wait 10s                                                                                         | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 82   | S0            | Power off, then on; wait 10 s                                                                                                                | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 83   | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 84   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 85   | S0            | Press [i] button                                                                                                                             | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 86   | S4            | Half-press shutter button, then unpress and wait 10s                                                                                         | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 87   | S0            | Power off, then on; wait 10 s                                                                                                                | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 88   | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 89   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 90   | S0            | Press [i] button                                                                                                                             | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 91   | S4            | Press [i] button                                                                                                                             | S7         | Info display (non-DP5 route; DP5 ON)      | Off        |   E   | E / N / M |
| 92   | S7            | Half-press shutter button, then unpress and wait 10s                                                                                         | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 93   | S0            | Power off, then on; wait 10 s                                                                                                                | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 94   | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 95   | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M 
| 96   | S0            | Initialize all camera settings, <br> In [CUSTOM SETTINGS MENU] > [c3 Power off delay], <br> set each item to the maximum duration, exit menu | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 97   | S0            | Power off, then on; wait 10 s                                                                                                                | S17        | Live View (with DP1) | Off        |   E   | E / N / M |
| 98   | S17           | Press DISP button repeatedly until Info display is shown                                                                                     | S21        | Info display (explicit DP5 route; DP5 ON)      | Off        |   E   | E / N / M |
| 99   | S21           | Power off, then on                                                                                                                           | S37        | Info display (persistent fixation)    | Off        | **N** | E / N / M |
| 100  | S21           | Press DISP button                                                                                                                            | S17        | Live View (with DP1) | Off        |   E   | E / N / M |
| 101  | S17           | Power off, then on                                                                                                                           | S17        | Live View (with DP1) | Off        |   E   | E / N / M |
| ▼ |  **Context** | **MO (-; DP1-4=1,2,3,4; DP5=ON)**                                      |            |                                                                                               |                   |                                              |                   |
| 102  | S17           | Use the Monitor mode button to set it to "Monitor only"                                                                                      | S17        | Live View (with DP1) | Off        |   E   | E / N / M |
| 103  | S17           | Press DISP button repeatedly until Info display is shown                                                                                     | S21        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 104  | S21           | Power off, then on                                                                                                                           | S37        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 105  | S37           | Press DISP button                                                                                                                            | S17        | Live View (with DP1) | Off        |   E   | E / N / M |
| 106  | S17           | Power off, then on                                                                                                                           | S17        | Live View (with DP1) | Off        |   E   | E / N / M |
| 107  | S17           | Press DISP button repeatedly until Info display is shown                                                                                     | S21        | Info display (explicit DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 108  | S21           | Open LCD monitor                                                                                                                             | S25        | Info display (explicit DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 109  | S25           | Power off, then on                                                                                                                           | S38        | Info display (persistent fixation)    | Off        | **N** | E / N / M |
| 110  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 111  | S1            | Power off, then on                                                                                                                           | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 112  | S1            | Close LCD monitor                                                                                                                            | S17        | Live View (with DP1) | Off        |   E   | E / N / M |
| ▼ |  **Context** | **PV (OD; DP1-4=1,2,3,4; DP5=ON)**                                      |            |                                                                                               |                   |                                              |                   |
| 113  | S17           | Use the Monitor mode button to set it to"Prioritize viewfinder (1 or 2)."                                                                    | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 114  | S0            | Press DISP button repeatedly until Info display is shown                                                                                     | S21        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 115  | S21           | Open LCD monitor                                                                                                                             | S25        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 116  | S25           | Half-press shutter button                                                                                                                    | S38        | Info display (persistent fixation)    | Off        | **N** | E / N / M |
| 117  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 118  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 119  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 120  | S0            | Press DISP button repeatedly until Info display is shown                                                                                     | S21        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 121  | S21           | Press and hold the Fn button                                                                                                                 | S12        | WB adjustment displayed              | Off        |   E   | E / N / M |
| 122  | S12           | Open the LCD slowly (<10°) while holding the Fn button                                                                                       | S12        | WB adjustment displayed              | Off        |   E   | E / N / M |
| 123  | S12           | Open the LCD slowly further (≥20°) while holding the Fn button.                                                                              | *S15*      | Live View with the WB adjustment overlay    | Off                 |   E   | E / N / M |
| 124  | S15           | Release the Fn button                                                                                                                        | S1         | Live View (with DP1)                 | Off        |   E   | E / N / M |
| 125  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 126  | S0            | Open LCD monitor                                                                                                                             | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 127  | S38           | Half-press shutter button                                                                                                                    | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 128  | S38           | Close LCD monitor                                                                                                                            | S37        | Info display (persistent fixation)   | Off        | **M** | E / N / M |
| 129  | S37           | Press and hold the Fn button                                                                                                                 | S12        | WB adjustment displayed              | Off        |   E   | E / N / M |
| 130  | S12           | Open the LCD further (≥20°) while holding the Fn button.                                                                                     | S15        | Live View with the WB adjustment overlay    | Off                 |   E   | E / N / M |
| 131  | S15           | Power off the device while holding the Fn button, then release the Fn button and power it on.                                                | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 132  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 133  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 134  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 135  | S0            | Press DISP button repeatedly until Info display is shown                                                                                     | S21        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 136  | S21           | Open LCD monitor (<10°)                                                                                                                      | S25        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 137  | S25           | Close LCD monitor                                                                                                                            | S21        | Nothing display                    | Off        |   E   | E / N / M |
| 138  | S21           | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 139  | S0            | Open LCD monitor                                                                                                                             | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 140  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 141  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 142  | S0            | Press DISP button repeatedly until Info display is shown                                                                                     | S21        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 143  | S21           | Open LCD monitor (≥20°)                                                                                                                      | S25        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 144  | S25           | Close LCD monitor                                                                                                                            | S21        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 145  | S21           | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 146  | S0            | Open LCD monitor                                                                                                                             | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 147  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 148  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 149  | S0            | Open LCD monitor (<10°)                                                                                                                      | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 150  | S0            | Open LCD monitor (≥20°) , then press DISP button                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 151  | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 152  | S0            | Press [i] button                                                                                                                             | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 153  | S4            | Open LCD monitor (<10°)                                                                                                                      | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 154  | S4            | Close LCD monitor                                                                                                                            | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 155  | S4            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 156  | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 157  | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 158  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 159  | S0            | Press [i] button                                                                                                                             | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 160  | S4            | Open LCD monitor (≥20°)                                                                                                                      | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 161  | S4            | Close LCD monitor                                                                                                                            | S37        | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        | **N** | E / N / M |
| 162  | S37           | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 163  | S0            | Open LCD monitor                                                                                                                             | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 164  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 165  | S1            | Press DISP button; then close LCD monitor                                                                                                    | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 166  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 167  | S0            | Press and hold the Fn button                                                                                                                 | S12        | Only the WB adjustment overlay                | Off        |   E   | E / N / M |
| 168  | S12           | Release the Fn button                                                                                                                        | S7         | Info display (non-DP5 route; DP5 ON)         | Off        |   E   | E / N / M |
| 169  | S7            | Open LCD monitor (<10°)                                                                                                                      | S7         | Info display (non-DP5 route; DP5 ON)         | Off        |   E   | E / N / M |
| 170  | S7            | Close LCD monitor                                                                                                                            | S7         | Info display (non-DP5 route; DP5 ON)         | Off        |   E   | E / N / M |
| 171  | S7            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 172  | S0            | Open LCD monitor                                                                                                                             | S22        | Live View (with DP2) | Off        |   E   | E / N / M |
| 173  | S22           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 174  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 175  | S0            | Press and hold the Fn button                                                                                                                 | S12        | Only the WB adjustment overlay                | Off        |   E   | E / N / M |
| 176  | S12           | Release the Fn button                                                                                                                        | S7         | Info display (non-DP5 route; DP5 ON)         | Off        |   E   | E / N / M |
| 177  | S7            | Open LCD monitor (≥20°)                                                                                                                      | S7         | Info display (non-DP5 route; DP5 ON)         | Off        |   E   | E / N / M |
| 178  | S7            | Close LCD monitor                                                                                                                            | S6         | Info display (non-DP5 route; DP5 ON)  | Off        |   E   | E / N / M |
| 179  | S6            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 180  | S0            | Open LCD monitor                                                                                                                             | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 181  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 182  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 183  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 184  | S0            | Press DISP button repeatedly until Info display is shown                                                                                     | S21        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 185  | S21           | Open LCD monitor (≥20°)                                                                                                                      | S25        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 186  | S25           | Power off, then on                                                                                                                           | S38        | Info display (persistent fixation)      | Off        | **N** | E / N / M |
| 187  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 188  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 189  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 190  | S0            | Press DISP button repeatedly until Info display is shown                                                                                     | S21        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 191  | S21           | Open LCD monitor (≥20°)                                                                                                                      | S25        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 192  | S25           | Half-press shutter button                                                                                                                    | S38        | Info display (persistent fixation)    | Off        | **N** | E / N / M |
| 193  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 194  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 195  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 196  | S0            | In [CUSTOM SETTINGS MENU] > [d19 Custom monitor shooting display], <br> select Display 1 and Display 5,then exit                             | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 197  | S0            | Press [i] button                                                                                                                             | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 198  | S4            | Press [i] button                                                                                                                             | S7         | Info display (non-DP5 route; DP5 ON)                 | Off        |   E   | E / N / M |
| 199  | S7            | Open LCD monitor (≥20°)                                                                                                                      | S6         | Info display (non-DP5 route; DP5 ON)                 | Off        |   E   | E / N / M |
| 200  | S6            | Close LCD monitor                                                                                                                            | S7         | Info display (non-DP5 route; DP5 ON)                 | Off        |   E   | E / N / M |
| 201  | S7            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 202  | S0            | Open LCD monitor (≥20°)                                                                                                                      | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 203  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 204  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 205  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 206  | S0            | Open LCD monitor                                                                                                                             | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 207  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 208  | S0            | Press [i] button                                                                                                                             | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 209  | S4            | Open LCD monitor (≥20°)                                                                                                                      | S5         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 210  | S5            | Press [i] button                                                                                                                             | S6         | Info display (non-DP5 route; DP5 ON)                 | Off        |   E   | E / N / M |
| 211  | S6            | Close LCD monitor                                                                                                                            | S7         | Info display (non-DP5 route; DP5 ON)                 | Off        |   E   | E / N / M |
| 212  | S7            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 213  | S0            | Open LCD monitor (≥20°)                                                                                                                      | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 214  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 215  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 216  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 217  | S0            | Open LCD monitor                                                                                                                             | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 218  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 219  | S0            | Press [i] button                                                                                                                             | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 220  | S4            | Open LCD monitor (≥20°)                                                                                                                      | S5         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 221  | S5            | Close LCD monitor                                                                                                                            | S4         | Info display (non-DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 222  | S4            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 223  | S0            | Open LCD monitor                                                                                                                             | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 224  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 225  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 226  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 227  | S0            | Open LCD monitor                                                                                                                             | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 228  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 229  | S0            | Open LCD monitor (≥20°)                                                                                                                      | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 230  | S1            | Press DISP button                                                                                                                            | S25        | Info display (explicit DP5 route; DP5 ON)        | Off        |   E   | E / N / M |
| 231  | S25           | Power off, then on                                                                                                                           | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 232  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 233  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 234  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 235  | S0            | Open LCD monitor                                                                                                                             | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 236  | S1            | Press DISP button                                                                                                                            | S25        | Info display (explicit DP5 route; DP5 ON)             | Off        |   E   | E / N / M |
| 237  | S25           | Press [i] button                                                                                                                             | S34        | Info display (explicit DP5 route; DP5 ON) with [i] menu   | Off        |   E   | E / N / M |
| 238  | S34           | Power off, then on                                                                                                                           | S38        | Info display (persistent fixation)   | Off        | **N** | E / N / M |
| 239  | S38           | Press DISP button                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 240  | S1            | Press DISP button; then close LCD monitor                                                                                                    | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 241  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| ▼ |  **Context** | **PV (OD; DP1-4=1,2,3,4; DP5=OFF)**                                      |            |                                                                                               |                   |                                              |                   |
| 242  | S0            | In [CUSTOM SETTINGS MENU] > [d19 Custom monitor shooting display], un-check Display 5, <br> check Display  1 to 4 ; then exit                | S0 | Nothing display                               | Off                                        |   E   | E / N / M |
| 243  | S0            | Press [i] button                                                                                                                             | S45        | Info display (non-DP5 route; DP5 OFF)  <br> with [i] menu | Off        |   E   | E / N / M 
| 244  | S45           | Press [i] button                                                                                                                            | S40        | Info display (non-DP5 route; DP5 OFF)  | Off        |   E   | E / N / M |
| 245  | S40           | Open LCD monitor                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 246  | S1            | Press DISP button; then close LCD monitor                                                                                                   | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 247  | S0            | Press [i] button                                                                                                                            | S45        | Info display (non-DP5 route; DP5 OFF)  <br> with [i] menu | Off        |   E   | E / N / M |
| 248  | S45           | Open LCD monitor                                                                                                                            | S30        | Live View with [i] menu               | Off                                        |   E   | E / N / M |
| 249  | S30           | Press [i] button                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 250  | S1            | Press DISP button; then close LCD monitor                                                                                                   | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 251  | S0            | Press [i] button                                                                                                                            | S45        | Info display (non-DP5 route; DP5 OFF)  <br> with [i] menu | Off        |   E   | E / N / M |
| 252  | S45           | Open LCD monitor                                                                                                                            | S30        | Live View with [i] menu              | Off        |   E   | E / N / M |
| 253  | S30           | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 254  | S0            | Press DISP button                                                                                                                           | S40        | Info display (non-DP5 route; DP5 OFF)  | Off        |   E   | E / N / M |
| 255  | S40           | Press DISP button                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 256  | S0            | Open LCD monitor                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 257  | S1            | Press DISP button                                                                                                                           | S22         | Live View (with DP2) | Off        |   E   | E / N / M |
| 258  | S22           | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 259  | S0            | Press DISP button                                                                                                                           | S40        | Info display (non-DP5 route; DP5 OFF)  | Off        |   E   | E / N / M |
| 260  | S40           | Open LCD monitor                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 261  | S1            | Press DISP button                                                                                                                           | S22         | Live View (with DP2) | Off        |   E   | E / N / M |
| 262  | S22           | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 263  | S0            | Press DISP button                                                                                                                           | S40        | Info display (non-DP5 route; DP5 OFF)  | Off        |   E   | E / N / M |
| 264  | S40           | Open LCD monitor                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 265  | S1            | Press DISP button; then close LCD monitor                                                                                                   | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 266  | S0            | Press DISP button                                                                                                                           | S40        | Info display (non-DP5 route; DP5 OFF)  | Off        |   E   | E / N / M |
| 267  | S40           | Press [i] button                                                                                                                            | S45        | Info display (non-DP5 route; DP5 OFF)  <br> with [i] menu | Off        |   E   | E / N / 
| 268  | S45           | Open LCD monitor                                                                                                                            | S30        | Live View with [i] menu              | Off        |   E   | E / N / M |
| 269  | S30           | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 270  | S0            | Press DISP button                                                                                                                           | S40        | Info display (non-DP5 route; DP5 OFF)  | Off        |   E   | E / N / M |
| 271  | S40           | Open LCD monitor                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 272  | S1            | Press [i] button                                                                                                                             | S30        | Live View with [i] menu              | Off        |   E   | E / N / M |
| 273  | S30           | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 274  | S0            | Power off, then on                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 275  | S0            | Press and hold the Fn button                                                                                                                 | S12        | WB adjustment displayed              | Off        |   E   | E / N / M |
| 276  | S12           | Open the LCD slowly (<10°) while holding the Fn button                                                                                       | S12        | WB adjustment displayed              | Off        |   E   | E / N / M |
| 277  | S12           | Release the Fn button                                                                                                                        | S40        | Info display (non-DP5 route; DP5 OFF) | Off        |   E   | E / N / M |
| 278  | S40           | Press and hold the Fn button                                                                                                                 | S12        | WB adjustment displayed              | Off        |   E   | E / N / M |
| 279  | S12           | Open the LCD slowly further (≥20°) while holding the Fn button.                                                                              | *S15*      | Live View with the WB adjustment overlay    | Off                 |   E   | E / N / M |
| 280  | S15           | Release the Fn button                                                                                                                        | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 281  | S1            | Press DISP button ; then Press and hold the Fn button                                                                                        | S15      | Live View with the WB adjustment overlay    | Off                 |   E   | E / N / M |
| 282  | S15           | Close the LCD while holding the Fn button                                                                                                    | *S12*        | WB adjustment displayed              | Off        |   E   | E / N / M |
| 283  | S12           | Release the Fn button                                                                                                                        | S40         | Info display (non-DP5 route; DP5 OFF) | Off        |   E   | E / N / M |
| 284  | S40           | Press and hold the Fn button                                                                                                                 | S12        | WB adjustment displayed              | Off        |   E   | E / N / M |
| 285  | S12           | Release the Fn button                                                                                                                        | S40        | Info display (non-DP5 route; DP5 OFF) | Off        |   E   | E / N / M |
| 286  | S40           | Open LCD monitor                                                                                                                             | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 287  | S1            | Close LCD monitor                                                                                                                            | S0         | Nothing display                    | Off        |   E   | E / N / M |
| ▼ |  **Context** | **PV (OD; DP1-4=1,2,3,4; DP5=ON)**                                   |            |                                                                                               |                   |                                              |                   |
| 288  | S0             | In [CUSTOM SETTINGS MENU] > [d19 Custom monitor shooting display], check Display 5, <br> ensure that Display  1 to 5 are checked; then exit | S0 | Nothing display                               | Off                                        |   E   | E / N / M |
| 289  | S0             | Open LCD monitor                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 290  | S1             | Press DISP button                                                                                                                           | S22         | Live View (with DP2) | Off        |   E   | E / N / M |
| 291  | S22            | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 292  | S0             | Open LCD monitor                                                                                                                            | S22         | Live View (with DP2) | Off        |   E   | E / N / M |
| 293  | S22            | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 294  | S0             | Press DISP button                                                                                                                           | S7         | Info display (non-DP5 route; DP5 ON)         | Off        |   E   | E / N / M |
| 295  | S7             | Open LCD monitor                                                                                                                            | S6         | Info display (non-DP5 route; DP5 ON)                 | Off        |   E   | E / N / M |
| 296  | S6             | Press DISP button                                                                                                                           | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 297  | S1             | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 298  | S0             | Open LCD monitor                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 299  | S1             | Press DISP button                                                                                                                           | S22         | Live View (with DP2) | Off        |   E   | E / N / M |
| 300  | S22            | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 301  | S0             | Press DISP button                                                                                                                           | S21        |Info display (explicit DP5 route; DP5 ON)    | Off        |   E   | E / N / M |
| ▼ |  **Context** | **AS (OD; DP1-4=1,2,3,4; DP5=ON)**                                      |            |                                                                                               |                   |                                              |                   |
| 302  | S21            | Use the Monitor mode button to set it to "Automatic display switch" (Context E)                                                             | S18         | Live View (with DP2) | Off        |   E   | E / N / M |
| 303  | S18            | Open LCD monitor                                                                                                                            | S22         | Live View (with DP2) | Off        |   E   | E / N / M |
| 304  | S22            | Press DISP button repeatedly until Display 1 is shown                                                                                       | S1          | Live View (with DP1) | Off        |   E   | E / N / M |
| 305  | S1             | Close LCD monitor                                                                                                                           | S17         | Live View (with DP1) | Off        |   E   | E / N / M |
| ▼ |  **Context** | **PV (OD; DP1-4=1,2,3,4; DP5=OFF)**                                      |            |                                                                                               |                   |                                              |                   |
| 306  | S17            | Use the Monitor mode button to set it to "Prioritize viewfinder (1 or 2)" (Context A)                                                       | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 307  | S0             | In [CUSTOM SETTINGS MENU] > [d19 Custom monitor shooting display], un-check Display 5, <br> ensure that Display  1 to 4 are checked; then exit | S0 | Nothing display                               | Off                                        |   E   | E / N / M |
| 308  | S0             | Open LCD monitor                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 309  | S1             | Press DISP button                                                                                                                           | S22         | Live View (with DP2) | Off        |   E   | E / N / M |
| 310  | S22            | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 311  | S0             | Open LCD monitor                                                                                                                            | S22         | Live View (with DP2) | Off        |   E   | E / N / M |
| 312  | S22            | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 313  | S0             | Press DISP button                                                                                                                           | S40         | Info display (non-DP5 route; DP5 OFF) | Off        |   E   | E / N / M |
| 314  | S40            | Open LCD monitor                                                                                                                            | S1         | Live View (with DP1) | Off        | **M** | E / N / M |
| 315  | S1             | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 316  | S0             | Open LCD monitor                                                                                                                            | S1         | Live View (with DP1) | Off        |   E   | E / N / M |
| 317  | S1             | Press DISP button                                                                                                                           | S22         | Live View (with DP2) | Off        |   E   | E / N / M |
| 318  | S22            | Close LCD monitor                                                                                                                           | S0         | Nothing display                    | Off        |   E   | E / N / M |
| 319  | S0             | Press DISP button                                                                                                                           | S41        |Info display (explicit DISP route; DP5 OFF)   | Off        |   E   | E / N / M |
| ▼ |  **Context** | **AS (OD; DP1-4=1,2,3,4; DP5=OFF)**                                      |            |                                                                                               |                   |                                              |                   |
| 320  | S41            | Use the Monitor mode button to set it to "Automatic display switch" (Context E)                                                             | S18         | Live View (with DP2) | Off        |   E   | E / N / M |
| 321  | S18            | Open LCD monitor                                                                                                                            | S22         | Live View (with DP2) | Off        |   E   | E / N / M |
| 322  | S22            | Press DISP button repeatedly until Display 1 is shown                                                                                       | S1          | Live View (with DP1) | Off        |   E   | E / N / M |
| 323  | S1             | Close LCD monitor                                                                                                                           | S17         | Live View (with DP1) | Off        |   E   | E / N / M |






---

### Observational Notes

---

#### 【1】 Observation of Fixation Occurrence Based on LCD Open/Close State and Operation Timing

In this section, “fixation” is treated as having occurred when the Info display remains active, or reappears, at a timing where Live View would normally be expected from the shooting-display context.

---

#### ▼ Context PV(OD; DP1-4=1,2,3,4; DP5=ON): LCD Open → [Operations] → LCD Close → LCD Open

Steps 1–20

**Fixation did not occur**

* LCD Open → LCD Close → LCD Open (Steps 14–16)
* LCD Open → Half-press shutter button → LCD Close → LCD Open (Steps 1–4)
* LCD Open → Press [i] button → Half-press shutter button → LCD Close → LCD Open (Steps 4–8)
* LCD Open → Press DISP button repeatedly until Info display (Display 5) is shown → LCD Close → LCD Open (Steps 8–11)

In the last sequence, although the Info display remained visible on the LCD, the persistence caused solely by closing and reopening the LCD monitor is not classified here as fixation.

**Fixation occurred**

* LCD Open → Press DISP button repeatedly until Info display (Display 5) is shown → Half-press shutter button → LCD Close → LCD Open (Steps 16–20)

In this sequence, the Info display did not disappear after shutter-button half-press and remained persistent afterward. Therefore, this sequence is classified as fixation.

---

#### ▼ Context PV(OD; DP1-4=1,2,3,4; DP5=ON): LCD Close → [Operations] → Power OFF → ON → LCD Open

Steps 25–61 and 75–94

**Fixation did not occur**

* LCD Close → Press [i] button → Press [i] button → Power off, then on → LCD Open (Steps 25–29)
* LCD Close → Press [i] button → Power off, then on → LCD Open (Steps 30–33)
* LCD Close → Press DISP button once → Power off, then on → LCD Open (Steps 34–37)
* LCD Close → Press [i] button → Press [i] button → Half-press shutter button → Power off, then on → LCD Open (Steps 89–94)
* LCD Close → Press [i] button → Half-press shutter button → Power off, then on → LCD Open (Steps 84–88)
* LCD Close → Press DISP button once → Half-press shutter button → Power off, then on → LCD Open (Steps 79–83)

**Fixation occurred**

* LCD Close → Press [i] button → Press [i] button → LCD Open → LCD Close → Power off, then on → LCD Open (Steps 38–43)
* LCD Close → Press [i] button → LCD Open → LCD Close → Power off, then on → LCD Open (Steps 48–52)
* LCD Close → Press DISP button once → LCD Open → LCD Close → Power off, then on → LCD Open (Steps 57–61)

---

#### ▼ Context PV(OD; DP1-4=1,2,3,4; DP5=ON): LCD Open → [Operations] → Power OFF → ON

Steps 66–70

**Fixation did not occur**

* LCD Open → Press [i] button → Power off, then on

**Fixation occurred**

* LCD Open → Press DISP button repeatedly until Info display (Display 5) is shown → Power off, then on

---

#### ▼ Context MO(-; DP1-4=1,2,3,4; DP5=ON): LCD Close → [Operations] → Power OFF → ON

Steps 102–112

**Fixation occurred**

* LCD Close → Press DISP button repeatedly until Info display (Display 5) is shown → Power off, then on (Steps 103–104)
* LCD Close → Press DISP button repeatedly until Info display (Display 5) is shown → LCD Open → Power off, then on (Steps 107–109)

---

#### Note

Regardless of the presence or absence of the [i] menu overlay, and regardless of the route by which the Info display was reached, fixation appears to occur when the camera reaches a condition in which Live View would normally be expected, but the Info display is shown instead.

It should also be noted that when exiting from an Info display reached via Display 5 by pressing the DISP button, returning to Live View with the Display 1 layer is a natural result of the DISP display cycle. However, when exiting from an Info display that did not originate from Display 5, the camera was also observed to reset to Display 1 rather than restoring the previously active Live View display layer (Steps 44, 53, and 62).

The same fixation behavior was also observed under `Context PV(OD; DP1-4=1; DP5=ON)` (Steps 196–241), indicating that the phenomenon is not limited to configurations in which Display 1–4 are all enabled.


---

#### 【2】 Observation of Fixation Around the LCD Opening Threshold Angle

Steps 113–195

Under `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`, the LCD monitor was observed to turn on when the opening angle increased from 0° and reached approximately 15° (Steps 123 and 149–150).

The following observations examine whether the occurrence of fixation depends on this LCD opening threshold angle, in combination with several different display-entry operations.

---

#### ▼ Context PV(OD; DP1-4=1,2,3,4; DP5=ON): LCD Docked → [Operations] → LCD Open (<10°) → LCD Close → Power OFF → ON → LCD Open

**Fixation did not occur**

* LCD Docked → Press DISP button repeatedly until Info display (Display 5) is shown → LCD Open (<10°) → LCD Close → Power OFF → ON → LCD Open (Steps 135–140)
* LCD Docked → Press [i] button → LCD Open (<10°) → LCD Close → Power OFF → ON → LCD Open (Steps 152–157)
* LCD Docked → Press and release the Fn button → LCD Open (<10°) → LCD Close → Power OFF → ON → LCD Open (Steps 167–172)

**Fixation occurred**

* None observed

---

#### ▼ Context PV(OD; DP1-4=1,2,3,4; DP5=ON): LCD Docked → [Operations] → LCD Open (≥20°) → LCD Close → Power OFF → ON → LCD Open

**Fixation did not occur**

* None observed

**Fixation occurred**

* LCD Docked → Press DISP button repeatedly until Info display (Display 5) is shown → LCD Open (≥20°) → LCD Close → Power OFF → ON → LCD Open (Steps 142–146)
* LCD Docked → Press [i] button → LCD Open (≥20°) → LCD Close → Power OFF → ON → LCD Open (Steps 159–163)
* LCD Docked → Press and release the Fn button → LCD Open (≥20°) → LCD Close → Power OFF → ON → LCD Open (Steps 175–180)

---

#### Note

The contrast between the `<10°` and `≥20°` observations suggests that fixation is associated not merely with the physical act of moving the LCD monitor, but with crossing the LCD activation threshold. In these observations, fixation occurred only when the LCD monitor was opened beyond the activation threshold, where the LCD would normally be expected to enter an active shooting-display state.

Regarding Step 123, slow-motion video review showed that at the moment the opening angle reached approximately 15°, the display transitioned instantly through the following sequence:

`WB adjustment display with Live View and Display 1 layer`
→ `Live View with Display 1 layer, with the WB display disappearing`
→ `S15: Live View active, Display 1 layer hidden, and WB display re-illuminated`

This suggests that the LCD activation threshold involves a rapid internal transition between display-routing states.

By contrast, in Step 279 under `Context PV(OD; DP1-4=1,2,3,4; DP5=OFF)`, when the LCD monitor crossed the same approximate threshold, Live View appeared naturally underneath the WB adjustment overlay without visible flicker. This suggests that disabling Display 5 changes how the Info/WB-related display route interacts with the LCD activation transition.





#### 【3】 Observation of Fixation and LCD Threshold Behavior with Display 5 Disabled

Steps 242–287

As discussed in Case B1, one form of the Info display is Display 5, introduced as part of the Z-series shooting-display system, while other visually similar Info displays can be reached through non-Display 5 routes.

In this section, Display 5 was disabled in order to observe whether persistent fixation still occurs and how the Info-related routes behave when Display 5 is unavailable.

---

#### ▼ Context PV(OD; DP1-4=1,2,3,4; DP5=OFF)

In all of the following sequences, persistent fixation was not observed:

* LCD Docked → Press [i] button → LCD Open (Steps 251–253)
  Note: The corresponding sequence produced fixation with DP5=ON in Steps 48–50.

* LCD Docked → Press [i] button → LCD Open → Press [i] button (Steps 247–250)
  Note: The corresponding sequence produced fixation with DP5=ON in Steps 208–211.

* LCD Docked → Press [i] button → Press [i] button → LCD Open (Steps 243–246)
  Note: The corresponding sequence produced fixation with DP5=ON in Steps 38–41.

* LCD Docked → Press DISP button → LCD Open (Steps 259–262)
  Note: The corresponding sequence produced fixation with DP5=ON in Steps 57–58.

* LCD Docked → Press DISP button → Press DISP button → LCD Open (Steps 254–258)

* LCD Docked → Press DISP button → LCD Open → Press [i] button (Steps 270–273)

* LCD Docked → Press DISP button → Press [i] button → LCD Open (Steps 266–269)

---

#### Note

Regarding Steps 279 and 282, as noted above, when the LCD monitor crossed the activation threshold in Step 279, Live View appeared naturally underneath the WB adjustment overlay without any visible flicker.

By contrast, when closing the LCD monitor in Step 282, the display transition was observed as follows:

`WB adjustment display`
→ blackout
→ momentary Live View without overlay
→ disappearance of Live View
→ WB adjustment display reappears

Among the seven sequences listed above, all except the seventh ended with Live View. However, in each of those cases, the previously active display layer was not preserved. Instead, the camera returned to Display 1 (Steps 253, 249, 245, 260, 256, and 271).

This suggests that disabling Display 5 prevents persistent fixation, but does not necessarily preserve the previous Live View display layer when returning from an Info-related route.

---

#### 【4】Observation of Display 2–4 Resetting to Display 1 After Passing Through the Info Display

The following two sets of observations were conducted to examine whether Live View display layers such as Display 2, Display 3, or Display 4 are preserved after passing through an Info-related display state.

---

#### ▼ Context PV(OD; DP1-4=1,2,3,4; DP5=ON) → Context AS(OD; DP1-4=1,2,3,4; DP5=ON)

Steps 288–305

Under `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`, opening and closing the LCD monitor did not by itself change the active Live View display layer (Step 290).

However, as observed earlier, passing through the Info display caused the camera to reset to Display 1 rather than preserving the previously active display layer (Step 296).

It was also newly confirmed that simply changing the monitor mode does not by itself reset the display layer.

---

#### ▼ Context PV(OD; DP1-4=1,2,3,4; DP5=OFF) → Context AS(OD; DP1-4=1,2,3,4; DP5=OFF)

Steps 306–323

Under `Context PV(OD; DP1-4=1,2,3,4; DP5=OFF)`, opening and closing the LCD monitor likewise did not by itself change the active Live View display layer (Step 311).

However, as in the DP5=ON observations, passing through the Info display caused the camera to reset to Display 1 rather than preserving the previously active display layer (Step 314).

It was also confirmed in this configuration that simply changing the monitor mode does not by itself reset the display layer.

---

#### 【5】Summary

Case B3 suggests that persistent Info fixation is closely associated with moments when the LCD monitor becomes an active shooting display, especially around the LCD opening threshold. Disabling Display 5 prevents the observed fixation, but does not fully preserve the previously active Live View display layer: after passing through Info-related routes, the camera often returns to Display 1 rather than the prior Live View display mode.

These observations suggest that Display 5 fixation and Display-layer reset should be treated as related but distinct issues.


---

### Additional Note: A Temporary Live View Bypass That Does Not Reset the Underlying State
Under `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`, an additional bypass-like behavior was observed when the Fn button retained its default white-balance function.

If the LCD monitor is closed and the Fn button is pressed and held, then the LCD monitor is opened while the Fn button remains held down, Live View appears underneath the white-balance adjustment overlay. Releasing the Fn button then provides a usable Live View display.

However, this behavior does not appear to reset the underlying persistent Info / Display 5 state. If the LCD monitor is then closed and opened normally, the camera returns to the Info display. Repeating the same operation — closing the LCD monitor, holding the Fn button, and opening the LCD monitor while the Fn button remains held — can again produce Live View underneath the white-balance overlay.

This bypass is therefore not a stable recovery path.

Moreover, if a photograph is taken from this temporarily obtained Live View state, the image is recorded, but Live View then disappears. The LCD shows only the Display 1 overlay against a dark background. Exposure-related indicators remain active, but the through-image is no longer displayed.

After this occurs, subsequent shooting, and repeating the Fn-held LCD-opening operation do not restore the through-image. The display remains in a Display 1 overlay state without Live View.

For this reason, this behavior is best understood not as a recovery method, but as a one-shot bypass that temporarily exposes a Live View rendering path without clearing the underlying display-state problem.

