# 🛡️ Durmazlar VS · Safety 4.0 Analizi

**Durmazlar (Durma) VS Serisi CNC Hidrolik Giyotin Makas** için fonksiyonel emniyet ve endüstriyel siber güvenlik analizi.
*Safety 4.0 Bootcamp (Inspecco × Kriptarium) laboratuvar föyleri · Lab 1–4*

![Makine](https://img.shields.io/badge/Makine-Durmazlar%20VS%20Giyotin%20Makas-1f8f84)
![Kapsam](https://img.shields.io/badge/Kapsam-Lab%201--4-1e2d4a)
![Standart](https://img.shields.io/badge/IEC-62443-e55b33)
![Mevzuat](https://img.shields.io/badge/AB-2023%2F1230%20%C2%B7%20CRA-b8291f)

---

## 📌 Proje hakkında

Bu çalışmada seçilen makine, yeni AB düzenlemelerinin ortak sorusu üzerinden incelenir:

> **"Bir saldırgan makinenin dijital tarafına girerse, makinenin başındaki insana ne olur?"**

- **Makine Yönetmeliği (AB) 2023/1230:** 20 Ocak 2027'den itibaren siber müdahalenin emniyet fonksiyonunu bozmasına karşı koruma ister.
- **Siber Dayanıklılık Yasası (CRA) (AB) 2024/2847:** dijital bileşenli ürünlere siber güvenlik, SBOM ve olay bildirimi yükümlülükleri getirir.

Analiz yalnızca **herkese açık bilgilere** dayanır; firmayla iletişime geçilmemiştir. Doğrulanamayan noktalar *(varsayım)* olarak işaretlidir.

## ⚙️ Makine özeti

| Özellik | Değer |
|---|---|
| Makine | Durmazlar VS Serisi CNC Hidrolik Giyotin Makas (örnek model: VS 3016) |
| Kapasite | 3080 mm kesme boyu × 16 mm sac kalınlığı |
| Kontrol | Durma D-Touch 7 dokunmatik CNC |
| CNC eksenleri | Arka dayama, bıçak boşluğu, kesme açısı |
| Emniyet | Ön ışık bariyeri (parmak koruması yerine), arka ışık bariyeri, acil stop |
| Baskın tehlike | İnen bıçak ve hidrolik baskı ayakları: el/parmak kesilmesi ve ezilmesi |

## 🗂️ Repo yapısı

```
durmazlar-vs-safety40-analiz/
├── README.md                          ← bu dosya
├── KAYNAKLAR.md                       ← kaynaklar, varsayımlar, mevzuat
├── analiz/
│   └── SWOT.md                        ← SWOT analizi
├── laboratuvarlar/
│   ├── lab-1-safety-architecture.md   ← emniyet fonksiyonu haritası
│   ├── lab-2-iec62443-zone-conduit.md ← bölge / geçiş diyagramı
│   ├── lab-3-threat-risk-matrix.md    ← risk kaydı (L × S × E)
│   └── lab-4-secure-remote-access.md  ← güvenli uzak erişim mimarisi
└── pdf/
    └── Durmazlar_VS_Lab1-4_Doldurulmus.pdf  ← doldurulmuş föyler (baskıya hazır)
```

## 🧪 Laboratuvarlar

| Lab | Konu | Çıktı | Öne çıkan bulgu |
|:-:|---|---|---|
| [1](laboratuvarlar/lab-1-safety-architecture.md) | Safety Architecture | Safety Function Map | Işık bariyeri → emniyet ünitesi → hidrolik emniyet valfleri zinciri; CNC ile dijital kesişim noktası |
| [2](laboratuvarlar/lab-2-iec62443-zone-conduit.md) | IEC 62443 Mini Workshop | Zone / Conduit Diagram | 4 bölge; uzak servis DMZ'ye taşınmalı, emniyet bölgesine yazma yolu olmamalı |
| [3](laboratuvarlar/lab-3-threat-risk-matrix.md) | Threat & Risk + Risk Matrix | Risk Register | En kritik senaryo: açık uzak servis + paylaşılan şifre → parmak kesilmesi (skor 18) |
| [4](laboratuvarlar/lab-4-secure-remote-access.md) | Secure Remote Access | Secure Architecture | Beş ilke (jump server, VPN, MFA, kayıt, varsayılan kapalı) + emniyet bağımsızlığı gereksinimi |

📄 Baskıya hazır sürüm: [`pdf/Durmazlar_VS_Lab1-4_Doldurulmus.pdf`](pdf/Durmazlar_VS_Lab1-4_Doldurulmus.pdf)

## 📊 SWOT analizi

Makinenin Safety 4.0 olgunluğu güçlü yönler, zayıf yönler, fırsatlar ve tehditler açısından [`analiz/SWOT.md`](analiz/SWOT.md) dosyasında değerlendirilmiştir.

| 💪 Güçlü | ⚠️ Zayıf | 🚀 Fırsat | 🔥 Tehdit |
|---|---|---|---|
| Ayrı emniyet yolu, CNC ile otomatik ayar | USB/ağ saldırı yüzeyi, dijital kesişim | AB mevzuatına erken uyumla rekabet avantajı | Uzak parametre manipülasyonu, yamaların emniyeti bozması |

## 📚 Kaynaklar

Kaynak listesi, varsayımlar ve ilgili standartlar için: [`KAYNAKLAR.md`](KAYNAKLAR.md)

---

> ⚖️ **Not:** Bu çalışma bir eğitim çıktısıdır; resmî denetim, uygunluk değerlendirmesi veya belgelendirme değildir ve CE/mevzuat uygunluğu garantisi vermez.
