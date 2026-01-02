# Temel subdomain keşfi
subfinder -d target.com

# Belirli bir domainin alt alanlarını bulma
subfinder -d target.com -o subdomains.txt

# Güvenlik tarama listesi kullanarak subdomain keşfi
subfinder -d target.com -w /path/to/subdomain_wordlist.txt

# Subfinder ile çoklu domain taraması
subfinder -d target1.com -d target2.com -o subdomains.txt

# Subdomain taraması yaparken DNS çözümleyici kullanma
subfinder -d target.com -r 8.8.8.8 -o subdomains.txt

# DNS kaynaklarını kullanarak subdomain bulma
subfinder -d target.com -sf /path/to/active_subdomains.txt -o final_subdomains.txt
