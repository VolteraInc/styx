#v0.6.4

File Selection
- Added *.GBP extension to file picker (Thanks Rick)
- Deleting a file will force circuit processing again.
- Fixed bug where loading recent files could load incorrect files.

Gerber Processing
- Improved Gerber processing - better support for thermals and self intersecting lines.
- Fixed minor parsing issue seen in Diptrace and Pulsonix Gerbers (Thanks Rick & Steve)
- Fixed minor Drill file issue seen in Kicad files when origin was in top left. (Thanks @emcniece)

Other
- Prevent multiple pads from being confirmed at the same time. (Thanks Mikey Mike!)

#v0.6.3
- Raise the probe higher during alignment confirmation to ensure we exit vias

#v0.6.2

Double Sided
- Introduced ability to do a 'Simple' or 'Aligned' print.
- Simple prints allow you to print exactly where you want.
- Aligned prints require you to locate 2 points on the circuit. (Identical to solder procedure)
- If loading a bottom gerber file, print will automatically be mirrored.
- Added a smarter algorithm for identifying the 2 points to locate.

Gerber Processing
- Rounded pads should now render properly.
- When filling pads, allow the innermost pass to be a line, instead of forcing it to be a rectangle. This will reduce over-filling.
- Detect and ignore fully enveloped pads (e.g. a small pad inside of a large one) to avoid double dispensing.
- Improved handling of very small Eagle pads with rounded corners.
- Fixed minor bug processing non-vector text from Altium Gerbers.

Firmware (0.0.11)
- Fix to help prevent probe from pushing into calibration plate.

Other
- Alt+C opens the gCode Console
- Release notes display on startup the first time a new version is opened.
- Increased default print speed by 66%
- Changed default print settings to improve filling of large pads and wide traces.

Bug Fixes
- Fixed minor bug where the wrong pad was highlighted in large circuits during Locate Pads step.
- Fixed authentication problem that occurred when sending the support package for some users.
- Fixed software crash that would occur when dragging around selection box in print & calibrate step


#v0.5.0
- Removed *.DRL extension as an option from hole file selection. Only *.TXT files are supported.
- Reduced Z-Motor speed which fixed height variation issues in extended prints.
- Minor bug fix when extracting serial port information.
- Added ability to bake wet ink from the reflow procedure.
- After a setting is changed, system will prevent a print until change has been applied.
- System will prevent settings from being changed while a print is active.
- Procedure Status and Print Status will be displayed to user when relevant.
- Software will no longer connect to B1 printers (Incompatible anyway)

Known Issues
- It is still possible to change settings while a print is active if +/- arrows were pressed.


#v0.4.3
- Reduced unnecessary logging.

#v0.4.2
- Fixed critical bug that occurred when log files exceeded a certain size

#v0.4.1
- Fixed minor bug that occurred after probing.

#v0.4.0
- Added *Restore Defaults* button in the settings window. Also default settings appear as placeholders.
- Typing custom settings is possible now. Previous data validation was broken/frustrating.
- App will periodically check for software updates.
- If a circuit file fails to load, the app should recover and allow you to upload another file.
- Added 3 more firmware errors to help detect faulty/unexpected probe triggering.
- Printer will rotate dispenser gears before descending (fixes a poorly mounted dispenser by meshing gears)
- Fixed critical bug in logging where the maximum file size was not being respected (resulting in abnormally large log files)
- Fixed critical bug in windows installer where files could not be loaded.
- Files that fail to load, can now be submitted through the support package.
- Added keyboard shortcuts for easier calibration (- , + )

#v0.3.1
- Fixed minor bug where printer expected a dispenser to be mounted when starting a bake cycle.

#v0.3.0
- Enhanced support page. Able to submit support package through App.
- Firmware will automatically update if no printer does not report it's version. (Helps with botched upgrades)
- Highlighted pad indicator is more obvious (Yellow & Pulsing)
- Added Alt+R shortcut to release motors. And motors will release after parking.

#v0.2.1
- Automatic FW Updates added. SW will check on startup.
- Added E-stop overlay to indicate when E-Stop was pressed.
- LED glow lights will not go fully dark
- If thermistor is disconnected, heater will turn off after 10 seconds of no temperature change.
- Corrected default Solder Paste height from 0.1mm to 0.14mm
- Increased motor timeout to 5 mins & Locate Pads step will reset if motors not homed.
- System will raise when preparing probe/dispenser.
- Added selective print video to solder paste dispensing.

#v0.2.0
- Added e-stop shortcut (esc,esc)
- [Mac] Remove unnecessary items from Application menu
- Update sidebar videos
- Update help links

#v0.1.8
- Updated Hello World GTL
