# HTTPX Cheat Sheet (Güncel ve Pratik)

# Tek hedef tarama
echo target.com | httpx

# Birden fazla hedef stdin ile
echo -e "target.com\nexample.com" | httpx

# Hedef listesini dosyadan oku
httpx -l targets.txt

# Belirli portları tara
echo target.com | httpx -p 80,443,8080

# Her hedefe belirli bir path ekle
echo target.com | httpx -path /robots.txt

# Birden fazla path kullan (dosyadan)
echo target.com | httpx -path paths.txt

# Durum kodunu göster
echo target.com | httpx -sc

# Sayfa başlığını göster
echo target.com | httpx -title

# İçerik uzunluğunu göster
echo target.com | httpx -cl

# Web sunucusu bilgisini göster
echo target.com | httpx -server

# Teknoloji tespiti yap
echo target.com | httpx -td

# IP adresini göster
echo target.com | httpx -ip

# CNAME kaydını göster
echo target.com | httpx -cname

# ASN bilgisi göster
echo target.com | httpx -asn

# Durum koduna göre filtrele (sadece 200 göster)
echo target.com | httpx -sc -mc 200

# Belirli durum kodlarını gizle (örnek: 404)
echo target.com | httpx -sc -fc 404

# Yanıt içeriğinde belirli string eşleşmesi
echo target.com | httpx -ms "admin"

# Yanıt içeriğinde belirli string filtreleme
echo target.com | httpx -fs "Not Found"

# Sessiz mod (sadece sonuç URL'leri)
echo target.com | httpx -silent

# Çıktıyı dosyaya yaz
httpx -l targets.txt -silent -o canli_hostlar.txt

# JSON formatında çıktı al
echo target.com | httpx -sc -title -json -o info.json

# CSV formatında çıktı al
httpx -l targets.txt -sc -title -csv -o rapor.csv

# Renkli çıktıyı kapat
echo target.com | httpx -nc

# Özel HTTP başlığı ekle
echo target.com | httpx -H "Referer: test.com" -H "X-Custom: 123"

# HTTP yönlendirmeleri takip et
echo http://target.com | httpx -fr -sc -title

# Proxy ile çalıştır
echo target.com | httpx -proxy http://127.0.0.1:8080

# Thread sayısını belirle
httpx -l targets.txt -t 100 -silent

# Saniyede gönderilecek istek sayısını sınırla
httpx -l targets.txt -rl 30 -silent

# Sabit User-Agent kullan (rastgeleyi devre dışı bırakmanın yolu)
echo target.com | httpx -H "User-Agent: MyScanner/1.0"
