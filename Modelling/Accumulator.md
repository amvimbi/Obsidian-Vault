Below is the accumulator model as we have it. The level can be calculated from the average density and the quality weighted densities.

## $M = V*\rho$

## $Level = \frac{(\rho -\rho _{vsat})Z}{(\rho_{lsat}-\rho_{vsat})}$ where Z is the tank height
## $V\left( ρ+h\frac{∂\rho}{∂h​​​}|_{P} \right)\frac{dh}{dt}​=V\left(1−h​\frac{∂\rho}{∂P}|_{h}​​​\right)\frac{dP}{dt}​+\dot{m}_{in}\dot{h}_{in}​−\dot{m}_{out}\dot{​h}_{out}​+Q$

## $V\left(\frac{∂P}{∂ρ}\frac{​dP}{dt}​|_{ h}+\frac{∂h}{∂ρ}​\frac{dh}{dt}|_{ P}\right)=\dot{m}_{in}​−\dot{m}_{out}​$

We can rearrange the energy conservation equation thus;

## $\frac{dh}{dt}​= \frac{\dot{m}_{in}\dot{h}_{in}​−\dot{m}_{out}\dot{​h}_{out} + q}{V\left( ρ+h\frac{∂\rho}{∂h​​​}|_{P} \right)} + \frac{V\left(1−h​\frac{∂\rho}{∂P}|_{h}​​​\right)}{V\left( ρ+h\frac{∂\rho}{∂h​​​}|_{P} \right)}\frac{dP}{dt}​$


## $\frac{dt}{dh}​= \frac{1}{V\left( ρ+h\frac{∂h}{∂ρ​​​}|_{P} \right)}\left(\dot{m}_{in}\dot{h}_{in}​−\dot{m}_{out}\dot{​h}_{out} + {V\left(1−h​\frac{∂P}{∂ρ}|_{h}​​​\right)}\frac{dP}{dt} +Q\right)​$

Buckholt et al. Richter mass conservation

## $\frac{dt}{dh} ​= \frac{1}{M}\left(\dot{m}_{in}\left(\dot{h}_{in}​−h\right)+\dot{m}_{out}\left(\dot{​h}_{out}-h\right) + V\frac{dt}{dP} + Q\right)$

## Linearizing the Accumulator

![[Control volume.png]]

![[Control volumeII.png]]

Here the objective is to have a dynamic equation in terms of the specific enthalpy from which a corresponding pressure may be found through the output equation. 
## For finding variation in dhldh

The corner cases are;

- Hin = 113kJ/kg, Q in is 5kW. This corresponds to stepping from ~10 Bar, the density was 104.
- Hin = 200kJ/kg, Q in is 5kW. This corresponds to stepping from ~35 Bar, the density was 104.
- Hin = 200kJ/kg, Q in is 1kW. This corresponds to stepping from ~35 Bar, the density was 707.
- Hin = 113kJ/kg, Q in is 5kW. This corresponds to stepping from ~10 Bar, the density was 707.

