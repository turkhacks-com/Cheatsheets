#     SUBFINDER CHEATSHEET
### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com
#### Subfinder GitHub: https://github.com/projectdiscovery/subfinder

---

## Nedir:
Subfinder, pasif DNS kaynaklarını kullanarak **hızlı ve sessiz subdomain keşfi** yapan, recon zincirinin ilk halkası olan yüksek performanslı bir keşif aracıdır. Amass’a göre daha sessiz, httpx ve nuclei öncesi yüzey keşfi için idealdir.

---

## ## TEMEL KULLANIM

#### Temel subdomain keşfi
```bash
subfinder -d target.com
```

#### Sonuçları dosyaya kaydet
```bash
subfinder -d target.com -o subdomains.txt
```

---

## ## KAYNAK / WORDLIST

#### Özel wordlist ile tarama
```bash
subfinder -d target.com -w /path/to/subdomain_wordlist.txt
```

#### DNS resolver belirle
```bash
subfinder -d target.com -r 8.8.8.8 -o subdomains.txt
```

---

## ## ÇOKLU HEDEF

#### Birden fazla domaini tara
```bash
subfinder -d target1.com -d target2.com -o subdomains.txt
```

---

## ## AKTİF / PASİF KEŞİF

#### Aktif domain listesinden pasif keşif
```bash
subfinder -d target.com -sf /path/to/active_subdomains.txt -o final_subdomains.txt
```

---

## İpuçları

- subfinder çıktısı direkt `httpx` → `nuclei` → `ffuf` zincirine girer  
- Sessiz recon için idealdir  
- Büyük scope’larda Amass yerine ilk tercih olmalıdır  

---
