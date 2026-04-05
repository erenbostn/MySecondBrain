# Architecture Notes

## 1. Merkez Orkestrasyon Noktasi

Repodaki ana orkestrasyon dosyasi `src/main.py` dosyasidir. CLI parser burada kurulur ve tum alt komutlar burada baglanir.

Kaynaklar:
- [src/main.py#L21](/home/eren/Desktop/claw-code/src/main.py#L21)

## 2. Workspace Ozet Katmani

`src/port_manifest.py`, `src/` altindaki Python dosyalarini sayar ve top-level module listesini uretir. `src/context.py`, `src`, `tests`, `assets` ve `archive/claude_code_ts_snapshot/src` yollarini tek bir `PortContext` nesnesinde toplar.

Kaynaklar:
- [src/port_manifest.py#L30](/home/eren/Desktop/claw-code/src/port_manifest.py#L30)
- [src/context.py#L19](/home/eren/Desktop/claw-code/src/context.py#L19)

## 3. Snapshot Kaynaklari

Komut ve tool envanteri dogrudan JSON snapshot dosyalarindan gelir.
- `src/commands.py` -> `src/reference_data/commands_snapshot.json`
- `src/tools.py` -> `src/reference_data/tools_snapshot.json`

Kaynaklar:
- [src/commands.py#L10](/home/eren/Desktop/claw-code/src/commands.py#L10)
- [src/tools.py#L11](/home/eren/Desktop/claw-code/src/tools.py#L11)

## 4. Komut ve Tool Davranisi

`execute_command` ve `execute_tool` gercek komut veya tool calistirmaz. Ikisi de yalnizca temsil metni dondurur.

`src/execution_registry.py` dosyasindaki `MirroredCommand.execute` ve `MirroredTool.execute` metodlari da ayni temsil fonksiyonlarini cagirir.

Kaynaklar:
- [src/commands.py#L75](/home/eren/Desktop/claw-code/src/commands.py#L75)
- [src/tools.py#L81](/home/eren/Desktop/claw-code/src/tools.py#L81)
- [src/execution_registry.py#L14](/home/eren/Desktop/claw-code/src/execution_registry.py#L14)
- [src/execution_registry.py#L23](/home/eren/Desktop/claw-code/src/execution_registry.py#L23)

## 5. Query Engine

`src/query_engine.py`, manifest, command backlog ve tool backlog verilerini kullanarak turn ciktisi uretir. Session kimligi burada olusturulur. Session verisi `.port_sessions` altina JSON olarak yazilir.

Kaynaklar:
- [src/query_engine.py#L35](/home/eren/Desktop/claw-code/src/query_engine.py#L35)
- [src/query_engine.py#L61](/home/eren/Desktop/claw-code/src/query_engine.py#L61)
- [src/query_engine.py#L140](/home/eren/Desktop/claw-code/src/query_engine.py#L140)
- [src/session_store.py#L16](/home/eren/Desktop/claw-code/src/session_store.py#L16)

## 6. Runtime

`src/runtime.py`, context, setup, system init, execution registry ve query engine katmanlarini birlestirir. Route islemi `_score` fonksiyonunda goruldugu uzere token eslesmesine dayanir.

Kaynaklar:
- [src/runtime.py#L24](/home/eren/Desktop/claw-code/src/runtime.py#L24)
- [src/runtime.py#L176](/home/eren/Desktop/claw-code/src/runtime.py#L176)
- [src/runtime.py#L185](/home/eren/Desktop/claw-code/src/runtime.py#L185)

## 7. Setup ve Baslangic Katmani

`src/setup.py`, setup raporu uretir. `src/prefetch.py` icindeki butun prefetch fonksiyonlari simule edilmis sonuc nesnesi dondurur. `src/deferred_init.py`, trusted degeri `True` ise tum bayraklari `True`, `False` ise tum bayraklari `False` yapar.

Kaynaklar:
- [src/setup.py#L64](/home/eren/Desktop/claw-code/src/setup.py#L64)
- [src/prefetch.py#L14](/home/eren/Desktop/claw-code/src/prefetch.py#L14)
- [src/prefetch.py#L18](/home/eren/Desktop/claw-code/src/prefetch.py#L18)
- [src/prefetch.py#L22](/home/eren/Desktop/claw-code/src/prefetch.py#L22)
- [src/deferred_init.py#L23](/home/eren/Desktop/claw-code/src/deferred_init.py#L23)
- [src/system_init.py#L8](/home/eren/Desktop/claw-code/src/system_init.py#L8)

## 8. Graph ve Pool Katmani

`src/command_graph.py`, komutlari `builtins`, `plugin_like` ve `skill_like` olarak ayirir. `src/tool_pool.py`, `get_tools` sonucunu `ToolPool` nesnesine sarar. `src/bootstrap_graph.py`, bootstrap asamalarini sabit string listesi olarak tanimlar.

Kaynaklar:
- [src/command_graph.py#L29](/home/eren/Desktop/claw-code/src/command_graph.py#L29)
- [src/tool_pool.py#L28](/home/eren/Desktop/claw-code/src/tool_pool.py#L28)
- [src/bootstrap_graph.py#L16](/home/eren/Desktop/claw-code/src/bootstrap_graph.py#L16)

## 9. Mode Yuzeyleri

`src/remote_runtime.py` icindeki `remote`, `ssh` ve `teleport` modlari placeholder detay metni dondurur. `src/direct_modes.py` icindeki `direct-connect` ve `deep-link` modlari da sabit alanlara sahip rapor nesnesi dondurur.

Kaynaklar:
- [src/remote_runtime.py#L16](/home/eren/Desktop/claw-code/src/remote_runtime.py#L16)
- [src/remote_runtime.py#L20](/home/eren/Desktop/claw-code/src/remote_runtime.py#L20)
- [src/remote_runtime.py#L24](/home/eren/Desktop/claw-code/src/remote_runtime.py#L24)
- [src/direct_modes.py#L16](/home/eren/Desktop/claw-code/src/direct_modes.py#L16)
- [src/direct_modes.py#L20](/home/eren/Desktop/claw-code/src/direct_modes.py#L20)
