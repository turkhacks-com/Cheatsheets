#     JOHN THE RIPPER CHEATSHEET
### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com
#### John GitHub: https://github.com/openwall/john

---

## Nedir:
John the Ripper (JtR), hash’lenmiş parolaların **wordlist, rule, mask ve brute‑force** yöntemleriyle çözülmesini sağlayan endüstri standardı bir parola denetim (password auditing) motorudur. CTF, red‑team ve gerçek dünya parola güvenliği testlerinde temel araçtır.

---

## ## TEMEL KULLANIM

#### Basit parola çözme
```bash
john --wordlist=/path/to/wordlist.txt --format=raw-md5 hashfile.txt
```

#### Otomatik hash formatı tanıma
```bash
john --wordlist=/path/to/wordlist.txt --format=auto hashfile.txt
```

#### Çözülmüş parolaları görüntüleme
```bash
john --show hashfile.txt
```

---

## ## HASH FORMATLARI

#### MD5
```bash
john --format=raw-md5 --wordlist=/path/to/wordlist.txt hashfile.txt
```

#### SHA1 / SHA256
```bash
john --format=raw-sha1   --wordlist=/path/to/wordlist.txt hashfile.txt
john --format=raw-sha256 --wordlist=/path/to/wordlist.txt hashfile.txt
```

#### NTLM (Windows)
```bash
john --format=ntlm --wordlist=/path/to/wordlist.txt hashfile.txt
```

#### Unix Shadow / DES
```bash
john --format=shadow    --wordlist=/path/to/wordlist.txt /etc/shadow
john --format=descrypt --wordlist=/path/to/wordlist.txt hashfile.txt
```

---

## ## SALT / KURAL / MASKE

#### Salt’lı hash çözme
```bash
john --format=raw-md5 --wordlist=/path/to/wordlist.txt hashfile.txt --salts
```

#### Rule kullanımı
```bash
john --wordlist=/path/to/wordlist.txt --rules=best64 hashfile.txt
john --wordlist=/path/to/wordlist.txt --rules=Jumbo  hashfile.txt
```

#### Mask brute‑force
```bash
john --mask='?l?u?d?d?d?d?d?d' --min-length=8 --max-length=8 hashfile.txt
john --mask='?l?l?l?l?d?d' --min-length=6 --max-length=6 hashfile.txt
```

---

## ## PERFORMANS / OTURUM

#### Çok çekirdekli çalışma
```bash
john --fork=4 --wordlist=/path/to/wordlist.txt hashfile.txt
```

#### Durum kontrolü
```bash
john --status
```

#### Kaldığı yerden devam
```bash
john --restore
```

---

## ## DOSYA & ÇIKTI

#### Çözülenleri dosyaya kaydet
```bash
john --show hashfile.txt > cracked_passwords.txt
```

#### Tüm desteklenen formatları listele
```bash
john --list=formats
```

---

## ## ARŞİV / CTF / GERÇEK DÜNYA

#### ZIP / RAR parola çözme
```bash
john --format=zip --wordlist=/path/to/wordlist.txt zipfile.zip
john --format=rar --wordlist=/path/to/wordlist.txt rarfile.rar
```

#### .htpasswd
```bash
john --format=crypt --wordlist=/path/to/wordlist.txt .htpasswd
```

#### SQL dump MD5
```bash
john --format=raw-md5 --wordlist=/path/to/wordlist.txt sql_dump.txt
```

#### Windows NTLM brute‑force
```bash
john --incremental --format=ntlm target_hashes.txt
```

---

## İpuçları

- İlk deneme her zaman **wordlist + rules** ile yapılmalıdır  
- Sonra **mask brute‑force**, en sonda **incremental** önerilir  
- cracked çıktıları nuclei / hydra zincirine feed edilebilir  

---
