
#  DIRECTORY FUZZING CHEATSHEET
### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com

---

## Nedir:
Directory / content fuzzing, web sunucularında **gizli dizinler, admin panelleri, yedek dosyalar, API endpoint’leri ve unutulmuş kaynakları** tespit etmek için kullanılan brute‑force tabanlı keşif tekniğidir.

---

## ## FEROXBUSTER

#### Temel dizin taraması
```bash
feroxbuster -u https://target.com -w /usr/share/wordlists/dirb/common.txt
```

#### Thread sayısını artır
```bash
feroxbuster -u https://target.com -w wordlist.txt -t 50
```

#### Dosya uzantıları ile tarama
```bash
feroxbuster -u https://target.com -w wordlist.txt -x php,txt,bak,zip,old
```

#### Recursive (alt dizinlere inerek)
```bash
feroxbuster -u https://target.com -w wordlist.txt -r
```

#### Durum kodu filtreleme
```bash
feroxbuster -u https://target.com -w wordlist.txt -s 200,204,301,302
```

#### Proxy (Burp / Tor)
```bash
feroxbuster -u https://target.com -w wordlist.txt --proxy http://127.0.0.1:8080
```

---

## ## WF UZZ

#### Temel fuzz
```bash
wfuzz -c -z file,/usr/share/wordlists/dirb/common.txt --hc 404 https://target.com/FUZZ
```

#### Dosya uzantıları ile
```bash
wfuzz -c -z file,wordlist.txt --hc 404 https://target.com/FUZZ.php
```

#### HTTP method fuzz
```bash
wfuzz -c -z list,GET-POST-PUT-DELETE https://target.com/FUZZ
```

#### Cookie / Header ile fuzz
```bash
wfuzz -c -z file,wordlist.txt -H "User-Agent: FUZZ" https://target.com/
```

---

## ## FFUF

#### Temel fuzz
```bash
ffuf -u https://target.com/FUZZ -w /usr/share/wordlists/dirb/common.txt
```

#### Dosya uzantıları ile
```bash
ffuf -u https://target.com/FUZZ -w wordlist.txt -e .php,.bak,.old,.zip,.txt
```

#### Status code filtreleme
```bash
ffuf -u https://target.com/FUZZ -w wordlist.txt -mc 200,204,301,302
```

#### Boyut bazlı filtre
```bash
ffuf -u https://target.com/FUZZ -w wordlist.txt -fs 4242
```

#### Recursive fuzz
```bash
ffuf -u https://target.com/FUZZ -w wordlist.txt -recursion
```

#### Header / Cookie ile fuzz
```bash
ffuf -u https://target.com/FUZZ -w wordlist.txt -H "Authorization: Bearer FUZZ"
```

---

## ## WORDLIST ÖNERİLERİ

| Amaç | Wordlist |
|----|------|
| Genel | dirb/common.txt |
| Büyük | raft-large-directories.txt |
| API | api-endpoints.txt |
| Backup | backup-files.txt |
| Admin | admin-panels.txt |

---

## İpuçları

- Önce küçük wordlist → sonra büyük liste  
- Status 301/302 mutlaka incele  
- Backup (.bak, .old, .zip) uzantıları çok kritik bulgudur  
- API dizinleri ayrı wordlist ile fuzz edilmelidir  

---
