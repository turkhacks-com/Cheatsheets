### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com
#### Amass GitHub: https://github.com/owasp-amass/amass

---

## Nedir:
Amass, OWASP tarafından geliştirilen, **attack surface discovery** (saldırı yüzeyi keşfi) odaklı bir keşif aracıdır.  
Pasif/aktif yöntemlerle alt domain, ASN, IP aralıkları, whois, network haritalama ve OSINT kaynaklarını kullanarak hedef organizasyonun dışa açık varlıklarını tespit etmek için kullanılır.

---

## ## ENUMERATION / DISCOVERY

#### 1. Basit bir alt domain taraması
```bash
amass enum -d example.com
```

#### 2. Pasif bilgi toplama (Sadece OSINT/veritabanı kaynakları)
```bash
amass enum -passive -d example.com
```

#### 3. Aktif tarama (DNS çözümleme ve aktif kaynaklar)
```bash
amass enum -active -d example.com
```

#### 4. Belirli OSINT kaynaklarını kullanarak tarama (Virustotal, Sublist3r vb.)
```bash
amass enum -d example.com -src
```

---

## ## INTEL / NETWORK DISCOVERY

#### 5. Whois ve IP aralıklarını gösterme
```bash
amass intel -whois -d example.com
```

#### 6. Belirli bir IP aralığına göre alt domain keşfi
```bash
amass intel -addr 192.168.1.0/24
```

---

## ## OUTPUT / BATCH

#### 7. Tespit edilen alt domainleri dosyaya kaydetme
```bash
amass enum -d example.com -o subdomains.txt
```

#### 8. Birden fazla domaini aynı anda tarama
```bash
amass enum -df domains.txt
```

---

## ## MAP / TOPOLOGY

#### 9. Ağ haritası oluşturma (aktif keşif + varlık ilişkilendirme)
```bash
amass map -d example.com
```

---

## ## PROXY / OPSEC

#### 10. Proxy üzerinden tarama (Tor veya Burp Suite)
```bash
amass enum -proxy socks5://127.0.0.1:9050 -d example.com
```

---

## İpuçları

- Büyük hedeflerde **-passive** ile başlayın, sonra **-active** ile derinleştirin.  
- Çıktıları **subdomains.txt** gibi dosyalara kaydedip; HTTP probeleri, Nuclei, Dalfox gibi araçlarla zincirleyin.  
- Proxy kullanımı OPSEC ve hız/limit yönetimi için faydalıdır.

---
