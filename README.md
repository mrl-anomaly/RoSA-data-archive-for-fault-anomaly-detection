![alt text](https://github.com/mrl-anomaly/MIT-MRL-RoSA-Data-Archive/blob/main/graphical_abstract.png?raw=true)

# MIT-MRL-RoSA-Data-Archive

**Welcome to the Rotodynamic System with Synthetic Anomaly (RoSA) dataset**

This place stores all the data sequence that are open access to the community.

To cite this dataset:
```
@INPROCEEDINGS{Yeung2022-mt,
  title     = "{RoSA:A} Mechatronically Synthesized Dataset for Rotodynamic
               System Anomaly Detection",
  booktitle = "{IEEE/RSJ} International Conference on Intelligent Robots and
               Systems ({IROS})",
  author    = "Yeung, Yip Fun and Alshehri, Ali and Paul-Ajuwape, Alex and
               Tahiry, Farida and Furokawa, Mikio and Hirano, Takayuki and
               Youcef-toumi, Kamal",
  year      =  2022
}
```

**Current release - the archive contains data sequence of the following real-time modulated health conditions:**
1. Healthy mode (84 sequences of the rotordynamic plant operating under various **speeds** and a normal damping load)
2. Manual N-mode (51 sequences of the rotordynamic plant operating under various **speeds** and **lateral deflections**) 
3. MC-generated V-mode (50 sequences sequences of the rotordynamic plant operating under various **speeds** and **external vibrations**)
4. Manual D-mode (50 sequences sequences of the rotordynamic plant operating under various **speeds** and **increased damping loads**)

Each sequence is a .csv file that contains the columns described below in **Column Annotation**. Visualization of the signals are generated and packed in the folders for your convenience.

**How faulty data is generated:**

Unlike traditional methods that generates faulty conditions with **time-invariant** faulty components like bearings, shaft couplings, etc, our method follow a more automated way, such that we can generate large amount of **time-varying** synthetic faults. In essence, we build an automated setup to inject different type of faulty patterns into a rotordynamic plant. The faulty patterns in this dataset includes vibration (e.g., simulating different faulty bearings), abnormal lateral load, and abnormal damping torque load. They are named as 'V', 'N' and 'D' modes, respectively.

The automated setup allows us to command the severity of faults in **real-time**. Thus, for every time step, the faulty condition is actively modulated and **annotated**, giving users the chance to invesigate time-varying fault **prediction** algorithms. (Arguably, traditional fault generation methods only grant users with out-of-the-box **diagnostic/detection** capacity.)



For more information about the automated synthesis apparatus, checkout:
```
@INPROCEEDINGS{Yeung2021-yg,
  title     = "A {General-Purpose} Anomalous Scenario Synthesizer for Rotary
               Equipment",
  booktitle = "{IEEE} International Conference on Robotics and Automation",
  author    = "Yeung, Yip Fun and Alshehri, Ali and Wampler, Lois and Furokawa,
               Mikio and Hirano, Takayuki and Youcef-toumi, Kamal",
  year      =  2021
}
```


**Updates**
Update - (10/31/22):
1. This dataset is presented in the 2022 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS 2022). 
2. RoSA-II with better instrumentation and more extensive scope of anomalies is planned.

Update - (7/19/22):
This dataset will be presented in the 2022 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS 2022), stay tuned!


**Column Annotation:**

| Public Column Name | Description |
| --- | --- |
| Time | DAQ Main Host time in millis() | 
| Rel Time | Relative time computed from 'Time'| 
| MCU Time | DAQ MCU time (Use above 2 instead***) |
| Sample Freq | Sampling frequency for every time step (no smoothing used) |


| Condition State (Label) Space Column Name | Description |
| --- | --- |
| N-mode? | Whether N-mode anomalous state is on or not|
| V-mode? | Whether V-mode anomalous state is on or not|
| D-mode? | Whether D-mode anomalous state is on or not|
|Binary Macro Health Mode | Whether plant is experiencing anomaly (A) or healthy (H)|
| Multi-class Sublevel Mode | Sublevel Mode of the plant, expands anomaly(A) to V/D/N ({0,1,2,3}; notice V-mode overwrites N-mode; notice currently D do not coexist with V/N modes|
| Multi-class Sublevel Mode Enc | Category number based on 'Multi-class Sublevel Mode' | 
| N-mode attribute | Lateral force reading introduced to the plant |
| V-mode attribute | Active vibration frequency introduced to the plant |
| D-mode attribute | External damper motor resistance (15ohm is regular operating condition) |
| Force Sensor Number | Which force sensor to read for N-mode and V-mode (already taken care of, don't use***) |
| Tool Head Number | EoAT number for N-mode and V-mode (no numerical meaning***) |

| Measurement (Feature) Space Column Name | Description | Sensor |
| --- | --- | --- |
| Desired Speed | Desired operating angular velocity of the shaft | MCU internal | 
| Actual Speed | Actual operating angular velocity of the shaft  | 12-bit Encoder installed on the plant | 
|Shaft Control Effort | Control effort to maintain the angular speed of the shaft | MCU PWM |  
| Orient. xyz| Orientation of the shaft | IMU installed on the shaft | 
| AngVel. xyz| Angular velocity of the shaft | IMU installed on the shaft |  
| LinAcc. xyz| Linear acceleration of the shaft | IMU installed on the shaft |  
| Mag. xyz | Magnetic field around the shaft | IMU installed on the shaft |  
| Quat. xyzw | Quaternion representation of the shaft | IMU installed on the shaft |  
| Temp | Temperature around the shaft |  Temperature Sensor installed on the shaft|
| Audio | Audio reading around the shaft |  Audio Sensor installed on the shaft|
| Strain Gage| Strain reading on the surface of the shaft| Strain Gage Sensor installed on the shaft |

*** Note: all other columns in the .csv files are DEPRECATED or already accounted for to generate the above columns. It would be meaningless to use them. ****
