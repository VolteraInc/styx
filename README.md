#v0.12.0
- Release the motors when STOP is pressed. This forces the printer to re-calibrate the tool on the next action.
- Delay tool calibration until an action, e.g. OUTLINE, CALIBRATE, etc.
- Drag-based selection is now aligned to the circuit. It's odd at first, but make selection
  on a rotated circuit as easy as it is for unrotated circuits
- Click-based selection now has a few pixels of tolerance, so near misses will still select
- Fix: Click-based selection properly selects the closest path
- Fix: When reconnecting to the printer, remind it what the current tool is.
- Fix: Alt+o will no longer executes an Outline outside of the OutlineStep
- Fix: detect printer’s ‘--start--’ message even when it’s prefixed with a partially sent message from the previous run
- Fix: Handle early end-of-file when parsing gerbers.

#v0.11.2
- reduced sensitivity of hole detection (thanks @fred and @matt)

#v0.11.1
- Solder procedure now accepts a holes file
- Display an error and stop probing if probe drops into a hole or misses board
- Highlight forum announcements in the notification window
- Accept gerber files with a .art extension
- Accept text-based excellon files with a .drl extension
- Fixed a rare whitescreen issue during app launch (thanks @ryan13)

#v0.10.1
- Fixed bug where the first trace in Eagle Gerbers was discarded.

#v0.10.0
Disconnections while Heating
- Eliminate occasional disconnects while heating by disabling PID control
- Display an error if printer disconnects while baking

Gerber Changes
- Improved handling of irregular shaped polygons (Like 'S' or figure '8's)
- Ignore deprecated 'Mirror Image' and 'Axis Select' commands
- Fixed pad handling for Kicad Gerbers.
- Improved handling of Gerbers that use Paint and Scratch approach when creating pads.
- Single pass lines that intersect with other single pass lines will no longer be split into separate lines

Connection Handling
- More precise switching from normal communication to firmware upload mode
- Improve handling of printer resets
- Wait until the printer boot up completes before allowing user to send commands to it.
- Disable Home and E-Stop buttons during firmware upload and when not connected (thanks HP)
- Show the firmware upload overlay, if uploading, after closing another overlay (e.g. release notes, support, etc) (thanks HP)

Other
- Stop heating and move to the home position when a procedure is closed or ended
- Fixed issue where support package would fail to submit if printer was not connected.
- Eliminate extra character that was sometimes added to gcode console when using the alt+c shortcut

#v0.9.0
Forum Integration
- Show headlines from forums on dashboard and during dispense steps

Alignment
- Fixed bug in align circuit that was preventing holes from being used in some cases (@matt)
- Keep probe closer to the surface when aligning (thanks @mharris, @a2retro)

Gerber Processing
- Split traces to prevent double dispensing when traces overlap
- Resolved 3 CAD program specific problems (Allegro, Ultiboard)

Other
- Prevent dispense height of 0 (thanks Nick)
- Allow probe pitch as low as 0.1mm (thanks James)
- Disable print height adjustment buttons when at min or max value
- No more whitescreen if you rush to the alignment step before the circuit is fully processed (@alroyalmeida)
- Enhanced logging to help track down whitescreen bug

#v0.8.0
- Improved error messages especially when loading circuits
- Ability to *Load Last Circuit* even if printer is disconnected (Thanks @a2retro)
- Added *.GBR extension to solder paste dispenser (Thanks @mHarris)
- Removed panning ability in print preview. Consistent with Eagle UI.
- Resolved a print preview glitch that occurred when bounding box in selective print was dragged outside preview area.
- For small rectangular pads, center line will actually be centered, instead of offset to a side.
- During Align Circuit, ability to select alignment pads
- During Align Circuit, use measured position of first pad to improve estimated position of second pad (Thanks @a2retro)
- Ability to compensate for backlash in X and Y axis through firmware parameter.

#v0.7.0

- Step size during fine movement in locate pads reduced from 0.1mm to 0.05mm.
- Single line traces will now be truncated at pads. Should prevent probe from descending into holes. (Thanks @emcniece, @agustinbmed)
- Improved recovery from serial communication errors.
- Software will reconnect to a printer if it happens to appear on a different port after a disconnect.
- Firmware update will retry if errors occur.
- Resolved an invalid function call that would have left the app in a semi-responsive state.

#v0.6.5
- Prefer holes when selecting targets for aligned prints.
- Fixed binding conflict with arrow keys when console is visible.

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
