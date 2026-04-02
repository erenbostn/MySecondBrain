# Architecture Notes

## 1. Manifest ve workspace tarama

`src/port_manifest.py`, `src/` altindaki tum `.py` dosyalarini sayiyor ve top-level modul/subsystem dagilimini uretiyor.

Ana noktalar:

- `build_port_manifest()` dosya sistemini dogrudan tarar.
- Top-level isimleri `Counter` ile toplar.
- Bazi bilinen dosyalara sabit notlar ekler; diger her sey "Python port support module" olarak etiketlenir.

Kaynak:

- `src/port_manifest.py:30`
- `src/port_manifest.py:38`
- `src/port_manifest.py:48`

## 2. Command ve tool yuzeyi

### Commands

`src/commands.py`, gercek command implementasyonlari yerine `commands_snapshot.json` icinden `PortingModule` listesi yukler.

Davranis:

- snapshot okur
- query/filter yapar
- execute edildiginde gercek is yapmak yerine "would handle prompt" mesaji dondurur

Kaynak:

- `src/commands.py:10`
- `src/commands.py:23`
- `src/commands.py:60`
- `src/commands.py:75`

### Tools

`src/tools.py`, command katmaninin ayni mantigini tool tarafinda uygular.

Ek olarak:

- simple mode filtresi var
- MCP filtreleme var
- permission context ile isim/prefix bazli engelleme var

Kaynak:

- `src/tools.py:11`
- `src/tools.py:24`
- `src/tools.py:56`
- `src/tools.py:62`
- `src/tools.py:81`

## 3. Query engine

`src/query_engine.py`, bu kod tabaninin "gercek cevap ureten LLM engine" katmani degil; daha cok session state, usage sayaci, transcript ve ozet cikisi ureten bir port simulasyonu.

Ana akis:

- workspace manifest ile init olur
- prompt'u kaydeder
- eslesen command/tool adlarini cikisa yazar
- permission denial sayisini ozetler
- kaba token sayaci tutar
- transcript'i memory'de saklar
- session'i JSON olarak persist eder

Kaynak:

- `src/query_engine.py:35`
- `src/query_engine.py:61`
- `src/query_engine.py:106`
- `src/query_engine.py:129`
- `src/query_engine.py:140`
- `src/query_engine.py:171`

Onemli detay:

- `UsageSummary.add_turn()` gercek tokenizasyon degil, kelime sayisi tabanli kaba bir sayaç kullaniyor.
- `structured_output`, JSON render etmeye calisiyor ama burada da gercek schema enforcement yok.

## 4. Runtime ve routing

`src/runtime.py`, metadata tabanli route/bootstrap/session kurgusunu bir araya getiriyor.

Akis:

1. prompt tokenlara bolunuyor
2. command ve tool snapshot listeleri uzerinde string eslesmesiyle skor veriliyor
3. secilen komut/araclar registry uzerinden "execute" ediliyor
4. query engine'e ayni prompt aktariliyor
5. session diske persist ediliyor

Kaynak:

- `src/runtime.py:89`
- `src/runtime.py:90`
- `src/runtime.py:109`
- `src/runtime.py:118`
- `src/runtime.py:122`
- `src/runtime.py:134`
- `src/runtime.py:154`

Mimari sonucu:

- routing semantik veya yapisal bir planner degil
- basit token/eslesme skoru ile calisiyor
- execution tarafi da gercek tool invocation degil, anlatisal placeholder

## 5. Setup, prefetch ve trust

`src/setup.py`, `src/prefetch.py` ve `src/deferred_init.py` birlikte bir startup hikayesi kuruyor.

Ama mevcut implementasyon seviyesinde bunlarin cogu simulated/placeholder:

- prefetch sonuclari sabit metinler donduruyor
- deferred init, `trusted=True` ise tum bayraklari `True` yapiyor
- startup steps, raporlama amacli

Kaynak:

- `src/setup.py`
- `src/prefetch.py`
- `src/deferred_init.py`
- `src/system_init.py`
- `src/bootstrap_graph.py`

## 6. Session ve transcript kaliciligi

Session modeli basit:

- `TranscriptStore` mesaj listesi tutar
- `flush()` sadece `flushed=True` bayragi set eder
- `save_session()` `.port_sessions/` altina JSON yazar
- `load_session()` bu JSON'u tekrar `StoredSession` olarak okur

Kaynak:

- `src/transcript.py`
- `src/session_store.py`

Bu tasarim, ileri seviye runtime persistence degil; analiz ve raporlama odakli hafif bir session izi sunuyor.

## 7. Placeholder subsystem package'leri

`src/assistant/__init__.py`, `src/bridge/__init__.py`, `src/utils/__init__.py` ve benzerleri gercek alt modul implementasyonu icermiyor.

Bunlar:

- ilgili `subsystems/*.json` snapshot dosyasini okur
- `ARCHIVE_NAME`, `MODULE_COUNT`, `SAMPLE_FILES`, `PORTING_NOTE` expose eder

Bu, klasorlerin esasen "ported subsystem metadata placeholder" oldugunu gosteriyor.

## 8. Parity audit mantigi

`src/parity_audit.py`, yerel archive var ise:

- root file coverage
- directory coverage
- toplam dosya orani
- command/tool snapshot sayilari

gibi metrikleri raporluyor.

Ancak burada da parity, davranissal esdegerlik degil; daha cok ad/yuzey/envanter seviyesinde karsilastirma.

Kaynak:

- `src/parity_audit.py:7`
- `src/parity_audit.py:13`
- `src/parity_audit.py:34`
- `src/parity_audit.py:121`
