# Subaru ECU Definitions and Instructions for MerpMod

This repository is used to develop Subaru ECU definitions for use with:
*   Romraider http://www.romraider.com
*	ECUFlash http://www.tactrix.com

Discussion thread at RomRaider for this repo: http://www.romraider.com/forum/viewtopic.php?f=34&t=8635

# Branches:
*	Stable branch: Contains the latest NON-experimental definitions. These definitions have been thoroughly debugged and tested.
*	Beta branch: Formerly "Experimental". Contains definitions with finalized 'bases' that are newly defined for a particular rom. Considered safe for use by advanced users.
*	Alpha branch: Contains definitions that are under active development. **DO NOT USE THIS BRANCH UNLESS YOU ARE A DEVELOPER OR A DEVELOPER'S TESTER**
*	MerpMod branch: Bleeding edge testing of patches **DO NOT USE THIS BRANCH UNLESS YOU ARE A DEVELOPER OR A DEVELOPER'S TESTER**

Benefits of using Git:
*	Better tracking of definition history/changes.
*	Easier to implement standardization of new tables, scalings, descriptions, formats, etc.
*	Ease of use for end users, no more scouring a forum to find definitions or get an updated def.
*	Easier to collaborate and stay organized.
*	By pointing RomRaider or ECUFlash at the local repo, you can easily switch between different branches for quick tests/comparisons.

#WARNING: These definitions are EXPERIMENTAL!

These definition files are created as the result of the extremely
complex and time consuming process of reverse-engineering the factory ECU.
Because of this complexity, it is necessary to make certain assumptions and,
therefore, it is impossible to always deal in absolutes in regards to
representations made by these definitions. In addition, due to this complexity
and the numerous variations among different ECUs, it is also impossible to
guarantee that the definitions will not contain errors or other bugs. What this
all means is that there is the potential for bugs, errors and misrepresentations
which can result in damage to your motor, your ECU as well the possibility of
causing your vehicle to behave unexpectedly on the road, increasing the risk of
death or injury. Modifications to your vehicle's ECU may also be in violation of
local, state and federal laws. By using these definition files, either directly
or indirectly, you agree to assume 100% of all risk and RomRaider's creators and
contributors shall not be held responsible for any damages or injuries you
receive. This product is for advanced users only. There are no safeguards in
place when tuning with RomRaider. As such, the potential for serious damage and
injury still exists, even if the user does not experience any bugs or errors. As
always, use at your own risk.

# XML INSTRUCTIONS

# RomRaider Logger definition:
*	ECUFlash/subaru standard/merpslogger.xml
*	Select this RomRaider logger definition from the settings menu.

# ECUFlash definitions:
*	Select the entire 'subaru standard' folder in ECUFlash settings.

# SPEED DENSITY USE

*	Switchable between MAF, SD, and MAF/SD Blending using SD Mode Switch
*	Start with MAF mode, log SD output, and calculate error to build VE Table
*	Use blending to overcome idle stability issues

# REV LIMITER USE

Launch Control
*	Active when clutch is pressed and vehicle speed is below FFS threshold.
*	Deactivated by pressing the brake pedal.

Flat Foot Shift (FFS)
*	Active when clutch is pressed and vehicle speed is above FFS threshold.
*	Calculates rev limit based on gear ratio

# CEL FLASHING USE

Retains use of CEL light for true CELS! In the event of a true CEL, flashing still works, just inverted!

CEL flashes when FBKC or estimated EGT Exceeds thresholds AND engine load exceeds threshold set in ECUFlash

CEL Will Recall IAM when you press Clutch + Cruise resume button
*	1 Flashes = IAM 16 (NO KNOCK)
*	-2 Flashes = IAM 15
*	-17 Flashes = IAM 0 (BAD KNOCK)

#TEST INSTRUCTIONS

Visit #RomRaider IRC Channel on FreeNode for support!
If urgent, e-Mail or gChat to merrill@sharptuning.com

SD Test
*	Log RPM, Manifold Relative Pressure, and all "MM SD" parameters.
*	Log idle and normal driving.

Rev Limit Test
*	Log RPM and all "MM LC/Launch Control", "MM RevLimit Active", "MM Clutch Flags", and "MM Brake Flags" parameters.
*	Log idle and test by fully pressing clutch, no brakes, and try to raise RPM over limit.

FFS Test
*	Log RPM, "MM FFS", and "MM ** Flags" parameters.
*	Log while driving. Hold throttle 100% in a higher gear and press clutch in. Release clutch when fueling resumes.

CEL Test
*	Log all "MM ** Flags" parameters.
*	With ignition on, test IAM recall: Press clutch and cruise control resume. Note behavior of CEL light.
*	While driving, log RPM, Engine Load, FBKC, AF sensor 1 resistance, and "MerpMod CEL Signal". Note behavior of CEL light and compare to logs.

THIS SOFTWARE IS PROVIDED "AS IS". USE AT YOUR OWN RISK. NO WARRANTY. THIS SOFTWARE IS LICENSED TO YOU “AS IS,” AND WITHOUT ANY WARRANTY OF ANY KIND, WHETHER ORAL, WRITTEN, EXPRESS, IMPLIED OR STATUTORY, INCLUDING BUT NOT LIMITED TO WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. AUTHOR DOES NOT WARRANT THAT THIS SOFTWARE DOES NOT INFRINGE ANY RIGHTS OF THIRD PARTIES.


