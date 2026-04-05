# Repo Overview

## Bu Repo Nedir

Bu repo, Python ile yazilmis bir porting workspace'tir. README bunu dogrudan "clean-room Python rewrite" ve "Python porting workspace" olarak tanimliyor. Ana CLI giris noktasi `src/main.py` dosyasidir.

Kaynaklar:
- [README.md#L28](/home/eren/Desktop/claw-code/README.md#L28)
- [README.md#L56](/home/eren/Desktop/claw-code/README.md#L56)
- [src/main.py#L21](/home/eren/Desktop/claw-code/src/main.py#L21)

## Repo Yapisi

Kok dizinde su yapilar var:
- `src`
- `tests`
- `assets`
- `.github`

`.github` altinda yalnizca funding dosyasi bulunuyor. Workflow dosyasi bulunmuyor.

Kaynaklar:
- [.github/FUNDING.yml](/home/eren/Desktop/claw-code/.github/FUNDING.yml)
- [tests/test_porting_workspace.py#L15](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L15)

## Paketleme Durumu

Repoda `package.json`, `pyproject.toml`, `requirements.txt` ve `setup.cfg` dosyalari yok. README'de verilen kullanim ornekleri dogrudan `python3 -m src.main ...` ve `python3 -m unittest ...` komutlaridir.

Kaynaklar:
- [README.md#L103](/home/eren/Desktop/claw-code/README.md#L103)
- [README.md#L121](/home/eren/Desktop/claw-code/README.md#L121)

## CLI Yuzeyi

Ana komut yuzeyi `src/main.py` icinde tanimlidir. Dosya, `summary`, `manifest`, `parity-audit`, `setup-report`, `command-graph`, `tool-pool`, `commands`, `tools`, `route`, `run-session`, `turn-loop`, `flush-transcript`, `load-session`, `remote-mode`, `ssh-mode`, `teleport-mode`, `direct-connect-mode`, `deep-link-mode`, `show-command`, `show-tool`, `exec-command` ve `exec-tool` alt komutlarini tanimlar.

Kaynak:
- [src/main.py#L21](/home/eren/Desktop/claw-code/src/main.py#L21)

## Temel Mimari Gercegi

Bu repoda komut ve tool envanteri JSON snapshot dosyalarindan yuklenir.
- `src/commands.py`, `src/reference_data/commands_snapshot.json` dosyasini okur.
- `src/tools.py`, `src/reference_data/tools_snapshot.json` dosyasini okur.

`execute_command` ve `execute_tool` gercek islem yapmaz; "Mirrored ... would handle ..." metni dondurur. `execution_registry.py` da ayni temsil mantigini kullanir.

Kaynaklar:
- [src/commands.py#L10](/home/eren/Desktop/claw-code/src/commands.py#L10)
- [src/commands.py#L22](/home/eren/Desktop/claw-code/src/commands.py#L22)
- [src/commands.py#L75](/home/eren/Desktop/claw-code/src/commands.py#L75)
- [src/tools.py#L11](/home/eren/Desktop/claw-code/src/tools.py#L11)
- [src/tools.py#L23](/home/eren/Desktop/claw-code/src/tools.py#L23)
- [src/tools.py#L81](/home/eren/Desktop/claw-code/src/tools.py#L81)
- [src/execution_registry.py#L9](/home/eren/Desktop/claw-code/src/execution_registry.py#L9)
- [src/execution_registry.py#L47](/home/eren/Desktop/claw-code/src/execution_registry.py#L47)
