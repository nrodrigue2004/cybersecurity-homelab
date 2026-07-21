# Security Onion Configuration Notes

## Purpose
Security Onion is used to practice network security monitoring, investigation, and log analysis in the isolated lab.

## Monitoring design
- The sensor observes a mirrored copy of selected internal lab traffic.
- Zeek and Suricata concepts are used to examine network metadata and alerts.
- The management interface is represented publicly as <SECURITY_ONION_HOST>; real hostnames, addresses, and console URLs are not published.

## Defensive operations practice
- Review available telemetry after approved lab activity.
- Document the data source, hypothesis, time window, observations, and limitations before drawing conclusions.
- Keep event exports, PCAPs, dashboards, and raw logs private because they may contain identifiers or user activity.

## Validation
Any monitoring or detection exercise should identify its test scope, expected network evidence, observed evidence, and cleanup steps. This repository does not claim detections that have not been documented with supporting evidence.
