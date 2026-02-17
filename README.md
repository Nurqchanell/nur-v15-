 # NUR v15.3-stable – The Evolving Fortress

**Byzantine Tolerant • Forward-Secure • HSM-Protected Distributed Secret Vault**

NUR is a high-security, distributed secret management system designed for environments where compromise is not an option.

It shards sensitive data (API keys, certificates, database credentials, crypto seeds, patient records, classified codes) using **Shamir Secret Sharing (3/5 threshold)**, encrypts with **AES-256-GCM** (HSM-backed), protects communication with **mandatory mTLS**, and runs natively on Kubernetes.

### Key Features

- **Byzantine Fault Tolerance** – Secret remains secure even if 2/5 nodes are malicious  
- **Per-Operation Forward Secrecy** – Master key evolves after every use  
- **Snapshot / VM Restore Resistance** – Jump-ahead counter prevents access to old states  
- **Master Key Never in RAM** – Rust sidecar + HSM integration (YubiHSM, AWS CloudHSM, Thales Luna)  
- **Distributed Replay Protection** – Redis Sentinel + Bloom filter  
- **Guaranteed Zeroization** – Rust `zeroize` crate wipes ephemeral keys from memory  
- **Kubernetes Native** – Helm chart, StatefulSet, PodDisruptionBudget, topologySpreadConstraints  
- **Observability** – Prometheus metrics + Grafana dashboards (Resilience Index)  
- **Immutable Audit Logging** – PostgreSQL WORM tables  

### Use Cases

- Banking & Fintech (SWIFT keys, payment tokens, HSM offload)  
- Healthcare & Pharma (PHI, clinical trial secrets, medical device keys)  
- Defense & Government (classified communication keys, satellite/uav command codes)  
- Enterprise Kubernetes secret management at scale  
- Blockchain & DeFi (multi-sig wallet seeds, oracle keys)  

### Black Box Enterprise Model

- **Rust Sidecar** — Distributed as pre-compiled binary only (source code closed)  
- **Python Orchestrator Client** — Open-source (limited to client library)  
- **Enterprise Edition** — Full source code, SLA, priority support, custom tuning – commercial license required  

**For licensing, pricing, demo or pilot inquiries:** [sales@nur.systems](mailto:NeutralPoint1@proton.me)

### Quick Start (Community Edition)

```bash
# 1. Add Helm repo and install
helm repo add nur https://charts.nur.systems
helm install nur nur/nur-v15 --namespace nur-system --create-namespace

# 2. Encrypt a test message (using Python client)
python3 -c "
from nur_client import NURClient
client = NURClient()
encrypted = client.encrypt(b'Test secret message')
print('Encryption successful')
"
