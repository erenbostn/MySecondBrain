---
tarih: 2026-03-31
etiketler:
  - 
priority: 0
---

# Google Stitch Mcp Cli


# 🎨 Google Stitch MCP: CLI & Terminal Kurulum Rehberi

Google Stitch tasarımlarını (Design DNA) **Antigravity** dışında, kendi terminaliniz veya farklı IDE'ler üzerinden yönetmek için bu rehberi kullanabilirsiniz.

---

## 🛠️ 1. Hazırlık: API Anahtarını Alma

Stitch verilerine dışarıdan erişebilmek için bir kimlik doğrulama anahtarına ihtiyacınız var.

1. [stitch.withgoogle.com](https://stitch.withgoogle.com/) adresine gidin.
    
2. Sağ üstteki **Profil İkonu** > **Stitch Settings** yolunu izleyin.
    
3. **API Key** bölümünden yeni bir anahtar oluşturun ve güvenli bir yere kopyalayın.
    

---

## 🚀 2. Kurulum (CLI)

En popüler ve stabil araç olan `@_davideast/stitch-mcp` paketini kullanacağız. Node.js yüklü olduğundan emin olun.

### Otomatik Yapılandırma

Aşağıdaki komut; kimlik doğrulama ve MCP istemci ayarlarını otomatik olarak yapar:

Bash

```
npx @_davideast/stitch-mcp init
```

> [!TIP] Sürekli Kullanım İçin
> 
> Eğer bu aracı sık kullanacaksanız global olarak kurabilirsiniz:
> 
> `npm install -g @_davideast/stitch-mcp`

---

## 💻 3. Temel Terminal Komutları

Aşağıdaki komutlarda `<PROJE_ID>` kısmını Stitch projenizin URL'sinde bulunan ID ile değiştirin.

|**İşlem**|**Komut**|
|---|---|
|**Tasarımları Önizle**|`npx @_davideast/stitch-mcp serve -p <PROJE_ID>`|
|**Ekranları Listele**|`npx @_davideast/stitch-mcp screens -p <PROJE_ID>`|
|**Astro Sitesi Üret**|`npx @_davideast/stitch-mcp site -p <PROJE_ID>`|
|**Proxy Modu (AI için)**|`npx @_davideast/stitch-mcp proxy`|

---

## 🧩 4. Gelişmiş Yetenekler (Stitch Skills)

Google Labs tarafından sağlanan özel yetenekleri ekleyerek terminalinizin fonksiyonlarını artırabilirsiniz.

### React Bileşenlerine Dönüştürme

Tasarım ekranlarını doğrudan React koduna çevirmek için:

Bash

```
npx skills add google-labs-code/stitch-skills --skill react-components --global
```

### Tasarım Dökümantasyonu (Design MD)

Tasarım sisteminizi Markdown formatında dökümante etmek için:

Bash

```
npx skills add google-labs-code/stitch-skills --skill design-md --global
```

---

## 🤖 5. Obsidian / Claude Desktop Entegrasyonu (Opsiyonel)

Eğer bu MCP sunucusunu bir AI asistanına (örneğin Claude Desktop) bağlamak isterseniz, `claude_desktop_config.json` dosyanıza şu satırları ekleyin:

JSON

```
{
  "mcpServers": {
    "stitch": {
      "command": "npx",
      "args": ["-y", "@_davideast/stitch-mcp", "proxy"],
      "env": {
        "STITCH_API_KEY": "YOUR_API_KEY_HERE"
      }
    }
  }
}
```

---

## 📌 Notlar

- **Proje ID Nerede?** Projenizi tarayıcıda açtığınızda URL şu şekildedir: `.../p/PROJE_ID_BURADADIR/...`
    
- **Güncelleme:** Araçları güncel tutmak için `npx @_davideast/stitch-mcp@latest` komutunu kullanabilirsiniz.
    

---

#google #stitch #mcp #terminal #cli #guide

--- 

## 🔗 Bağlantılar
- [[ ]]