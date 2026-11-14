# NEXUS güncelleme yayınlama rehberi

## İlk kurulum — yalnızca yayıncı bilgisayarında

1. NEXUS v9.3 kaynak paketini ayrı bir klasöre çıkartın. Çalışan v9.1'i kaldırmayın.
2. `Publisher_Araclari.py keygen` ile Ed25519 imza anahtarlarını **uygulama proje klasörünün dışında**, yerel ve erişimi kısıtlı bir klasörde oluşturun. `private.pem` çevrimiçi servislere gönderilmez. Güvenli, çevrimdışı yedeğini alın.
3. `Publisher_Araclari.py configure` ile şu HTTPS adresini ve `public.b64` dosyasını uygulamaya derleme öncesi tanıtın:

   `https://raw.githubusercontent.com/arwonxy0/NEXUS-Updates/main/latest.json`

4. İmza anahtarı sadece **herkese açık** kısmıyla EXE içine yerleştirilir. Kaynak testleri / Qt smoke ve kurulum betikleri Windows'ta çalıştırılır.
5. NEXUS v9.3'ü **bir defa** eski sürümün üzerine yerinde yükseltin. Bu sürümde çevrimiçi güncelleme denetimi ancak yayınlanmış, geçerli bir `latest.json` olduğunda çalışır.

## Her sonraki sürüm için

1. Yeni Windows kurulum dosyasını oluşturun. İsim birebir şu biçimde olmalıdır: `MetinTuslari_NEXUS_v9_4_0_Setup.exe` (sürümü değiştirin).
2. Program kayıtlarını etkileyen değişiklikleri test edin; Inno Setup `AppId` ve kullanıcı veri yolu aynı kalsın. ZIP ve EXE hash doğrulamasını yapın.
3. GitHub Releases altında `v9.4.0` gibi uygun tag ile yeni bir sürüm açın, **yalnızca test edilmiş** kurulum dosyasını yükleyin. Yayın indirme URL'si:

   `https://github.com/arwonxy0/NEXUS-Updates/releases/download/v9.4.0/MetinTuslari_NEXUS_v9_4_0_Setup.exe`

4. Aynı **yerel özel anahtar** ile `Publisher_Araclari.py sign` komutunu çalıştırarak gerçek kurulum dosyasının imzalı `latest.json` bildirimini oluşturun. Bildirimde `product`, `version`, `setup_url`, `sha256`, `size`, `notes`, `signature` alanları bulunur.
5. Kurulum dosyasının herkese açık URL'si çalıştıktan sonra **imzalı** `latest.json` dosyasını deponun `main` dalının köküne yükleyin (önce dosya yoksa oluşturun, sonra mevcut dosyayı güncelleyin).
6. Başka bir Windows cihazından `Güncellemeleri Denetle` → `İndir ve Güncelle` akışını, kaynak yedeğini ve kurulum sonrası veri bütünlüğünü doğrulayın.

## Güvenlik ve kurtarma

- `private.pem` hiçbir zaman depoya, Release'e, ChatGPT'ye veya yüklenen ZIP'e eklenmez.
- `public.b64` paylaşılabilir; özel anahtarın kaybı veya değişmesi eski EXE'lerde anahtar uyuşmazlığına yol açar.
- `latest.json` için **imzasız yer tutucu/dummy** dosyası yüklemeyin. Geçerli sürüm yoksa dosya mevcut olmayabilir.
- İndirme ve kurulum kullanıcı onayını gerektirir. Otomatik sessiz kurulum varsayılmaz.
- Yeni sürüm sorun çıkarırsa önceki güvenilir Setup.exe elle kullanılabilir; AppData ve yedek klasörleri silinmez.
- Python kaynak kodu, kullanıcı veri klasörü, günlükler veya kişisel içerikler bu genel depoya aktarılmaz.
