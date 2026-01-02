# RustScan - Geniş ve Ayrıntılı Cheatsheet

---
## Bölüm 1: Temel Tarama Komutları
---

# Bir hedefin tüm portlarını tarar ve açık portları Nmap'in varsayılan betikleriyle (-sC -sV) analiz eder
rustscan -a 10.10.10.5

# Ham soket erişimiyle (daha hızlı) tarama yapmak için sudo ile çalıştırın
sudo rustscan -a 10.10.10.5

# Sadece açık portları keşfeder, Nmap taraması yapmaz (hızlı kontrol için)
rustscan -a 10.10.10.5 --no-nmap

# RustScan'in kendi banner'larını ve ilerleme çubuğunu gizleyerek sadece sonucu gösterir
rustscan -a 10.10.10.5 -q

---
## Bölüm 2: Hedef Belirtme
---

# Birden fazla hedefi (IP veya alan adı) boşluk bırakarak tarama
rustscan -a 10.10.10.5 api.example.com test.site

# CIDR notasyonunda bir alt ağı tarama
rustscan -a 10.10.10.0/24

# Hedef listesini bir dosyadan okuma (her satırda bir hedef)
rustscan -a /path/to/targets.txt

# Bir hedefi tarama dışı bırakma
rustscan -a 10.10.10.0/24 --exclude 10.10.10.254

---
## Bölüm 3: Port Kontrolü ve Aralık Belirtme
---

# Sadece belirli portları virgülle ayırarak tarama
rustscan -a 10.10.10.5 --ports 21,22,80,443,3306,8080

# Belirli bir port aralığını tarama
rustscan -a 10.10.10.5 --ports 1-1024

# En popüler 1000 portu tarama
rustscan -a 10.10.10.5 --top

# Belirli portları ve aralıkları bir arada kullanma
rustscan -a 10.10.10.5 --ports 80,443,8000-8100

# Taranacak portları bir string (dizi) olarak verme
rustscan -a 10.10.10.5 --ports "80, 443, 1337"

---
## Bölüm 4: Gelişmiş Nmap Entegrasyonu
---

# "--" sonrası tüm komutları Nmap'e aktarır. Bu örnek agresif (-A) ve hızlı (-T4) bir tarama yapar.
rustscan -a 10.10.10.5 -- -A -T4

# Hedefin ping (ICMP) isteklerine cevap vermediği durumlarda taramayı zorlamak için (-Pn)
rustscan -a 10.10.10.5 -- -Pn -A

# Nmap ile UDP port taraması yapma (-sU), bu işlem TCP'ye göre yavaştır
rustscan -a 10.10.10.5 -- -sU --top-ports 20

# Belirli bir Nmap betiğini (script) çalıştırma
rustscan -a 10.10.10.5 -- -sV --script="http-title,http-headers"

# Açık olan tüm portlarda (-p-) çok detaylı bir Nmap taraması başlatma
rustscan -a 10.10.10.5 -- -p- -A -v

---
## Bölüm 5: Performans Optimizasyonu
---

# Aynı anda taranacak port sayısını (batch size) artırarak taramayı hızlandırma (Varsayılan: 4500)
rustscan -a 10.10.10.5 -b 6500

# Port taraması için zaman aşımı süresini (timeout) milisaniye cinsinden artırma (Yavaş ağlar için)
rustscan -a 10.10.10.5 -t 2000

# Açık dosya limiti (ulimit) değerini manuel olarak ayarlama (Genellikle RustScan bunu otomatik yapar)
rustscan -a 10.10.10.5 -u 5000

# Portların taranma sırasını değiştirme (Serial veya Random)
rustscan -a 10.10.10.5 --scan-order Serial

---
## Bölüm 6: Çıktı Yönetimi
---

# Makine tarafından okunabilir (greppable) formatta sadece IP ve açık portları listeleme
rustscan -a 10.10.10.5 -g

# Nmap çıktısını normal metin (.nmap) olarak kaydetme
rustscan -a 10.10.10.5 -- -oN nmap_sonuclari.txt

# Nmap çıktısını XML (.xml) formatında kaydetme
rustscan -a 10.10.10.5 -- -oX nmap_sonuclari.xml

# Nmap çıktısını tüm formatlarda (nmap, gnmap, xml) kaydetme
rustscan -a 10.10.10.5 -- -oA nmap_sonuclari_tum_formatlar

---
## Bölüm 7: Diğer Faydalı Komutlar
---

# Tarama için belirli bir ağ arayüzünü (network interface) kullanma
rustscan -a 10.10.10.5 -i eth1

# Taranan ana bilgisayar adları için DNS çözümlemesini devre dışı bırakma
rustscan -a example.com --no-dns

# Erişilemeyen hedefleri tekrar deneme sayısını belirleme
rustscan -a 10.10.10.5 --tries 3

# RustScan versiyonunu kontrol etme
rustscan --version
