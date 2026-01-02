#     FFUF CHEATSHEET
### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com
#### FFUF GitHub: https://github.com/ffuf/ffuf

---

## Nedir:
FFUF (Fuzz Faster U Fool), web uygulamalarında **directory, parameter, value, vhost, header ve authentication fuzzing** işlemlerini yüksek hızda yapabilen, filtreleme ve çıktı formatlama özellikleriyle bug bounty ve pentest dünyasının standart fuzzing aracıdır.

---

## ## DIRECTORY / CONTENT DISCOVERY

#### 1. Basit dizin taraması (Wordlist ile)
```bash
ffuf -u https://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt
```

---

## ## PARAMETER FUZZING

#### 2. GET parametre adı fuzzing
```bash
ffuf -u "https://example.com/index.php?FUZZ=1" -w /usr/share/wordlists/params.txt
```

#### 3. POST isteği ile değer fuzzing
```bash
ffuf -u "https://example.com/login" -X POST -d "username=admin&password=FUZZ" -w /usr/share/wordlists/rockyou.txt
```

#### 4. Çoklu parametre fuzzing
```bash
ffuf -u "https://example.com/index.php?FUZZ=FUZZ2" \
-w /usr/share/wordlists/params.txt:/usr/share/wordlists/values.txt
```

---

## ## HEADER / WAF / VHOST

#### 5. Özel header ile fuzzing
```bash
ffuf -u "https://example.com/FUZZ" -H "User-Agent: Mozilla" -w /usr/share/wordlists/dirb/common.txt
```

#### 6. HTTP koduna göre filtreleme (Sadece 200)
```bash
ffuf -u https://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt -mc 200
```

#### 7. Büyük-küçük harf ile WAF bypass denemesi
```bash
ffuf -u "https://example.com/FuZz" -w /usr/share/wordlists/dirb/common.txt -mc 200
```

#### 8. Alt domain / VHost fuzzing
```bash
ffuf -u "https://FUZZ.example.com" \
-w /usr/share/wordlists/subdomains.txt \
-H "Host: FUZZ.example.com"
```

```bash
ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt \
-u http://nahamstore.thm/ \
-H "Host: FUZZ.nahamstore.thm" -fw 125
```

---

## ## OUTPUT / RAPOR

#### 9. Sonuçları JSON formatında kaydet
```bash
ffuf -u https://example.com/FUZZ \
-w /usr/share/wordlists/dirb/common.txt \
-o results.json -of json
```

---

## İpuçları

- `-fw` (filter word count) ve `-fs` (filter size) çok kritik filtrelerdir  
- VHost fuzzing, gizli admin panellerinin %60’ını ortaya çıkarır  
- Parametre fuzzing API endpoint keşfinde altın madendir  
- Büyük wordlist ile başlamadan önce küçük liste ile baseline çıkarın  

---
