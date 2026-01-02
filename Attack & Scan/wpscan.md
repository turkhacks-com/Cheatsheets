# Basit bir WordPress site taraması yap
wpscan --url https://example.com

# Kullanıcı adlarını enumerate et (author id ve API yoluyla)
wpscan --url https://example.com -e u

# Tüm kullanıcıları, eklentileri, temaları enumerate et
wpscan --url https://example.com -e at,ap,u

# Zayıf şifre brute force denemesi yap
wpscan --url https://example.com -U usernames.txt --passwords /path/to/wordlist.txt

# Tek bir kullanıcıya brute force saldırısı
wpscan --url https://example.com -U admin --passwords /path/to/wordlist.txt

# Proxy kullanarak tarama yap
wpscan --url https://example.com --proxy socks5://127.0.0.1:9050

# Tarama sonuçlarını dosyaya kaydet
wpscan --url https://example.com -o output.txt

# API Token ile WPScan Vulnerability Database kullan
wpscan --url https://example.com --api-token YOUR_TOKEN_HERE

# User-Agent değiştirmek
wpscan --url https://example.com --random-user-agent

# SSL sertifikasını yok sayarak tarama yap
wpscan --url https://example.com --disable-tls-checks

# HTTP Basic Auth kullanarak giriş yaparak tarama yap
wpscan --url https://example.com --basic-auth user:password

# Belirli bir eklentiyi test et
wpscan --url https://example.com --plugins-detection mixed

# Daha ayrıntılı çıktı almak için verbose
wpscan --url https://example.com --verbose

# Timeout süresini ayarla
wpscan --url https://example.com --request-timeout 30
