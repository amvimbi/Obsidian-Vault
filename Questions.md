

## 2024-12-03

- [x] Ask about implicit definitions for the PID in MATLAB
- [x] In Demo, the takeover was done by DP1016 vs DPC2022 (Because the dP for NV1016 could have a variable dP) (Wrong, the takeover was done the other way round)
- [x] The PID Object, taking can be set using a LUT
- [x] Dani about the pump discharge logic

## 2024-12-04

- [ ] Effective V?
- [x] Ask about CERN supervision?

- [x] Demo spends longer time in step 2
- [x] ATMS used a radiator, the 2PACL introduced an R744 - this increases capacity?
- [x] Chiller Doc
- [x] LEWA LGD3 6kW each? Nominal Flow 1.5?
- [x] Exporting values as an object

## 2024-12-04

- [x] Ask Dani about the PLC hierarchy - speak to this in the description of Demo
## 2024-12-07

- [x] Ask if Ph are independent (Ph)
- [x] Ask about the DAE
- [x] Pump discharge warmer by Detector cold (startup)
- [ ] Demo in SHC and colder at the inlet (Our HX is probably not modeled correctly TBS)
- [x] Ask about gain scheduling code
- [x] Ask about the Update of AMS
	- [x] Was capacity improvement needed for Velo
- [x] Pump may go supercritical for high pressurization
- [x] Pressure Drop before evaporators
- [x] Rangeability
- [x] The chiller HTC
## 2024-12-10

- [x] Confirm the units for get Partials
- [x] Ask about the units if d$P/dh$

DTC can control in NFT Control

## 2024-12-18

- [ ] Why was there an imbalance in the HXs

## 2024-01-26

- [x] The mass flow equation: The units of $Cv$ don't have a good physical interpretation.

## 2024-01-26

- [x] The valve CV5x4?, does it server as a expansion or mass flow control: The dP is set by the compressor. The Valve still expands to more or lest the same point just at different mass flows.
- [x] The chiller seems not to be coping with the $S0$ load. (valve was not properly handling reverse flow)
## 2025-03-11

- [x] Plant 9 chiller?
- [ ] The correlation $\frac{dP}{dz}$
- [ ] Boundaries? Raul

## 2025-05-14

- [ ] Why not remove TC4080 and only have STC4080 with parameters updated for the switch between heater temperature control and the Accumulator $T_{sat}$?
- [ ] IF-THEN-ELSE statements don't have discontinuity handling and we need these for Transition Logic.
- [ ] We have algebraic loops due to controller connections to the muxes.
- [ ] Use the PARALLEL keyword

## 2025-05-17

- [ ] 