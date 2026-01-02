### Turkhacks.com | Bug researchers team
#### GitHub: https://github.com/turkhacks-com
#### Hydra GitHub: https://github.com/vanhauser-thc/thc-hydra

#### Nedir:
Hydra, ağ servisleri üzerinde kimlik doğrulama mekanizmalarını test etmek için kullanılan çok protokollü bir parola deneme (password auditing / brute-force test) aracıdır. Zayıf parolaları ve yanlış yapılandırılmış giriş servislerini tespit etmeye yarar.

---

#### HTTP POST metoduyla şifre denemesi yap
`hydra -l admin -P /path/to/wordlist.txt http://example.com/login POST /login.php username=^USER^&password=^PASS^`

#### SSH servisi üzerinden brute force denemesi yap
`hydra -l root -P /path/to/wordlist.txt ssh://example.com`

#### FTP servisi üzerinden brute force denemesi yap
`hydra -l user -P /path/to/wordlist.txt ftp://example.com`

#### Birden fazla hedefe aynı anda saldırı yap
`hydra -L users.txt -P /path/to/wordlist.txt ssh://target1.com ssh://target2.com`

#### HTTP Auth ile saldırı
`hydra -l admin -P /path/to/wordlist.txt http-get://example.com/protected_page/`

#### Wordlist ile HTTP Basic Authentication brute force saldırısı
`hydra -l admin -P /path/to/wordlist.txt -s 80 -vV example.com http-get`

#### Telnet servisinde brute-force şifre denemesi yap
`hydra -l admin -P /path/to/wordlist.txt telnet://example.com`

#### HTTPS servisi üzerinden brute force denemesi
`hydra -l admin -P /path/to/wordlist.txt https://example.com`

#### Hedef üzerinde şifre denemesi için proxy kullan
`hydra -l admin -P /path/to/wordlist.txt -s 443 -vV https://example.com -p proxy_ip:proxy_port`

#### JSON Web Token (JWT) brute force saldırısı yap
`hydra -l admin -P /path/to/wordlist.txt -s 443 -vV https://example.com/api/login -json`
