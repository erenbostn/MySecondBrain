# Confirmed Facts

Bu dosyada sadece dogrudan kaynak koddan dogrulanan bilgiler yazilir.

## Kodun Ne Yaptigi

- Ana CLI giris noktasi `src/main.py` dosyasidir.
- Komut envanteri `src/reference_data/commands_snapshot.json` dosyasindan yuklenir.
- Tool envanteri `src/reference_data/tools_snapshot.json` dosyasindan yuklenir.
- Session verisi `.port_sessions` klasorune JSON olarak kaydedilir.
- Parity audit, `archive/claude_code_ts_snapshot/src` yolunu referans alir.
- `QueryEnginePort.submit_message`, prompt ve eslesen komut/tool adlarini ozet satirlarina cevirir.
- `QueryEnginePort.stream_submit_message`, `message_start`, `command_match`, `tool_match`, `permission_denial`, `message_delta` ve `message_stop` eventleri uretir.

Kaynaklar:
- [src/main.py#L21](/home/eren/Desktop/claw-code/src/main.py#L21)
- [src/commands.py#L10](/home/eren/Desktop/claw-code/src/commands.py#L10)
- [src/tools.py#L11](/home/eren/Desktop/claw-code/src/tools.py#L11)
- [src/session_store.py#L16](/home/eren/Desktop/claw-code/src/session_store.py#L16)
- [src/parity_audit.py#L7](/home/eren/Desktop/claw-code/src/parity_audit.py#L7)
- [src/query_engine.py#L61](/home/eren/Desktop/claw-code/src/query_engine.py#L61)
- [src/query_engine.py#L106](/home/eren/Desktop/claw-code/src/query_engine.py#L106)

## Kodun Ne Yapmadigi

- `execute_command` gercek komut calistirmaz.
- `execute_tool` gercek tool calistirmaz.
- `prefetch.py` icindeki prefetch fonksiyonlari gercek entegrasyon yerine simule edilmis sonuc dondurur.
- `remote`, `ssh`, `teleport`, `direct-connect` ve `deep-link` modlari rapor nesnesi dondurur.
- `replLauncher.py`, interaktif REPL baslatmaz; sabit bir banner metni dondurur.

Kaynaklar:
- [src/commands.py#L75](/home/eren/Desktop/claw-code/src/commands.py#L75)
- [src/tools.py#L81](/home/eren/Desktop/claw-code/src/tools.py#L81)
- [src/prefetch.py#L14](/home/eren/Desktop/claw-code/src/prefetch.py#L14)
- [src/prefetch.py#L18](/home/eren/Desktop/claw-code/src/prefetch.py#L18)
- [src/prefetch.py#L22](/home/eren/Desktop/claw-code/src/prefetch.py#L22)
- [src/remote_runtime.py#L16](/home/eren/Desktop/claw-code/src/remote_runtime.py#L16)
- [src/remote_runtime.py#L20](/home/eren/Desktop/claw-code/src/remote_runtime.py#L20)
- [src/remote_runtime.py#L24](/home/eren/Desktop/claw-code/src/remote_runtime.py#L24)
- [src/direct_modes.py#L16](/home/eren/Desktop/claw-code/src/direct_modes.py#L16)
- [src/direct_modes.py#L20](/home/eren/Desktop/claw-code/src/direct_modes.py#L20)
- [src/replLauncher.py](/home/eren/Desktop/claw-code/src/replLauncher.py)

## Kesin Sorun

- `src/task.py` kiriktir. Dosya kendi icinden kendini import ediyor.
- `src/tasks.py` da ayni kirik importa baglidir.
- Repo icinde `PortingTask` sinifinin tanimi yoktur.

Kaynaklar:
- [src/task.py#L3](/home/eren/Desktop/claw-code/src/task.py#L3)
- [src/tasks.py#L3](/home/eren/Desktop/claw-code/src/tasks.py#L3)
