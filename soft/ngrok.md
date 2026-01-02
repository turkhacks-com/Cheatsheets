# HTTP servisini 8080 portundan tünelle
ngrok http 8080

# Belirli bir alt alan adıyla HTTP tünel aç (ücretli hesap gerekir)
ngrok http -subdomain=mycustomsub 8080

# HTTPS servisini 443 portundan tünelle
ngrok http https://localhost:443

# TCP servisini tünelle (ör. SSH için 22. port)
ngrok tcp 22

# Belirli bir protokol ve port ile TCP tüneli aç
ngrok tcp 3306

# Yapılandırma dosyasını kullanarak tünel başlat
ngrok start --config ~/.ngrok2/ngrok.yml mytunnel

# Bölge seçerek tünel aç (ör. Avrupa)
ngrok http -region=eu 8080

# Auth token ekleyerek kimlik doğrula (ilk kez kurulum için)
ngrok authtoken YOUR_AUTH_TOKEN

# Tüm aktif tünelleri listeler
ngrok tunnels

# Tünel trafiğini incelemek için web arayüzünü kullan (varsayılan: http://127.0.0.1:4040)
# (Ayrı komut değil, bilgilendirme)

# HTTP Basic Auth korumalı tünel aç
ngrok http -auth="user:password" 8080

# HTTP başlığını yeniden yaz
ngrok http -host-header=rewrite 8080

# Tünel oturumunu log dosyasına kaydet
ngrok http 8080 --log=stdout > ngrok.log

# Kendi konfig dosyanı belirt
ngrok http --config /path/to/ngrok.yml 8080
