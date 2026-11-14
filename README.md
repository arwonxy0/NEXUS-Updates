# NEXUS Updates

Metin Tuşları — NEXUS için **resmî güncelleme yayın deposu**.

**Durum:** Yayın kanalı hazırlanıyor. Henüz indirilebilir bir NEXUS sürümü veya etkin bir `latest.json` yayımlanmadı. Çalışan v9.1'i kaldırmayın.

## Güncelleme adresleri

- İmzalı sürüm bildirimi: `https://raw.githubusercontent.com/arwonxy0/NEXUS-Updates/main/latest.json`
- Kurulum paketleri: [GitHub Releases](https://github.com/arwonxy0/NEXUS-Updates/releases)
- Gelecekteki bir kurulum dosyasının örnek yolu: `https://github.com/arwonxy0/NEXUS-Updates/releases/download/v9.4.0/MetinTuslari_NEXUS_v9_4_0_Setup.exe`

**Önemli:** Bu adresler şimdilik yapılandırma içindir; yukarıdaki örnek kurulum dosyası henüz yoktur.

## Güvenli yayın ilkeleri

1. Uygulama yalnızca HTTPS ve yayıncı Ed25519 imzasıyla doğrulanmış `latest.json` dosyasını kabul eder.
2. İndirilen `Setup.exe`, imzalı bildirimin boyutu ve SHA-256 değeriyle eşleşmelidir.
3. Kullanıcı onayı olmadan kurulum çalıştırılmaz; yeni sürümde aynı Inno Setup `AppId` korunur.
4. **`private.pem`, AppData, pano geçmişi, kullanıcı profilleri, yedek ZIP'leri veya erişim anahtarları bu depoya yüklenmez.**
5. Sürüm yayınlanmadan önce Windows testleri ve gerçek kurulum/yedek doğrulaması tamamlanır.

İmza anahtarı ve yayın adımları için [GUVENLI_YAYIN.md](GUVENLI_YAYIN.md) dosyasına bakın.

Bu depo **kaynak kod deposu değil**, genel erişimli güncelleme dağıtım deposudur.
