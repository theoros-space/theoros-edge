# theoros-edge requirements

| ID | Requirement | Verification |
|---|---|---|
| EDGE-REQ-001 | The runtime shall not allocate memory after initialisation. | Inspection, test |
| EDGE-REQ-002 | The runtime shall verify the CRC-32 and signature of a model before loading it. | Test |
| EDGE-REQ-003 | Every target shall reproduce the C reference outputs bit for bit. | Test |
| EDGE-REQ-004 | Inference shall be deterministic for identical inputs. | Test |
| EDGE-REQ-005 | A failed inference shall leave the payload in a safe state and report an error code. | Test |
| EDGE-REQ-006 | Peak RAM, latency and energy per tile shall be measured and published per target. | Test |

Status: baseline, November 2026. Changes need approval from the CTO.
