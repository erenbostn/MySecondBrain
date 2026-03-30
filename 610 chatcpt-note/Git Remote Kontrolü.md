---
tarih: 2026-03-30
etiketler:
  - git
  - remote
priority: 0
---
← [[610 chatcpt-note/_index|ChatGpt Notes Page]] || 🏠 [[Home Page]] || [[600 full notes/_index|Full Notes Page]]


# 🔹 1) Önce remote bilgileri güncelle

```bash
git fetch
```

👉 Bu çok kritik

- GitHub’daki **yeni branchleri / commitleri indirir**
    
- ama dosyalarına dokunmaz
    

> ❗ `fetch` yapmadan baktığın liste eski olabilir

---

# 🔹 2) Remote branchleri listele

```bash
git branch -r
```

örnek çıktı:

```text
origin/main
origin/uiv4
origin/feature/navbar
```

👉 Bunlar **GitHub’daki branchler**

---

# 🔹 3) Hem local hem remote görmek

```bash
git branch -a
```

örnek:

```text
* main
  uiv4
  remotes/origin/main
  remotes/origin/feature/navbar
```

---

# 🔥 En pratik kullanım (senin için)

Her zaman şu 2’liyi kullan:

```bash
git fetch
git branch -a
```

---

# 🔍 “Yeni branch var mı?” nasıl anlarsın

### Senin localde:

```bash
git branch
```

```text
main
uiv4
```

### Remote’ta:

```bash
git branch -r
```

```text
origin/main
origin/uiv4
origin/feature/navbar
```

👉 Burada şunu anlarsın:

- `feature/navbar` **remote’ta var**
    
- ama localde yok
    

---

# 🔹 Remote branch’i local’e almak

```bash
git checkout -b feature/navbar origin/feature/navbar
```

veya modern:

```bash
git switch -c feature/navbar origin/feature/navbar
```

👉 Bu:

- remote branch’i alır
    
- localde branch oluşturur
    
- otomatik ona geçer
    

---

# 🔹 Remote ile local senkron mu?

```bash
git status
```

örnek:

```text
Your branch is up to date with 'origin/main'
```

veya:

```text
Your branch is behind 'origin/main' by 2 commits
```

---

# 🔹 Remote URL kontrolü

```bash
git remote -v
```

örnek:

```text
origin  https://github.com/user/repo.git (fetch)
origin  https://github.com/user/repo.git (push)
```

👉 doğru repo mu kontrol edersin

---

# 🔥 Mini özet (çok net)

- `git fetch` → remote bilgileri güncelle
    
- `git branch -r` → remote branchleri gör
    
- `git branch -a` → hepsini gör
    
- `git switch -c X origin/X` → remote branch’i local’e al
    

---

# 💣 En kritik hata

> ❌ fetch yapmadan branch kontrol etmek  
> → eski listeyi görürsün

---

# Sana net rutin

```bash
git fetch
git branch -a
```

← [[610 chatcpt-note/_index|ChatGpt Notes Page]] || 🏠 [[Home Page]] || [[600 full notes/_index|Full Notes Page]]