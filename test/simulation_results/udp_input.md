# udp_input
## Test: 0
| Time         | udp_input State   | udp_output State   | Output Model   | Output Port   | Value                     |
|--------------|-------------------|--------------------|----------------|---------------|---------------------------|
| 00:00:00:000 | INPUT-NO_MESSAGES | IDLE               |                |               |                           |
| 00:00:05:000 | INPUT-NO_MESSAGES | SENDING            | ir_message     | out           | 0 45.3833 -75.6976 100 45 |
| 00:00:05:020 | INPUT-NO_MESSAGES | IDLE               |                |               |                           |
| 00:00:05:100 | INPUT-MESSAGES    | IDLE               |                |               |                           |
| 00:00:05:120 | INPUT-NO_MESSAGES | IDLE               | udp_input      | o_message     | 0 45.3833 -75.6976 100 45 |
| 00:00:05:220 | INPUT-NO_MESSAGES | IDLE               |                |               |                           |
| 00:00:15:000 | INPUT-NO_MESSAGES | SENDING            | ir_message     | out           | 1 46.3833 -76.6976 200 46 |
| 00:00:15:020 | INPUT-MESSAGES    | IDLE               |                |               |                           |
| 00:00:15:040 | INPUT-NO_MESSAGES | IDLE               | udp_input      | o_message     | 1 46.3833 -76.6976 200 46 |
| 00:00:15:140 | INPUT-NO_MESSAGES | IDLE               |                |               |                           |
| 00:00:20:000 | IDLE-NO_MESSAGES  | IDLE               | ir_quit        | out           | 1                         |

