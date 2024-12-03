## Project Outcomes

 **DEMO simulation model with acceptable fidelity to experimental measurements**

* ±20% in pressures, temperatures, mass flow rates
* PID control parameters are 'sensible'
* Time constants of transients are acceptable

**Simulation scenarios to do:**
* Plant 1 startup
* Plant 9 startup
* Plant 1 to Plant 9 swap
* Plant 9 to Plant 1 re-takeover
* ATLAS Strips testing scenarios
* Surface storage operation

**Virtual Commissioning setup with all the hardware and software pieces in place**

* PLC set up and installed in a secure rack
* Dedicated computer with monitor, keyboard, mouse etc. from where to operate the machine
* PLC logic implemented
* PID controllers, either implemented on EcosimPro or on PLC, with similar

## User Stories

* Play around with swapping out CVs of valves to see which valve fits best
* Play around with different commissioning configurations, for example:
* 3 out of 4 loops are open, but one closed
* All loops open, but powers are halved
* CMS startup procedure with a mid-way stop to -20°C, but conducted on DEMO
* Investigate restarting when system still liquefied, vs after some time of warm up.