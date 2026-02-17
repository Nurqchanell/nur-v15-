
# NUR v15.3-stable – The Evolving Fortress

**Byzantine Tolerant • Forward-Secure • HSM-Protected Distributed Secret Vault**

NUR is a high-security distributed secret management system that shards sensitive data (API keys, certificates, database credentials, crypto seeds, etc.) using Shamir Secret Sharing (3/5 threshold), encrypts with AES-256-GCM, protects communication with mandatory mTLS, and runs natively on Kubernetes.

### Key Features

- **Byzantine Fault Tolerance** – Secret remains secure even if 2/5 nodes are malicious (3/5 threshold + combination filtering)
- **Per-Operation Forward Secrecy** – Master key evolves after every use
- **Snapshot / VM Restore Resistance** – Jump-ahead counter prevents access to old states
- **Master Key Never in RAM** – Rust sidecar + HSM (YubiHSM, AWS CloudHSM, Thales Luna)
- **Distributed Replay Protection** – Redis Sentinel + Bloom filter
- **Guaranteed Zeroization** – Rust `zeroize` crate ensures ephemeral keys are wiped
- **Kubernetes Native** – Helm chart, StatefulSet, PodDisruptionBudget, topologySpreadConstraints
- **Observability** – Prometheus metrics + Grafana dashboards (Resilience Index)
- **Immutable Audit Logging** – PostgreSQL WORM tables

### Use Cases

- Banking & Fintech (SWIFT keys, payment tokens)
- Healthcare & Pharma (patient data, clinical trial secrets)
- Defense & Government (classified communication keys)
- Blockchain & DeFi (multi-sig wallet seeds)
- Enterprise Kubernetes secret management

### Black Box Model

- **Rust Sidecar**: Distributed as pre-compiled binary only (source code closed)
- **Python Orchestrator Client**: Open-source (limited to client library)
- **Enterprise Edition**: Full source code, SLA, support, custom tuning – commercial license required

**For licensing, pricing, demo or pilot:** [sales@nur.systems](mailto:sales@nur.systems)

### Quick Start (Community Edition)

```bash
# 1. Install with Helm
helm repo add nur https://charts.nur.systems
helm install nur nur/nur-v15 --namespace nur-system --create-namespace

# 2. Encrypt a test message
python3 -c "
from nur_client import NURClient
client = NURClient()
encrypted = client.encrypt(b'Test secret message')
print('Encryption successful')
"



# nur-v15-
NUR v15.3-stable – Byzantine Tolerant, Forward-Secure, HSM-Protected Distributed Secret Management System
# NUR v15.3-stable – The Evolving Fortress

**Byzantine Tolerant • Forward-Secure • HSM-Protected Distributed Secret Vault**

NUR, yüksek güvenlik gerektiren ortamlarda sırları (API keys, certificates, database credentials, crypto seeds vb.) **parçalara böler**, **farklı node’lara dağıtır** ve **tek bir nokta ele geçirilse bile çözülememesini** sağlar.

### Neden NUR?

- **Byzantine Toleransı** – 2 node kötü niyetli olsa bile sır çözülemez (3/5 eşik + kombinasyon filtresi)
- **Forward Secrecy** – Her işlemde anahtar evrimleşir
- **Snapshot / VM Restore Koruması** – Jump-ahead counter ile eski verilere ulaşılamaz
- **Master Key Asla RAM’de Değil** – Rust sidecar + HSM (YubiHSM, CloudHSM, Thales)
- **Distributed Replay Koruması** – Redis Sentinel ile
- **Zeroization Garantili** – Rust zeroize ile bellek temizliği

### Kullanım Alanları
- Bankacılık & Fintech (SWIFT, ödeme anahtarları)
- Sağlık & Pharma (hasta verileri, klinik sırlar)
- Savunma & Devlet kurumları
- Blockchain & DeFi (multi-sig seed’ler)
- Kurumsal Kubernetes sır yönetimi

### Teknik Özellikler
- **Shamir Secret Sharing** (3/5 eşik)
- **AES-256-GCM** (HSM destekli)
- **Rust Sidecar** (zeroization + HSM)
- **mTLS + gRPC** (zorunlu karşılıklı doğrulama)
- **Redis Sentinel** (distributed nonce cache)
- **Kubernetes Native** (Helm chart, StatefulSet, PDB)

### Black Box Modeli
- **Rust Sidecar**: Sadece ön-derlenmiş binary olarak dağıtılır (kaynak kodu kapalı)
- **Python Orchestrator**: Sınırlı açık kaynak (client library)
- **Enterprise Edition**: Tam kaynak kodu + destek + SLA için lisans gereklidir

**Demo ve Test İsteği için:** [Contact Form](#) veya sales@nur.systems

---

## Getting Started (Community Edition)

```bash
# 1. Helm ile kurulum
helm repo add nur https://charts.nur.systems
helm install nur nur/nur-v15 --namespace nur-system --create-namespace

# 2. Test mesajı şifreleme
python3 -c "
from nur_client import NURClient
client = NURClient()
encrypted = client.encrypt(b'Test secret message')
print('Şifreleme başarılı')
"
