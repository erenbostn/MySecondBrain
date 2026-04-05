# Repo Overview

## One-line read

Bu repo, tam anlamiyla uretilmis bir son urun gibi degil; daha cok "Claude Code benzeri harness yuzeyini Python tarafinda metadata ve placeholder davranislarla yansitan" bir porting workspace gibi duruyor.

## Temel gozlem

- `README.md`, aktif kaynak agacinin Python-first oldugunu ve `src/` altinin "Python porting workspace" olarak konumlandirildigini soyluyor.
- Ana giris noktasi `src/main.py` ve cok sayida alt komut expose ediyor.
- Bu alt komutlarin buyuk kismi gercek entegrasyonlar calistirmaktan cok:
  - snapshot JSON verilerini okumak,
  - ozet/manifest cikarmak,
  - route/bootstrap/session benzeri akislari simule etmek,
  - placeholder execution mesaji dondurmek
    uzere tasarlanmis.

## Dizin yapisi

- `src/`: aktif Python kaynaklari
- `tests/`: agirlikla CLI ve metadata tabanli dogrulamalar
- `assets/`: README varliklari
- `.github/`: su an sadece funding metadata
- `docs/`: bu analiz notlari

## Kodu nasil okumak gerekiyor

Bu kod tabanini bir "runtime/product" olarak degil, bir "mirrored surface + inspection/reporting harness" olarak okumak daha dogru.

Ana omurga:

1. `src/main.py`
2. `src/port_manifest.py`
3. `src/commands.py`
4. `src/tools.py`
5. `src/query_engine.py`
6. `src/runtime.py`
7. `src/parity_audit.py`

## Ana veri kaynagi

Repo davranisinin onemli bir kismi `src/reference_data/` altindaki JSON snapshot'lar tarafindan besleniyor.

- `commands_snapshot.json`: mirrored command envanteri
- `tools_snapshot.json`: mirrored tool envanteri
- `archive_surface_snapshot.json`: parity audit icin referans metrikler
- `subsystems/*.json`: placeholder package metadata

Bu nedenle sistemin "zeka" veya "kapsam" hissinin ciddi bir kismi canli implementasyondan degil, referans veriden geliyor.

## Giris noktasi ve komut yuzeyi

`src/main.py` icinde parser, summary/manifest/parity-audit gibi raporlama komutlarinin yani sira route/bootstrap/turn-loop/exec-command/exec-tool gibi daha runtime-benzeri komutlari da expose ediyor.

Kaynak referanslari:

- `src/main.py:21`: CLI parser kurulumu
- `src/main.py:24`: summary
- `src/main.py:25`: manifest
- `src/main.py:26`: parity-audit
- `src/main.py:48`: route
- `src/main.py:52`: bootstrap
- `src/main.py:56`: turn-loop
- `src/main.py:160`: flush-transcript
- `src/main.py:200`: exec-command
- `src/main.py:204`: exec-tool

## Mimari yorum

Bu repo uc katmana ayriliyor gibi gorunuyor:

1. Snapshot/metadata katmani
   - `commands.py`
   - `tools.py`
   - `reference_data/*`

2. Raporlama ve orkestrasyon katmani
   - `port_manifest.py`
   - `query_engine.py`
   - `runtime.py`
   - `parity_audit.py`
   - `setup.py`

3. Placeholder subsystem/export katmani
   - `assistant/`, `bridge/`, `utils/` ve benzeri package'ler

## Testlere dair ilk okuma

Testler cok sayida CLI akis isletiyor gibi yazilmis olsa da odak noktasi gercek entegrasyon dogrulamasi degil; daha cok "beklenen stringler donuyor mu", "snapshot boyutlari yeterli mi", "placeholder akis kirilmadan calisiyor mu" tarzi kontratlar.

Bu da repo hedefinin "feature-complete runtime" yerine "mirrored structure and reporting surface" oldugunu destekliyor.

## Araclandirma gozlemi

Ust seviyede su tip dosyalar gorunmuyor:

- `pyproject.toml`
- `requirements*.txt`
- `setup.cfg`
- `tox.ini`
- `ruff.toml`
- `.pre-commit-config.yaml`
- `Makefile`

Bu, repoda paketleme/lint/typecheck/test orkestrasyonunun henuz minimal ya da eksik oldugunu dusunduruyor.
