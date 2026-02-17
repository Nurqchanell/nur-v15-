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
