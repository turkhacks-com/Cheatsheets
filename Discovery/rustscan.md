#         RUSTSCAN CHEATSHEET
### Turkhacks.com | Offensive Security Research
#### https://github.com/RustScan/RustScan

---

## Nedir:
RustScan, klasik Nmap taramalarından önce çalışan, **çok hızlı port keşfi** yapan ve bulunan açık portları otomatik olarak Nmap’e devreden bir port keşif motorudur. Modern pentest zincirlerinin ilk adımıdır.

---

# 1. TEMEL TARAMA

### Varsayılan tam tarama (port keşfi + nmap)
```bash
rustscan -a 10.10.10.5
```

### Root yetkisi ile ham soket hızlı tarama
```bash
sudo rustscan -a 10.10.10.5
```

### Sadece açık port keşfi (Nmap yok)
```bash
rustscan -a 10.10.10.5 --no-nmap
```

### Sessiz mod (sadece sonuç)
```bash
rustscan -a 10.10.10.5 -q
```

---

# 2. HEDEF YÖNETİMİ

### Çoklu hedef
```bash
rustscan -a 10.10.10.5 api.example.com test.site
```

### CIDR subnet tarama
```bash
rustscan -a 10.10.10.0/24
```

### Dosyadan hedef
```bash
rustscan -a targets.txt
```

### Hariç tutma
```bash
rustscan -a 10.10.10.0/24 --exclude 10.10.10.254
```

---

# 3. PORT YÖNETİMİ

### Belirli portlar
```bash
rustscan -a 10.10.10.5 --ports 21,22,80,443,3306,8080
```

### Port aralığı
```bash
rustscan -a 10.10.10.5 --ports 1-1024
```

### En popüler 1000 port
```bash
rustscan -a 10.10.10.5 --top
```

---

# 4. NMAP ENTEGRASYONU

### Agresif detaylı tarama
```bash
rustscan -a 10.10.10.5 -- -A -T4
```

### ICMP kapalı hedefler
```bash
rustscan -a 10.10.10.5 -- -Pn -A
```

### UDP tarama
```bash
rustscan -a 10.10.10.5 -- -sU --top-ports 20
```

### Script kullanımı
```bash
rustscan -a 10.10.10.5 -- -sV --script="http-title,http-headers"
```

### Full port deep scan
```bash
rustscan -a 10.10.10.5 -- -p- -A -v
```

---

# 5. PERFORMANS

### Batch size
```bash
rustscan -a 10.10.10.5 -b 6500
```

### Timeout
```bash
rustscan -a 10.10.10.5 -t 2000
```

### Ulimit
```bash
rustscan -a 10.10.10.5 -u 5000
```

---

# 6. OUTPUT

### Greppable
```bash
rustscan -a 10.10.10.5 -g
```

### Nmap çıktı
```bash
rustscan -a 10.10.10.5 -- -oA nmap_sonuclari
```

---

# 7. OPSEC / İPUÇLARI

- RustScan → httpx → nuclei → ffuf zinciri modern pentest standardıdır  
- RustScan her zaman **ilk adım** olmalıdır  
- `--no-nmap` modunda çıkan portları manuel hedef listesi olarak kullanın  

---
