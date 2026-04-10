---
tarih: 2026-03-29
etiketler:
  - docker
---
← 🧠 [[100 roughly/_index|Rough Idea Page]] | 🏠 [[Home Page]] | 🌊 [[110 research/_index|Deep Research Page]]

# [[Docker Usage]]

# 🐳 Docker – Temel Mantık

## Core Kavramlar

- **Dockerfile** → ortamın nasıl kurulacağını tarif eder
    
- **Image** → bu tariften üretilmiş hazır kalıp
    
- **Container** → çalışan instance (process gibi düşün)
    

👉 Özet:

```
Dockerfile → build → Image → run → Container
```

---

## Docker Neyi Çözer?

- “Benim bilgisayarımda çalışıyor” problemini çözer
    
- Ortam bağımlılıklarını standart hale getirir
    
- Tek komutla deploy sağlar
    

---

# 🧱 Dockerfile Mantığı

Örnek:

```dockerfile
FROM node:20
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "index.js"]
```

### Satır mantığı:

- `FROM` → base image seç
    
- `WORKDIR` → çalışma klasörü
    
- `COPY` → kodu container içine koy
    
- `RUN` → komut çalıştır (build/install)
    
- `CMD` → container başlayınca çalışacak şey
    

---

## COPY Nedir?

```dockerfile
COPY . .
```

👉 Host → container dosya kopyalar

Yoksa container içinde kod olmaz.

---

# 🧠 Image Nasıl Oluşur (Layer Mantığı)

Her satır = layer

```dockerfile
COPY package.json .
RUN npm install
COPY . .
```

👉 cache çalışır

- package değişmezse → npm install tekrar çalışmaz
    
- kod değişirse → sadece son layer değişir
    

---

# ⚖️ Base Image Seçimi

## Kriterler:

- Size (boyut)
    
- libc (glibc vs musl)
    
- Kullanım kolaylığı
    
- Security (CVE sayısı)
    

---

## Karşılaştırma

|Image|Durum|
|---|---|
|node:latest|büyük, kolay, güvensiz|
|node:slim|dengeli ✅|
|node:alpine|küçük ama riskli|
|distroless|çok güvenli ama zor|
|scratch|tamamen boş|

---

## Öneri

- öğrenme → `node:20`
    
- production → `node:20-slim`
    
- optimize → `node:20-alpine`
    

---

# 🧊 Alpine Nedir?

- minimal Linux distro
    
- çok küçük (~5-10MB)
    
- musl libc kullanır
    

### Artı:

- hızlı
    
- küçük
    

### Eksi:

- bazı paketler bozulur
    
- debug zor
    

---

# 🧬 Multi-stage Build (Çok önemli)

```dockerfile
FROM golang:1.19-alpine as build
...
RUN go build -o app

FROM scratch
COPY --from=build /app/app app
```

## Mantık:

1. build ortamı (tool’lar var)
    
2. final ortam (sadece sonuç)
    

👉 sadece binary kalır

---

## Neden?

- image küçülür
    
- güvenlik artar
    
- gereksiz şeyler silinir
    

---

# 🧠 Container vs VM

|Container|VM|
|---|---|
|host kernel kullanır|kendi kernel|
|hızlı|ağır|
|küçük|büyük|

---

# 🧩 Docker Image = Ne?

👉 “Linux + runtime + app”

Örnek:

```
node:20 = debian + node
```

---

# 🧪 Windows vs Linux

- Containerlar genelde **Linux**
    
- Windows’ta bile arka planda Linux çalışır (WSL2)
    

👉 ayrı Windows container gerekmez (çoğu zaman)

---

# 🚀 Production Deploy

## Akış:

1. Dockerfile yaz
    
2. image build et
    
3. registry’ye push et
    
4. server pull + run
    

---

## Örnek:

```bash
docker build -t my-api .
docker push user/my-api
docker pull user/my-api
docker run -p 3000:3000 user/my-api
```

---

## Gerçek kullanım

Genelde:

- app
    
- db (postgres)
    
- cache (redis)
    
- reverse proxy (nginx)
    

👉 birlikte çalışır (docker compose)

---

# 🔐 Production Kuralları

- secret’ı image içine koyma
    
- volume kullan (db için)
    
- reverse proxy kullan
    
- latest yerine version kullan
    
- image küçük tut
    

---

# 🧠 Dil vs Docker (Go vs Node)

## Go avantaj:

- tek binary
    
- küçük image
    
- hızlı deploy
    

## Ama:

- her iş için uygun değil
    

---

## Dil seçimi:

|İş|Dil|
|---|---|
|AI / CV|Python|
|Web SaaS|Node / TS|
|High perf backend|Go|

---

# 🔥 En Kritik Özet

- Docker = ortamı paketleme
    
- Image = çalıştırılabilir kalıp
    
- Container = çalışan instance
    
- Base image seçimi = trade-off
    
- Multi-stage = production standardı
    

---


## 🔗 Bağlantılar
- [[ ]]	


← 🧠 [[100 roughly/_index|Rough Idea Page]] | 🏠 [[Home Page]] | 🌊 [[110 research/_index|Deep Research Page]]