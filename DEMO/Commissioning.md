## Alarms to be tested by operation team:

==2025-02-12==

- [x] CS1e_A1_ST8074_TS
Forced Mode ST8074 to 9.5C (threshold was 10). After 10s full system stopped.
#todo TS is propagated to FS and all stops?

- [x] CS1e_A1_ST8074_AL 
Forced Mode ST8074 to 10.5 (threshold was 11). After 10s AL triggered.

- [x] CS1e_A1_SH5d60_TS7
Forced SH5d60 to 14.5 K (threshold is 15). After 10s TS triggered.

- [x] CS1e_A1_ST4080_FS
Forced ST4080 to 9.5 (threshold 10). Alarm triggered. System went to FS.

- [x] CS1e_A1_ST4080_AL
Forced ST4080 to 10.5 (threshold 11). 10s alarm triggered.

- [x] CS1e_P1_DP1014_IOEr_TS
Put DPC1014 on Manual Mode (activation allows .MMoSt *or* AuRegSt)
Disconnected PT1s18: activated
Disconnected PT1014: activated

- [x] CS1e_P1_DP1s14_IOEr_TS
Put DPC1s14 on Manual Mode
Disconnected PT1014: activated
Disconnected PT8074: activated (also caused plant FS)

- [x] CS1e_P1_DP9s82_IOEr_TS
- Put DPC9s82 on Manual Mode
- Disconnected PT1s18: activated
- Disconnected PT9082: activated

- [x] CS1e_P1_DP1016_IOEr_TS
- Put DPC1016 on manual mode
- Disconnected PT1016: activated
- Disconnected PT9082: activated

- [x] CS1e_P1_DP2022_IOEr_TS
- Put DPC2022 on manual mode
- Disconnected PT2022: activated
- PT8074: activated (also caused plant FS)

==2025-02-13==
- Kept DPC2022 in regulation mode
- Disconnected PT2022: alarm also activated

- [x] CS1e_P1_DT9a97_IOEr_TS
- Put DTC9a97 in manual mode
- disconnected PT9082: alarm triggered
- disconnected TT9a98: alarm triggered

- [x] CS1e_P1_SH5a48_IOEr_TS
- Put SHC5a48 in manual mode
- disconnected PT5a48: alarm triggered
- disconnected TT5a48: alarm triggered

- [x] CS1e_P1_SH5a58_IOEr_TS
- Put SHC5a58 in manual mode
- disconnected PT5a58: alarm triggered
- disconnected TT5a58: alarm triggered

- [x] CS1e_P1_DT9b97_IOEr_TS
- - Put DTC9b97 in manual mode
- disconnected PT9082: alarm triggered
- disconnected TT9b98: alarm triggered

- [x] CS1e_P1_SH5b48_IOEr_TS
- Put SHC5b48 in manual mode
- disconnected PT5b48: alarm triggered
- disconnected TT5b48: alarm triggered

- [x] CS1e_P1_SH5b58_IOEr 
- Put SHC5b58 in manual mode
- disconnected PT5b58: alarm triggered
- disconnected TT5b58: alarm triggered

- [ ] CS1e_P1_DP2022_TS

## Calculations to be tested by operation team:

- [x] CS1e_A1_LT4h84 
	- check formula on git and verify with sensor input

- [x] CS1e_A1_LT4j84
	- have heater cable working
	- check formula on git and verify with dp input
	- check response with different levels/setpoints
- At 10:45, Viren implemented the formula in matlab and verified with the current status of the plant with current dp at 90 mbar. This was confirmed to give the output of 12%, which was also the case in SCADA
- Forced mode put the dp at 75 and 105 mbar, confirmed to give -4% and 26.6%

- [ ] CS1e_A1_LT4080
	- have both LT4h84 and LT4j84 confirmed

- [x] CS1e_A1_CV5d40_Rq 
	- have STC4080 active
	- when cooling request is below 20%, CV5d40 should be closed
	- when cooling request is above 20%, CV5d40 should be linearly open
	- verify linear correlation (calculation)
- Set cooling request in forced mode and look at valve position
- Tested at 10% and 60%
- CV5d40 was respectively 0% and 50%

- [x] CS1e_A1_CV5d42_Rq
	- have STC4080 active
	- when cooling request is 0%, CV5d42 should be closed
	- when cooling request is above 0%, CV5d42 should be linearly open
	- verify linear correlation (calculation)
- Set cooling request in forced mode and look at valve position
- CV5d42_t3 and CV5d42_t4 were respectively set temporarily to 10% and 90%
- Tested at 5%, 50%, 95%
- CV5d42 was respectively 0%, 50% and 100%

- [x] CS1e_A1_HeatRq
	- have STC4080 active
	- when STC4080 is below 50%, heating request should be 0% (and heaters off)
	- when STC4080 is above 50%, heating request is linear
	- verify linea correlation (by calculation)
* Output positioning. Set outputs and look at heating request
* Checked at 55% and 90% STC4080 output
* Heating request 10% and 80% confirmed.

- [x] CS1e_A1_CoolRq
	- have STC4080 active
	- when STC4080 is below 50%, cooling request should be linear between 0& and 100%
	- CoolRq_tL should be set to a non-zero value
	- when STC4080 is between 50% and 80%, CooLRq should return the non-zero value
	- Above 80% verify linear correlation from non-zero value to 0%
* CoolRq_tL set to 10%. CV5d40 always open at 10% therefore.
* Output positioning.
* Checked at STC4080 at 45%, 25%, 75% and 90%.
* CoolRq was respectively 19%, 55%, 10% and 5%. As per graph.

- [x] CS1e_A1_STC8074_TSP 
	- operate STC8074 at slighty higher setpoint compated to STC4080
	- verify following logic:
		- IF Detector_Pressurization.x OR Detector_Circulation.x THEN
		  STC8074_TSP := MIN(STC8074_TSP_tH, MAX(DetTemp, STC4080_USP));
		  ELSE
		  STC8074_TSP := STC4080_USP;
		  END_IF;
	- currently in Detector_Circulation
	- STC8074_TSP corresponds to DetTemp at 17'C
	- Changed USP to 18'C, and STC8074_TSP also changed to 18'C
	- changed STC8074_TSP_tH to 16'C and STC8074_TSP changed to 16'C
	- in operation_mode, STC8074_TSP is equal to STC4080_USP, confirmed by changing STC4080_USP from 0'C to -1'C

- [x] CS1e_A1_STC8074_ASP
	- confirmed in Detector Pressurisation and before that ASP is equal to DetTemp(@17) + 5C
	- confirmed in Detector Circulation ASP is equal to DetTemp(@17)
	- in operation_mode, STC8074_ASP is equal to STC4080_USP, confirmed by changing STC4080_USP from 0'C to -1'C

- [x] CS1e_A1_STC4080_TSP
	- set BPR_limit to -1'C, while TSP was at 0'C. It took the minimum of the two

- [ ] CS1e_A1_STC4080_ASP
	- confirmed for detector_pressurisation
	- confirmed for detector_circulation by forcing DetTemp to be lower than BPR_limit
	- *to be confirmed in accumulator_control and operation*

- [x] CS1e_A1_STC4080_Kc  

- [x] CS1e_A1_STC4080_Ti  
- For both Kc and Ti the following was done
- t1 and t2 are set at 48% and 52%
- first Kc and Ti were checked at STC4080 output positioning at 0%
- then checked at output 50% to make sure they were not changing
- then to output 55% to see the change
- then back to 50% to make sure the dead zone works both ways
- then back to auto

**Heaters**
TT4x82_OHL_Ttl = 50C
TT4x82_OHL_TtH = 90C
OHL_tL = 50
OHL_tH = 100

![[2025-02-13-tc4x82-ohl.png]]

- [x] CS1e_A1_TC4a82_OHL
* ==2025-02-13==
* Confirmed by setting TT4a82 to 50C, 70C, 90C
* Heater OHL went to 100%, 75%, 50%
* Same procedure for all the rest below.
- [x] CS1e_A1_TC4b82_OHL
- [x] CS1e_A1_TC4c82_OHL
- [x] CS1e_A1_TC4d82_OHL
- [x] CS1e_A1_TC4e82_OHL
- [x] CS1e_A1_TC4f82_OHL

- [x] CS1e_A1_STC4080_OHL  

![[2025-02-13-stc4080-ohl.png]]
STC4080_OHL_TtL = 70C
STC4080_OHL_TtH = 90C
STC4080_OHL_tL = 50%
STC4080_OHL_tH = 100%

checked at 14C, 70C, 75C, 80C, 90C, and 100C
returned respectively 100%, 100%, 87.5%, 75%, 50%, 50%

- [x] CS1e_A1_STC4080_OLL
![[2025-02-13--stc4080-oll.png]]
STC4080_OLL1TtL = 0K 
STC4080_OLL1TtH = 4K
STC4080_OLL1_tH = 75%

checked at 4K, 3K, 2K, -1K
returned respectively 0%, 18.8%, 37.5% and 75%

- [ ] CS1e_A1_STC4080_SP_spd

- [x] CS1e_A1_STC4080_FSLL
- changed STC4080_TSP from 15'C to 16'C. Active setpoint slowly changed from 15'C to 16'C and with it the FSLL
- additionally, changing FSLL_t1 from 5'C to 4'C also changed the FSLL from 10'C to 11'C

- [x] CS1e_A1_STC4080_ALLL
- checked similarly to calculation above

- [ ] CS1e_A1_STC8074_FSLL
- this is linked to STC4080.ActSP, instead of STC8074.ActSP

- [ ] CS1e_A1_STC8074_ALLL
- this is linked to STC4080.ActSP, instead of STC8074.ActSP

- [x] CS1e_P1_DPC2022_SP 
	- setpoint changes when changing the two separate linked setpoint parameters

- [x] CS1e_P1_DTC5a40_SP1
- see procedure for DTC5a42_SP1

- [x] CS1e_P1_DTC5a40_SP
- see procedure for DTC5a42_SP

- [x] CS1e_P1_DTC5a4x_SPdrift
	- see b-side drift calculation

- [x] CS1e_P1_DTC5a40_K
- at 5K, boost = 1
- at 4K, boost = 2
- at 3K, boost = 3
- each time, SP was 6 K

- [x] CS1e_P1_DTC5a40_Kc
- for each cases above, the default for Kc = 10
- the results were 10, 20 30

- [x] CS1e_P1_DTC5a42_SP1
	- underlying calculation verified by changing STC5a42_USP and changing DTC5x4x_SP_p1
	- DTC5a42_USP was changed from 7 K to 6 K
	- DTC5x4x_SP_p1 was changed from 1 K to 2 K

- [x] CS1e_P1_DTC5a42_SP
- from SP1 calculation, we could see that SP also changed correspondingly from 6K to 5K
- changing the SPdrift value to 5K also changed the SP variable to 5K, confirming both sides of the calculation

- [ ] CS1e_P1_DTC5a42_K

- [ ] CS1e_P1_DTC5a42_Kc

- [x] CS1e_P1_DTC5b4x_SPdrift
- calculation of ST9082 - ST5a48 - 2
- confirmed for 15'C and -51'C respectively, resulting in 64
- 75'C - 51'C became 124
- same for the a side, but not listed here

- [x] CS1e_P1_DTC5b40_SP1
- see procedure for DTC5a42_SP1

- [x] CS1e_P1_DTC5b40_SP
- see procedure for DTC5a42_SP

- [x] CS1e_P1_DTC5b40_K
- see for DTC5a40_K, same story

- [x] CS1e_P1_DTC5b40_Kc
- see DTC5a40_Kc, same story

- [x] CS1e_P1_DTC5b42_SP1
- see procedure for DTC5a42_SP1

- [x] CS1e_P1_DTC5b42_SP
- see procedure for DTC5a42_SP

- [ ] CS1e_P1_DTC5b42_K

- [ ] CS1e_P1_DTC5b42_Kc

- [x] CS1e_P1_SHC5b58_SP
	- changed SHC5b58_p1 from 2 K to 4 K to check if the calculation changes the setpoint
	- set SHC5a40 in regulation mode and see that the SHC5v58 setpoint changes with the SHC5a40 setpoint change

- [x] CS1e_P1_SHC5a58_SP
- see procedure above

- [x] CS1e_P1_DPC1014_OLL
- in the FA, it's a fixed parameter always at 0%

- [x] CS1e_P1_DTC5a40_OHL
- y-axis goes from 50% to 100%
- x-axis goes from 0.5'C to 1'C
- forced SH5a48 to 1'C, 0.75'C, 0.5'C and 0.4'C
- DTC5a40_OHL was respectively 100%, 75%, 50%, 50%

- [x] CS1e_P1_TT5a60_OHL
- y-axis goes from 4% to 100%
- x-axis goes from -25'C to -15'C
- forced SH5a48 to -15'C, -20'C and -25'C
- DTC5a42_OHL was respectively 100%, 52%, 4%

- [x] CS1e_P1_DTC5a42_OHL
- y-axis goes from 0% to 100%
- x-axis goes from 0'C to 5'C
- forced SH5a48 to 5'C, 2.5'C and 0'C
- DTC5a42_OHL was respectively 100%, 50%, 0%

- [x] CS1e_P1_DTC5b40_OHL
- confirmed, see procedure of DTC5a40_OHL

- [x] CS1e_P1_TT5b60_OHL
- see procedure for TT5a60_OHL

- [x] CS1e_P1_DTC5b42_OHL
- confirmed, see procedure for DTC5a52_OHL

- [x] CS1e_P1_DP2022_t1
	- confirmed by changing DP2022_t2 and DPC2022_SP to different values