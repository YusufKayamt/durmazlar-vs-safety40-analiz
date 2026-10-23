# Lab 3 · Threat & Risk + Risk Matrix

> **Çıktı:** Risk Register → Evidence Pack **EP 04 Risk Assessment**

**Kavram:** Senaryo = kim → hangi kapı → ne yapar → zincir → **fiziksel sonuç**. Skor = L × S × E (her biri 1–3). S=3 ise skor düşük olsa bile öne alınır.

**Kapılar (ipucu):** Uzak servis bağlantısı (varsayım) · paylaşılan servis şifresi · USB portu · fabrika ağı / ERP'den kesim listesi aktarımı · D-Touch 7 dokunmatik ekran — *fiziksel sonuç adayları: bıçakta el/parmak kesilmesi, baskı ayağında parmak ezilmesi, arka dayamada sıkışma.*

## Risk Register

| # | Senaryo (kim → kapı → zincir → fiziksel sonuç) | L | S | E | Skor | Öncelik |
|---|---|:-:|:-:|:-:|:-:|---|
| 1 | Uzaktan saldırgan → açık uzak servis bağlantısı + paylaşılan servis şifresi → CNC'den emniyet ünitesine giden izin sinyalini/strok ayarını değiştirir → operatör sacı hizalarken bıçak/baskı ayağı iner: parmak kesilmesi, ezilme. | 2 | 3 | 3 | **18** | Kritik |
| 2 | Bakımcı/ziyaretçi → kilitsiz USB → zararlı yazılım veya değiştirilmiş kesim programı CNC'ye → arka dayama beklenmedik hareket eder, kesim beklenmedik tetiklenir → arka bölgede ayar yapan kişi sıkışır/yaralanır. | 2 | 3 | 2 | **12** | Yüksek (S=3) |
| 3 | Ağdaki kişi → ERP'den gelen kesim listesi / ekran verisi → baskı ayağı/hidrolik durumu ekranda yanlış gösterilir → operatör makineyi duruyor sanıp bıçak hattına uzanır → parmak ezilmesi/kesilmesi. | 1 | 3 | 2 | **6** | Orta → S=3 öne alındı |

Ölçek: 🔴 Kritik 18–27 · 🟠 Yüksek 9–17 · 🟡 Orta 4–8 · ⚪ Düşük 1–3

## Sorular

### 1. En yüksek öncelikli senaryonuz hangisi? Bir cümleyle: neden bu?

Senaryo 1: açık uzak servis + paylaşılan şifre en kolay yoldur, operatör günde yüzlerce kez bıçak hattına yaklaşır (E=3) ve sonuç geri dönüşsüz parmak kaybıdır; S=3, skor 18 (Kritik).

### 2. S=3 olup skoru düşük kalan senaryonuz var mı? Nasıl görünür kılacaksınız?

Evet, Senaryo 3: skoru 6 (Orta) ama S=3. Risk Register'da "S=3 – öne alındı" etiketiyle ayrı işaretlenir, skor düşük diye kapatılmaz; ERP→CNC aktarımına doğrulama ve ekran verisine bütünlük kontrolü için sahip ve tarih atanır.

> **Altın kural:** Zincir "veri çalındı" ile bitiyorsa emniyet bulgusu değildir — bir adım daha gidin: bu, hattaki insana ne yapar?
