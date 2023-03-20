# MIT-MRL-RoSA-Data-Archive

<a href="url"><img src="https://github.com/mrl-anomaly/MIT-MRL-RoSA-Data-Archive/blob/main/RoSA%20flyer%20cropped.png" align="center" width="600" ></a>

## Welcome to the Rotodynamic System with Synthetic Anomaly (RoSA) dataset :) 

This dataset is released for scholars to develop and validate fault detection, diagnostic, and prediction algorithms on rotor systems.

To cite this dataset:
```
@INPROCEEDINGS{Yeung2022-ez,
  title     = "{RoSA:A} Mechatronically Synthesized Dataset for Rotodynamic
               System Anomaly Detection",
  booktitle = "2022 {IEEE/RSJ} International Conference on Intelligent Robots
               and Systems ({IROS})",
  author    = "Yeung, Yip Fun and Paul-Ajuwape, Alex and Tahiry, Farida and
               Furokawa, Mikio and Hirano, Takayuki and Youcef-Toumi, Kamal",
  pages     = "2642--2649",
  month     =  oct,
  year      =  2022
}

```

**The dataset generation process is described in detail in the following paper:**

[Yeung, Yip Fun, Alex Paul-Ajuwape, Farida Tahiry, Mikio Furokawa, Takayuki Hirano, and Kamal Youcef-Toumi. 2022. “RoSA:A Mechatronically Synthesized Dataset for Rotodynamic System Anomaly Detection” In 2022 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), 2642–49.](https://ieeexplore.ieee.org/abstract/document/9982146)

*If you are not interested in the details, a short description of this dataset is presented below.* 

**Current release - the archive contains data sequence of the following real-time modulated healthy/faulty conditions:**
1. Healthy mode (84 sequences of the rotordynamic plant operating under various **speeds** and a **normal damping load**)
2. Manual N-mode (51 sequences of the rotordynamic plant operating under various **speeds** and **lateral deflections**) 
3. MC-generated V-mode (50 sequences sequences of the rotordynamic plant operating under various **speeds** and **external vibrations**)
4. Manual D-mode (50 sequences sequences of the rotordynamic plant operating under various **speeds** and **increased damping loads**)

Each sequence is a .csv file that contains the columns described below in the *Column annotation* section. Visualization of the each .csv file is generated and packed in the folders as a .png file for your convenience.

**Unique properties of this dataset and how faulty data is generated？**

Unlike traditional methods that generate faulty conditions with **time-invariant** faulty components like bearings, shaft couplings, etc, our method follows a more automated way, such that we can generate large amount of **time-varying** synthetic faults. In essence, we build an automated setup to inject different types of faulty patterns into a rotordynamic plant. The faulty patterns in this dataset include vibration (e.g., simulating different faulty bearings), abnormal lateral load, and abnormal damping torque load. They are named as 'V', 'N' and 'D' modes, respectively.

The automated setup allows us to command the severity of faults in **real-time**. Thus, in a streaming fashion, the faulty condition is actively **modulated** and **annotated**, giving users the chance to invesigate and validate time-varying fault **prediction** algorithms. (Arguably, traditional fault generation methods only grant users with out-of-the-box **diagnostic/detection** capacity.)


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

**Difference between 'manual' and 'mc-generated' data:**

Each mode has a specific faulty attribute whose trajectory is designed and executed by automated apparatus. The N-mode attribute is the amount of shear load, V-mode is the vibration frequency, and D-mode is the damping motor's resistance. 

For 'manual' data, the attributes are commanded by a human operator. For 'mc-generated' data, the attribute's trajectory is rolled out with a Markov-Chain process, and programmed into the automated apparatus.

The detail of this trajectory generation logic is described in [*RoSA:A Mechatronically Synthesized Dataset for Rotodynamic System Anomaly Detection*](https://ieeexplore.ieee.org/abstract/document/9982146), and the detail of the execution is described in [*A General-Purpose Anomalous Scenario Synthesizer for Rotary Equipment*](https://ieeexplore.ieee.org/abstract/document/9561841).

## **Contact**

The two citations of the dataset description and the apparatus are written at high levels that might be unnecessarily confusing for direct usage of this dataset. So please don't hesitate to reach out to yyeung@mit.edu for additional explanations.


## **Updates**

Update - (2/27/23):
RoSA-II's instrument is ready, and will be presented in 2022 International Conference on Robotics and Automation (ICRA 2023), stay tuned! The tentative title is *Robotic Method and Instrument to Efficiently Synthesize Faulty Conditions and Mass-Produce Faulty-Conditioned Data*.


Update - (10/31/22):
1. This dataset is presented in the 2022 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS 2022). 
2. RoSA-II with better instrumentation and more extensive scope of anomalies is planned.

Update - (7/19/22):
This dataset will be presented in the 2022 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS 2022), stay tuned!


## **Column annotation in the .csv files**

**_Vanilla Use Case_**: Without loss of generality and consider a supervised Neural-Network-based fault detection algorithm. The condition state variables should be treated as the labels, and the measurement variables should be treated as the features.


| Shared Column | Description |
| --- | --- |
| Time | DAQ Main Host time in milliseconds | 
| Rel Time | Relative time computed from 'Time'| 
| MCU Time | DAQ MCU time (Deprecated, *use 'Time' and 'Rel Time' instead***) |
| Sample Freq | Sampling frequency for per time step|

| Condition State (Label) Space Column | Description |
| --- | --- |
| N-mode? | Whether N-mode faulty synthesis is on or not|
| V-mode? | Whether V-mode faulty synthesis is on or not|
| D-mode? | Whether D-mode faulty synthesis is on or not|
| Binary Macro Health Mode | Whether plant is faulty (A) or healthy (H)|
| Multi-class Sublevel Mode | Detailed faulty mode; expands faulty(A) to V/D/N {0,1,2,3}; notice 'V' overwrites 'N'|
| Multi-class Sublevel Mode Enc | Encoded numerical values based on 'Multi-class Sublevel Mode' | 
| N-mode attribute | Lateral force reading introduced to the plant |
| V-mode attribute | Active vibration frequency introduced to the plant |
| D-mode attribute | External damper motor resistance (15ohm is regular operating condition) |
| Force Sensor Number | Which force sensor to read for N-mode and V-mode (*trivial meaning, kept for completeness*) |
| Tool Head Number | EoAT number for N-mode and V-mode (*trivial meaning, kept for completeness*) |

| Measurement (Feature) Space Column | Description | Sensor |
| --- | --- | --- |
| Desired Speed | Commanded angular velocity of the shaft | MCU internal | 
| Actual Speed | Actual angular velocity of the shaft| 12-bit Encoder installed on the plant| 
| Shaft Control Effort | Control effort to drive the shaft | MCU PWM |  
| Orient. xyz | Orientation of the shaft | IMU installed on the shaft | 
| AngVel. xyz | Angular velocity of the shaft | IMU installed on the shaft |  
| LinAcc. xyz | Linear acceleration of the shaft | IMU installed on the shaft |  
| Mag. xyz | Magnetic field around the shaft | IMU installed on the shaft |  
| Quat. xyzw | Quaternion representation of the shaft | IMU installed on the shaft|  
| Temp | Temperature around the shaft | Temperature sensor installed on the shaft|
| Audio | Audio reading around the shaft | Audio sensor installed on the shaft|
| Strain Gage| Strain reading on the surface of the shaft| Strain gage Sensor installed on the shaft|

*Note: all other columns in the .csv files are DEPRECATED or effectively substituted by the above columns.*
