# Changelog

All notable changes to this project will be documented in this file.

## [Krifto-V1] - 2022-10-19

### Documentation
    
- Updated README.md ([0752f92](0752f92fa78aefa71e456dade1c3d3a3abe69f64)) 
  
  


### Features
    
- Enable host action commands ([b0579df](b0579df1235e5c4383eb5b86837ec4ed3a856742)) 
  This makes interfacing with USB hosts such as OctoPrint much more
convenient.

see https://marlinfw.org/docs/configuration/configuration.html#host-action-commands
  

- Enabled PID for bed temperature ([574be3e](574be3ee72057184828f70c9856e60bb6a6d5bb3)) 
  The bed seems to heat up a bit slower initially with these settings, but
doesn't go full bang-on/bang-off, but rather gets nicely PID-controlled

see https://en.wikipedia.org/wiki/PID_controller
and https://marlinfw.org/docs/configuration/configuration.html#pid

specific settings gratefully taken from
mlee12382/Neptune_3@72679f17df79fb7b09e46fc8703e7c4f8c2b8e4a
  

- Enable nozzle park ([65880b8](65880b83b044991ddadbdea0de7191888d9d1c6a)) 
  This is in preparation for the filament change (M600).

Nozzle should now come over to the front left side when told to park.

see https://marlinfw.org/docs/configuration/configuration.html#nozzle-park
  

- Enable quick home ([c69365f](c69365fbf585c7f308bc9195eb6997017b6e81ab)) 
  Home both X and Y at the same time, shaving off some seconds off
before finally being able to obsessively watch that first layer.
  

- Enable realtime reporting commands ([80f07c3](80f07c30cba25b6fab533aca5627d840ad2c25ce)) 
  This should give more information to USB hosts, e.g. OctoPrint.
  

- Enable setting BAUD rate over serial (M575) ([cdcc19e](cdcc19ee3dad08dda7bce6ebee37f2a1c307ad3a)) 
  Allows a USB host to change the BAUD rate if needed. Not sure how
this could be useful, but seems to be a nice option to have.
  

- Bumped BAUD rate to 250000 ([9ed82a6](9ed82a6dba55b4ef73cd3cecf5a6a095cfa883b8)) 
  This should make printing over USB more reliable.
  

- Enable long filename support for the host ([09b7dfe](09b7dfe77407f3d2461e8cf395b4be7d80346368)) 
  Makes OctoPrint and other see more than just the FILENA~1.GCO.

see https://marlinfw.org/docs/configuration/configuration.html#long-filenames
  

- Enable cancel objects reporting ([29361ce](29361cee74c3410de355170fb78a355519676056)) 
  allows for individually cancelling printing of objects, if defined in the gcode

see https://marlinfw.org/docs/configuration/configuration.html#cancel-objects
  

- Set fast pwm for the fan ([2c60b93](2c60b9320caec47a0510b50ce55dba33a270b0e4)) 
  see https://marlinfw.org/docs/configuration/configuration.html#fast-pwm-fan
  

- Enable adaptive step smoothing ([203a752](203a7522712424b5e2c2539bfdd52c18a4a9defc)) 
  see https://marlinfw.org/docs/configuration/configuration.html#adaptive-step-smoothing
  

- Enable S-Curve Acceleration ([80e5a4e](80e5a4e8244f2f2a1e943b3a00eb8542b078526d)) 
  see https://marlinfw.org/docs/configuration/configuration.html#acceleration
  

- Enable advanced pause / filament change M600 ([53b68c9](53b68c9b9baf585ccd373df8d731004174daf3cb)) 
  Note that this requires a host (e.g. OctoPrint over USB). The  LCD
firmware does not know how to handle the necessary prompts.

For this to work go to your OctoPrint settings -> Printer -> Serial Connection ->
Firmware & Protocol and add M876 to the list of Emergency commands. The firmware
listens to this command for confirmation, and hence this need to be allowed
through by OctoPrint in the first place.

see https://marlinfw.org/docs/configuration/configuration.html#advanced-pause
  

- Enable G26 mesh validation command ([255c9ec](255c9ecb668f83b6a5c0dc14d3e9eea94de4e9f3)) 
  see https://marlinfw.org/docs/configuration/configuration.html#bed-leveling
  

- Enable probe repeatability test M48 ([3b83d80](3b83d80dc4ff5570cbd0f44ee46664913335dd3e)) 
  see https://marlinfw.org/docs/configuration/configuration.html#probe-testing
  

- More reasonable load/purge lengths for M600 ([d866f73](d866f73aa1e2406a000bbbe70eac0768728038fb)) 
  
  

- Enable ADVANCED_OK ([11e9cdb](11e9cdb9484f994e1f4882fcf168ce12509a2c40)) 
  Include extra information about buffers in "ok" messages, should help
stability with USB-hosts.

see https://marlinfw.org/docs/configuration/configuration.html#buffer-/-hosts
  

- Enable sending full report to host ([2a2fd8d](2a2fd8d842560cae7dc6b2f051fdad4594fa78b4)) 
  This should improve the ability of OctoPrint (and other USB host software)
to interface with the machine.
  

- Increase buffer sizes for USB printing ([2a41d9b](2a41d9b021f7251c0b201cf03e4223178ca43749)) 
  Bumped buffer sizes to prevent stuttering and bad quality prints
when printing over USB (e.g. with OctoPrint).

see https://community.octoprint.org/t/a-list-of-recommended-marlin-features/39048

Note that you should put M400 at the top of your end-gcode in your slicer.
This is causes the buffer of commands in the path planner to be emptied
before doing other end-of-print tasks, such as turning of the heaters

see also: https://marlinfw.org/docs/configuration/configuration.html#buffer-/-hosts
  

- Enable M154 and M115 (pos/geo reporting) ([30fa9d0](30fa9d034da67a7d61467125fa7580a9f7c9669b)) 
  Enable automatic reporting of position (M154)
and extend M115 output to report geometry

see https://marlinfw.org/docs/configuration/configuration.html#auto-report
and https://marlinfw.org/docs/configuration/configuration.html#extended-capabilities-report
  

- Enable junction deviation ([633e2ae](633e2ae96ede03c1431e48c42d0c68590b9dbecb)) 
  replace the original CLASSIC_JERK acceleration
mode with Marlin's default Junction Deviation
see https://marlinfw.org/docs/configuration/configuration.html#acceleration
  


### Miscellaneous Tasks
    
- Translated chinese comments ([3d4d017](3d4d017275dafb7a53c19fa9cf76881218091da9)) 
  
  

- Set author and info ([c1db9f5](c1db9f561ebc2632bceef0142c9ca6bfdf1ab5ba)) 
  
  

- Translate some comments to English ([071bc87](071bc8728e21466367e04a093f1809ffe10b4b55)) 
  
  


### Customization
    
- Set default e-steps to 138.2 ([38d0a36](38d0a36777be299d9e5c6834daacd9ab1c47fa46)) 
  Warning, this may not be the right value for your machine!
Elegoo's default firmware has e-steps at 130, which caused to be a slight
under-extrusion on my machine.

Check out how to calibrate the E-Steps here:
https://my3dlife.com/how-to-calibrate-your-e-steps-simple-guide-and-calculator/

Note that the LCD of the Neptune 3 does not support reading or setting this value.

Over OctoPrint or some other host, send M503 to read the current values (where it says
steps per unit), then use the above link to measure and calculate the new value.

Then go in and set the new value using M92 E<yournewlycalculatedvalue>.

If you want to make this setting permanent over printer power off/on cycles, write
the new settings to EEPROM using M500.
  



<!-- generated by git-cliff -->
