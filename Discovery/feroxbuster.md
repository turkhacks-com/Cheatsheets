#  FEROXBUSTER CHEATSHEET
### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com
#### Feroxbuster GitHub: https://github.com/epi052/feroxbuster

---

## Nedir:
Feroxbuster, Rust ile yazılmış, **yüksek hızlı ve çok iş parçacıklı (multi‑threaded)** bir directory / file brute‑force (dirbusting) aracıdır.  
Büyük wordlist’ler ve geniş hedef yüzeylerinde, Gobuster/Dirsearch gibi araçlara göre daha hızlı ve kararlı çalışır.

---

## ## TEMEL KULLANIM

#### Basit dizin taraması
```bash
feroxbuster -u http://target.com -w /path/to/wordlist.txt
```

#### HTTP üzerinden dizin taraması (thread artırılmış)
```bash
feroxbuster -u http://target.com -w /path/to/wordlist.txt -t 50
```

#### HTTPS üzerinden dizin taraması
```bash
feroxbuster -u https://target.com -w /path/to/wordlist.txt
```

---

## ## DOSYA UZANTILARI / RESPONSE KODLARI

#### Belirli uzantılar ile tarama
```bash
feroxbuster -u http://target.com -w /path/to/wordlist.txt -x .php,.html
```

#### Sadece belirli HTTP durum kodlarını göster
```bash
feroxbuster -u http://target.com -w /path/to/wordlist.txt -s 200
```

---

## ## HIZ / METHOD / HEADER

#### Paralel thread sayısını artır
```bash
feroxbuster -u http://target.com -w /path/to/wordlist.txt -t 100
```

#### Farklı HTTP metodunu test et (POST)
```bash
feroxbuster -u http://target.com -w /path/to/wordlist.txt -X POST
```

#### Özel header ile tarama
```bash
feroxbuster -u http://target.com -w /path/to/wordlist.txt -H "X-Forwarded-For: 127.0.0.1"
```

---

## ## ADVANCED

#### Directory listing taraması + yüksek hız
```bash
feroxbuster -u http://10.10.112.88/ \
-w /usr/share/wordlists/dirb/big.txt \
--scan-dir-listings -t 100
```

---

## İpuçları

- `.bak`, `.old`, `.zip` uzantıları mutlaka ekleyin  
- 301/302 sonuçlarını manuel inceleyin  
- Büyük hedeflerde `-t 100` üzeri ciddi hız kazandırır  
- İlk taramayı küçük wordlist ile yapıp sonra genişletmek en sağlıklısıdır  

---
