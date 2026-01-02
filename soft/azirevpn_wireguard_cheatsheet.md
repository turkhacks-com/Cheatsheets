# AzireVPN WireGuard Cheatsheet (Linux/Fedora)

## ᴹ Gerekli Paketlerin Kurulumu

**Fedora:**

```bash
sudo dnf install wireguard-tools resolvconf
```

**Debian/Ubuntu:**

```bash
sudo apt install wireguard resolvconf
```

---

## ᴾ Konfigürasyon Dosyasını Al

1. [https://www.azirevpn.com](https://www.azirevpn.com) adresine giriş yap.
2. "WireGuard" sekmesine git.
3. Yeni cihaz/profil oluştur veya mevcut profili indir.
4. Dosya genellikle şu formatta olur: `azirevpn-[ülke].conf`

---

## 📁 Konfig Dosyasını Yerleştirme

```bash
sudo mkdir -p /etc/wireguard
sudo cp ~/Downloads/azirevpn-fi.conf /etc/wireguard/
sudo chmod 600 /etc/wireguard/azirevpn-fi.conf
```

> `.conf` dosya adına dikkat edin: `azirevpn-fi.conf`, `azirevpn-se.conf` vb.

---

## 🚀 VPN Bağlantısını Başlatma

```bash
sudo wg-quick up azirevpn-fi
```

- IP adresin değişmiş olur.
- Durumu kontrol etmek için:

```bash
sudo wg show
```

---

## 🚫 VPN’i Durdurma

```bash
sudo wg-quick down azirevpn-fi
```

---

## 🔁 Otomatik Başlatma (isteğe bağlı)

```bash
sudo systemctl enable wg-quick@azirevpn-fi
```

Kapatmak için:

```bash
sudo systemctl disable wg-quick@azirevpn-fi
```

---

## 🌐 IP Değişimini Kontrol Et

```bash
curl ifconfig.me
```

Alternatif:

```bash
curl ipinfo.io
```

---

## ⚠️ Troubleshooting

- **Bağlantı kurulmadıysa**:

  - `sudo wg show` ile hata detaylarına bak.
  - DNS sorunları için `resolvconf` kurulu olduğuna emin ol.
  - Firewall ayarlarını kontrol et.

- **Konfig dosyası okunamıyorsa:**

  - `chmod 600` ile dosya izinlerini düzelt.
  - `sudo` ile çalıştırdığından emin ol.

---

## 🔄 Özet Komutlar

```bash
sudo dnf install wireguard-tools resolvconf
sudo cp ~/Downloads/azirevpn-fi.conf /etc/wireguard/
sudo chmod 600 /etc/wireguard/azirevpn-fi.conf
sudo wg-quick up azirevpn-fi
curl ifconfig.me
sudo wg-quick down azirevpn-fi
```

