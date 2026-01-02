#     POST-EXPLOITATION & PRIVILEGE ESCALATION RESOURCES
### Turkhacks.com | Bug Researchers Team

---

## Reverse Shell & Payload Methodology

### PayloadsAllTheThings – Reverse Shell Cheatsheet  
https://github.com/swisskyrepo/PayloadsAllTheThings

**Ne işe yarar:**  
PayloadsAllTheThings, sızma testlerinde kullanılan payload metodolojilerini, bypass tekniklerini ve post-exploitation yaklaşımlarını derleyen dünyanın en büyük açık kaynak koleksiyonudur.  
Reverse shell cheatsheet bölümü, farklı dil ve ortamlarda bağlantı kurma mantığını, kısıtlı shell ortamlarında hareket kabiliyetini ve bağlantı sürekliliği konularını metodolojik olarak açıklar.

**Kullanım aşaması:**  
İlk erişim (initial foothold) elde edildikten sonra **kontrolün stabilize edilmesi**, kabuk yeteneklerinin genişletilmesi ve kısıtlı ortamlarda kalıcılık sağlamak için referans kaynağı olarak kullanılır.

---

## Linux Privilege Escalation & Local Enumeration Araçları

---

### linPEAS  
https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS  

**Ne işe yarar:**  
Linux sistemlerde otomatik **zayıf yapılandırma**, yanlış izinler, SUID dosyaları, cron job açıkları, kernel zafiyetleri ve credential leak’leri tespit eden tam otomatik enumeration aracıdır.

**Ne zaman kullanılır:**  
Sisteme giriş sağlandıktan sonra **ilk çalıştırılması gereken araçtır**. Saniyeler içinde saldırı yüzeyini çıkartır.

---

### LinEnum  
https://github.com/rebootuser/LinEnum  

**Ne işe yarar:**  
Manuel analiz odaklıdır. Sistem kullanıcıları, sudo yetkileri, servisler, dosya izinleri ve potansiyel yükseltme yollarını listeler.

**Ne zaman kullanılır:**  
linPEAS sonrası, elde edilen çıktının **manuel doğrulanması ve derinleştirilmesi** için idealdir.

---

### Linux Exploit Suggester (LES)  
https://github.com/mzet-/linux-exploit-suggester  
https://github.com/The-Z-Labs/linux-exploit-suggester  
https://github.com/jondonas/linux-exploit-suggester-2  

**Ne işe yarar:**  
Çalışan kernel sürümüne göre **bilinen privilege escalation zafiyetlerini** ve potansiyel exploit adaylarını listeler.

**Ne zaman kullanılır:**  
Kernel bazlı bir yükseltme yolu aranıyorsa kullanılır.

---

### Linux Smart Enumeration (lse)  
https://github.com/diego-treitos/linux-smart-enumeration  

**Ne işe yarar:**  
Gürültüsüz ve “smart” modda çalışarak, sistemde gerçekten kritik olan bulguları öne çıkarır.

**Ne zaman kullanılır:**  
CTF ve gerçek sızma testlerinde, zaman verimli analiz için.

---

### Linux Priv Checker  
https://github.com/linted/linuxprivchecker  

**Ne işe yarar:**  
Klasik privilege escalation kontrollerinin otomatik bir derlemesidir. Eski sistemlerde hâlâ çok etkilidir.

---

### PEASS-ng (Framework)  
https://github.com/carlospolop/PEASS-ng  

**Ne işe yarar:**  
linPEAS, winPEAS, macPEAS ve diğer tüm PEAS araçlarını kapsayan ana framework’tür.  
Kurumsal red team / bug bounty zincirlerinde **standart haline gelmiştir**.

---

## GTFOBins  
https://gtfobins.github.io/

**Ne işe yarar:**  
Linux sistemlerde bulunan **standart binary’lerin nasıl yetki yükseltme, dosya okuma/yazma, komut çalıştırma veya sandbox kaçışı için kullanılabileceğini** belgeleyen bir referans deposudur.

**Neden kritiktir:**  
Bir sistemde exploit yoksa bile, yanlış yetkilendirilmiş “normal” programlar üzerinden tam yetki kazanılmasını sağlar.

---

## Recon → Exploit → PrivEsc Zinciri

Standart operasyon zinciri:

```
subfinder → httpx → nuclei → initial foothold
→ linPEAS → GTFOBins → exploit suggester → root
```

Bu kaynakların tamamı bu zincirin **post-exploitation ve privilege escalation katmanını** oluşturur.

---

Bu koleksiyon, senin hazırladığın cheatsheet arşivinin **en kritik katmanı**dır.  
Sonraki adım olarak istersen bu set için ayrıca:

- “CTF hızlı yükseltme akış şeması”
- “Real-world bug bounty privilege escalation playbook”
hazırlayabiliriz.
