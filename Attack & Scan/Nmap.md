# TEMEL NMAP KULLANIMI

# Basit port taraması (ilk 1000 port)
nmap target.com

# Daha fazla port tarama (ilk 5000 port)
nmap -p-5000 target.com

# Tüm portları tarama (0-65535)
nmap -p- target.com

# Hedefin canlı olup olmadığını kontrol etme (ping scan)
nmap -sn target.com

# Tek bir portu tarama
nmap -p 443 target.com

# Belirli bir port aralığını tarama
nmap -p 20-100 target.com

# Birden fazla portu tarama
nmap -p 22,80,443 target.com

# Belirli bir IP aralığını tarama
nmap 192.168.1.0/24

# Tüm yerel ağı tarama
nmap -sn 192.168.1.0/24

# SERVİS VE VERSİYON TESPİTİ

# Servis ve versiyon bilgisi toplama
nmap -sV target.com

# Derin servis taraması
nmap -sV --version-intensity 9 target.com

# İşletim sistemi tespiti (OS Detection)
nmap -O target.com

# Firewall arkasındaki işletim sistemini belirleme
nmap -O --fuzzy target.com

# SERVİS & OS TESPİTİNİ BİRLİKTE KULLANMA
nmap -A target.com

# GİZLİ TARAMALAR (STEALTH SCAN)

# TCP SYN taraması (stealth mode)
nmap -sS target.com

# TCP Connect taraması
nmap -sT target.com

# UDP taraması
nmap -sU target.com

# NULL taraması (firewall atlatma)
nmap -sN target.com

# FIN taraması (firewall atlatma)
nmap -sF target.com

# Xmas taraması (firewall atlatma)
nmap -sX target.com

####  PING TARAMALARI
# Ping taraması (hangi cihazlar aktif)
nmap -sn 192.168.1.0/24

# Ping bypass (Eğer ICMP kapalıysa)
nmap -Pn target.com

# Firewall bypass için düşük hızda tarama
nmap --max-rate 10 target.com

#### FARKLI AĞ PROTOKOLLERİYLE TARAMA
# TCP taraması
nmap -sT target.com

# UDP taraması
nmap -sU target.com

# IP protokol taraması
nmap -sO target.com

# IPv6 taraması
nmap -6 target.com

# PORT TARAMA TEKNİKLERİ

# SYN scan (stealth mode, hızlı)
nmap -sS target.com

# Tam TCP bağlanma taraması
nmap -sT target.com

# UDP taraması (yavaş olabilir)
nmap -sU target.com

# Açık portları listeleme
nmap --open target.com

# Güvenlik duvarı tespit etme
nmap -sA target.com

####  PORT TARAMASI İLE DETAYLI BİLGİLER TOPLAMA
# Hangi servislerin çalıştığını gösterir
nmap -sV -p 80,443,22 target.com

# İşletim sistemini belirleme
nmap -O target.com

# Tüm portlar ve detaylı bilgi
nmap -sV -O -p- target.com

# Firewall olup olmadığını belirleme
nmap -sA target.com

# FARKLI TARAYICI İZLERİ KULLANMA (EVASION TECHNIQUES)

# Taramayı yavaşlatarak güvenlik sistemlerinden kaçınma
nmap -T2 target.com

# Farklı bir user-agent ile tarama yapma
nmap --script=http-useragent target.com

# Ağ trafiğini şifreleyerek tarama yapma
nmap --script=ssl-enum-ciphers target.com

# GÜVENLİK AÇIKLARINI TESPİT ETME

# Zafiyet taraması (script tarama)
nmap --script=vuln target.com

# Exploit edilebilir servisleri tarama
nmap --script=exploit target.com

# Hedef sistemin hangi saldırılara açık olduğunu belirleme
nmap --script=auth target.com

# SSL protokolünün güvenliğini test etme
nmap --script=ssl-cert target.com

# Belirli bir güvenlik açığını test etme
nmap --script=http-vuln-cve2017-5638 target.com

#### BRUTE FORCE TARAMALARI
# SSH brute-force
nmap --script=ssh-brute target.com

# FTP brute-force
nmap --script=ftp-brute target.com

# MySQL brute-force
nmap --script=mysql-brute target.com

# SNMP brute-force
nmap --script=snmp-brute target.com

# RDP brute-force
nmap --script=rdp-brute target.com

#### WEB SERVİS TARAMALARI
# HTTP başlıklarını ve bilgiler toplama
nmap --script=http-headers target.com

# HTTP servis versiyonu öğrenme
nmap --script=http-server-header target.com

# Web sitesindeki dizinleri keşfetme
nmap --script=http-enum target.com

# Web uygulamalarındaki potansiyel güvenlik açıklarını belirleme
nmap --script=http-vuln* target.com

# SSL/TLS güvenlik analizleri yapma
nmap --script=ssl-enum-ciphers target.com

#### BANNER GRABBING (Servislerin Banner Bilgilerini Alma)
# FTP banner grabbing
nmap --script=ftp-banner target.com

# SMTP banner grabbing
nmap --script=smtp-banner target.com

# HTTP server bilgisi alma
nmap --script=http-title target.com

# SNMP bilgilerini toplama
nmap --script=snmp-info target.com

# DOSYA ÇIKTISI VE LOG KAYDI

# Taramayı kaydetme (XML, normal, grepable format)
nmap -oA scan_output target.com

# Taramayı sadece XML formatında kaydetme
nmap -oX scan.xml target.com

# Taramayı sadece düz metin formatında kaydetme
nmap -oN scan.txt target.com

# Taramayı grepable formatta kaydetme
nmap -oG scan.gnmap target.com

#### ZAMANLAYICI SEÇENEKLERİ (PERFORMANCE OPTIONS)
# En hızlı tarama modu (dikkatli kullanılmalı)
nmap -T5 target.com

# Daha yavaş ancak güvenlik duvarlarını atlamak için kullanılabilir
nmap -T1 target.com

# Orta seviye hız
nmap -T3 target.com

# Firewall atlatmak için düşük hız
nmap --max-rate 10 target.com

#### ÖZEL PAKET VE FARKLI PORTLAR İLE ANALİZ
# Belirli bir kaynak port ile tarama
nmap --source-port 53 target.com

# Tüm TCP bayraklarını belirleme
nmap --scanflags SYNFINACK target.com

# NMAP SCRIPT ENGINE (NSE) KULLANIMI

# Tüm scriptleri listeleme
nmap --script-help=*

# Hedefteki SQL injection açıklarını tarama
nmap --script=http-sql-injection target.com

# Açık veritabanlarını bulma
nmap --script=mysql-empty-password target.com

# FTP anonim erişimini test etme
nmap --script=ftp-anon target.com
