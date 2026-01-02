##################
#                #
#   XSS - GUIDE   #
#                #
##################

### Turkhacks.com | Bug Researchers Team
#### GitHub: https://github.com/turkhacks-com

---

## XSS Nedir
Cross-Site Scripting (XSS), kullanıcıdan alınan verinin filtrelenmeden HTML/JS bağlamına sokulmasıyla ortaya çıkan, tarayıcı tarafında kod çalıştırmaya kadar gidebilen bir zafiyettir.

---

## XSS Türleri

| Tür | Açıklama |
|----|---------|
| Reflected | Request ile gelir, response’ta döner |
| Stored | DB’ye kaydolur, herkese çalışır |
| DOM | JS tarafında oluşur |
| Blind | Sonuç görünmez, log veya admin panelinde patlar |

---

## Zayıf Olmaya Aday Noktalar

- Arama formları  
- Yorum alanları  
- Profil bilgileri  
- Header yansıtımı  
- Cookie / User-Agent yansımaları  
- PDF / Excel export alanları  

---

## Test Mantığı

| Test Türü | Amaç |
|----------|-----|
| HTML break testleri | Etiket kapanıyor mu |
| Attribute context | Çift tırnak kırılıyor mu |
| JS context | Script içine düşüyor mu |
| URL context | javascript: çalışıyor mu |
| Event handler | on* çalışıyor mu |

---

## En Sık Hata Yapılan Filtreler

| Hata | Sonuç |
|-----|-----|
| Sadece <script> engellemek | Bypass edilir |
| encode etmemek | Stored XSS |
| innerHTML kullanmak | DOM XSS |
| CSP tanımlamamak | Zincirleme exploit |

---

## Güvenli Kodlama Rehberi

### PHP
```php
echo htmlspecialchars($input, ENT_QUOTES, 'UTF-8');
```

### JS
```js
element.textContent = userInput;
```

### Template Engines
- Escape by default
- Raw output sadece whitelist ile

---

## CSP (Content Security Policy)

Örnek:
```
Content-Security-Policy: default-src 'self'; script-src 'self';
```

---

## WAF/CDN Davranışları

| Sistem | Davranış |
|------|---------|
| Cloudflare | Inline scriptleri keser |
| Akamai | JS protocol bloklar |
| AWS WAF | Event handler pattern yakalar |

---

## Bug Bounty Rapor Şablonu

**Title:** Stored XSS in comment field  
**Impact:** Account hijacking  
**Steps:**  
1. Input X inserted  
2. Stored  
3. Victim opens page  
4. JS executed  

---

## Code Review Checklist

- [ ] innerHTML var mı  
- [ ] encode edilmiş mi  
- [ ] CSP var mı  
- [ ] DOM sanitize var mı  
- [ ] JSON output escape edilmiş mi  

---

## Profesyonel Test Araçları

- Burp Suite  
- OWASP ZAP  
- XSStrike  
- Dalfox  
- Nuclei XSS templates  

---

## Güvenli Test Yaklaşımı

- Payload yerine marker string kullan  
- Context mapping yap  
- Template escape analiz et  
- DOM flow takip et  
