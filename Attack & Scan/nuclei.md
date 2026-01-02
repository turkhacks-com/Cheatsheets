### Turkhacks.com | Bug researchers team
#### GitHub: https://github.com/turkhacks-com
#### Nuclei GitHub: https://github.com/projectdiscovery/nuclei

#### Nedir:
Nuclei, web uygulamaları, ağ servisleri ve altyapılar üzerinde otomatik zafiyet taraması yapmak için kullanılan, YAML tabanlı template sistemiyle çalışan hızlı ve özelleştirilebilir bir güvenlik tarama aracıdır.

---

## NUCLEI CHEAT SHEET (Güncel ve Pratik)

---

## TEMEL KULLANIM

#### Tek hedef tarama
`echo https://target.com | nuclei -t cves/`

#### Hedef listesini dosyadan oku
`nuclei -l targets.txt -t cves/`

#### Belirli bir template ile tarama
`echo https://target.com | nuclei -t vulnerabilities/wordpress/wp-file-manager.yaml`

#### Template klasörü ile tarama
`echo https://target.com | nuclei -t vulnerabilities/`

#### Tüm yerel template’leri kullan
`echo https://target.com | nuclei -t ~/nuclei-templates/`

---

## TEMPLATE FİLTRELEME

#### Kategoriye göre tarama
`echo https://target.com | nuclei -t cves/`  
`echo https://target.com | nuclei -t misconfiguration/`  
`echo https://target.com | nuclei -t exposures/`

#### Severity (önem düzeyi) filtreleme
`echo https://target.com | nuclei -t cves/ -severity critical,high`

#### Tag ile filtreleme
`echo https://target.com | nuclei -tags cve,wordpress`

#### Belirli CVE ID
`echo https://target.com | nuclei -id CVE-2021-26855`

---

## ÇIKTI VE FORMAT

#### Çıktıyı dosyaya yaz
`nuclei -l targets.txt -t cves/ -o output.txt`

#### JSON formatında çıktı
`nuclei -l targets.txt -t cves/ -json -o output.json`

#### Sessiz mod
`nuclei -l targets.txt -t cves/ -silent`

#### Renkli çıktıyı kapat
`nuclei -l targets.txt -t cves/ -nc`

#### Hata bastırma
`nuclei -l targets.txt -t cves/ -silent -es info,error`

---

## PROXY, HIZ VE THREAD

#### Proxy ile tarama
`echo https://target.com | nuclei -t cves/ -proxy http://127.0.0.1:8080`

#### Rate limit
`nuclei -l targets.txt -t cves/ -rate-limit 50`

#### Thread sayısı
`nuclei -l targets.txt -t cves/ -c 100`

#### Burp Suite proxy + custom UA
`nuclei -l targets.txt -t cves/ -proxy http://127.0.0.1:8080 -H "User-Agent: custom-agent"`

---

## OOB / INTERACTSH

#### OOB zafiyetleri için Interactsh
`echo https://target.com | nuclei -t dns/ -interactsh-url https://interact.sh`

---

## TEMPLATE YÖNETİMİ

#### Template güncelle
`nuclei -update-templates`

#### Template dizinini göster
`nuclei -update -ut`

---

## HIZLI KRİTİK TARAMA

#### Kritik & yüksek seviyeli zafiyetleri tara
`nuclei -l targets.txt -t cves/ -severity critical,high -silent -o criticals.txt`

---

## ÖRNEK SCANNING

`echo http://testphp.vulnweb.com/ | nuclei -t ~/nuclei-templates/ -o vulnweb_genel.txt`  
`echo http://testphp.vulnweb.com/ | nuclei -t cves/ -o vulnweb_cves.txt`  
`echo http://testphp.vulnweb.com/ | nuclei -t technologies/ -o vulnweb_techs.txt`  
`echo http://testphp.vulnweb.com/ | nuclei -tags sqli,xss,lfi,rce -severity critical,high -o vulnweb_critical.txt`  
`echo http://testphp.vulnweb.com/ | nuclei -tags xss -o vulnweb_xss.txt`  
`echo http://testphp.vulnweb.com/ | nuclei -t ~/nuclei-templates/ -silent -nc -o final.txt`
