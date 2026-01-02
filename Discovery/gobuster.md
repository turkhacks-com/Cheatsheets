
#    GOBUSTER CHEATSHEET                   
### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com
#### Gobuster GitHub: https://github.com/OJ/gobuster

---

## Nedir:
Gobuster, Go ile yazılmış, **directory / file brute force**, **DNS subdomain discovery** ve **VHost keşfi** için kullanılan hızlı bir içerik keşif aracıdır. Pentest ve bug bounty süreçlerinde en yaygın kullanılan discovery araçlarından biridir.

---

## ## DIRECTORY / CONTENT DISCOVERY

#### Temel dizin taraması
```bash
gobuster dir -u http://target.com -w /path/to/wordlist.txt
```

#### HTTP protokolü ile dizin taraması (thread artırılmış)
```bash
gobuster dir -u http://target.com -w /path/to/wordlist.txt -t 50
```

#### HTTPS üzerinden dizin taraması
```bash
gobuster dir -u https://target.com -w /path/to/wordlist.txt
```

#### URL listesi ile dizin taraması
```bash
gobuster dir -u http://target.com -w urls.txt
```

---

## ## SUBDOMAIN / DNS DISCOVERY

#### Subdomain taraması
```bash
gobuster dns -d target.com -w /path/to/subdomain_wordlist.txt
```

#### DNS resolver belirleyerek hızlı subdomain taraması
```bash
gobuster dns -d target.com -w /path/to/subdomain_wordlist.txt -t 50 --dns-resolver 8.8.8.8
```

---

## ## OUTPUT / EXTENSION

#### Dosya uzantıları ve çıktı kaydı
```bash
gobuster dir -u http://target.com \
-w /path/to/wordlist.txt \
-x .php,.html \
-o output.txt
```

---

## İpuçları

- `.bak`, `.old`, `.zip` uzantıları mutlaka eklenmelidir  
- DNS modunda **resolver belirtmek** hız ve doğruluk sağlar  
- Çıktıları Nuclei / ffuf / httpx zincirinde kullanın  
- Büyük hedeflerde `-t 50`+ ciddi hız kazandırır  

---
