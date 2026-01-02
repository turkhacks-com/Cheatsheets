# Temel dizin taraması
gobuster dir -u http://target.com -w /path/to/wordlist.txt

# HTTP protokolü kullanarak dizin taraması
gobuster dir -u http://target.com -w /path/to/wordlist.txt -t 50

# HTTPS ile dizin taraması
gobuster dir -u https://target.com -w /path/to/wordlist.txt

# Subdomain taraması
gobuster dns -d target.com -w /path/to/subdomain_wordlist.txt

# Subdomain taraması DNS ZONE transferi yaparak
gobuster dns -d target.com -w /path/to/subdomain_wordlist.txt -t 50 --dns-resolver 8.8.8.8

# URL listesi ile dizin taraması
gobuster dir -u http://target.com -w urls.txt

# Hedefteki dizinler için URL ve HTTP yanıt kodlarını gösterme
gobuster dir -u http://target.com -w /path/to/wordlist.txt -x .php,.html -o output.txt
