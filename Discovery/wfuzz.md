#### WFuzz, HTTP parametrelerini brute force yaparak zafiyetleri keşfetmeye yarayan güçlü bir araçtır.
# Basit parametre brute force
wfuzz -c -z file,/path/to/wordlist.txt --hc 404 http://target.com/FUZZ

# Hedef URL'ye POST isteği göndererek parametreleri brute force
wfuzz -c -z file,/path/to/wordlist.txt --hc 404 -X POST -d "username=admin&password=FUZZ" http://target.com/login

# Hedef URL'ye belirli bir parametre ile brute force (örneğin, "FUZZ" ile değiştirilecek)
wfuzz -c -z file,/path/to/wordlist.txt --hc 404 http://target.com/page.php?id=FUZZ

# Belirli bir parametre üzerinden brute force
wfuzz -c -z file,/path/to/wordlist.txt http://target.com/search?query=FUZZ

# URL'deki belirli bir parametreyi test etme
wfuzz -c -z file,/path/to/wordlist.txt -u "http://target.com/page?file=FUZZ.html"

# HTTP header'larını brute force etme
wfuzz -c -z file,/path/to/wordlist.txt --header "X-Custom-Header: FUZZ" http://target.com

# Verbose (detaylı) çıktılarla parametreleri test etme
wfuzz -c -v -z file,/path/to/wordlist.txt http://target.com/FUZZ
