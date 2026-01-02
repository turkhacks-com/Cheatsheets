# 1. Basit bir alt domain taraması
amass enum -d example.com

# 2. Pasif bilgi toplama (Sadece veritabanlarından bilgi çeker)
amass enum -passive -d example.com

# 3. Aktif tarama (DNS çözümlerini de kullanır)
amass enum -active -d example.com

# 4. Belirli kaynakları kullanarak tarama yapma (Virustotal, Sublist3r vb.)
amass enum -d example.com -src

# 5. Whois ve IP aralıklarını gösterme
amass intel -whois -d example.com

# 6. Alt domainleri belirli bir IP aralığına göre bulma
amass intel -addr 192.168.1.0/24

# 7. Tespit edilen alt domainleri bir dosyaya kaydetme
amass enum -d example.com -o subdomains.txt

# 8. Birden fazla domaini aynı anda tarama
amass enum -df domains.txt

# 9. Ağ haritası oluşturma (Aktif keşif ve bilgi toplama)
amass map -d example.com

# 10. Proxy üzerinden tarama yapma (Tor veya Burp Suite üzerinden yönlendirme)
amass enum -proxy socks5://127.0.0.1:9050 -d example.com

