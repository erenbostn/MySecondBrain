# Reference Data And Package Map

## Reference Data Yapisi

`src/reference_data/` altinda su ana dosyalar bulunur:
- `archive_surface_snapshot.json`
- `commands_snapshot.json`
- `tools_snapshot.json`
- `subsystems/*.json`

`subsystems` klasoru altinda 29 adet JSON dosyasi vardir.

Kaynaklar:
- [src/reference_data/archive_surface_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/archive_surface_snapshot.json)
- [src/reference_data/commands_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/commands_snapshot.json)
- [src/reference_data/tools_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/tools_snapshot.json)

## Snapshot Dosyalarinin Kullanimi

- `src/commands.py`, `commands_snapshot.json` dosyasini okur.
- `src/tools.py`, `tools_snapshot.json` dosyasini okur.
- `src/parity_audit.py`, `archive_surface_snapshot.json` dosyasini okur.

Kaynaklar:
- [src/commands.py#L10](/home/eren/Desktop/claw-code/src/commands.py#L10)
- [src/commands.py#L22](/home/eren/Desktop/claw-code/src/commands.py#L22)
- [src/tools.py#L11](/home/eren/Desktop/claw-code/src/tools.py#L11)
- [src/tools.py#L23](/home/eren/Desktop/claw-code/src/tools.py#L23)
- [src/parity_audit.py#L9](/home/eren/Desktop/claw-code/src/parity_audit.py#L9)
- [src/parity_audit.py#L121](/home/eren/Desktop/claw-code/src/parity_audit.py#L121)

## Archive Snapshot Sayilari

`archive_surface_snapshot.json` icinde su sayilar yazilidir:
- `total_ts_like_files = 1902`
- `command_entry_count = 207`
- `tool_entry_count = 184`

Kaynak:
- [src/reference_data/archive_surface_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/archive_surface_snapshot.json)

## Subsystem Snapshot Semasi

Subsystem JSON dosyalari ayni temel alanlari tasir:
- `archive_name`
- `package_name`
- `module_count`
- `sample_files`

Ornek:
- [src/reference_data/subsystems/assistant.json](/home/eren/Desktop/claw-code/src/reference_data/subsystems/assistant.json)

## Alt Paketlerin Yapisi

`src/` altinda birinci seviyede 30 adet alt paket vardir. Bunlarin 29'u sadece tek bir `__init__.py` dosyasindan olusur. Tek istisna `src/reference_data` paketidir.

Kaynaklar:
- [src/assistant/__init__.py#L1](/home/eren/Desktop/claw-code/src/assistant/__init__.py#L1)
- [src/reference_data](/home/eren/Desktop/claw-code/src/reference_data)

## Placeholder Paket Deseni

Alt paketlerin `__init__.py` dosyalari ortak bir desen kullanir:
- `reference_data/subsystems/<ad>.json` dosyasini okur
- `ARCHIVE_NAME` sabitini olusturur
- `MODULE_COUNT` sabitini olusturur
- `SAMPLE_FILES` sabitini olusturur
- `PORTING_NOTE` sabitini olusturur

Ornek:
- [src/assistant/__init__.py#L8](/home/eren/Desktop/claw-code/src/assistant/__init__.py#L8)

## Paket ve Snapshot Adlari

`src/reference_data/subsystems/*.json` dosya adlari ile `src/` altindaki alt paket adlari eslesen seti olusturur. Bu eslesen paketler sunlardir:
- `assistant`
- `bootstrap`
- `bridge`
- `buddy`
- `cli`
- `components`
- `constants`
- `coordinator`
- `entrypoints`
- `hooks`
- `keybindings`
- `memdir`
- `migrations`
- `moreright`
- `native_ts`
- `outputStyles`
- `plugins`
- `remote`
- `schemas`
- `screens`
- `server`
- `services`
- `skills`
- `state`
- `types`
- `upstreamproxy`
- `utils`
- `vim`
- `voice`

Kaynaklar:
- [src/reference_data/subsystems](/home/eren/Desktop/claw-code/src/reference_data/subsystems)
- [src/assistant](/home/eren/Desktop/claw-code/src/assistant)

