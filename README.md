# Project Crimson Beacon - Wireshark Network Traffic Analysis

## Overview
An entry-level defensive security investigation focused on analyzing unencrypted HTTP traffic, tracking DNS resolutions, inspecting session streams, and extracting network artifacts using Wireshark.

## Objectives
- Capture live interface traffic and isolate HTTP/DNS protocols using display filters.
- Reconstruct network sessions to identify suspicious request headers (User-Agents).
- Correlate HTTP connections with their preceding DNS query/response cycles.
- Extract transmitted payload objects directly from raw PCAPs.

## Investigation Findings & IOCs (Indicators of Compromise)

Indicator / Field | Discovered Value | Analysis & Significance |
 **Source IP** | `172.32.251.22` | Internal host initiating outbound request 
 **Destination Domain** | `httpbin.org` | Target host queried during analysis 
 **Destination IP** | `98.88.64.13` | External web server IP resolved via DNS 
 **DNS Transaction ID** | `0x8b2d` | Query matching host resolution to `8.8.8.8` 
 **User-Agent** | `curl/8.13.0` | Command-line HTTP request (non-browser execution) 
 **Extracted File** | `ip` (`application/json`) | Payload retrieved containing client origin IP 

## Key Learnings & Skills Demonstrated
1. **Filter Application:** Used `http` and `dns` display filters to isolate specific protocol flows out of multi-thousand packet captures.
2. **TCP Stream Inspection:** Analyzed raw HTTP request/response headers to detect non-standard User-Agent strings.
3. **Artifact Extraction:** Utilized Wireshark's **Export Objects -> HTTP** tool to reconstruct and isolate downloaded files from network streams.

## Tools Used
- **Wireshark** (Packet Capture & Protocol Analyzer)
- **Windows Command Prompt (`curl`)** (Traffic Generation)
