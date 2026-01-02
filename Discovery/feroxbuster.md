#### Feroxbuster, hızlı ve verimli bir dirbusting aracıdır. Büyük veri kümeleriyle çalışırken daha hızlıdır.
# Basit dizin taraması
feroxbuster -u http://target.com -w /path/to/wordlist.txt

# HTTP üzerinden dizin taraması
feroxbuster -u http://target.com -w /path/to/wordlist.txt -t 50

# HTTPS üzerinden dizin taraması
feroxbuster -u https://target.com -w /path/to/wordlist.txt

# Belirli bir dosya uzantısı ile dizin taraması
feroxbuster -u http://target.com -w /path/to/wordlist.txt -x .php,.html

# HTTP yanıt kodları ile tarama yapma
feroxbuster -u http://target.com -w /path/to/wordlist.txt -s 200
  
# Paralel istek yaparak taramayı hızlandırma
feroxbuster -u http://target.com -w /path/to/wordlist.txt -t 100

# Farklı HTTP metodlarını test etme (GET, POST)
feroxbuster -u http://target.com -w /path/to/wordlist.txt -X POST

# Otomatik HTTP header'ları ile tarama
feroxbuster -u http://target.com -w /path/to/wordlist.txt -H "X-Forwarded-For: 127.0.0.1"

#Example usage
feroxbuster -u http://10.10.112.88/ -w /usr/share/wordlists/dirb/big.txt --scan-dir-listings -t 100
