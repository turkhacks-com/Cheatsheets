### Turkhacks.com | Bug researchers team
#### Source: https://gtfobins.github.io/

---

## LINUX PRIVILEGE ESCALATION

---

## 1. SUID ve SGID Bitleri Ayarlı Dosyaları Bulma

`find / -type f -perm -04000 -ls 2>/dev/null`  
SUID bit ayarlı dosyaları listele

`find / -type f -perm -02000 -ls 2>/dev/null`  
SGID bit ayarlı dosyaları listele

`find / -type f -perm -4000 -o -perm -2000 -ls 2>/dev/null`  
SUID veya SGID bit ayarlı dosyaları listele

**Açıklama:**  
SUID ve SGID bitleri, dosyaların sahibi veya grubu gibi çalıştırılmasını sağlar.  
Bu tür dosyalar privilege escalation için kullanılabilir.

---

## 2. Root Olarak Çalıştırılabilen Dosyalar

`sudo -l`  
Kullanıcının çalıştırabileceği sudo yetkili komutları listele

**Açıklama:**  
Eğer bir komutu sudo ile parola girmeden çalıştırabiliyorsan, o komut üzerinden root yetkisi alabilirsin.

---

## 3. Kullanıcı ve Grup Bilgileri

`id`  
Mevcut kullanıcı ID ve grup bilgileri

`whoami`  
Aktif kullanıcı

`groups`  
Kullanıcının ait olduğu gruplar

**Açıklama:**  
Kullanıcı grupları ve yetkileri privilege escalation için önemli ipuçları içerebilir.

---

## 4. Cron Job Kontrolü

`ls -la /etc/cron*`  
Cron jobları listele

`cat /etc/crontab`  
Zamanlanmış görevleri incele

**Açıklama:**  
Root tarafından çalıştırılan ve kötü yapılandırılmış cron görevleri exploit edilebilir.

---

## 5. Shell Erişimi Olan Kullanıcılar

`cat /etc/passwd | grep -v "nologin\|false"`

**Açıklama:**  
Root veya yüksek yetkili kullanıcıların shell erişimi olup olmadığını kontrol edebilirsin.

---

## 6. SSH Anahtarlarını Bulma

`find / -name "*.pem" 2>/dev/null`  
`find / -name "*.pub" 2>/dev/null`  
`find / -name "id_rsa" 2>/dev/null`

**Açıklama:**  
SSH anahtarları, başka hesaplara erişim sağlamak için kullanılabilir.

---

## 7. Yazılabilir Dizinleri Bulma

`find / -writable -type d 2>/dev/null`

**Açıklama:**  
Eğer önemli sistem dizinlerine yazma iznin varsa, privilege escalation için kullanılabilir.

---

## 8. Setcap Yetkili Dosyalar

`getcap -r / 2>/dev/null`

**Açıklama:**  
cap_setuid, cap_net_bind_service gibi yetkiler root yetkisi almak için kullanılabilir.

---

## 9. Çalışan Süreçleri Görüntüleme

`ps aux`  
`ps aux | grep root`

**Açıklama:**  
Açık bırakılan yetkili servisler privilege escalation için kullanılabilir.

---

## 10. Kernel ve Dağıtım Bilgileri

`uname -a`  
`cat /etc/os-release`

**Açıklama:**  
Kernel ve sistem sürümü, exploit edilebilir zafiyetler için ipucu verir.

---

## 11. Linux Exploit Suggester

`wget https://raw.githubusercontent.com/jondonas/linux-exploit-suggester-2/master/linux-exploit-suggester-2.pl`  
`chmod +x linux-exploit-suggester-2.pl`  
`perl linux-exploit-suggester-2.pl`

**Açıklama:**  
Sistemde çalışabilecek kernel exploitlerini otomatik listeler.

---

## 12. LinPEAS

`wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh`  
`chmod +x linpeas.sh`  
`./linpeas.sh`

**Açıklama:**  
LinPEAS, sistemdeki privilege escalation yollarını otomatik analiz eder.

---

## SONUÇ

Yukarıdaki komutlar Linux sistemlerde yetki yükseltme vektörlerini analiz etmek için kullanılır.  
Etik hacking ve güvenlik araştırmaları kapsamında kullanılmalıdır.
