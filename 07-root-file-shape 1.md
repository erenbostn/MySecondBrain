# Root File Shape

## En Uzun Kok Dosyalar

Satir sayisina gore en uzun kok dosyalar:
- `src/main.py`: `213`
- `src/query_engine.py`: `193`
- `src/runtime.py`: `192`
- `src/parity_audit.py`: `138`
- `src/tools.py`: `96`
- `src/commands.py`: `90`
- `src/setup.py`: `77`

Kaynak:
- [src/main.py](/home/eren/Desktop/claw-code/src/main.py)
- [src/query_engine.py](/home/eren/Desktop/claw-code/src/query_engine.py)
- [src/runtime.py](/home/eren/Desktop/claw-code/src/runtime.py)
- [src/parity_audit.py](/home/eren/Desktop/claw-code/src/parity_audit.py)

## Kisa Kok Dosyalar

Satir sayisi dusuk olan kok dosyalar:
- `src/interactiveHelpers.py`: `5`
- `src/replLauncher.py`: `5`
- `src/task.py`: `5`
- `src/ink.py`: `6`
- `src/costHook.py`: `8`
- `src/projectOnboardingState.py`: `10`
- `src/tasks.py`: `11`
- `src/cost_tracker.py`: `13`
- `src/query.py`: `13`

Bu dosyalar veri sinifi, kucuk helper veya kisa sarmalayici niteligindedir.

Kaynak:
- [src/interactiveHelpers.py](/home/eren/Desktop/claw-code/src/interactiveHelpers.py)
- [src/replLauncher.py](/home/eren/Desktop/claw-code/src/replLauncher.py)
- [src/task.py](/home/eren/Desktop/claw-code/src/task.py)
- [src/query.py](/home/eren/Desktop/claw-code/src/query.py)

## Import Merkezleri

Kok moduller arasinda en merkezi import noktasi `src/main.py` dosyasidir. Bu dosya su modullerden import yapar:
- `bootstrap_graph`
- `command_graph`
- `commands`
- `direct_modes`
- `parity_audit`
- `permissions`
- `port_manifest`
- `query_engine`
- `remote_runtime`
- `runtime`
- `session_store`
- `setup`
- `tool_pool`
- `tools`

Kaynak:
- [src/main.py#L5](/home/eren/Desktop/claw-code/src/main.py#L5)

`src/runtime.py` ikinci merkez dosyadir. Bu dosya su modullerden import yapar:
- `commands`
- `context`
- `history`
- `models`
- `query_engine`
- `setup`
- `system_init`
- `tools`
- `execution_registry`

Kaynak:
- [src/runtime.py#L5](/home/eren/Desktop/claw-code/src/runtime.py#L5)

`src/query_engine.py` da baglayici merkezlerden biridir. Bu dosya su modullerden import yapar:
- `commands`
- `models`
- `port_manifest`
- `session_store`
- `tools`
- `transcript`

Kaynak:
- [src/query_engine.py#L7](/home/eren/Desktop/claw-code/src/query_engine.py#L7)

## Kesin Sonuc

Kok dosya sekli, repodaki agirligin dort alanda toplandigini gosterir:
- CLI orkestrasyonu
- query/session katmani
- runtime route katmani
- parity audit katmani
