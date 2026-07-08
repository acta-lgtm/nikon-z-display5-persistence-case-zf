# Nikon Support Confirmation Notes

> Published: 2026-06-24　| Last Updated: 2026-07-07

## Display 5 (“Info”) Persistence and Recovery Behavior on the Nikon Z f, Z8, and Z9

This document summarizes operational confirmations received from Nikon support regarding Display 5 (“Info”) behavior on Nikon Z-series cameras.

The investigation initially focused on the Nikon Z f. Nikon support later confirmed that the sequences described in CASE 02 through CASE 09 produced the same results on the Nikon Z8 and Z9 under the specified test conditions.

For the Z8 and Z9, Nikon support also confirmed that the relevant LCD-monitor behavior corresponds to the behavior observed on the Nikon Z f when [Automatic monitor display switch] is set to "On (when monitor docked)" on the Z f.

For operations that use the Fn button on the Nikon Z f, Nikon support performed corresponding operations on the Z8 and Z9 using controls that provide equivalent functionality, such as the WB button where appropriate.

The purpose of this document is not to reproduce the entire support correspondence, but to extract the confirmations most relevant to Display 5 / Info persistence, shutter-button half-press recovery, LCD / EVF transition behavior, shooting-display recovery, burst shooting behavior, and multiple-exposure overlay shooting behavior.

Supplementary observations made independently on the owned Nikon Z f and D6, as well as on a separately tested Z9, are also noted where relevant. These supplementary observations are clearly distinguished from the operational confirmations provided by Nikon support.

--- 
  
## <a id="case01"></a> CASE 01. Power-Cycle Persistence of Display 5

### 1.1

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor, starting with the screen facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (any lens is acceptable).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on |  Power off  | Power on | Press DISP button repeatedly<br> until Display 5 is shown | Power off | Power on |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Z f.1.1 <br> `Context AS(O; DP1-4=1,2,3,4; DP5=ON)`| LCD: Live View (with DP1)<br>EVF: Off  | LCD: No display<br>EVF: Off    | LCD: Live View (with DP1)<br>EVF: Off  | LCD: Info display <br>EVF: Off | LCD: No display<br>EVF: Off  | LCD: Info display <br>EVF: Off |  

This confirmation was made under default settings. 

It was confirmed that **the Info display is not initialized or cleared by turning the power on and off**, but instead continues to persist.  
This leads to the lock issue described later.

### Supplementary Observation

This phenomenon was also observed on the Z9.


---

## <a id="case02"></a> CASE 02. MENU Half-Press Returns to Display 5

### 2.1

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor (dock it against the camera body), starting with the screen facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (any lens is acceptable).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on                                   | Open LCD                                   | Press [MENU] button           | Half-press                                 |
| :------- | :------- | :------- | :------------------ | :--------- |
| Z f.2.1 <br> `Context AS(O; DP1-4=1,2,3,4; DP5=ON)`| LCD: Live View (with DP1)<br>EVF: Off | LCD: Live View (with DP1)<br>EVF: Off | LCD: Menu display<br>EVF: Off | LCD: Live View (with DP1)<br>EVF: Off |

### 2.2

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor (dock it against the camera body), starting with the screen facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (any lens is acceptable).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on                                   | Open LCD                                   | Press DISP button repeatedly<br> until Display 5 is shown | Press [MENU] button           | Half-press                                  | Half-press                                  |
| :------- | :------- | :------- | :-------------------------------------------------------- | :------------------ | :--------- | :--------- |
| Z f.2.2  <br> `Context AS(O; DP1-4=1,2,3,4; DP5=ON)` | LCD: Live View (with DP1)<br>EVF: Off | LCD: Live View (with DP1)<br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Menu display<br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off |

This confirmation was made under default settings when the MENU screen is displayed on the LCD and the shutter button is half-pressed.

- Z f.2.1: If the Info was not displayed prior to displaying the MENU screen, a half-press returns to the Live View.
- Z f.2.2: On the other hand, if the Info was displayed prior to displaying the MENU screen, a half-press does not return to the Live View but returns to the Info display.  

Therefore, it was confirmed that **a half-press does not necessarily return to the Live View**, but returns to the state immediately preceding the MENU screen, meaning that the transition outcome depends on the history.  
This is exactly the transition Step 5 or Step 28 from S3 shown in [case-a1-concept-map-cat.svg](../case-a1-concept-map-cat.svg).  
This means that support has confirmed one of the characteristics of this camera: that subsequent states cannot be predicted without considering not only the current state but also past history.


### Supplementary Observation

This phenomenon was also observed on the Z9.

In addition, on the D6, it has been observed that whether the Info was displayed beforehand or not, a half-press on the MENU screen clears both the MENU screen and the Info display to transition to the shooting state.



---

## <a id="case03"></a> CASE 03. EVF Live View Appears Temporarily, but LCD Returns to Info

### 3.1

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor (dock it against the camera body), starting with the screen facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (any lens is acceptable).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on                                   | Press [MENU] button           | Look into the EVF                         | Half-press                                  | Move eye away from EVF                     |
| :------- | :------- | :------------------ | :---------------- | :--------- | :--------------------- |
| Z f.3.1 <br> `Context AS(O; DP1-4=1,2,3,4; DP5=ON)` | LCD: Live View (with DP1)<br>EVF: Off | LCD: Menu display<br>EVF: Off | LCD: No display<br>EVF: On (Menu display) | LCD: No display<br>EVF: On (Live View) | LCD: Live View (with DP1)<br>EVF: Off |

### 3.2

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor (dock it against the camera body), starting with the screen facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (any lens is acceptable).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on                                   | Press DISP button repeatedly  <br> until Display 5 is shown | Press [MENU] button           | Look into the EVF                         | Half-press                                  | Move eye away from EVF                      |
| :------- | :------- | :--------------------------------------------------------- | :------------------ | :---------------- | :--------- | :--------------------- |
| Z f.3.2 <br> `Context AS(O; DP1-4=1,2,3,4; DP5=ON)` | LCD: Live View (with DP1)<br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Menu display<br>EVF: Off | LCD: No display<br>EVF: On (Menu display) | LCD: No display<br>EVF: On (Live View) | LCD: Info display <br>EVF: Off |

This confirmation covers the state after removing the eye from the EVF, following a sequence where the MENU screen is displayed under default settings, the user looks through the EVF, and a half-press is performed.

- Z f.3.1: If the Info  was not displayed prior to displaying the MENU screen, the LCD returns to the Live View.  
- Z f.3.2: On the other hand, if the Info was displayed prior to displaying the MENU screen, the LCD does not return to the Live View but returns to the Info display.  

In other words, it was confirmed that a half-press does not necessarily return to the Live View, but returns to the screen immediately preceding the MENU screen; in this case as well, similar to CASE-02, the **transition outcome depends on the history**.

### Supplementary Observation

This phenomenon was also observed on the Z9.

---

## <a id="case04"></a> CASE 04. LCD Opening Changes Info Recovery: DISP Route

### 4.1

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor, starting with the screen facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (any lens is acceptable).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Turn the power off

</details>

### Confirmation Results

| Sequence | Power on                                   | Press DISP button repeatedly <br> until Display 5 is shown | Half-press                                  | Press DISP button repeatedly<br> until Display 5 is shown | Open LCD                                    | Half-press                                  |
| :------- | :------- | :---------------------------------------------------- | :--------- | :---------------------------------------------------- | :------- | :--------- |
| Z f.4.1 <br> `Context AS(O; DP1-4=1,2,3,4; DP5=ON)` | LCD: Live View (with DP1)<br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off |

### 4.2

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor so that the screen is facing toward you.
2. Initialize the camera.
3. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
4. Go to [SETUP MENU] > [Limit monitor mode selection] and select only "Prioritize viewfinder (1)".
5. Go to [SETUP MENU] > [Automatic monitor display switch] and select "On (when monitor docked)".
6. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on                    | Press DISP button                           | Half-press                  | Press DISP button                           | Open LCD                                    | Half-press                                  |
| :------- | :------- | :---------------- | :--------- | :---------------- | :------- | :--------- |
| Z f.4.2 <br> `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)` | LCD: No display<br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Off<br>EVF: On when eye sensor is active | LCD: Info display <br>EVF: Off | LCD: Info display<br>EVF: Off | LCD: Info display<br>EVF: Off |

### 4.3

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor so that the screen is facing toward you.
2. Initialize the camera.
3. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
4. Go to [SETUP MENU] > [Limit monitor mode selection] and select only "Prioritize viewfinder (1)".
5. Go to [SETUP MENU] > [Automatic monitor display switch] and select "On (when monitor docked)".
6. Go to [CUSTOM SETTINGS MENU] > [d19 Custom monitor shooting display] and uncheck "Display 5".
7. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on                    | Press DISP button                           | Half-press                  | Press DISP button                           | Open LCD                                   | Half-press                                 |
| :------- | :------- | :---------------- | :--------- | :---------------- | :------- | :--------- |
| Z f.4.3 <br> `Context PV(OD; DP1-4=1,2,3,4; DP5=OFF)` | LCD: No display<br>EVF: Off | LCD: Info display<br>EVF: Off | LCD: No display<br>EVF: Off | LCD: Info display<br>EVF: Off | LCD: Live View (with DP1)<br>EVF: Off | LCD: Live View (with DP1)<br>EVF: Off |


The Info display can be displayed through various routes.  

First, there is the Info display as Display 5, which is reached by repeatedly pressing the DISP button when the "LCD is in the active state" during shooting. Each time the DISP button is pressed, the screen changes to Display 1, Display 2, and so on, until it reaches Display 5.  
As for the "LCD is in the active state," the following cases during power-on can be cited:
- In Automatic display switch mode, meaning under default settings `Context AS(O; DP1-4=1,2,3,4; DP5=ON)`, when you are sufficiently far from the viewfinder and the eye sensor is not activated.
- In Monitor only mode `Context MO(-; DP1-4=1,2,3,4; DP5=ON)`.
- In Prioritize viewfinder & Auto monitor switch (docked only), meaning `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`, when the LCD monitor is open.  

Note that Display 5 is classified as a shooting screen, as indicated by the fact that it can be selected under [CUSTOM SETTINGS MENU] > [d19 Custom monitor shooting display]. However, it is actually a full-screen display and does not accompany Live View.

In addition, other routes to display the Info display include pressing the DISP button once when the "LCD is not in the active state," or through other methods.
In CASE-04, we focus on the Info display when the DISP button is pressed once among these routes, and the others will be handled in CASE-05.


- Z f.4.1 is the case under default settings `Context AS(O; DP1-4=1,2,3,4; DP5=ON)`.  
Both before and after opening the LCD, it is the Info display as Display 5, and Nikon confirmed that **the Info display fixates** on the monitor in both cases.

- Z f.4.2 is the case in Prioritize viewfinder & Auto monitor switch (docked only) `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`.  
Nikon Support has clearly stated that while the Info display before opening the LCD turns off with a half-press to provide Live View inside the EVF, **the Info display after passing through the action of opening the LCD does not turn off with a half-press** and instead fixates.  
 The Info display before opening the LCD is reached by pressing the DISP button only once, so it is considered not to be Display 5. Since it does not fixate and Live View is obtained inside the EVF, this behavior is considered consistent with the Info display behavior from DSLRs.  
On the other hand, the Info display immediately prior to opening the LCD is also considered not to be Display 5, but it is reasonable to view that opening the LCD transforms it into a fixated Info display. Regarding the state at this moment, Nikon explicitly states in their response:
"Even if you keep pressing it halfway, it does not become a live view display. Also, because the monitor is open, the EVF display does not become active. (Literal translation)"  
This suggests that the critical transition is not merely entering the Info display, but entering the LCD active shooting-display context while an Info-related display is present.

- Z f.4.3 is the case in Prioritize viewfinder & Auto monitor switch (docked only) `Context PV(OD; DP1-4=1,2,3,4; DP5=OFF)`, which means that the Display 5 display is disabled in Z f.4.2.
Disabling was possible via [CUSTOM SETTINGS MENU] > [d19 Custom monitor shooting display].  
The comparison with Z f.4.2 is noteworthy; while the Info display before opening the LCD exhibits the same behavior as Z f.4.2, it was confirmed that the Info display after passing through the action of opening the LCD also turns off with a half-press.  
The Info display observed in Z f.4.3 turns off with a half-press and immediately transitions the camera to a shooting-ready state, which can be said to be consistent with the behavior of the Info display since the DSLR era.
Based on these points, in Z f.4.2, although the Info display immediately prior to opening the LCD is not Display 5, is it not fair to say that opening the LCD transforms it into an Info display that possesses fixation characteristics, namely Display 5.

Furthermore, regarding the deadlock issue (CASE-07 below) that triggered the launch of this repository, I communicated with Nikon repeatedly. Six months after the initial inquiry, I received the following message concerning Display 5:

> Regarding the phenomenon where, when the function of the questioned DISP button was disabled, if the LCD monitor is opened while the i menu is displayed, the info display remains and does not return to the shooting screen, if the customer does not need the info display, could you **try the desired operation after unchecking [Screen 5]** in the setting of Custom Menu [d19: Custom Shooting Display (Monitor)]? (Literal translation)

It is reasonable to view this response as symbolic of the fact that Display 5 holds the key to the fixation phenomenon.


### Supplementary Observation

Regarding Z f.4.1, it has been observed on the Z f in my possession that both before and after opening the LCD, looking through the EVF turns off the monitor at that moment to provide Live View, and removing the eye from the EVF displays the Info display on the monitor again.

This phenomenon was also observed on the Z9.

---

## <a id="case05"></a> CASE 05. LCD Opening Changes Info Recovery: [i] / Fn Routes

### 5.1

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor so that the screen is facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (no lens-specific differences were observed within the scope of our validation).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Go to [SETUP MENU] > [Limit monitor mode selection] and select only "Prioritize viewfinder (1)".
6. Go to [SETUP MENU] > [Automatic monitor display switch] and select "On (when monitor docked)".
7. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on                    | Press [i] button                            | Half-press                  | Press [i] button                            | Open LCD                                    | Half-press                                  | Half-press                                  |
| :------- | :------- | :--------------- | :--------- | :--------------- | :------- | :--------- | :--------- |
| Z f.5.1 <br> `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)` | LCD: No display<br>EVF: Off | LCD: Info display with [i] menu<br>EVF: Off | LCD: Off<br> EVF: On when eye sensor is active | LCD: Info display with [i] menu<br>EVF: Off | LCD: Info display with [i] menu<br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off |

### 5.2

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor so that the screen is facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (no lens-specific differences were observed within the scope of our validation).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Go to [SETUP MENU] > [Limit monitor mode selection] and select only "Prioritize viewfinder (1)".
6. Go to [SETUP MENU] > [Automatic monitor display switch] and select "On (when monitor docked)".
7. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on                    | Press and Release the Fn button            | Half-press                  |Press and Release the Fn button             | Open LCD                                    | Half-press                                  |
| :------- | :------- | :------------------------------ | :--------- | :------------------------------ | :------- | :--------- |
| Z f.5.2 <br> `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)` | LCD: No display<br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Off<br>EVF: On when eye sensor is active | LCD: Info display <br>EVF: Off | LCD: Info display<br>EVF: Off | LCD: Info display <br>EVF: Off |

As stated in CASE-04, the Info display can be displayed through various routes.  
Since the Info display reached by pressing the DISP button once when the "LCD is not in the active state" was confirmed in CASE-04, in CASE-05 I requested confirmation for the other cases.

Both Z f.5.1 and Z f.5.2 are the case in Prioritize viewfinder & Auto monitor switch (docked only) `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`.
- Z f.5.1 is the case where the [i] button is pressed once, and the Info display is displayed in the background of the [i] menu.  
- Z f.5.2 is the case of "Press and Release the Fn button." Since White Balance adjustment is assigned to the Fn button in the default settings, the Info display is left displayed after passing through the WB adjustment screen.

It was confirmed that in both cases, while the Info display before opening the LCD turns off with a half-press to provide Live View inside the EVF, **the Info display after passing through the action of opening the LCD does not turn off with a half-press** and instead fixates.  
In this case as well, although the Info display immediately prior to opening the LCD is not Display 5, it is reasonable to view that opening the LCD transforms it into a fixating Info display.

### Supplementary Observation

It has also been observed on the D6 in my possession that when the [i] button is pressed once, the Info display is displayed in the background of the [i] menu, and pressing the [i] button once more causes the [i] menu to disappear, leaving only the Info display.

This phenomenon was also observed on the Z9. However, to adjust the white balance, I used the dedicated WB button instead of the Fn button.

---

## <a id="case06"></a> CASE 06. Display 5 Disabled: Info No Longer Fixates, but Display Index Resets

### 6.1

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor, starting with the screen facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (any lens is acceptable).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Go to [SETUP MENU] > [Limit monitor mode selection] and select only "Prioritize viewfinder (1)".
6. Go to [SETUP MENU] > [Automatic monitor display switch] and select "On (when monitor docked)".
7. Go to [CUSTOM SETTINGS MENU] > [d19 Custom monitor shooting display] and uncheck "Display 5".
8. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on                    | Open LCD                     | Press DISP button ,once   | Close LCD             | Open LCD            | Close LCD           | Press [i] button             | Open LCD          |Half-press        |
| :------- | :------- | :------- | :---------------------- | :-------- | :------- | :-------- | :--------------- | :------- | :--------- |
| Z f.6.1 <br> `Context PV(OD; DP1-4=1,2,3,4; DP5=OFF)` | LCD: No display<br>EVF: Off | LCD: Live View (with DP1)<br>EVF: Off| LCD: Live View (with DP2)<br>EVF: Off| LCD: No display<br>EVF: Off | LCD: Live View (with DP2)<br>EVF: Off| LCD: No display<br>EVF: Off | LCD: Info display with [i] menu<br>EVF: Off | LCD: Live View with [i] menu<br>EVF: Off | LCD: Live View (with DP1)<br>EVF: Off |

This is a transition confirmation after displaying the Info display with Display 5 disabled.

It was confirmed that the Display 2 layer, which was displayed before displaying the Info display, is **reset to the Display 1 layer after passing through the Info display** reached by pressing the [i] button once.


### Supplementary Observation

This phenomenon was also observed on the Z9.

In addition, it has also been observed on the D6 in my possession that when the [i] button is pressed once, the Info display is displayed in the background of the [i] menu, and pressing the [i] button once more causes the [i] menu to disappear, leaving only the Info display.


---

## <a id="case07"></a> CASE 07. DISP Disabled: Practical Lock / Recovery Failure

### 7.1

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor so that the screen is facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (no lens-specific differences were observed within the scope of our validation).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Go to [SETUP MENU] > [Limit monitor mode selection] and select only "Prioritize viewfinder (1)".
6. Go to [SETUP MENU] > [Automatic monitor display switch] and select "On (when monitor docked)".
7. Go to [CUSTOM SETTINGS MENU] > [f2 Custom controls (shooting)] and assign "None" (OFF) to the DISP button.
8. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on                    | Press [i] button                           | Open LCD                                     | Half-press                  | Press DISP button        |
| :------- | :------- | :--------------- | :------- | :--------- | :---------------- |
| Z f.7.1 `DISP button = "OFF None"`<br>`Context PV(OD; DP1-4=1,2,3,4; DP5=ON)` | LCD: No display<br>EVF: Off | LCD: Info display with [i] menu<br>EVF: Off | LCD: Info display with [i] menu<br>EVF: Off |  LCD: Info display <br>EVF: Off  | LCD: Info display <br>EVF: Off|

### 7.2

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor so that the screen is facing toward you.
2. Initialize the camera.
3. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
4. Go to [SETUP MENU] > [Limit monitor mode selection] and select only "Prioritize viewfinder (1)".
5. Go to [SETUP MENU] > [Automatic monitor display switch] and select "On (when monitor docked)".
6. Go to [CUSTOM SETTINGS MENU] > [f2 Custom controls (shooting)] and assign "None" (OFF) to the DISP button.
7. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on                    | Press [i] button                           | Open LCD                                     | Half-press                  | Press [i] button                            | Press DISP button, once                            | Press [MENU] button        | Half-press                                  | Power off, then on                     |
| :------- | :------- | :--------------- | :------- | :--------- | :--------------- | :---------------------- | :------------------ | :--------- | :----------------- |
| Z f.7.2 `DISP button = "OFF None"`<br>`Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`| LCD: No display<br>EVF: Off | LCD: Info display with [i] menu<br>EVF: Off | LCD: Info display with [i] menu<br>EVF: Off |  LCD: Info display <br>EVF: Off  | LCD: Info display with [i] menu <br>EVF: Off   | LCD: Info display  with [i] menu <br>EVF: Off   | LCD: Menu display<br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off |

This is a confirmation of a phenomenon where, under a certain setting, the Info fixates on the LCD after a specific operation, **making it impossible to obtain Live View, and furthermore, an immediate recovery path is severed without any warning due to customization**.

- Z f.7.1 is the phenomenon that motivated the launch of this repository and is also the article posted on  [![Nikon Rumors](https://nikonrumors.com/2026/01/05/critical-ui-deadlock-issue-on-the-nikon-zf-camera-with-firmware-update-c-version-3-00.aspx/)](https://nikonrumors.com/2026/01/05/critical-ui-deadlock-issue-on-the-nikon-zf-camera-with-firmware-update-c-version-3-00.aspx/).  
This is the content that Nikon replied was a specification, and I requested reconfirmation once again.
 This confirms the practical recovery problem that motivated this repository: after an Info-related route enters the LCD active state, shutter-button half-press does not restore Live View, and if DISP has been disabled by customization, the most immediate recovery route is unavailable.
 
- Z f.7.2 is a confirmation that subsequent attempts to recover to Live View following Z f.7.1 do not succeed with any of the [i] button, DISP button, MENU button, or even cycling the power. 
Nikon support confirmed the extended recovery-failure sequence with the DISP button function disabled. 
After the [i] button route and LCD opening, shutter-button half-press removed the [i] menu overlay but left the LCD on the Info display. Pressing the [i] button again restored the [i] menu over the Info display. Pressing the DISP button did not restore Live View, because the DISP function had been disabled. 
The MENU button still opened the MENU screen. However, when the shutter button was half-pressed from the MENU screen, the camera returned to the Info display rather than to Live View.  
Power cycling also did not clear the state. After turning the camera off and on again and waiting ten seconds, the LCD still showed the Info display. A further shutter-button half-press again left the camera on the Info display.

This confirmation is important because it shows that the problem is not merely a temporary display state. Under this customization, several ordinary recovery operations — [i], DISP, MENU → half-press, power cycling, and shutter-button half-press after power cycling — failed to restore a composition-capable Live View display.

CASE 07 confirms the practical consequence of disabling the DISP recovery path: once the Info display has entered the persistent state, the camera can remain trapped in Info across menu operations, shutter-button half-press, and power cycling.

### Supplementary Video Observation: Z f and Z9

A supplementary video record was also made using both the Nikon Z f and the Z9.

The sequence corresponds closely to Z f.7.2, except that in the video the final power-cycle step was performed by removing and reinserting the battery. 
In both cameras, the same core behavior was observed: after the Info display entered the persistent state, ordinary recovery operations did not restore a composition-capable Live View display.

The Z9 observation is not a Nikon support confirmation. However, it is important supplementary evidence suggesting that this behavior may not be limited to a single Z f unit.

- [![Reference Video for Z f.7.2](https://youtu.be/CgRiFayc5yQ)](https://youtu.be/CgRiFayc5yQ)
- [![Reference Video for the specific Z9](https://youtu.be/JXYC30shRI8)](https://youtu.be/JXYC30shRI8)

---

## <a id="case08"></a> CASE 08. Info Display During Burst Shooting

### 8.1

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor (dock it against the camera body), starting with the screen facing toward you.
2. Insert a writable memory card capable of high-speed continuous shooting. Format it in advance if necessary.
3. Initialize the camera.
4. Attach an appropriate lens and remove the lens cap (no lens-specific differences were observed within the scope of our validation).
5. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
6. The exposure mode can be any mode, such as Manual or Aperture Priority. However, since continuous shooting will be performed, adjust settings appropriately so that the shutter speed is faster than approximately 1/60 sec.
7. Go to [PHOTO SHOOTING MENU] > [Release mode] and select "Continuous H".
8. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on | Look into the EVF, Half-press shutter button | Press the shutter button to initiate continuous release <br> for the initial five seconds | Without lifting finger from the shutter button, move eye away from EVF <br> and continue continuous release for an additional five seconds |  Without lifting finger from the shutter button, look into the EVF <br> for the final five seconds  | Lift finger from the shutter button and  move eye away from EVF |
| :------- | :-------- | :-------- | :-------- | :-------- | :-------- | :-------- |
| Z f.8.1 <br>`Context AS(O; DP1-4=1,2,3,4; DP5=ON)`| LCD: Live View (with DP1)<br>EVF: Off | LCD: No display<br>EVF: On (Live View) |LCD: No display<br>EVF: On (Live View)*Burst flickering|LCD: Live View (with DP1)*Burst flickering<br>EVF: Off |LCD: No display<br>EVF: On (Live View)*Burst flickering|LCD: Live View (with DP1)<br>EVF: Off |

### 8.2

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor (dock it against the camera body), starting with the screen facing toward you.
2. Insert a writable memory card capable of high-speed continuous shooting. Format it in advance if necessary.
3. Initialize the camera.
4. Attach an appropriate lens and remove the lens cap (no lens-specific differences were observed within the scope of our validation).
5. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
6. The exposure mode can be any mode, such as Manual or Aperture Priority. However, since there is a step where continuous shooting is performed, adjust settings appropriately so that the shutter speed is faster than approximately 1/60 sec.
7. Go to [PHOTO SHOOTING MENU] > [Release mode] and select "Continuous H".
8. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on |Press DISP button repeatedly until Display 5 is shown | Look into the EVF, Half-press shutter button | Press the shutter button to initiate continuous release <br> for the initial five seconds | Without lifting finger from the shutter button, move eye away from EVF <br> and continue continuous release for an additional five seconds |  Without lifting finger from the shutter button, look into the EVF <br> for the final five seconds  | Lift finger from the shutter button and  move eye away from EVF |
| :------- | :-------- | :-------- | :-------- | :-------- | :-------- | :-------- | :-------- |
| Z f.8.2 <br>`Context AS(O; DP1-4=1,2,3,4; DP5=ON)`| LCD: Live View (with DP1)<br>EVF: Off | LCD: Info display <br>EVF: Off| LCD: No display<br>EVF: On (Live View)|LCD: No display<br>EVF: On (Live View)*Burst flickering|LCD: Info display <br>EVF: Off |LCD: No display<br>EVF: On (Live View)*Burst flickering|LCD: Info display<br>EVF: Off |


Up to CASE-07, confirmations have been made regarding the behavior of the Info display before shooting, but CASE-08 handled the situation during shooting under default settings.

- Z f.8.1 is the result of continuous shooting performed immediately after turning on the power under default settings.  
Nikon support confirmed the baseline continuous-shooting behavior when the camera had not been placed into the Display 5 / Info state.  
In this sequence, the camera started with the LCD monitor active and showing Live View with Display 1. When the photographer looked into the EVF and half-pressed the shutter button, the EVF displayed Live View and the LCD monitor turned off.
During continuous shooting, the EVF continued to show Live View, with screen flickering caused by continuous shooting. When the photographer moved their eye away while continuing to shoot, the LCD monitor turned on and displayed Live View with Display 1, again with screen flickering caused by continuous shooting. Looking into the EVF again returned the display to EVF Live View.

- Z f.8.2 is the result of continuous shooting performed after displaying Display 5 (Info display) immediately after turning on the power under default settings.  
Nikon support confirmed the continuous-shooting behavior after Display 5 / Info had been selected.  
In this sequence, the camera first started with the LCD monitor active and showing Live View with Display 1. The DISP button was then pressed repeatedly until the Info display was shown on the LCD monitor.  
After the photographer looked into the EVF and half-pressed the shutter button, the EVF displayed Live View and the LCD monitor turned off.  
During continuous shooting, the EVF continued to show Live View.  
However, when the photographer moved their eye away while continuing continuous shooting, the LCD monitor turned on and displayed the Info screen, not a through-image Live View display.  
Looking into the EVF again returned the display to EVF Live View. After continuous shooting ended and the photographer moved their eye away, the LCD monitor again displayed the Info screen.  
This confirmation is important because it contrasts directly with Z f.8.1.  
In Z f.8.1, when Display 5 / Info had not been selected, the LCD monitor displayed Live View with Display 1 during continuous shooting after the photographer moved their eye away from the EVF.  
In Z f.8.2, after Display 5 / Info had been selected, the LCD monitor displayed the Info screen instead.  
This indicates that the retained Display 5 / Info state can affect the LCD display even during continuous shooting, when a Live View display would normally be expected on the active viewing device.
I could not identify a practical photographic advantage in continuing to display the Info screen under this condition. The Info display does not provide a through-image for composition.  
During this condition, the Info display also did not appear to function as an active shooting-control display. While continuous shooting was in progress and the Info display was shown on the LCD monitor, attempts were made to change shutter speed and other shooting settings, but no response was observed.  
That is, because the LCD monitor during continuous shooting neither shows a Live View image nor functions as an operational display, it is difficult to consider this a meaningful continuous shooting display.

### Supplementary Video Observation: Z f and Z9

A supplementary video record was also made using both the Nikon Z f and the Z9.

Additionally, it was observed on the specific Z9 as well that it becomes impossible to exit the Info display during continuous shooting. This has been made into videos along with the Z f.
- [![Reference Video for Z f.8.2](https://youtu.be/Linzjau-Ucg)](https://youtu.be/Linzjau-Ucg)
- [![Reference Video for the specific Z9](https://youtu.be/_l8WBW9vs6I)](https://youtu.be/_l8WBW9vs6I)


---

## <a id="case09"></a> CASE 09. Info Display During Multiple-Exposure Overlay Shooting

### 9.1

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor, starting with the screen facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (any lens is acceptable).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Go to [PHOTO SHOOTING MENU] > [Multiple exposure] > [Multiple exposure mode] and select "On (series)".
6. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on | Press the shutter button<br> to take the 1st shot of multiple exposure | Look into the EVF | Move eye away from EVF | Press the shutter button<br> to take the 2nd shot of multiple exposure |
| :------- | :-------- | :-------- | :-------- | :-------- | :-------- |
| Z f.9.1 <br>`Context AS(O; DP1-4=1,2,3,4; DP5=ON)`| LCD: Live View (with DP1)<br>EVF: Off | LCD: The 1st shot is superimposed on the live View (with DP1), and the multiple exposure icon flashes<br>EVF: Off | LCD: No display<br>EVF: The 1st shot is superimposed on the live View, and the multiple exposure icon flashes| LCD: The 1st shot is superimposed on the live View (with DP1), and the multiple exposure icon flashes<br>EVF: Off | LCD: Live View (with DP1)<br>EVF: Off |


### 9.2

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor, starting with the screen facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (any lens is acceptable).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Go to [PHOTO SHOOTING MENU] > [Multiple exposure] > [Multiple exposure mode] and select "On (series)".
6. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on | Press DISP button repeatedly <br> until Display 5 is shown | Press the shutter button<br> to take the 1st shot of multiple exposure | Look into the EVF | Move eye away from EVF | Press the shutter button<br> to take the 2nd shot of multiple exposure |
| :------- | :-------- | :-------- | :-------- | :-------- | :-------- | :-------- |
| Z f.9.2 <br>`Context AS(O; DP1-4=1,2,3,4; DP5=ON)`| LCD: Live View (with DP1)<br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: No display<br>EVF: The 1st shot is superimposed on the live View, and the multiple exposure icon flashes | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off |

### 9.3

<details>
<summary><i>Settings for Reproduction (Click to expand)</i></summary>

1. Close the LCD monitor so that the screen is facing toward you.
2. Initialize the camera.
3. Attach an appropriate lens and remove the lens cap (any lens is acceptable).
4. To prevent the camera from powering off unexpectedly during validation, go to [CUSTOM SETTINGS MENU] > [c3 Power off delay] and set each item to the maximum time.
5. Go to [SETUP MENU] > [Limit monitor mode selection] and select only "Prioritize viewfinder (1)".
6. Go to [SETUP MENU] > [Automatic monitor display switch] and select "On (when monitor docked)".
7. Go to [PHOTO SHOOTING MENU] > [Multiple exposure] > [Multiple exposure mode] and select "On (series)".
8. Turn the power off.

</details>

#### Confirmation Results

| Sequence | Power on |  Press and Release the Fn button | Press the shutter button<br> to take the 1st shot of multiple exposure | Look into the EVF | Move eye away from EVF | Press the shutter button<br> to take the 2nd shot of multiple exposure |
| :------- | :-------- | :-------- | :-------- | :-------- | :-------- | :-------- |
| Z f.9.3 <br>`Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`| LCD: Live View (with DP1)<br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off | LCD: Info display <br>EVF: Off |

- Z f.9.1 is the baseline multiple-exposure overlay shooting behavior.  
Nikon support confirmed the baseline behavior of multiple-exposure overlay shooting when Display 5 / Info had not been selected beforehand.  
The camera started with the LCD monitor Live View  and after the first exposure, the LCD monitor displayed the through-image with the first captured frame superimposed faintly.  
When the photographer looked into the EVF, the LCD monitor turned off and the EVF displayed the same superimposed through-image, and when  the photographer moved their eye away, it switched back to the LCD monitor.  
After the second exposure was taken, the camera returned to LCD Live View.  
This confirms the normal baseline behavior as described in the manual.

- Z f.9.2 is the multiple-exposure overlay shooting after Display 5 / Info.  
Nikon support  confirmed that the LCD monitor does not display the superimposed image when Display 5 / Info has been selected beforehand.  
The camera started with the LCD monitor Live View, and the DISP button was pressed repeatedly until the Info display was shown on the LCD monitor.  
After the first exposure, the LCD monitor remained on the Info display.  
When the photographer looked into the EVF, the LCD monitor turned off and the EVF displayed the superimposed through-image, but when  the photographer moved their eye away, the LCD monitor returned to the Info display.  
After the second exposure was taken, the LCD monitor still displayed the Info screen.  
This confirmation is important because it contrasts directly with Z f.9.1, where both devices displayed the superimposed through-image when Display 5 had not been selected.  
This indicates that the retained Display 5 / Info state can affect the LCD display even during multiple-exposure overlay shooting, a mode whose purpose is to aid composition by superimposing earlier exposures.

- Z f.9.3 is the multiple-exposure overlay shooting after Fn / Info route and LCD Opening.  
Nikon support confirmed an additional multiple-exposure overlay shooting sequence under `Context PV(OD; DP1-4=1,2,3,4; DP5=ON)`, involving the Fn-button route and LCD opening. 
The camera started with both the LCD monitor and EVF off.  
After the Fn button was pressed and released, the LCD monitor displayed the Info screen, and even when the LCD monitor was then opened, the LCD continued to display the Info screen.   
After the first exposure was taken, the LCD monitor still remained on the Info display.  
Since this confirmation was performed under the Viewfinder Priority setting, the EVF did not turn on even when the photographer looked into it, and the LCD monitor continued to display the Info screen.  
Moving the eye away afterwards did not change the display state.  
After the second exposure was taken, the LCD monitor still displayed the Info screen.  
This means that, under this route, the expected multiple-exposure overlay view was not available at all during the tested sequence.

It may be argued that the Info display can still be useful for changing camera settings. However, this does not resolve the issue.  
The purpose of overlay shooting, as described in the manual, is to aid composition by superimposing earlier exposures on the view through the lens. An Info display without a through-image cannot provide that compositional aid.

Moreover, the manual also warns that changing camera settings during multiple-exposure shooting may end multiple-exposure shooting. 
For that reason, the ability to view or change settings on the Info display cannot be treated as an equivalent substitute for the intended overlay shooting display.
