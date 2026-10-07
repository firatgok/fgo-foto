# FGO Foto · Fırat Gök Ortodonti

CR3 fotoğraflarını tarayıcıda tam çözünürlüklü JPEG’e dönüştüren web uygulaması.

**Web:** https://firatgok.github.io/fgo-foto/

- CR3 dosyalarını veya klasörleri sürükleyip bırakın.
- JPEG kalitesini seçin; varsayılan 95.
- Fotoğraflar kendi cihazınızda LibRaw WebAssembly ile işlenir. Sunucuya fotoğraf yüklenmez.
- JPEG’leri tek tek veya ZIP olarak indirin.
- Destekleyen tarayıcılarda Belgeler’i seçerek içindeki `fgo foto` klasörüne kaydedin. Mevcut dosyalar numaralandırılarak korunur.
- Dönüştürmeyi durdurabilir, tamamlanan sonuçları indirebilirsiniz.

Güncel masaüstü Chrome/Edge önerilir. HTTPS veya localhost gerekir. İlk ziyarette dönüşüm motorunu etkinleştirmek için sayfa bir kez yenilenebilir. Büyük RAW fotoğraflarında yeterli RAM gerekir; dosya başına sınır 200 MB. Kamera desteği LibRaw sürümüne bağlıdır. JPEG kayıplıdır, RAW metadata/EXIF/GPS aktarılmaz; kamera içi JPEG ile renklerin tamamen aynı olması beklenmez. Sayfa kapatıldığında indirilmemiş sonuçlar saklanmaz.

## Geliştirme

Node.js 22.12+ ile:

```sh
npm ci
npm run dev
npm test
npm run build
```

Üretim çıktısı `dist/` klasöründedir. `coi-serviceworker.js`, LibRaw dosyaları ve lisanslar aynı alan adından sunulmalıdır; GitHub proje alt yolu desteklenir.

## GitHub üzerinden dağıtım

Tarayıcı ile yapılan ilk yüklemede kaynaklar `fgo-foto-source.zip` içindedir. Arşivi açarak tüm düzenlenebilir HTML/CSS/JS dosyalarına, bağımlılık kilidine ve testlere ulaşabilirsiniz. GitHub Actions kaynak arşivini açar, test eder, derler ve Pages’e yayımlar. Güncelleme için düzenlenen kaynak arşivini aynı dosya adıyla yükleyin. İsterseniz arşiv içeriğini depoya açıp standart Git iş akışına geçebilirsiniz.

Repo ayarı: Settings → Pages → Source: **GitHub Actions**.

Yalnız uygulama kaynakları ve marka görselleri bu depoya yüklenir. Fotoğraflar, örnek CR3 dosyaları, masaüstü EXE’ler ve yerel çalışma ortamları dahil değildir.

## Bileşenler

LibRaw-Wasm 1.6.0 / LibRaw 0.22.1, coi-serviceworker ve fflate kullanılır. Kaynak sürümleri ve lisans bildirimleri `web/public/third-party.html` ve `web/public/licenses/` içindedir.
