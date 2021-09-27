** Note: All sequence in this folder are NOT subject to any anomaly, meaning that anomaly encoding == 0, and force sensor 3 reading should be 0 throughout **
** In some sequence you will see that it is not 0, because of noise, and result in an anomaly encoding != 0. Down below I recorded all those sequence and  **
** I will upload the re-processed data when I have time. But in case you download the data before I re-process, set Force Sensor 3 to 0, and anomaly mode  **
** Encoding to 0 manually. Check the table below for more detail. **


** Short description of data sequence **

| Data Sequence  | Short Description | Further Process? |
| ------------- | ------------- |  ------------- |
| 35, 43-49, 77  | Healthy condition runtime  | Re-zero force sensor and reprocess|
| 38, 68, 69, 83| NA | Reuse id and overwrite |
| 97-100| Noisy force sensor 3 data| Re-zero force sensor and reprocess
| 89-92 | Battery went low so 1-2 time steps missed| NA|
| 80,91,92 | Recorded plant warm up process as well| NA|
| Otherwise  | Healthy condition runtime   | NA |
