# Temel Kullanım - Bir Parolayı Çözme
john --wordlist=/path/to/wordlist.txt --format=raw-md5 hashfile.txt

# Hedef Hash Formatı Belirleme - MD5
john --format=raw-md5 --wordlist=/path/to/wordlist.txt hashfile.txt

# Hedef Hash Formatı Belirleme - SHA256
john --format=raw-sha256 --wordlist=/path/to/wordlist.txt hashfile.txt

# Hedef Hash Formatı Belirleme - NTLM
john --format=ntlm --wordlist=/path/to/wordlist.txt hashfile.txt

# Hedef Hash Formatı Belirleme - DES (Unix Shadow)
john --format=descrypt --wordlist=/path/to/wordlist.txt hashfile.txt

# Kullanıcıya Ait Hashleri Çözme (Unix Shadow)
john --format=shadow --wordlist=/path/to/wordlist.txt /etc/shadow

# Salt ile Parolayı Çözme
john --wordlist=/path/to/wordlist.txt --format=raw-md5 --salts hashfile.txt

# Salt'lı MD5 Hash Çözme
john --format=raw-md5 --wordlist=/path/to/wordlist.txt hashfile.txt --salts

# Hashlerin Çözülmüş Hallerini Görüntüleme
john --show hashfile.txt

# Çözülmüş Hashleri Dosyaya Kaydetme
john --show --format=raw-md5 hashfile.txt > cracked_passwords.txt

# Paralel Çalışma - Çok Çekirdekli Sistem Kullanımı
john --fork=4 --wordlist=/path/to/wordlist.txt hashfile.txt

# Düzenli Olarak Çözme Durumunu Görüntüleme
john --status

# Parola Dosyasını Karıştırma
john --wordlist=/path/to/wordlist.txt --rules --stdout

# Mask Kullanarak Parola Kırma (Örnek: Şifre 8 Karakter, Büyük/Küçük Harf, Sayı)
john --mask='?l?u?d?d?d?d?d?d' --min-length=8 --max-length=8 --wordlist=/path/to/wordlist.txt hashfile.txt

# Parola Dosyası İçindeki Tüm Hashleri Çözme
john --format=raw-md5 --wordlist=/path/to/wordlist.txt --test hashfile.txt

# Veritabanından Parola Çözümü İçin 'john' Çalıştırma
john --restore=session_name

# Mask Yöntemi ile Hedef Parolayı Çözme
john --mask='?l?l?l?l?d?d' --min-length=6 --max-length=6 --wordlist=/path/to/wordlist.txt hashfile.txt

# Parola Dosyasındaki Diğer Hash Formatlarını Tanımlama
john --list=formats

# Wordlist ile Birden Fazla Hash Dosyasını Çözme
john --wordlist=/path/to/wordlist.txt hashfile1.txt hashfile2.txt

# Salt ve Hash Formatı Otomatik Tanımlama
john --wordlist=/path/to/wordlist.txt --format=auto hashfile.txt

# ZIP Dosyasındaki Parolayı Çözme
john --format=zip --wordlist=/path/to/wordlist.txt zipfile.zip

# RAR Dosyasındaki Parolayı Çözme
john --format=rar --wordlist=/path/to/wordlist.txt rarfile.rar

# John ile Wordlist ve Kural Kullanımı
john --wordlist=/path/to/wordlist.txt --rules=Jumbo hashfile.txt

# Birden Fazla Wordlist Kullanma
john --wordlist=/path/to/wordlist1.txt --wordlist=/path/to/wordlist2.txt hashfile.txt

# Brute-Force ile Parola Çözme
john --incremental --format=raw-md5 hashfile.txt

# Potansiyel Hash Formatlarını Göstermek
john --list=formats | grep -i md5

# Hash Dosyasındaki Parola Çözme İşlemine Devam Etme
john --restore

# 'John' Çalışırken Parola Çözme Durumunu Gösterme
john --status

# 'John' Çalışırken Gelişmiş Deneme Yöntemlerini Gösterme
john --test=1 --wordlist=/path/to/wordlist.txt hashfile.txt

# Çözülen Parolaları 'John' Çalıştırma
john --show hashfile.txt

# Özel Kurallar Kullanarak Parola Kırma
john --wordlist=/path/to/wordlist.txt --rules=best64 hashfile.txt

# CTF: .htpasswd dosyasındaki parolayı çözme
john --format=crypt --wordlist=/path/to/wordlist.txt .htpasswd

# CTF: Web Application taraması sonucu ele geçirilen Base64 hash'in çözülmesi
john --format=base64 --wordlist=/path/to/wordlist.txt hashfile.txt

# CTF: SHA1 hashini çözme
john --format=raw-sha1 --wordlist=/path/to/wordlist.txt hashfile.txt

# Gerçek Dünya: SQL dump'dan alınan MD5 hashini çözme
john --format=raw-md5 --wordlist=/path/to/wordlist.txt sql_dump.txt

# Gerçek Dünya: Unix Shadow dosyasındaki şifreleri çözme
john --format=shadow --wordlist=/path/to/wordlist.txt /etc/shadow

# Gerçek Dünya: Şirket içi parola denemeleri için brute-force
john --incremental --format=ntlm --wordlist=/path/to/wordlist.txt target_hashes.txt

# John the Ripper ile parolaların hashlerini, şifreleri hızlıca çözme
john --wordlist=/path/to/wordlist.txt --rules --format=raw-md5 hashfile.txt

# Hash dosyasını batch mode ile çözme
john --batch --wordlist=/path/to/wordlist.txt hashfile.txt

# Salt'lı hash çözme
john --format=raw-md5 --wordlist=/path/to/wordlist.txt hashfile.txt --salts

# Çözülen hashleri belirli bir dosyaya kaydetme
john --show hashfile.txt > cracked_passwords.txt
