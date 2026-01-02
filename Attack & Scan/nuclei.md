# Nuclei Cheat Sheet (Güncel ve Pratik)

# Tek hedef tarama
echo https://target.com | nuclei -t cves/

# Hedef listesini dosyadan oku
nuclei -l targets.txt -t cves/

# Belirli bir template ile tarama (tek dosya)
echo https://target.com | nuclei -t vulnerabilities/wordpress/wp-file-manager.yaml

# Template klasörü ile tarama
echo https://target.com | nuclei -t vulnerabilities/

# Tüm yerel template'leri kullan
echo https://target.com | nuclei -t ~/nuclei-templates/

# Template kategorilerine göre tarama (cves, misconfig, exposures vs.)
echo https://target.com | nuclei -t cves/
echo https://target.com | nuclei -t misconfiguration/
echo https://target.com | nuclei -t exposures/

# Belirli bir severity (önem düzeyi) ile filtrele
echo https://target.com | nuclei -t cves/ -severity critical,high

# Etiket (tags) ile template filtreleme
echo https://target.com | nuclei -tags cve,wordpress

# Belirli bir CVE ID'si ile tarama
echo https://target.com | nuclei -id CVE-2021-26855

# Çıktıyı dosyaya yaz
nuclei -l targets.txt -t cves/ -o output.txt

# JSON formatında çıktı
nuclei -l targets.txt -t cves/ -json -o output.json

# Sessiz mod (sadece sonuçları gösterir)
nuclei -l targets.txt -t cves/ -silent

# Renkli çıktıyı kapat
nuclei -l targets.txt -t cves/ -nc

# Hataları gösterme (sessiz hata modu)
nuclei -l targets.txt -t cves/ -silent -es info,error

# Proxy ile tarama yap
echo https://target.com | nuclei -t cves/ -proxy http://127.0.0.1:8080

# Rate limit (saniyede istek sayısını sınırlama)
nuclei -l targets.txt -t cves/ -rate-limit 50

# Thread sayısını belirle
nuclei -l targets.txt -t cves/ -c 100

# Burp Suite proxy kullanımı için
nuclei -l targets.txt -t cves/ -proxy http://127.0.0.1:8080 -H "User-Agent: custom-agent"

# Interactsh destekli template’leri kullanmak için (OOB zafiyetleri)
echo https://target.com | nuclei -t dns/ -interactsh-url https://interact.sh

# Template güncelle
nuclei -update-templates

# Template dizini göster
nuclei -update -ut

# Özetle tüm hedefleri hızlıca tara ve sonuçları listele
nuclei -l targets.txt -t cves/ -severity critical,high -silent -o criticals.txt


# SCANNING 
echo http://testphp.vulnweb.com/ | nuclei -t ~/nuclei-templates/ -o vulnweb_genel.txt
echo http://testphp.vulnweb.com/ | nuclei -t cves/ -o vulnweb_cves.txt
echo http://testphp.vulnweb.com/ | nuclei -t technologies/ -o vulnweb_techs.txt
echo http://testphp.vulnweb.com/ | nuclei -tags sqli,xss,lfi,rce -severity critical,high -o vulnweb_critical.txt
echo http://testphp.vulnweb.com/ | nuclei -tags xss -o vulnweb_xss.txt
echo http://testphp.vulnweb.com/ | nuclei -t ~/nuclei-templates/ -silent -nc -o final.txt
