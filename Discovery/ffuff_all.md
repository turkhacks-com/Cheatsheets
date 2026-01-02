# 1. Basit bir dizin taraması (Wordlist ile)
ffuf -u https://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt

# 2. Parametre fuzzing (GET isteğinde parametre adı deneme)
ffuf -u "https://example.com/index.php?FUZZ=1" -w /usr/share/wordlists/params.txt

# 3. POST isteği ile fuzzing
ffuf -u "https://example.com/login" -X POST -d "username=admin&password=FUZZ" -w /usr/share/wordlists/rockyou.txt

# 4. Birden fazla parametreyi aynı anda fuzz etmek
ffuf -u "https://example.com/index.php?FUZZ=FUZZ2" -w /usr/share/wordlists/params.txt:/usr/share/wordlists/values.txt

# 5. Özel başlık (header) ekleyerek fuzzing
ffuf -u "https://example.com/FUZZ" -H "User-Agent: Mozilla" -w /usr/share/wordlists/dirb/common.txt

# 6. HTTP yanıt kodlarına göre filtreleme (Sadece 200 yanıtları göster)
ffuf -u https://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt -mc 200

# 7. WAF bypass için büyük-küçük harf denemesi
ffuf -u "https://example.com/FuZz" -w /usr/share/wordlists/dirb/common.txt -mc 200

# 8. Alt domain fuzzing (VHost bulma)
ffuf -u "https://FUZZ.example.com" -w /usr/share/wordlists/subdomains.txt -H "Host: FUZZ.example.com"
ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -u http://nahamstore.thm/ -H "Host: FUZZ.nahamstore.thm" -fw 125 

# 9. Sonuçları bir dosyaya kaydetme (JSON formatında)
ffuf -u https://example.com/FUZZ -w /usr/share/wordlists/dirb/common.txt -o results.json -of json


