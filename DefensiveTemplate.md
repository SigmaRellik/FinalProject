# Blue Team: Summary of Operations

## Table of Contents
- Network Topology
- Description of Targets
- Monitoring the Targets
- Patterns of Traffic & Behavior
- Suggestions for Going Further

### Network Topology
_TODO: Fill out the information below._

The following machines were identified on the network:
- Name of VM 1: `Target1`
  - **Operating System**: `Linux OS`
  - **Purpose**: `General Purpose`
  - **IP Address**: `192.168.110`
- Name of VM 2: `Target2`
  - **Operating System**: `Linux OS`
  - **Purpose**: `General Purpose`
  - **IP Address**: `192.168.1.115`
- Etc.

### Description of Targets
_Answer the questions below._

The target of this attack was: `Target 1` (192.168.110).

Target 1 is an Apache web server and has SSH enabled, so ports 80 and 22 are possible ports of entry for attackers. As such, the following alerts have been implemented:

### Monitoring the Targets

Traffic to these services should be carefully monitored. To this end, we have implemented the alerts below:

#### Name of Alert 1
`Excessive HTTP Errors`

Alert 1 is implemented as follows:
- **Metric**: `WHEN count() GROUPED OVER top 5 'http.response.status_code' IS ABOVE 400 FOR THE LAST 5 minutes`
  - **Threshold**: `Above 400 for the last 5 minutes`
  - **Vulnerability Mitigated**: `It can flag a DoS attack due to the excessive requests`
  - **Reliability**: `Rated medium reliability due to false positive. Reason user error creating these alerts`

#### Name of Alert 2
`HTTP Request Size Monitor`

Alert 2 is implemented as follows:
- **Metric**: `WHEN sum() of http.request.bytes OVER all documents IS ABOVE 3500 FOR THE LAST 1 minute`
  - **Threshold**: `Above 3500 for the last minute`
  - **Vulnerability Mitigated**: `It can flag XSS (cross-site scripting) attacks`
  - **Reliability**: `Rated high reliability due to being able to block large payload requests`

#### Name of Alert 3
Alert 3 is implemented as follows:
  - **Metric**: `WHEN max() OF system.process.cpu.total.pct OVER all documents IS ABOVE 0.5 FOR THE LAST 5 minutes`
  - **Threshold**: `Above 0.5 for the last 5 minutes`
  - **Vulnerability Mitigated**: `It can alert for any malicious script running in the system that potentially affecting performance`
  - **Reliability**: `Rated a low reliability due to the low threshold. Increase the threshold for the reliability to increase`



