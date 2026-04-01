---
tarih: 2026-03-30
etiketler:
  - 
priority: 10000
---
🤖[[610 chatcpt-note/_index|ChatGpt Notes Page]] || 🏠 [[Home Page]] || 📝 [[600 full notes/_index|Full Notes Page]] ||👨‍💻 [[620 programming language/_index|Programming Language Page]] 

# ⚙️ Temel Mantık

Git yapısı:

```text
Laptop  →  
           → GitHub (remote)
PC      →
```

- Bilgisayarlar **birbirini görmez**
    
- Sadece **GitHub üzerinden senkron olurlar**
    
    

---

## 💻 Laptop / PC fark etmez — başlarken

```bash
git status
git branch
git fetch
git pull --rebase
```

### Ne yapıyor?

- `status` → repo temiz mi
    
- `branch` → doğru branch’te misin
    
- `fetch` → remote bilgileri al
    
- `pull --rebase` → en güncel hale gel
    

---

## 🛠️ Çalışırken

Kod yazdıktan sonra:

```bash
git status
git diff
```

### Amaç:

- hangi dosyalar değişti
    
- hangi satırlar değişti
    

---

## 📦 Commit süreci

```bash
git add .
git commit -m "Ne yaptığını anlat"
```

---

## 🚀 Push öncesi güvenlik adımı

```bash
git fetch
git pull --rebase
git push
```

### Neden?

- Diğer bilgisayardan yeni commit gelmiş olabilir
    
- push sırasında patlamazsın
    

---

## 🔁 Diğer bilgisayara geçtiğinde

```bash
git status
git branch
git fetch
git pull --rebase
```

> ❗ Direkt kod yazmaya başlama

---

# 🔍 `git diff` Nedir?

## Tanım

> Commit edilmemiş değişiklikleri gösterir

---

## Kullanım

```bash
git diff
```

---

## Örnek çıktı

```diff
- const title = "Home";
+ const title = "Homepage";
```

---

## Anlamı

- `-` eski satır
    
- `+` yeni satır
    

---

## Varyasyonlar

```bash
git diff            # henüz stage edilmemiş
git diff --staged   # commit’e hazır olanlar
```

---

## Ne zaman kullanılır?

- commit atmadan önce kontrol
    
- yanlış değişiklikleri görmek
    
- debug
    

---

# ⚠️ Conflict Nedir?

## Tanım

> Git aynı satırı otomatik birleştiremediğinde oluşur

---

## Ne zaman olur?

- aynı dosya
    
- aynı satır
    
- farklı değişiklik
    

---

## Örnek

Laptop:

```js
const title = "Home";
```

PC:

```js
const title = "Homepage";
```

👉 conflict çıkar

---

## Çözüm süreci

1. Dosyayı aç
    
2. Şu yapıyı görürsün:
    

```text
<<<<<<< HEAD
Home
=======
Homepage
>>>>>>> branch
```

3. Doğru olanı seç
    
4. Sonra:
    

```bash
git add .
git rebase --continue
```

---

# 🧹 Working Tree Temizliği

## `git status` çıktısı

### Temiz durum:

```text
nothing to commit, working tree clean
```

---

## Kirli durum:

```text
modified: file.js
```

---

## Ne yapabilirsin?

### 1) Commit et

```bash
git add .
git commit -m "..."
```

---

### 2) Değişikliği sil

```bash
git restore file.js
```

---

### 3) Geçici sakla (stash)

```bash
git stash
```

geri almak:

```bash
git stash pop
```

---

# ✅ En Güvenli Kullanım

## Başlangıç

```bash
git status
git branch
git fetch
git pull --rebase
```

---

## Bitiş

```bash
git status
git add .
git commit -m "..."
git fetch
git pull --rebase
git push
```

---

# 🧠 Özet

- `git diff` → ne değiştirdim
    
- `git status` → repo durumu
    
- `git pull --rebase` → en güncel hale gel + temiz history
    
- `git push` → değişiklikleri gönder
    

---



## 🔗 Bağlantılar
- [[ ]]




🤖[[610 chatcpt-note/_index|ChatGpt Notes Page]] || 🏠 [[Home Page]] || 📝 [[600 full notes/_index|Full Notes Page]] ||👨‍💻 [[620 programming language/_index|Programming Language Page]] 