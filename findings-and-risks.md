# Findings And Risks

## Yuksek oncelikli gozlemler

### 1. Repo davranisi snapshot-agirlikli, implementasyon-hafif

En merkezi command/tool akislarinin ciddi bir kismi JSON snapshot okuyup metinsel cevap donduruyor.

Etkisi:

- sistem oldugundan daha "tam" gorunebilir
- gercek runtime kabiliyeti ile raporlanan yuzey birbirine karisabilir

Ilgili dosyalar:

- `src/commands.py`
- `src/tools.py`
- `src/query_engine.py`
- `src/runtime.py`

### 2. Testler placeholder davranisi onayliyor, gercek entegrasyon degil

`tests/test_porting_workspace.py` icinde cok sayida `subprocess.run()` var; ancak dogrulamalar agirlikla:

- belirli stringlerin cikmasi
- snapshot adetlerinin esik ustunde olmasi
- placeholder modlarin cevap donmesi

uzerine kurulu.

Etkisi:

- test gecmesi, runtime gercekliginin saglam oldugu anlamina gelmeyebilir
- behavior coverage ile surface coverage karistirilabilir

Ilgili dosya:

- `tests/test_porting_workspace.py`

### 3. `src/task.py` potansiyel olarak hatali veya eksik

`src/task.py` kendi icinden `PortingTask` import etmeye calisiyor:

- `src/task.py:3`

Ama repo icinde `class PortingTask` tanimi bulunamadi. `src/tasks.py` bu sinifi kullanmaya calisiyor:

- `src/tasks.py:3`
- `src/tasks.py:6`

Etkisi:

- bu alan ya eksik port edilmis
- ya da dosya yanlis uretilmis / placeholder seviyesinde kalmis

Bu, incelemede gorulen en somut yapisal sorunlardan biri.

### 4. Setup/trust/prefetch sistemi daha cok anlatisal

`run_setup()`, `run_deferred_init()`, prefetch fonksiyonlari ve bootstrap graph bir startup hikayesi kuruyor; ancak mevcut kod seviyesinde bunlarin buyuk bolumu sabit veya simulated sonuc donduruyor.

Etkisi:

- repo gercek startup orchestration'dan cok onu temsil eden bir model sunuyor
- "hazir runtime" beklentisi olusturabilir

Ilgili dosyalar:

- `src/setup.py`
- `src/prefetch.py`
- `src/deferred_init.py`
- `src/bootstrap_graph.py`

### 5. Packaging/lint/typecheck altyapisi gorunur degil

Ust seviyede asagidaki dosyalar bulunmadi:

- `pyproject.toml`
- `requirements*.txt`
- `setup.cfg`
- `tox.ini`
- `ruff.toml`
- `.pre-commit-config.yaml`
- `Makefile`

Etkisi:

- gelistirme standardi ve tekrar uretilebilirlik belirsiz
- repo daha cok deneysel/ara katman hissi veriyor

## Orta oncelikli gozlemler

### 6. Permission modeli cok sinirli

`ToolPermissionContext`, isim veya prefix bazli bloklama yapiyor. Daha zengin capability/policy modeli yok.

Ilgili dosya:

- `src/permissions.py`

### 7. Routing mantigi token substring eslesmesi kadar basit

`PortRuntime._score()` yalnizca token'in isim/source_hint/responsibility alanlarinda gecip gecmedigine bakiyor.

Ilgili dosya:

- `src/runtime.py:176`
- `src/runtime.py:186`

Etkisi:

- route sonuclari kolayca yuzeysel kalabilir
- anlamsal niyet cozumu yapildigi izlenimi verilmemeli

### 8. Session flush semantigi cok hafif

`TranscriptStore.flush()` gercek IO yapmiyor; yalnizca `flushed=True` yapiyor. Kalicilik asil olarak `save_session()` ile ayri yerde oluyor.

Ilgili dosyalar:

- `src/transcript.py`
- `src/session_store.py`

## Sonuc cikarimi

Bu repo su asamada en dogru sekilde soyle okunmali:

- bir urun-runtime degil
- bir porting/workspace/projection katmani
- referans snapshot'larla zenginlestirilmis bir inspection ve mirrored-surface araci

Bu fark, ileride yapacagimiz tum incelemelerde ana zihinsel model olmali.
