| Tag              | Signal Type | Description                      | PLC Direction |
| ---------------- | ----------- | -------------------------------- | ------------- |
| LT-101           | AI          | Service water tank level, 0–100% | Input         |
| P-101A_RunFB     | DI          | Pump A running feedback          | Input         |
| P-101A_Fault     | DI          | Pump A fault/trip feedback       | Input         |
| P-101B_RunFB     | DI          | Pump B running feedback          | Input         |
| P-101B_Fault     | DI          | Pump B fault/trip feedback       | Input         |
| XV-101A_OpenFB   | DI          | Pump A valve open feedback       | Input         |
| XV-101A_ClosedFB | DI          | Pump A valve closed feedback     | Input         |
| XV-101B_OpenFB   | DI          | Pump B valve open feedback       | Input         |
| XV-101B_ClosedFB | DI          | Pump B valve closed feedback     | Input         |
| PT-101           | AI          | Discharge pressure               | Input         |
| LSHH-101         | DI          | Tank high-high level switch      | Input         |
| LSLL-101         | DI          | Tank low-low level switch        | Input         |
| P-101A_Start     | DO          | Start Pump A                     | Output        |
| P-101B_Start     | DO          | Start Pump B                     | Output        |
| XV-101A_Open     | DO          | Open Pump A valve                | Output        |
| XV-101A_Close    | DO          | Close Pump A valve               | Output        |
| XV-101B_Open     | DO          | Open Pump B valve                | Output        |
| XV-101B_Close    | DO          | Close Pump B valve               | Output        |

DI = Digital Input
DO = Digital Output
AI = Analog Input
AO = Analog Output
