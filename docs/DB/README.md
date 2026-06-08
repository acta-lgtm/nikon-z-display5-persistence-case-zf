# Phase 2: Definition B (Fine-grained Analysis)

During ongoing observation, it became evident that the "Info display" and the "Info display with [i] menu overlay" must be analyzed as distinct states. Furthermore, the "Info display" corresponds to the item displayed when "Display 5" is selected under the menu setting [d19 Custom monitor shooting display]. Based on these insights, the state definitions have been further refined. Focusing on the Information Display appears to be key to understanding this camera's behavior, and the detailed observation results are archived here.

## 1. State Definitions
- State S0 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  EVF off

- State S1 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Live View with the Display 1 overlay displayed on the LCD monitor \
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
  EVF off \
    (Note: Visually, states S4, S33, S43, and S45 appear identical. See "Info-State Classification" for details.)


- State S5 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Info display with [i] menu overlay on the LCD monitor \
  EVF off \
    (Note: Visually, states S5, S34, S44, and S46 appear identical. See "Info-State Classification" for details.)

- State S6 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Info displayed on the LCD monitor \
  EVF off \
    (Note: Visually, states S6, S25, S38, S39, and S42 appear identical. See "Info-State Classification" for details.)

- State S7 \
  LCD monitor docked \
  Info displayed on the LCD monitor \
  EVF off \
    (Note: Visually, states S7, S21, S37, S40, and S41 appear identical. See "Info-State Classification" for details.)

- State S8 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with the Display 1 overlay displayed in the EVF

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
  Only the White balance adjustment overlay displayed on the LCD monitor \
  EVF off

- State S13 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Only the White balance adjustment overlay displayed on the LCD monitor \
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
  Live View with the Display 1 overlay displayed on the LCD monitor \
  EVF off

- State S18 \
  LCD monitor docked \
  Live View with the Display 2 overlay displayed on the LCD monitor \
  EVF off

- State S19 \
  LCD monitor docked \
  Live View with the Display 3 overlay displayed on the LCD monitor \
  EVF off

- State S20 \
  LCD monitor docked \
  Live View with the Display 4 overlay displayed on the LCD monitor \
  EVF off

- State S21 \
  LCD monitor docked \
  Display 5 = Info display displayed on the LCD monitor \
  EVF off \
    (Note: Visually, states S7, S21, S37, S40, and S41 appear identical. See "Info-State Classification" for details.)

- State S22 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Live View with the Display 2 overlay displayed on the LCD monitor \
  EVF off

- State S23 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Live View with the Display 3 overlay displayed on the LCD monitor \
  EVF off

- State S24 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Live View with the Display 4 overlay displayed on the LCD monitor \
  EVF off

- State S25 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Display 5 = Info display displayed on the LCD monitor \
  EVF off \
    (Note: Visually, states S6, S25, S38, S39, and S42 appear identical. See "Info-State Classification" for details.)

- State S26 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with the Display 2 overlay displayed in the EVF

- State S27 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with the Display 3 overlay displayed in the EVF

- State S28 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with the Display 4 overlay displayed in the EVF

- State S29 \
  LCD monitor docked \
  Live View with [i] menu overlay on the LCD monitor \
  EVF off

- State S30 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Live View with [i] menu overlay on the LCD monitor \
  EVF off

- State S31 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with [i] menu overlay displayed in the EVF

- State S32 \
  LCD monitor docked \
  Live View with the WB adjustment overlay displayed on the LCD monitor \
  EVF off

- State S33 \
  LCD monitor docked \
  Info display with [i] menu overlay on the LCD monitor \
  EVF off \
    (Note: Visually, states S4, S33, S43, and S45 appear identical. See "Info-State Classification" for details.)

- State S34 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Info display with [i] menu overlay on the LCD monitor \
  EVF off \
    (Note: Visually, states S5, S34, S44, and S46 appear identical. See "Info-State Classification" for details.)

- State S35 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Picture Review displayed in the EVF

- State S36 \
  LCD monitor docked \
  Picture Review displayed on the LCD monitor \
  EVF off

- State S37 \
  LCD monitor docked \
  Info display persistently fixed on the LCD monitor \
  EVF off \
    (Note: Visually, states S7, S21, S37, S40, and S41 appear identical. See "Info-State Classification" for details.)


- State S38 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Info display persistently fixed on the LCD monitor \
  EVF off \
    (Note: Visually, states S6, S25, S38, S39, and S42 appear identical. See "Info-State Classification" for details.)

- State S39 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Info display shown on the LCD monitor while Display 5 is disabled \
  EVF off \
    (Note: Visually, states S6, S25, S38, S39, and S42 appear identical. See "Info-State Classification" for details.)

- State S40 \
  LCD monitor docked \
  Info display shown on the LCD monitor while Display 5 is disabled \
  EVF off \
    (Note: Visually, states S7, S21, S37, S40, and S41 appear identical. See "Info-State Classification" for details.)

- State S41 \
  LCD monitor docked \
  Info display shown on the LCD monitor via DISP while Display 5 is disabled \
  EVF off \
    (Note: Visually, states S7, S21, S37, S40, and S41 appear identical. See "Info-State Classification" for details.)

- State S42 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Info display shown on the LCD monitor via DISP while Display 5 is disabled \
  EVF off \
    (Note: Visually, states S6, S25, S38, S39, and S42 appear identical. See "Info-State Classification" for details.)
   
- State S43 \
  LCD monitor docked \
  Info display with [i] menu overlay persistently fixed on the LCD monitor \
  (Temporary state before S37) \
  EVF off
    (Note: Visually, states S4, S33, S43, and S45 appear identical. See "Info-State Classification" for details.)
   
- State S44 \
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Info display with [i] menu overlay persistently fixed on the LCD monitor \
  (Temporary state before S38) \
  EVF off
    (Note: Visually, states S5, S34, S44, and S46 appear identical. See "Info-State Classification" for details.)

- State S45\
  LCD monitor docked \
  Info display with [i] menu overlay shown on the LCD monitor while Display 5 is disabled \
  EVF off \
    (Note: Visually, states S4, S33, S43, and S45 appear identical. See "Info-State Classification" for details.)

- State S46\
  LCD monitor open (20 degrees or more and 140 degrees or less) \
  Info display with [i] menu overlay shown on the LCD monitor while Display 5 is disabled \
  EVF off \
    (Note: Visually, states S5, S34, S44, and S46 appear identical. See "Info-State Classification" for details.)

- State S47 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Menu displayed in the EVF


   
---

### Info-State Classification

As the observations progressed, multiple visually similar “Info” states
were found to exhibit different operational behaviors depending on
their route of entry, Display 5 configuration, overlay state,
and persistence history.

To manage these distinctions, the following extended Info-state
classification table was introduced.


| State No | LCD Status [State Transition Table]                           | LCD    | DP5        | Display 5 route | non-Display 5 route | with [i] menu | persistent | note   |
| :------------- | :------------------------------------------------ | :--------------------- | :------------- | :-------------------------- | :-------------- | :------------- | :------------- | :------------- |
| S6       | Info display (non-DP5 route;<br> DP5 ON)                     | Open   | On         | N          | Y          | N         | N          |                                                |
| S7       | Info display (non-DP5 route; <br>DP5 ON)                     | Docked | On         | N          | Y          | N         | N          |                                                |
| S25      | Info display (explicit DP5 route; <br>DP5 ON)                | Open   | On         | Y          | N          | N         | N          |                                                |
| S21      | Info display (explicit DP5 route; <br>DP5  ON)               | Docked | On         | Y          | N          | N         | N          |                                                |
| S39      | Info display (non-DP5 route; <br>DP5 OFF)                    | Open   | Off        | N          | Y          | N         | N          |                   |  
| S40      | Info display (non-DP5 route; <br>DP5 OFF)                    | Docked | Off        | N          | Y          | N         | N          |                                                |
| S42      | Info display (explicit DP5 route; <br>DP5 OFF)               | Open   | Off        | Y          | N          | N         | N          |                                                |
| S41      | Info display (explicit DP5 route; <br>DP5 OFF)               | Docked | Off        | Y          | N          | N         | N          |                                                |
| S5       | Info display (non-DP5 route; <br>DP5 ON) with [i] menu       | Open   | On         | N          | Y          | Y         | N          |                                                |
| S4       | Info display (non-DP5 route; <br>DP5 ON) with [i] menu       | Docked | On         | N          | Y          | Y         | N          |                                                |
| S34      | Info display (explicit DP5 route; <br>DP5 ON) with [i] menu  | Open   | On         | Y          | N          | *Y*       | N          | DISP button (Info display) -> Press [i] button |
| S33      | Info display (explicit DP5 route; <br>DP5 ON) with [i] menu  | Docked | On         | Y          | N          | *Y*       | N          | DISP button (Info display) -> Press [i] button |
| S46      | Info display (non-DP5 route; <br>DP5 OFF) with [i] menu      | Open   | Off        | N          | Y          | Y         | N          |                                                |
| S45      | Info display (non-DP5 route; <br>DP5 OFF) with [i] menu      | Docked | Off        | N          | Y          | Y         | N          |                                                |
| S44      | Info display (persistent fixation)                           | Open   | Don't care | Don't care | Don't care | Y         | *Y*        | Temporary state before S38 |
| S43      | Info display (persistent fixation)                           | Docked | Don't care | Don't care | Don't care | Y         | *Y*        | Temporary state before S37 |
| S38      | Info display (persistent fixation)                           | Open   | Don't care | Don't care | Don't care | N         | Y          |                                                |
| S37      | Info display (persistent fixation)                           | Docked | Don't care | Don't care | Don't care | N         | Y          |                                                | 



[Note] 
 > “DP5” indicates whether Display 5 (Info display) is enabled in [d19 Custom monitor shooting display].
 
 > “DP5 OFF” indicates that Display 5 is disabled in the same menu,
> even though visually similar Info displays may still appear
> through other operational routes.
>
> Display 5 route:
  Info reached through the normal Live View display-cycle sequence
  where Display 5 is enabled and selected as one of the shooting display modes.
>
> non-Display 5 route:
  Info reached through routes other than the Display 5 cycle, including single-DISP invocation when Live View is not currently displayed, Fn release, [i] menu dismissal, or other display-routing behavior.
>
> “persistent fixation” refers to states in which the Info display
> remains or reappears after interruption, regardless of the original
> entry route.

[Note] "with [i] menu" is an abbreviation for "with [i] menu overlay."

---

## 2. Analyzed Cases

The following cases document progressively refined observations
regarding the behavior of the Information Display ("Info")
and its interaction with display routing, monitor states,
and shooting operations.

### [Case B1: The Shadow Double](./Case_B1_Shadow.md)
Observation of multiple activation pathways leading to visually identical Info-display states with different operational behavior.

### [Case B2: In the Fray of the Focus](./Case_B2_Fray.md)
Observation of persistent Info-display behavior during actual shooting operations, including continuous burst shooting.

### [Case B3: Cornering the Shadow: A Trace from the Past](./Case_B3_Cornering.md)
Observation of how monitor routing conditions and LCD activity influence Info-display persistence and recovery behavior.

---

## 3. Methodology
- **Visualization Tool:** Graphviz (dot)
- **Recording Methodology:** Generation of state transition tables based on empirical operation logs and repetitive stress testing to detect micro-transitions and internal flag mismatches.

