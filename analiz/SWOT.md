# SWOT Analizi · Durmazlar VS CNC Hidrolik Giyotin Makas

> **Bakış açısı:** Makinenin Safety 4.0 olgunluğu, yani fonksiyonel emniyet + siber güvenlik birlikte. Değerlendirme, Lab 1–4 bulgularına ve yalnızca herkese açık bilgilere dayanır. **(V)** işareti, açık kaynakta doğrulanamayan varsayımlara dayanan maddeleri gösterir.

## Özet matris

| | **Yararlı** | **Zararlı** |
|---|---|---|
| **İç (makine)** | **💪 Güçlü yönler (S)**<br>• Ayrı emniyet yolu: ön + arka ışık bariyeri<br>• CNC ile otomatik ayar (insan müdahalesi azalır)<br>• Olgun, yaygın ürün ailesi; Türk üretici | **⚠️ Zayıf yönler (W)**<br>• USB ve ağ bağlantısı saldırı yüzeyi açar<br>• CNC ↔ emniyet ünitesi arasında dijital kesişim<br>• Paylaşılan servis şifresi, oturum kaydı yok (V) |
| **Dış (çevre)** | **🚀 Fırsatlar (O)**<br>• Makine Yönetmeliği 2023/1230 ve CRA ile AB pazarında fark yaratma<br>• IEC 62443 uyumlu uzak servis bir satış argümanı<br>• SBOM ve yama süreci müşteri güveni sağlar | **🔥 Tehditler (T)**<br>• Uzak servis yoluyla parametre manipülasyonu (V)<br>• Yamaların emniyet validasyonunu bozması<br>• Uyum zorunlulukları: 2026–2027 süreleri |

---

## 💪 Güçlü yönler (Strengths)

1. **Emniyet yolu fiziksel olarak ayrı tasarlanmış.** Ön ışık bariyeri parmak korumasının yerini alıyor, arka bölge de ışık bariyeriyle korunuyor. Lab 4'te gösterildiği gibi bu, *"saldırgan girse bile insan korunur"* ilkesinin temelidir.
2. **CNC ile otomatik ayar.** Arka dayama, bıçak boşluğu ve kesme açısı CNC ile ayarlanıyor. Operatörün elle ayar için tehlike bölgesine girme ihtiyacı azalıyor.
3. **Belirgin ve iyi tanımlanmış tehlike.** Tek baskın tehlike (inen bıçak) ve tek emniyet fonksiyonu olduğu için risk değerlendirmesi ve validasyon nispeten sade.
4. **Olgun ürün ailesi.** VS serisi yıllardır dünya genelinde satılıyor. Saha deneyimi, yedek parça ve servis ağı geniş.

## ⚠️ Zayıf yönler (Weaknesses)

1. **USB ve ağ bağlantısı bir saldırı yüzeyi.** D-Touch 7 CNC USB ile program alıyor. Fabrika ağı ve uzak servis bağlantısıyla (V) birlikte bu, Lab 3'teki Senaryo 1 ve 2'nin giriş kapısıdır.
2. **Dijital kesişim noktası.** CNC ile emniyet ünitesi arasındaki izin, muting ve strok sinyalleri, emniyetin dijital bağımlılığını oluşturuyor (Lab 1, Soru 7–8).
3. **Erişim yönetimi zayıf (V).** Paylaşılan servis şifresi, MFA eksikliği, oturum kaydı olmaması ve sürekli açık bağlantı (Lab 4 "Mevcut" sütunu).
4. **Açık kaynak bilgisi sınırlı.** Emniyet ünitesinin türü (emniyet rölesi mi, Safety PLC mi), PL değeri ve siber güvenlik özellikleri broşürlerde net değil. Bu, kullanıcının risk değerlendirmesini zorlaştırıyor.

## 🚀 Fırsatlar (Opportunities)

1. **Yeni AB mevzuatı bir rekabet avantajı olabilir.** Makine Yönetmeliği (AB) 2023/1230, 20 Ocak 2027'den itibaren siber müdahaleye karşı korumayı zorunlu kılıyor. Erken uyum sağlayan Türk üreticiler AB ihracatında öne geçer.
2. **Güvenli uzak servis bir hizmet modeline dönüşebilir.** Jump server + VPN + MFA + oturum kaydı ile tasarlanmış uzak servis (Lab 2 Görev B), hem güvenlik hem de ücretli bakım hizmeti olarak satılabilir.
3. **SBOM ve şeffaf yama süreci.** CRA kapsamında SBOM ve açık bildirimi müşteri güveni oluşturur, kurumsal alıcıların tedarikçi değerlendirmelerinde puan kazandırır.
4. **Safety 4.0 belgelendirmesi.** IEC 62443 ve EN ISO 13849 birlikte ele alınırsa "siber dayanıklı emniyet" etiketi bir pazarlama değeri yaratabilir.

## 🔥 Tehditler (Threats)

1. **Uzak parametre manipülasyonu (V).** Lab 3'teki kritik senaryo (skor 18): açık uzak servis + paylaşılan şifre → strok/izin sinyali değişikliği → parmak kesilmesi.
2. **Yamaların emniyeti bozması.** Kritik bir CVE yaması CNC zamanlamasını değiştirip durma süresini ve emniyet mesafesini etkileyebilir; her yama emniyet doğrulaması gerektirir (Lab 5).
3. **Mevzuat süreleri.** CRA bildirim yükümlülükleri 11 Eylül 2026'da başladı, tüm hükümler 11 Aralık 2027'de yürürlüğe giriyor. Hazırlıksız üretici için AB pazar erişimi risk altında.
4. **Sahadaki eski makineler.** Ağa sonradan bağlanan eski VS makineleri, yeni koruma önlemlerinden yoksun kalabilir.

---

## Sonuç ve öneriler

| Strateji | Öneri |
|---|---|
| **S–O** (güçlü yönle fırsatı yakala) | Ayrı emniyet yolu mimarisini belgeleyip Makine Yönetmeliği 2023/1230 uyumunun kanıtı olarak sun. |
| **W–O** (zayıflığı fırsatla gider) | Uzak servisi IEC 62443 mantığıyla yeniden tasarla (DMZ, jump server, MFA, kayıt) ve hizmet olarak paketle. |
| **S–T** (güçlü yönle tehdide karşı koy) | Emniyet ünitesine ağdan yazma yolunu tamamen kapat; uzaktan yapılan her değişiklikten sonra durma süresi testini zorunlu kıl. |
| **W–T** (zayıflık + tehdit = acil) | USB kilidi, kişisel hesaplar, SBOM ve yama-validasyon prosedürünü 2027 öncesinde devreye al. |

> ⚖️ Bu analiz bir eğitim çıktısıdır; resmî denetim, uygunluk değerlendirmesi veya belgelendirme değildir.
