### Turkhacks.com | Bug researchers team
#### GitHub: https://github.com/turkhacks-com
#### Nmap GitHub: https://github.com/nmap/nmap

#### Nedir:
Nmap, ağ üzerindeki cihazları, açık portları, çalışan servisleri, versiyon bilgilerini ve olası güvenlik zafiyetlerini tespit etmek için kullanılan güçlü bir ağ keşif ve güvenlik tarama aracıdır.

---

## TEMEL NMAP KULLANIMI

#### Basit port taraması (ilk 1000 port)
`nmap target.com`

#### Daha fazla port tarama (ilk 5000 port)
`nmap -p-5000 target.com`

#### Tüm portları tarama (0-65535)
`nmap -p- target.com`

#### Hedefin canlı olup olmadığını kontrol etme (ping scan)
`nmap -sn target.com`

#### Tek bir portu tarama
`nmap -p 443 target.com`

#### Belirli bir port aralığını tarama
`nmap -p 20-100 target.com`

#### Birden fazla portu tarama
`nmap -p 22,80,443 target.com`

#### Belirli bir IP aralığını tarama
`nmap 192.168.1.0/24`

#### Tüm yerel ağı tarama
`nmap -sn 192.168.1.0/24`

---

## SERVİS VE VERSİYON TESPİTİ

#### Servis ve versiyon bilgisi toplama
`nmap -sV target.com`

#### Derin servis taraması
`nmap -sV --version-intensity 9 target.com`

#### İşletim sistemi tespiti (OS Detection)
`nmap -O target.com`

#### Firewall arkasındaki işletim sistemini belirleme
`nmap -O --fuzzy target.com`

#### Servis & OS tespitini birlikte kullanma
`nmap -A target.com`

---

## GİZLİ TARAMALAR (STEALTH SCAN)

#### TCP SYN taraması
`nmap -sS target.com`

#### TCP Connect taraması
`nmap -sT target.com`

#### UDP taraması
`nmap -sU target.com`

#### NULL taraması
`nmap -sN target.com`

#### FIN taraması
`nmap -sF target.com`

#### Xmas taraması
`nmap -sX target.com`

---

## PING TARAMALARI

#### Aktif cihazları bulma
`nmap -sn 192.168.1.0/24`

#### Ping bypass
`nmap -Pn target.com`

#### Düşük hızda tarama
`nmap --max-rate 10 target.com`

---

## FARKLI AĞ PROTOKOLLERİYLE TARAMA

#### TCP taraması
`nmap -sT target.com`

#### UDP taraması
`nmap -sU target.com`

#### IP protokol taraması
`nmap -sO target.com`

#### IPv6 taraması
`nmap -6 target.com`

---

## PORT TARAMA TEKNİKLERİ

#### Açık portları listeleme
`nmap --open target.com`

#### Güvenlik duvarı tespiti
`nmap -sA target.com`

---

## DETAYLI BİLGİ TOPLAMA

#### Servisleri göster
`nmap -sV -p 80,443,22 target.com`

#### Tüm portlar + OS + servis
`nmap -sV -O -p- target.com`

---

## EVASION / KAÇINMA TEKNİKLERİ

#### Yavaş tarama
`nmap -T2 target.com`

#### User-agent değiştirme
`nmap --script=http-useragent target.com`

#### SSL analizleri
`nmap --script=ssl-enum-ciphers target.com`

---

## ZAFİYET TARAMALARI

#### Genel zafiyet taraması
`nmap --script=vuln target.com`

#### Exploit edilebilir servisler
`nmap --script=exploit target.com`

#### Yetkilendirme zafiyetleri
`nmap --script=auth target.com`

---

## BRUTE FORCE TARAMALARI

#### SSH
`nmap --script=ssh-brute target.com`

#### FTP
`nmap --script=ftp-brute target.com`

#### MySQL
`nmap --script=mysql-brute target.com`

#### SNMP
`nmap --script=snmp-brute target.com`

#### RDP
`nmap --script=rdp-brute target.com`

---

## WEB SERVİS TARAMALARI

#### HTTP başlıkları
`nmap --script=http-headers target.com`

#### HTTP versiyon bilgisi
`nmap --script=http-server-header target.com`

#### Dizin keşfi
`nmap --script=http-enum target.com`

---

## BANNER GRABBING

#### FTP banner
`nmap --script=ftp-banner target.com`

#### SMTP banner
`nmap --script=smtp-banner target.com`

---

## DOSYA ÇIKTISI VE LOG

#### Tüm formatlarda kayıt
`nmap -oA scan_output target.com`

#### XML kayıt
`nmap -oX scan.xml target.com`

#### TXT kayıt
`nmap -oN scan.txt target.com`

#### Grepable kayıt
`nmap -oG scan.gnmap target.com`

---

## ZAMANLAYICI AYARLARI

#### En hızlı
`nmap -T5 target.com`

#### En yavaş
`nmap -T1 target.com`

#### Orta seviye
`nmap -T3 target.com`

---

## ÖZEL PAKET / PORT ANALİZİ

#### Kaynak port belirleme
`nmap --source-port 53 target.com`

#### TCP bayrakları
`nmap --scanflags SYNFINACK target.com`

---

## NMAP SCRIPT ENGINE (NSE)

#### Scriptleri listeleme
`nmap --script-help=*`

#### SQLi taraması
`nmap --script=http-sql-injection target.com`

#### Boş MySQL şifreleri
`nmap --script=mysql-empty-password target.com`

#### FTP anonim erişim
`nmap --script=ftp-anon target.com`
