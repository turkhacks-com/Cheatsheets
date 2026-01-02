### Turkhacks.com | Bug Researchers Team  
#### GitHub: https://github.com/turkhacks-com  
#### WPScan GitHub: https://github.com/wpscanteam/wpscan  

#### Nedir:
WPScan, WordPress tabanlı web sitelerinde kullanılan çekirdek sürüm, tema, eklenti ve kullanıcı yapılarını analiz ederek bilinen güvenlik açıklarını tespit etmeye yarayan profesyonel bir WordPress güvenlik tarama aracıdır. Resmi vulnerability veritabanı ile çalışır ve yetkili sızma testlerinde yaygın olarak kullanılır.

---

## Basit WordPress Tarama İşlemleri

#### Basit bir WordPress site taraması yap
```bash
wpscan --url https://example.com
```

#### Kullanıcı adlarını enumerate et (author id ve API yoluyla)
```bash
wpscan --url https://example.com -e u
```

#### Tüm kullanıcıları, eklentileri, temaları enumerate et
```bash
wpscan --url https://example.com -e at,ap,u
```

---

## Brute Force Testleri (Yetkili sistemlerde)

#### Zayıf şifre brute force denemesi yap
```bash
wpscan --url https://example.com -U usernames.txt --passwords /path/to/wordlist.txt
```

#### Tek bir kullanıcıya brute force saldırısı
```bash
wpscan --url https://example.com -U admin --passwords /path/to/wordlist.txt
```

---

## Proxy ve Kimlik Doğrulama

#### Proxy kullanarak tarama yap
```bash
wpscan --url https://example.com --proxy socks5://127.0.0.1:9050
```

#### HTTP Basic Auth kullanarak giriş yaparak tarama yap
```bash
wpscan --url https://example.com --basic-auth user:password
```

---

## Çıktı ve API Kullanımı

#### Tarama sonuçlarını dosyaya kaydet
```bash
wpscan --url https://example.com -o output.txt
```

#### API Token ile WPScan Vulnerability Database kullan
```bash
wpscan --url https://example.com --api-token YOUR_TOKEN_HERE
```

---

## Gelişmiş Ayarlar

#### User-Agent değiştirmek
```bash
wpscan --url https://example.com --random-user-agent
```

#### SSL sertifikasını yok sayarak tarama yap
```bash
wpscan --url https://example.com --disable-tls-checks
```

#### Belirli bir eklentiyi test et
```bash
wpscan --url https://example.com --plugins-detection mixed
```

#### Daha ayrıntılı çıktı almak için verbose
```bash
wpscan --url https://example.com --verbose
```

#### Timeout süresini ayarla
```bash
wpscan --url https://example.com --request-timeout 30
```
