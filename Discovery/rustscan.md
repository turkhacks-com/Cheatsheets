#     RUSTSCAN CHEATSHEET
### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com
#### RustScan GitHub: https://github.com/RustScan/RustScan

---

## Nedir:
RustScan, klasik Nmap taramalarını **çok yüksek hızda ön port keşfi** ile besleyen, Rust ile yazılmış ultra hızlı bir port tarayıcıdır. Açık portları milisaniyeler içinde keşfeder ve Nmap’e aktararak tam servis fingerprinting yapılmasını sağlar.

---

## ## TEMEL TARAMA

#### Tüm portları tara ve Nmap varsayılan scriptleriyle analiz et
```bash
rustscan -a 10.10.10.5
```

#### Ham soket ile ultra hızlı tarama
```bash
sudo rustscan -a 10.10.10.5
```

#### Sadece açık portları keşfet (Nmap çalıştırmaz)
```bash
rustscan -a 10.10.10.5 --no-nmap
```

#### Sessiz mod
```bash
rustscan -a 10.10.10.5 -q
```

---

## ## HEDEF BELİRTME

#### Çoklu hedef tarama
```bash
rustscan -a 10.10.10.5 api.example.com test.site
```

#### CIDR ile alt ağ taraması
```bash
rustscan -a 10.10.10.0/24
```

#### Dosyadan hedef oku
```bash
rustscan -a targets.txt
```

#### Hedef hariç tut
```bash
rustscan -a 10.10.10.0/24 --exclude 10.10.10.254
```

---

## ## PORT SEÇİMİ

#### Belirli portlar
```bash
rustscan -a 10.10.10.5 --ports 21,22,80,443,3306,8080
```

#### Port aralığı
```bash
rustscan -a 10.10.10.5 --ports 1-1024
```

#### En popüler portlar
```bash
rustscan -a 10.10.10.5 --top
```

#### Karma port listesi
```bash
rustscan -a 10.10.10.5 --ports 80,443,8000-8100
```

---

## ## NMAP ENTEGRASYONU

#### Agresif tarama
```bash
rustscan -a 10.10.10.5 -- -A -T4
```

#### Ping bypass
```bash
rustscan -a 10.10.10.5 -- -Pn -A
```

#### UDP port taraması
```bash
rustscan -a 10.10.10.5 -- -sU --top-ports 20
```

#### HTTP scriptleri
```bash
rustscan -a 10.10.10.5 -- -sV --script="http-title,http-headers"
```

#### Full detay Nmap
```bash
rustscan -a 10.10.10.5 -- -p- -A -v
```

---

## ## PERFORMANS

#### Batch size artır
```bash
rustscan -a 10.10.10.5 -b 6500
```

#### Timeout artır
```bash
rustscan -a 10.10.10.5 -t 2000
```

#### Ulimit ayarla
```bash
rustscan -a 10.10.10.5 -u 5000
```

#### Tarama sırası
```bash
rustscan -a 10.10.10.5 --scan-order Serial
```

---

## ## OUTPUT

#### Greppable çıktı
```bash
rustscan -a 10.10.10.5 -g
```

#### Nmap .txt
```bash
rustscan -a 10.10.10.5 -- -oN scan.txt
```

#### Nmap XML
```bash
rustscan -a 10.10.10.5 -- -oX scan.xml
```

#### Tüm formatlar
```bash
rustscan -a 10.10.10.5 -- -oA scan_all
```

---

## ## DİĞER

#### Network interface seç
```bash
rustscan -a 10.10.10.5 -i eth1
```

#### DNS kapat
```bash
rustscan -a example.com --no-dns
```

#### Retry sayısı
```bash
rustscan -a 10.10.10.5 --tries 3
```

#### Versiyon
```bash
rustscan --version
```

---

## İpuçları

- RustScan her zaman **ön tarama**, Nmap her zaman **derin analiz** içindir  
- `--no-nmap` + `httpx` = ultra hızlı yüzey keşfi  
- RustScan çıktısı direkt nuclei / ffuf zincirine girer  

---
