# Basit bir HTTP isteği yap
curl http://example.com

# HTTPS ile bir siteye istek yap
curl https://example.com

# Bir dosyayı indir
curl -O https://example.com/file.zip

# Dosyayı belirli bir adla kaydet
curl -o myfile.zip https://example.com/file.zip

# HTTP başlıklarını göster
curl -I https://example.com

# POST isteği gönder
curl -X POST -d "username=user&password=pass" https://example.com/login

# JSON veri ile POST isteği gönder
curl -X POST -H "Content-Type: application/json" -d '{"username":"user","password":"pass"}' https://example.com/api/login

# Bir API'ye kimlik doğrulama ile istek gönder
curl -u "kullanici:parola" https://example.com/api

# Cookie kullanarak istek yap
curl -b "sessionid=abcd1234" https://example.com/dashboard

# User-Agent değiştirerek istek yap
curl -A "Mozilla/5.0 (Windows NT 10.0; Win64; x64)" https://example.com

# Proxy üzerinden istek yap
curl -x http://proxyserver:port https://example.com

# Timeout belirleyerek istek yap
curl --max-time 10 https://example.com

# Yanıtı belirli bir dosyaya kaydet
curl -o response.html https://example.com

# Birden fazla URL'ye istek gönder
curl -O https://example.com/file1.zip -O https://example.com/file2.zip

# HTTP yanıt kodunu göster
curl -s -o /dev/null -w "%{http_code}" https://example.com

# Başlık (Header) ekleyerek istek yap
curl -H "Authorization: Bearer TOKEN" https://example.com/api

# FTP sunucusundan dosya indirme
curl -u "kullanici:parola" ftp://ftp.example.com/file.txt -o localfile.txt

