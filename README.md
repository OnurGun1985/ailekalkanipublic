# Aile Kalkanı

**Aile Kalkanı**, ebeveynlerin veya yasal vasilerin **18 yaşından küçük** bir çocuğun iPhone veya iPad’inde kullanımı denetlemesine yardımcı olan bir iOS uygulamasıdır. Uygulama **Türkçe** birincil dildir; **İngilizce** yerelleştirme de vardır.

> **Önemli:** Bu uygulama gizli izleme yazılımı değildir. Çocuğun cihazında, ebeveynin bilgisi ve izinleriyle kullanılmak üzere tasarlanmıştır. Yerel yasalara uyun.

---

## Ne yapar?

| Özellik | Açıklama |
|---------|----------|
| **Ebeveyn parolası** | 6–12 karakter; yalnızca tuzlanmış özet Anahtarlık’ta saklanır. Arka plandan dönünce yeniden sorulur. |
| **Uygulamalar** | Ekran Süresi izniyle kategori bazlı kullanım özeti ve uygulama listesi (seçilen dönem: 7–90 gün). |
| **Siteler** | Web kullanımı kategori ve site listesi (Safari geçmişi değil; Ekran Süresi verisi, gecikmeli olabilir). |
| **Kısıtlamalar** | Apple’ın seçicisiyle uygulama seçimi; seçilen uygulamalar adlarıyla listelenir; süreli engel. |
| **Bağlantılar** | Mobil veriyi kapatma için **Ayarlar** yönlendirmesi; isteğe bağlı süreli **Ayarlar ekranı kilidi** (mobil veriyi kapatmaz). Wi‑Fi üçüncü taraf uygulamalarla kapatılamaz. |
| **Ayarlar** | Feragatname, uygulama hakkında, parola değiştirme, destek ve sürüm bilgisi. |

Uzantılar: **Device Activity Report** (grafik/liste), **Monitor** (süre bitince engel/kilit kaldırma).

---

## Ne yapmaz?

- Mobil veriyi veya Wi‑Fi’yi tamamen kapatmaz (iOS buna izin vermez).  
- Yüklü tüm uygulamaların listesini göstermez (yalnızca Apple’ın seçicisindekiler).  
- Kullanım verisini geliştirici sunucusuna göndermez (bu sürüm).  
- Telefon, Mesajlar, Ayarlar gibi birçok sistem uygulamasını engelleyemez.

---

## Gizlilik özeti

| Veri | Nerede | Paylaşım |
|------|--------|----------|
| Ebeveyn parolası | Anahtarlık (hash) | Cihazda kalır |
| Zamanlama / engel kayıtları | App Group (`UserDefaults`) | Cihazda kalır |
| Ekran Süresi özetleri | Apple API’leri, cihazda işlenir | Bu uygulama sunucuya yüklemez |
| İzleme (tracking) | Yok | `NSPrivacyTracking: false` |

**Tam metin:** uygulama içi **Önemli bilgilendirme** ve aşağıdaki gizlilik politikası bağlantısı.

### Gizlilik politikası

Yayın öncesi gerçek bir HTTPS sayfası yayınlayın ve şu dosyada aynı adresi kullanın:

- Kod: `AileKalkani/AppLegalInfo.swift` → `privacyPolicyURLString`  
- App Store Connect → **Gizlilik Politikası URL’si**

**Şablon / taslak adres (değiştirin):**  
`https://example.com/aile-kalkani/gizlilik`

Politikada en az şunlar yer almalıdır: hangi verilerin işlendiği, cihazda saklama, sunucu olmaması, Ekran Süresi’nin Apple tarafından işlenmesi, ebeveyn/çocuk rolü, iletişim.

---

## Destek

| | |
|---|---|
| **E-posta** | `destek@example.com` — yayın öncesi `AppLegalInfo.swift` içinde güncelleyin |
| **Uygulama içi** | Ayarlar → Uygulama hakkında → Destek |

App Store Connect’teki **Destek URL’si** bu kanalla tutarlı olmalıdır.

---

## Lisans ve telif

- **Aile Kalkanı** telif hakkı ile korunur; kullanım App Store lisans koşulları ve uygulama içi feragatname ile sınırlıdır.  
- Kaynak kodu bu depoda özel mülkiyettir; izinsiz kopyalama veya dağıtım yasaktır (açık kaynak lisansı eklenmedikçe).  
- Apple, iPhone, iPad, iOS, Ekran Süresi ve ilgili adlar **Apple Inc.** ticari markalarıdır.

Uygulama “olduğu gibi” sunulur; belirli bir sonuç garanti edilmez. Hukuki sorular için yerel uzmana danışın.

---

## Geliştirme

### Gereksinimler

- macOS, Xcode  
- [XcodeGen](https://github.com/yonaskolb/XcodeGen)  
- Ücretli Apple Developer hesabı (Aile Denetimleri testi için)

### Derleme

```bash
xcodegen generate
open AileKalkani.xcodeproj
```

Simülatörde Aile Denetimleri ve web raporları sınırlıdır; **gerçek cihaz** önerilir.

### Proje yapısı (kısa)

- `AileKalkani/` — ana uygulama (SwiftUI)  
- `ReportExtension/` — kullanım raporu uzantısı  
- `MonitorExtension/` — zamanlama sonu  
- `Shared/` — ortak depolar ve sabitler  
- `project.yml` — XcodeGen tanımı  
- `AppStore/AppStoreConnect.md` — mağaza metinleri (TR/EN)  
- `DEPLOY.md` — App Store dağıtım rehberi (Türkçe)

---

## App Store dağıtımı

Ayrıntılı adımlar: **[DEPLOY.md](DEPLOY.md)**  
Mağaza metinleri ve anahtar kelimeler: **[AppStore/AppStoreConnect.md](AppStore/AppStoreConnect.md)**

Family Controls **dağıtım onayı:**  
https://developer.apple.com/contact/request/family-controls-distribution

---

## Sürüm

`MARKETING_VERSION` / build: `project.yml` (ör. 1.0 / 1). Uygulama içi sürüm: **Ayarlar** alt bilgisi veya **Uygulama hakkında**.
