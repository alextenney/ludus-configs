# Splunk-Mythic Attack Range

A range built so I can deploy C2 payloads and determine the logs a defender might see from the actions. 

## Machines

| Host    | IP        | VLAN |
| ------- | --------- | ---- |
| Splunk  | 10.2.20.1 | 20   |
| Windows | 10.2.20.3 | 20   |
| Linux   | 10.2.20.2 | 20   |
| Kali    | 10.2.99.1 | 99   |
| Mythic  | 10.2.99.2 | 99   |

## Network Rules

| Source  | Destination | Purpose         |
| ------- | ----------- | --------------- |
| Kali    | Mythic      | bi-directional  |
| Windows | Mythic      | bi-directional  |
| Linux   | Mythic      | bi-directional  |
| Linux   | Splunk      | uni-directional |
| Windows | Splunk      | uni-directional |

```mermaid
graph TD
  Kali[10.2.99.1<br>Kali]
  Mythic[10.2.99.2<br>Mythic]
  Windows[10.2.20.3<br>Windows]
  Linux[10.2.20.2<br>Linux]
  Splunk[10.2.20.1<br>Splunk]

  Kali <--> Mythic
  Windows <--> Mythic
  Linux <--> Mythic
  Linux --> Splunk
  Windows --> Splunk
```

