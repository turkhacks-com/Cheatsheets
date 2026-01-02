#     HTTPX CHEATSHEET
### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com
#### HTTPX GitHub: https://github.com/projectdiscovery/httpx

---

## Nedir:
HTTPX, büyük hedef listeleri üzerinde **canlı host tespiti**, HTTP servis keşfi, fingerprinting ve hızlı içerik analizi yapmak için kullanılan yüksek performanslı bir web probelama aracıdır. Nuclei, ffuf, dalfox ve diğer tarama zincirlerinin temelini oluşturur.

---

## ## TEMEL KULLANIM

#### Tek hedef tarama
```bash
echo target.com | httpx
```

#### Birden fazla hedef (stdin)
```bash
echo -e "target.com\nexample.com" | httpx
```

#### Hedef listesini dosyadan oku
```bash
httpx -l targets.txt
```

---

## ## PORT / PATH / YÖNLENDİRME

#### Belirli portları tara
```bash
echo target.com | httpx -p 80,443,8080
```

#### Her hedefe belirli path ekle
```bash
echo target.com | httpx -path /robots.txt
```

#### Path listesinden tara
```bash
echo target.com | httpx -path paths.txt
```

#### HTTP yönlendirmeleri takip et
```bash
echo http://target.com | httpx -fr -sc -title
```

---

## ## FINGERPRINT / META

#### Durum kodunu göster
```bash
echo target.com | httpx -sc
```

#### Sayfa başlığını göster
```bash
echo target.com | httpx -title
```

#### İçerik uzunluğu
```bash
echo target.com | httpx -cl
```

#### Sunucu bilgisi
```bash
echo target.com | httpx -server
```

#### Teknoloji tespiti
```bash
echo target.com | httpx -td
```

#### IP adresi
```bash
echo target.com | httpx -ip
```

#### CNAME kaydı
```bash
echo target.com | httpx -cname
```

#### ASN bilgisi
```bash
echo target.com | httpx -asn
```

---

## ## FILTER / MATCHER

#### Sadece 200 yanıtları göster
```bash
echo target.com | httpx -sc -mc 200
```

#### Belirli kodları gizle
```bash
echo target.com | httpx -sc -fc 404
```

#### İçerikte string eşleşmesi
```bash
echo target.com | httpx -ms "admin"
```

#### İçerikte string filtreleme
```bash
echo target.com | httpx -fs "Not Found"
```

---

## ## OUTPUT / FORMAT

#### Sessiz mod
```bash
echo target.com | httpx -silent
```

#### Çıktıyı dosyaya yaz
```bash
httpx -l targets.txt -silent -o canli_hostlar.txt
```

#### JSON çıktı
```bash
echo target.com | httpx -sc -title -json -o info.json
```

#### CSV çıktı
```bash
httpx -l targets.txt -sc -title -csv -o rapor.csv
```

#### Renkli çıktıyı kapat
```bash
echo target.com | httpx -nc
```

---

## ## HEADER / PROXY / OPSEC

#### Özel header ekle
```bash
echo target.com | httpx -H "Referer: test.com" -H "X-Custom: 123"
```

#### Proxy ile çalıştır
```bash
echo target.com | httpx -proxy http://127.0.0.1:8080
```

#### Thread sayısı
```bash
httpx -l targets.txt -t 100 -silent
```

#### Rate limit
```bash
httpx -l targets.txt -rl 30 -silent
```

#### Sabit User-Agent
```bash
echo target.com | httpx -H "User-Agent: MyScanner/1.0"
```

---

## İpuçları

- httpx çıktısı direkt **nuclei**, **ffuf**, **dalfox** zincirine girer  
- İlk adım her zaman httpx olmalı  
- `-mc 200` + `-title` kombinasyonu hızlı admin panel keşfi sağlar  

---
