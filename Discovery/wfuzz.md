#     WFUZZ CHEATSHEET
### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com
#### WFuzz GitHub: https://github.com/xmendez/wfuzz

---

## Nedir:
WFuzz, HTTP parametrelerini, dizinleri, dosyaları, header alanlarını ve veri payload’larını brute‑force ederek **gizli parametreler, LFI/RFI/XSS/IDOR ve yetkisiz erişim yüzeylerini** ortaya çıkaran çok yönlü bir fuzzing motorudur.

---

## ## TEMEL PARAMETRE FUZZING

#### Basit parametre brute‑force
```bash
wfuzz -c -z file,/path/to/wordlist.txt --hc 404 http://target.com/FUZZ
```

#### GET parametresi fuzzing
```bash
wfuzz -c -z file,/path/to/wordlist.txt http://target.com/page.php?id=FUZZ
```

#### Belirli parametre adı üzerinde fuzzing
```bash
wfuzz -c -z file,/path/to/wordlist.txt http://target.com/search?query=FUZZ
```

---

## ## POST / FORM FUZZING

#### POST isteği ile parola alanı brute‑force
```bash
wfuzz -c -z file,/path/to/wordlist.txt --hc 404 -X POST -d "username=admin&password=FUZZ" http://target.com/login
```

#### HTML dosya uzantıları üzerinden fuzzing
```bash
wfuzz -c -z file,/path/to/wordlist.txt -u "http://target.com/page?file=FUZZ.html"
```

---

## ## HEADER / ADVANCED

#### Özel HTTP header fuzzing
```bash
wfuzz -c -z file,/path/to/wordlist.txt --header "X-Custom-Header: FUZZ" http://target.com
```

#### Verbose mod (detaylı çıktı)
```bash
wfuzz -c -v -z file,/path/to/wordlist.txt http://target.com/FUZZ
```

---

## İpuçları

- wfuzz, `httpx` sonrası **gizli endpoint ve parametre keşfi** için en etkili araçlardan biridir  
- IDOR, LFI ve yetki atlama testlerinde `FUZZ` değişkeni kritik rol oynar  
- ffuf’a göre daha manuel ama daha esnektir  

---
