# 4.09.4 Evaluate Network Baseline

## Task

Evaluate and establish a baseline of normal network activity to identify anomalies and suspicious behavior during an incident response.

---

## Conditions

Given a deployed Security Onion instance, access to network traffic (via full packet capture and/or NetFlow), and knowledge of the target environment or mission network layout.

---

## Standards

* Collect representative data of normal network behavior.
* Document "normal" hosts, ports, protocols, services, and traffic patterns.
* Identify deviations or anomalies that may indicate lateral movement, beaconing, or command and control (C2) activity.
* Validate findings against known network diagrams, asset inventories, or mission briefs.

---

## End State

A documented network baseline is created, providing a reference point for detecting abnormal activity and informing containment and eradication efforts.

---

## Notes

- Baselines should be dynamic → update as more is learned during an engagement.
- Expect some "gray" traffic → not everything unknown is immediately malicious, but all anomalies must be explained or investigated.
- Capturing a good baseline early allows faster anomaly detection later.

---

## Manual Steps

### Step 1: Review Available Network Telemetry

Use Security Onion to determine what data sources you have:

- Zeek logs (connection logs, DNS logs, SSL/TLS metadata)
- Suricata/Snort alerts
- Full PCAP (via Stenographer/SO)
- NetFlow (if configured)

Verify data sources:

```bash
sudo so-status
```

Check that Zeek and Stenographer services are running.

---

### Step 2: Capture Representative Network Traffic

Use `tcpdump` to capture live traffic for review:

```bash
sudo tcpdump -i <interface> -w /nsm/baseline/baseline.pcap
```

Example:

```bash
sudo tcpdump -i eth0 -w /nsm/baseline/initial_baseline.pcap
```

> **Operator Note:** Try to capture multiple times of day if feasible → work hours vs after hours.

---

### Step 3: Analyze Network Traffic

Use the following tools:

#### Kibana (Security Onion Interface)

- Search Zeek logs:
  - `conn.log` → review top talkers, top protocols.
  - `dns.log` → identify DNS usage patterns.
  - `ssl.log` → identify common TLS communication.

Example search for top destinations:

```
_source:"conn.log" AND event_type:connection_summary
```

#### Wireshark (Local Analysis)

- Download `baseline.pcap` to local analyst laptop.
- Open in Wireshark.
- Use the following filters:

```text
ip.addr == <critical_server_IP>
```

```text
tcp.port == 3389
```

```text
dns
```

- Identify:
  - Frequent communications
  - Long-lived sessions
  - Unexpected external connections
  - High data volume transfers

---

### Step 4: Establish the Baseline

Document:

- Critical internal systems and normal communication partners
- Normal external IPs/domains contacted
- Common protocols used (HTTP, HTTPS, RDP, SMB, etc.)
- Expected port usage
- Typical volume and size of traffic flows

Sample format:

| Host/IP | Normal Communications | Protocols | Comments |
|---------|------------------------|-----------|----------|
| 192.168.1.10 | 192.168.1.1 (Gateway), DNS Server, File Server | DNS, SMB | Normal AD traffic |
| 192.168.1.15 | External vendor IP | HTTPS | Monitored VPN connection |

---

### Step 5: Identify Anomalies

Look for:

- Hosts communicating externally with rare IPs/domains
- Beacon-like traffic (small, regular packet sizes)
- Use of unusual ports (ex: high ports, custom C2 protocols)
- Lateral movement indicators (RDP, SMB, WMI across hosts)
- Large volume data exfiltration (big POSTs, downloads)

Tag all findings for further investigation.

---

### Step 6: Validate Findings with Asset Owners

If possible:

- Confirm known/unknown hosts with system owners or network administrators.
- Update baseline document with clarifications.

> **Operator Note:** Network diagrams are often incomplete or outdated — direct confirmation is better.

---

## Dependencies

* Working Security Onion deployment.
* Access to Zeek logs, full packet capture (PCAP), and Kibana.
* TCPDump/Wireshark.
* Analyst-level access to SO or network taps.

---

## Other Available Tools

| Tool | Platform | Installation | Usage |
|------|----------|--------------|-------|
| Zeek | Security Onion | Built-in | Deep network metadata parsing |
| Suricata/Snort | Security Onion | Built-in | IDS alerts |
| Wireshark | Cross-platform | Package manager | PCAP analysis |
| tcpdump | Linux | Built-in | Raw packet capture |

---

## Operator Recommendations and Additional Tools

### Operator Checklist

- [ ] Confirm all network sensors are operational (Zeek, Suricata, Stenographer).
- [ ] Capture baseline traffic via tcpdump and Zeek logs.
- [ ] Document normal hosts, services, ports, and protocols.
- [ ] Identify and tag suspicious behaviors or anomalies.
- [ ] Validate suspicious entries with asset owners or IR team leads.

### Best Practices

- Capture baselines during multiple shifts if possible.
- Update baseline throughout mission lifecycle as new information becomes available.
- Be cautious of "quiet C2" — beaconing may be subtle and blend in with normal traffic.
- Preserve original PCAP captures → forensic review later may be necessary.

---

## References

- [Zeek Documentation](https://docs.zeek.org/en/current/)
- [Wireshark Display Filter Reference](https://wiki.wireshark.org/DisplayFilters)
- [Security Onion Docs](https://docs.securityonion.net/en/latest/)

---

## Revision History

| Date | Version | Description | Author |
|------|---------|-------------|--------|
| 2025-05-02 | 1.0 | Created from scratch with deep operator guidance and procedural context | Leo |
