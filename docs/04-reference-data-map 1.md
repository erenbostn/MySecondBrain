# Reference Data Map

## Temel Dosyalar

`src/reference_data` altinda su temel snapshot dosyalari bulunur:
- `archive_surface_snapshot.json`
- `commands_snapshot.json`
- `tools_snapshot.json`
- `subsystems/*.json`

Kaynaklar:
- [src/reference_data/__init__.py#L1](/home/eren/Desktop/claw-code/src/reference_data/__init__.py#L1)
- [src/reference_data/archive_surface_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/archive_surface_snapshot.json)
- [src/reference_data/commands_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/commands_snapshot.json)
- [src/reference_data/tools_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/tools_snapshot.json)

## `archive_surface_snapshot.json`

Bu dosya su alanlari tasir:
- `archive_root`
- `root_files`
- `root_dirs`
- `total_ts_like_files`
- `command_entry_count`
- `tool_entry_count`

Mevcut snapshot degerleri:
- `total_ts_like_files`: `1902`
- `command_entry_count`: `207`
- `tool_entry_count`: `184`

Kaynak:
- [src/reference_data/archive_surface_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/archive_surface_snapshot.json)

## `commands_snapshot.json`

Bu dosya bir JSON liste tutar. Her kayitta su alanlar vardir:
- `name`
- `source_hint`
- `responsibility`

`src/commands.py` bu dosyayi okuyup `PortingModule` listesine cevirir.

Kaynaklar:
- [src/reference_data/commands_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/commands_snapshot.json)
- [src/commands.py#L22](/home/eren/Desktop/claw-code/src/commands.py#L22)

## `tools_snapshot.json`

Bu dosya da bir JSON liste tutar. Her kayitta su alanlar vardir:
- `name`
- `source_hint`
- `responsibility`

`src/tools.py` bu dosyayi okuyup `PortingModule` listesine cevirir.

Kaynaklar:
- [src/reference_data/tools_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/tools_snapshot.json)
- [src/tools.py#L23](/home/eren/Desktop/claw-code/src/tools.py#L23)

## `subsystems/*.json`

Her subsystem JSON dosyasi su alanlari tasir:
- `archive_name`
- `package_name`
- `module_count`
- `sample_files`

Ornek olarak `assistant.json` dosyasinda:
- `archive_name`: `assistant`
- `package_name`: `assistant`
- `module_count`: `1`
- `sample_files`: `assistant/sessionHistory.ts`

Kaynak:
- [src/reference_data/subsystems/assistant.json](/home/eren/Desktop/claw-code/src/reference_data/subsystems/assistant.json)

## Kod Tarafindaki Kullanim

Reference data kullanimi iki seviyededir:

1. Ana snapshot kullanimi
- `src/commands.py` -> `commands_snapshot.json`
- `src/tools.py` -> `tools_snapshot.json`
- `src/parity_audit.py` -> `archive_surface_snapshot.json`, `commands_snapshot.json`, `tools_snapshot.json`

2. Alt paket snapshot kullanimi
- `src/assistant/__init__.py` gibi alt paketler kendi `subsystems/<paket>.json` dosyasini okur

Kaynaklar:
- [src/commands.py#L10](/home/eren/Desktop/claw-code/src/commands.py#L10)
- [src/tools.py#L11](/home/eren/Desktop/claw-code/src/tools.py#L11)
- [src/parity_audit.py#L9](/home/eren/Desktop/claw-code/src/parity_audit.py#L9)
- [src/assistant/__init__.py#L8](/home/eren/Desktop/claw-code/src/assistant/__init__.py#L8)

## Kesin Sonuc

`src/reference_data` bu reponun merkez veri katmanidir. Komut envanteri, tool envanteri, parity sayilari ve alt sistem metadata'si bu klasorde tutulur.
