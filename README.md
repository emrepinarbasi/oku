# OKU

Mac ve Windows için yerel PDF okuma, sayfa düzenleme ve basılı Osmanlıca OCR denemesi.

**Sürüm: 0.3.0 — ön sürüm.** macOS sürümü Apple Silicon üzerinde çalıştırıldı. Windows x64 kurulum paketi üretildi; gerçek Windows 10/11 masaüstünde kurulum, açılış ve kullanım testi henüz yapılmadı. Windows uyumluluğu doğrulanmış bir kararlı sürüm olarak yayımlamayın.

## İndirilecek dosyalar

GitHub **Releases** bölümüne şu dosyaları ekleyin:

- `OKU-0.3.0-macOS-AppleSilicon.dmg`
- `OKU-0.3.0-Windows-10-11-x64-Setup.exe`
- `OKU-0.3.0-Kaynak.zip`
- `SHA256SUMS.txt`
- `THIRD_PARTY_LICENSES.txt` (kurulum dosyalarıyla birlikte dağıtın)

Büyük kurulum dosyaları normal Git deposuna yüklenmemelidir. Kaynak kod bu dizindedir; `.gitignore` derlenmiş uygulamaları ve çalışma ortamlarını dışarıda tutar. Hazırlanan dosyalar henüz GitHub'a yüklenmedi.

## Neler yapar?

- PDF okuma, metin arama, yakınlaştırma ve küçük resimlerle sayfa gezinme.
- Birleştirme, döndürme, bölme/çıkarma, silme ve sayfa sırası değiştirme.
- Türkçe OCR ve basılı Osmanlıca için Kraken / OpenITI model seçenekleri.
- OCR satırlarını düzeltme ve aranabilir PDF kopyası oluşturma.
- Kitap taramalarını ayırma, kenar kırpma, eğiklik düzeltme ve basılı sayfa eşlemesi.
- Klasörde arama, toplu işlem reçeteleri ve belge karşılaştırma.
- Vurgu/not derleme ve düzenlenebilir çalışma özeti taslağı.
- Küçük mavi logo, siyah-beyaz üç boyutlu menü simgeleri ve açılır/kapanır paneller.

Özelliklerin platforma göre kapsamı [özellik tablosunda](docs/FEATURES.md) açıklanır. Office biçimlerine dönüşüm, sertifikalı dijital imza, doğrulanmış PDF/A/PDF/X ve kapsamlı paragraf düzenleme bu sürümde yoktur.

## Kurulum

**Apple Silicon:** DMG'yi açın, OKU'yu Applications / Uygulamalar klasörüne sürükleyin. macOS 14+ için derlenmiştir; bu teslimde macOS 27.0.1 üzerinde denendi. Türkçe Vision OCR dil desteği işletim sistemi sürümüne bağlıdır. Intel paketi değildir.

**Windows:** x64 Windows 10 22H2 (19045+) ve Windows 11 hedeflenir. Kurulum EXE'si yönetici izni ister; uygulamayı, Microsoft Visual C++ bileşenini ve kaldırma programını kurar. PDF'yi **Birlikte Aç → OKU** ile açabilirsiniz. Varsayılan uygulama seçimi Windows ayarlarından kullanıcı tarafından yapılır. 32 bit ve ARM64 yerel paket sunulmuyor.

Python, Node veya Homebrew son kullanıcı kurulumu gerekmez. OCR modelleri paketin içindedir. Kurulum dosyaları **Apple noter onaylı / Authenticode imzalı değildir**; işletim sistemi yayıncı uyarısı gösterebilir.

Ayrıntılar: [Kurulum](docs/INSTALLATION.md), [derleme](docs/BUILD.md), [test durumu](docs/TEST_STATUS.md).

## Osmanlıca OCR

Osmanlıca tanıma genel Arapça Apple modeline dayanmaz. Osmanlıca verisi içeren `Kraken PP-OCRv6 medium` ve `OpenITI apt-20221130` modelleri kullanılır. Öncelik basılı kitap, dergi ve gazetelerdir; el yazısı doğruluğu doğrulanmadı. Modeller yeni baştan eğitilmedi, yayımlanmış modeller entegre edildi.

OCR sonucu hatasız metin değildir. Referans iki sayfa eğitim kaynaklarıyla örtüşebilir; bağımsız arşiv başarısı sayılmaz. Metin tanıma, Latin harflerine aktarım ve günümüz Türkçesine çeviri ayrı işlemlerdir; son ikisi bu sürümde yoktur.

[Araştırma ve sınırlamalar](docs/OSMANLICA-ARASTIRMA.txt).

## Gizlilik ve dosyalar

Belgeler yerel işlenir. Bulut hesabı veya belge yükleme hizmeti yoktur. OCR sırasında geçici dosyalar oluşturulur ve işlem sonunda silinir. Yeni PDF'ler kopya olarak kaydedilir. Küçültme, OCR uygulama ve bazı kitap işlemleri sayfaları görüntüye dönüştürebilir; formlar, bağlantılar ve işaretlemeler korunmayabilir. Kırpma kalıcı karartma değildir.

## Kaynak yapısı

```text
macos/          SwiftUI / AppKit / PDFKit / Vision uygulaması
windows/        Electron / PDF.js / pdf-lib / Tesseract.js uygulaması
scripts/        Mac DMG ve doğrulama yardımcıları
.github/        macOS ve Windows derleme iş akışları
third_party/    LGPL kitaplığının özgün kaynak dağıtımı
docs/           Kurulum, özellikler, test ve release belgeleri
```

Orijinal OKU kodu MIT lisanslıdır. Paketlenen bileşenler kendi lisanslarına tabidir; [bileşen bildirimlerini](THIRD_PARTY_NOTICES.md) okuyun.

## Ekran görüntüleri

![macOS](docs/macos-arayuz.png)

![Windows için ortak arayüz; görüntü bu Mac'teki Electron denemesinden](docs/windows-arayuz.png)

## Katkı ve hata bildirimi

[CONTRIBUTING.md](CONTRIBUTING.md) ve [SECURITY.md](SECURITY.md). Hata bildirirken kişisel veya telifli belgeleri izinsiz eklemeyin; sorun çıkaran küçük, anonimleştirilmiş örnek tercih edin.
