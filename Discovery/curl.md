#     CURL CHEATSHEET
### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com
#### cURL GitHub: https://github.com/curl/curl

---

## Nedir:
cURL, HTTP/HTTPS/FTP/SFTP/SMTP gibi birçok protokol üzerinden **istemci–sunucu iletişimini test etmek**, API çağrıları yapmak, dosya transferi gerçekleştirmek ve güvenlik testlerinde manuel istek simülasyonu yapmak için kullanılan çok yönlü bir CLI aracıdır.

---

## ## TEMEL HTTP KULLANIMI

#### Basit HTTP isteği
```bash
curl http://example.com
```

#### HTTPS isteği
```bash
curl https://example.com
```

#### Sadece HTTP başlıklarını göster
```bash
curl -I https://example.com
```

---

## ## DOSYA İNDİRME / KAYDETME

#### Dosyayı indir (orijinal adıyla)
```bash
curl -O https://example.com/file.zip
```

#### Dosyayı özel adla kaydet
```bash
curl -o myfile.zip https://example.com/file.zip
```

#### Birden fazla dosya indir
```bash
curl -O https://example.com/file1.zip -O https://example.com/file2.zip
```

#### Yanıtı HTML olarak kaydet
```bash
curl -o response.html https://example.com
```

---

## ## POST / API KULLANIMI

#### Form POST isteği
```bash
curl -X POST -d "username=user&password=pass" https://example.com/login
```

#### JSON ile POST
```bash
curl -X POST -H "Content-Type: application/json" \
-d '{"username":"user","password":"pass"}' https://example.com/api/login
```

#### Authorization header ile istek
```bash
curl -H "Authorization: Bearer TOKEN" https://example.com/api
```

---

## ## AUTH / COOKIE / HEADER

#### Basic Auth
```bash
curl -u "kullanici:parola" https://example.com/api
```

#### Cookie ile istek
```bash
curl -b "sessionid=abcd1234" https://example.com/dashboard
```

#### User‑Agent değiştir
```bash
curl -A "Mozilla/5.0 (Windows NT 10.0; Win64; x64)" https://example.com
```

---

## ## PROXY / TIMEOUT / KONTROL

#### Proxy üzerinden istek
```bash
curl -x http://proxyserver:port https://example.com
```

#### Timeout belirleme
```bash
curl --max-time 10 https://example.com
```

#### HTTP durum kodunu göster
```bash
curl -s -o /dev/null -w "%{http_code}" https://example.com
```

---

## ## FTP / DOSYA TRANSFER

#### FTP sunucusundan dosya indir
```bash
curl -u "kullanici:parola" ftp://ftp.example.com/file.txt -o localfile.txt
```

---

## ## İPUÇLARI

- `-v` parametresi detaylı debug çıktısı verir  
- API testlerinde `-H "Content-Type: application/json"` her zaman kullanılmalı  
- Büyük dosya transferlerinde `--limit-rate` bant genişliği kontrolü sağlar  

---
