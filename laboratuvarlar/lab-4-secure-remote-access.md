# Lab 4 · Secure Remote Access

> **Çıktı:** Secure Architecture → Evidence Pack **EP 02 + EP 06**

**Kavram:** İki katman, ikisi de şart: **erişim güvenliği** (ara nokta, VPN, MFA, kişisel hesap, kayıt, varsayılan kapalı) + **emniyet bağımsızlığı** (girse bile insan korunur).

## Görev A — mevcut → hedef

| 🔴 Mevcut (varsayılan durum) | 🟢 Hedef (beş ilke) |
|---|---|
| • Uzak servis bağlantısı D-Touch 7 CNC'ye doğrudan açık (varsayım)<br>• Tüm servis personeli aynı servis şifresini kullanıyor<br>• Bağlantı sürekli açık; ara nokta, VPN, MFA yok<br>• Oturum kaydı yok<br>• CNC ile emniyet ünitesi arasında ortak sinyal yolu var<br>• USB portu kilitsiz, ERP'den kesim listesi doğrulamasız geliyor | 1) Ara nokta: jump server (DMZ); CNC'ye doğrudan internet erişimi kapalı.<br>2) VPN tüneli.<br>3) MFA + kişisel servis hesapları; paylaşılan şifre kaldırılır.<br>4) Tam oturum kaydı.<br>5) Varsayılan kapalı: onaylı bakım penceresinde açılır.<br>Ek: Emniyet ünitesine ağdan yol yok; USB kilitli/taramalı; ERP aktarımı tek yönlü. |

*Varsayım: üretici uzak servis bağlantısı CNC'ye doğrudan açık, servis şifresi paylaşılıyor.*

## Görev B — functional safety köprüsü

### 1. Saldırgan tüm önlemlere rağmen içeri girerse: emniyet fonksiyonu etkilenir mi? Neden?

Bağımsızlık sağlanmışsa etkilenmemeli: ışık bariyeri → emniyet ünitesi → hidrolik emniyet valfleri zinciri CNC'den ayrı ve kablolu çalışırsa saldırgan CNC'yi ele geçirse bile bıçak, bariyer kesikken inemez. Emniyet parametreleri ağdan yazılabiliyorsa etkilenir; bu açıktır.

### 2. Işık bariyeri zincirinin uzak servis yolundan etkilenmemesi için GEREKSİNİMİ yazın (çözümü değil).

GEREKSİNİM: Işık bariyeri zinciri uzak servis ve CNC yolundan fiziksel/mantıksal olarak bağımsız olmalı; uzaktan emniyet parametresi yazma, muting veya bypass olmamalı; değişiklik yalnızca yerinde, yetkili, kayıtlı yapılmalı ve sonrasında durma süresi ölçümü + bariyer testi ile doğrulanmalı; iletişim kesilirse Safe State.

> Tarafsızlık notu: Bu föy çözüm tasarlatmaz; gereksinimi tanımlatır. Tasarım kararı firmanındır.
