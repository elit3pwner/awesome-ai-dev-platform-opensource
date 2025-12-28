# Server-Side Security Vulnerability Disclosure  
## Unauthenticated Access to Grafana Metrics Endpoint

---

## Summary

The Grafana metrics endpoint at `https://grafana.aixblock.io/metrics` is publicly accessible without authentication.  
An unauthenticated user can retrieve detailed internal metrics related to the Grafana instance, application behavior, enabled features, and runtime characteristics.

This exposure may aid attackers in reconnaissance, environment fingerprinting, and targeted exploitation.

---

## Affected Asset

- **URL:** https://grafana.aixblock.io/metrics  
- **Service:** Grafana  
- **Endpoint Type:** Prometheus metrics endpoint  

---

## Vulnerability Details

The `/metrics` endpoint is exposed publicly and does not enforce any form of authentication, authorization, or network-level restriction.

Accessing the endpoint returns a comprehensive set of Prometheus-formatted metrics, including but not limited to:

- Grafana version and commit hash
- Enabled and disabled feature toggles
- Encryption operation statistics
- HTTP handler paths and response characteristics
- Process memory usage and start time
- Internal service behavior and health indicators

This information is typically intended for internal monitoring systems (e.g., Prometheus) and should not be accessible to unauthenticated external users.

---

## Proof of Exposure

A direct unauthenticated `GET` request to the endpoint returns sensitive operational metrics.  
Sample (truncated) response:

<img width="1663" height="925" alt="image" src="https://github.com/user-attachments/assets/3a8fde86-45d8-4a49-b020-036b951f12ff" />
<img width="1919" height="879" alt="image" src="https://github.com/user-attachments/assets/34d46dc2-7b7a-40a6-8e60-d4340c572bf4" />
