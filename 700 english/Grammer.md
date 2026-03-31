- **Class:**  Grammer
- **Date:** 2026-03-31  
- **Topics:** #grammer


# 🧠 English Grammar Essentials for Tech & General Use

Bu notlar, teknik dokümantasyonlarda ve günlük konuşmalarda en sık karşılaşılan, anlamı doğrudan değiştiren kritik yapıları içerir.

---

## 1. Relative Clauses (İlgi Cümlecikleri)

Tıpkı senin örneğindeki `that` gibi, bir ismi tanımlamak için kullanılırlar.

|**Zamir**|**Kullanım Alanı**|**Örnek Cümle**|
|---|---|---|
|**Who**|İnsanlar için|The engineer **who** wrote this code is a genius.|
|**Which**|Nesneler/Hayvanlar için|The bug **which** caused the crash is fixed.|
|**That**|Her ikisi için (Daha yaygın)|The tool **that** we use is open-source.|
|**Whose**|İyelik/Aitlik bildirir|The company **whose** CEO resigned is Apple.|

> [!TIP]
> 
> Eğer "that/which/who"dan sonra bir **özne** geliyorsa (örn: The book that **I** read), bu zamiri cümleden atabilirsin. Ama bir **fiil** geliyorsa (senin örneğindeki gibi: that **developed**), asla atamazsın!

---

## 2. Passive Voice (Edilgen Yapı)

Özellikle teknik metinlerde (YOLOv11 was released...) eylemi kimin yaptığından ziyade, **eylemden etkilenen nesne** önemliyse kullanılır.

**Formül:** `Be + V3 (Past Participle)`

- **Active:** Python supports multiple libraries.
    
- **Passive:** Multiple libraries **are supported** by Python.
    

---

## 3. Conditionals (Koşul Cümleleri - If Clauses)

Yazılımdaki `if-else` mantığının aynısıdır. En önemli ikisi şunlardır:

### **Type 1: Real Possibility (Gerçek İhtimal)**

Gelecekte olması muhtemel durumlar.

- **Yapı:** `If + Present Simple, Will + V1`
    
- **Örnek:** If you **update** the drivers, the GPU **will perform** better.
    

### **Type 2: Unreal/Imaginary (Hayali Durumlar)**

Şu an için doğru olmayan, varsayımsal durumlar.

- **Yapı:** `If + Past Simple, Would + V1`
    
- **Örnek:** If I **had** more RAM, I **would run** this model locally.
    

---

## 4. Gerund vs. Infinitive (-ing mi, to mu?)

Bazı fiillerden sonra gelen ikinci fiilin formu anlamı belirler.

- **Gerund (-ing):** Genelde deneyimlerden veya genel durumlardan bahsederken.
    
    - _I enjoy **coding** in Rust._
        
- **Infinitive (to + V1):** Genelde bir amaç veya geleceğe yönelik bir niyet bildirirken.
    
    - _I want **to learn** more about AI._
        

|**Fiil**|**Takip Eden Yapı**|**Örnek**|
|---|---|---|
|**Avoid**|Gerund (-ing)|Avoid **using** global variables.|
|**Decide**|Infinitive (to)|We decided **to switch** to PyTorch.|
|**Stop**|Her ikisi (Anlam değişir!)|Stop **working** (Çalışmayı bırak) vs Stop **to work** (Çalışmak için dur).|

---

## 5. Present Perfect Tense (Belirsiz Geçmiş Zaman)

Geçmişte başlamış ve etkisi hala süren veya tam zamanı belli olmayan eylemler. Teknik dünyada "güncelleme" ve "deneyim" anlatırken can kurtarır.

- **Yapı:** `Have/Has + V3`
    
- **Örnek:** "We **have improved** the accuracy by 5%." (Ne zaman yaptığımız değil, sonucun şu an geçerli olması önemli.)
    

---
# 🚀 Advanced Grammar for Technical Precision

Bu bölüm, cümleleri daha profesyonelce kısaltmanı (reduction), mantıksal bağlar kurmanı ve teknik dokümantasyon dilini çözmeni sağlar.

---

## 1. Defining vs. Non-Defining Relative Clauses

Senin ilk sorduğun cümle bir **Defining** (Tanımlayıcı) yapıydı. Ancak virgül işin içine girince her şey değişir.

|**Tür**|**Özellik**|**Örnek**|
|---|---|---|
|**Defining**|Bilgi zorunludur, virgül kullanılmaz.|The GPU **that** we bought is fast. (Hangi GPU? Satın aldığımız.)|
|**Non-Defining**|Ekstra bilgi verir, virgül ile ayrılır.|This GPU, **which** cost $500, is fast. (Hangi GPU olduğu belli, fiyatı sadece ek bilgi.)|

> [!CAUTION]
> 
> **"That"** asla virgül ile (non-defining cümleciklerde) kullanılmaz. Sadece **"which"** veya **"who"** kullanılır.

---

## 2. Reduced Relative Clauses (Cümlecik Kısaltma)

Profesyonel metinlerde "that/which" atılarak cümleler sadeleştirilir. Bu, teknik raporlarda en sık göreceğin yapıdır.

### **Aktif Kısaltma (V-ing)**

Eğer cümle aktifse (yapan biriyse), "that + fiil" yerine sadece `-ing` gelir.

- **Tam Hali:** The script **that runs** the backup is broken.
    
- **Kısaltılmış:** The script **running** the backup is broken.
    

### **Pasif Kısaltma (V3)**

Eğer cümle edilgen ise, sadece fiilin 3. hali kalır.

- **Tam Hali:** The model **which was trained** on ImageNet is accurate.
    
- **Kısaltılmış:** The model **trained** on ImageNet is accurate.
    

---

## 3. Logical Connectors (Mantıksal Bağlaçlar)

Fikirleri birbirine bağlarken "and, but, so" yerine bunları kullanmak raporlarını akademik seviyeye taşır.

### **Zıtlık (Contrast)**

- **However / Nevertheless:** (Ancak) - Cümle başında kullanılır.
    
- **Despite / In spite of:** (-e rağmen) - Arkasından **isim** veya **V-ing** gelir.
    
    - _Example:_ **Despite** the high cost, we upgraded the server.
        

### **Neden-Sonuç (Cause-Effect)**

- **Therefore / Consequently:** (Bu yüzden / Sonuç olarak).
    
- **Due to:** (-den dolayı) - Arkasından isim gelir.
    
    - _Example:_ The delay was **due to** a network error.
        

---

## 4. Modal Verbs in Technical Context

Teknik dünyada olasılıklar ve zorunluluklar hassastır.

- **Should:** "Yapmalı"dan ziyade "Beklenti" bildirir.
    
    - _The update **should** fix the bug._ (Güncellemenin hatayı çözmesini bekliyoruz.)
        
- **May / Might:** Olasılık bildirir. "Might" daha düşük bir ihtimaldir.
    
    - _This change **might** affect performance._
        
- **Must vs. Have to:** * **Must:** Kişisel veya güçlü zorunluluk. (You must backup.)
    
    - **Have to:** Dışsal kurallar/gereklilikler. (We have to use Python 3.10 for this lib.)
        

---

## 5. The "Used to" Trio (Karıştırılan Üçlü)

Bunlar Obsidian'da yan yana durmalı çünkü sürekli birbirine karışır:

1. **Used to + V1:** Eskiden yapardım (artık yapmıyorum).
    
    - _I **used to** use TensorFlow._
        
2. **Be used to + V-ing:** Bir şeye alışkın olmak.
    
    - _I **am used to** coding at night._
        
3. **Get used to + V-ing:** Bir şeye alışmak (süreç).
    
    - _You will **get used to** this syntax soon._
        

---
# 🔗 Related Notes

- [[Grammer Master]]
    

    
