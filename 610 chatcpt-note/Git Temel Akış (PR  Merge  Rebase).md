---
tarih: 2026-04-11
etiketler:
  - 
priority: 0
---
🤖[[610 chatcpt-note/_index|ChatGpt Notes Page]] || 🏠 [[Home Page]] || 📝 [[600 full notes/_index|Full Notes Page]] ||👨‍💻 [[620 programming language/_index|Programming Language Page]] 

# Git Temel Akış (PR / Merge / Rebase)

## 🔹 1. Branch Mantığı

- `main` → stabil kod
    
- yeni iş → ayrı branch
    

```bash
git checkout main
git pull origin main
git checkout -b feature/xyz
```

---

## 🔹 2. Commit & Push

```bash
git add .
git commit -m "feat: xyz"
git push -u origin feature/xyz
```

- commit → lokal kayıt
    
- push → GitHub’a gönderme
    

---

## 🔹 3. Pull Request (PR)

**Tanım:**

> “Benim branch’imi main’e ekleyelim mi?”

- base: `main`
    
- compare: `feature/xyz`
    

PR = öneri, merge değildir

---

## 🔹 4. Code Review

PR açıldıktan sonra:

- kod kontrol edilir
    
- hata / iyileştirme bakılır
    

Örnek:

- naming kötü
    
- logic hatalı
    
- refactor önerisi
    

Düzeltme:

```bash
git add .
git commit -m "fix: review changes"
git push
```

PR otomatik güncellenir

---

## 🔹 5. Merge

Onay sonrası:

- branch → main’e katılır
    

Sonuç:

```id="merge-flow"
feature/xyz → main
```

---

## 🔹 6. Merge Conflict

**Ne zaman olur?**

- aynı dosyanın aynı kısmı değişirse
    

Örnek:

```tsx
// sen
<button>Sign In</button>

// başkası
<button>Log In Securely</button>
```

Git karar veremez → conflict

---

### Conflict görünümü:

```tsx
<<<<<<< HEAD
<button>Log In Securely</button>
=======
<button>Sign In</button>
>>>>>>> feature
```

---

### Çözüm:

- dosyayı aç
    
- doğru halini yaz
    
- işaretleri sil
    

```bash
git add .
git commit
git push
```

---

## 🔹 7. git pull (arka plan)

```bash
git pull
↓
git fetch
↓
git merge
```

### fetch

- remote’dan indirir
    
- koduna dokunmaz
    

### merge

- indirilen değişiklikleri ekler
    

---

## 🔹 8. git pull --rebase

```bash
git pull --rebase
↓
git fetch
↓
git rebase
```

---

## 🔹 9. Rebase Mantığı

**Tanım:**

> commitlerini al → güncel branch’in üstüne taşı

---

### Önce:

```id="rebase-before"
main:    A - B - C - F - G
feature:        \ 
                D - E
```

---

### Rebase sonrası:

```id="rebase-after"
A - B - C - F - G - D' - E'
```

- commitler yeniden yazılır
    
- daha temiz history
    

---

## 🔹 10. Merge vs Rebase

### merge:

- ekstra commit oluşturur
    
- geçmiş karışabilir
    

```id="merge-graph"
A - B - C - F - G
        \       \
         D - E --- M
```

---

### rebase:

- düz history
    
- commit ID değişir
    

```id="rebase-graph"
A - B - C - F - G - D' - E'
```

---

## 🔹 11. Kritik Kurallar

- `main`de direkt çalışılmaz
    
- her iş ayrı branch
    
- PR açmadan merge yok
    
- conflict normaldir
    
- rebase → sadece kendi branch’inde
    

---

## 🔹 12. Tek Cümlelik Özet

- PR → değişiklik öner
    
- Review → kontrol ettir
    
- Merge → birleştir
    
- Conflict → çakışmayı çöz
    
- Rebase → commitleri yeniden hizala
    

---

## 🔹 13. Standart Workflow

```bash
git checkout main
git pull origin main

git checkout -b feature/xyz

# kod yaz
git add .
git commit -m "feat: xyz"

git push -u origin feature/xyz
```

→ PR aç → review → merge

## 🔗 Bağlantılar
- [[ ]]



🤖[[610 chatcpt-note/_index|ChatGpt Notes Page]] || 🏠 [[Home Page]] || 📝 [[600 full notes/_index|Full Notes Page]] ||👨‍💻 [[620 programming language/_index|Programming Language Page]] 