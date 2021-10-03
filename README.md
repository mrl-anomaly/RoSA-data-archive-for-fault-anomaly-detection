# MIT-MRL-GPAD-Data-Archive

** Welcome to the Synthetic Time-Series General-Purpose Anomaly Dataset in Physical Domain (GPAD) Data Archive **

This place stores all the data sequence that are open access to the community.

For more knowledge about the dataset, please checkout this page: https://mrl-anomaly.github.io/#home.

Currently, the archive contains data sequence of the following health conditions:
1. Healthy mode (84 sequences)
2. Manual N-mode (51 sequences) 
3. MC-sampled V-mode (50 sequences)
4. Manual D-mode (50 sequences)

Data sequence to be compiled and added: (9/21/21: Might be delayed due to a thorough synthesizer apparatus upgrade)
1. MC-sampled Automated N-mode
2. Randomly-generated Automated V-mode
3. Combinational Axial + Radial Modes

Column Annotation:

| Public Column Name | Description |
| --- | --- |
| Time | DAQ Main Host time in millis() | 
| Rel Time | Relative time computed from 'Time'| 
| MCU Time | DAQ MCU time (Use above 2 instead) |
| Sample Freq | Sampling frequency for every time step (no smoothing used) |


| Label Space Column Name | Description |
| --- | --- |
| N-mode? | Whether N-mode anomalous event is on or not|
| V-mode? | Whether V-mode anomalous event is on or not|
| D-mode? | Whether D-mode anomalous event is on or not|
|Binary Macro Health Mode | Whether plant is experiencing anomaly (A) or healthy (H)|
| Multi-class Sublevel Mode | Sublevel Mode of the plant, expands A to V/D/N |
| Multi-class Sublevel Mode Enc | Category number based on 'Multi-class Sublevel Mode' | 
| N-mode attribute | Lateral force reading introduced to the plant |
| V-mode attribute | Active vibration frequency introduced to the plant |
| D-mode attribute | External damper motor resistance (15ohm is regular operating condition) |




