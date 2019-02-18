# Hierarchical-Building-Microgrid

[//]: # (Image References)
[image1]: ./Images/SEST2019_Building_MG_scheme.png "Hierarchical Model Predictive Control for buildings"

[//]: # (Video References)
[gif1]: ./Result/HBMG-PV_PEV_BAT_without_disturbance.gif
[gif2]: ./Result/HBMG-PV_PEV_BAT_with_disturbance.gif


## Introduction

This MATLAB code consists of a two-level Hierarchical Model Predictive Control (HMPC) implemented to manage a building microgrid equipped with Li-ion batteries, photovoltaic solar panels (PV) and plug-in electrical vehicles (PEV) as depicted in the following scheme. This control structure is a simplified one which highlights the tertiary control level with the implementation of the economic power dispatch.


![alt text][image1]

## Approach

### 1. Plant under study
* 1 Photovoltaic painel with real data (~0 - 1 kW)
* 1 Building with power consumption between 0 - 0.8 kW
* 1 Li-ion battery package (Capacity: 68 kWh/ Max. charging and discharging rate: +/- 10 kWh)
* 1 Electrical Vehicle with 1 Li-ion battery package (Capacity: 68 kWh/ Max. charging and discharging rate: +/- 2.5 kWh)

### 2. Proposed Control
* Tertiary Control layer with daily market
  * Horizon (Nh): 48h (_wheather forecast + power consumption_)
  * Ts': 24h (_each day the building sends to the community aggregator the electricity trading plan for the following day commitiment_)
  * Ts: 1h (_discretization of the electricity trading plan_)
* Tertiary Control layer with intraday market
  * Horizon (Nh): 6h (_wheather forecast + power consumption_)
  * Ts: 1h (_electricity purchasing or selling in last moment_)

## Code structure

The code was developped in object oriented fashion. The main file is called *Hierarchical_Building_Microgrid.m*. Therefore, to run the MPC controller, you only need to run this file. 

The entire code is structured into 9 classes:

* Photovoltaic.m
* Wind_Turbine.m
* Smart_Building.m
* Electrical_Vehicle.m
* Battery.m
* Electricity_Market.m
* Tertiary_Control.m
* Secondary_Control.m
* Common.m

## Simulation 

You can have a preview of the HMPC by seeing the simulations videos of the **Hierarchical Control without disturbance** and **Hierarchical Control with disturbance**:

#### Hierarchical Control without disturbance

![][gif1]

#### Hierarchical Control with disturbance

![][gif2]

