# Module Surface Map

## Ust Seviye Kod Dosyalari

`src/` kokunde hem davranis dosyalari hem de alias/temsil dosyalari bulunur. Dogrudan inceledigim kesin dosyalar:
- `main.py`
- `commands.py`
- `tools.py`
- `query_engine.py`
- `runtime.py`
- `setup.py`
- `parity_audit.py`
- `execution_registry.py`
- `history.py`
- `transcript.py`
- `session_store.py`
- `QueryEngine.py`
- `Tool.py`
- `task.py`
- `tasks.py`

Kaynak:
- [src/main.py](/home/eren/Desktop/claw-code/src/main.py)

## Snapshot Tabanli Alt Paketler

Toplam `29` alt paket `reference_data/subsystems/*.json` dosyalarina baglidir. Bu paketler `SNAPSHOT_PATH`, `_SNAPSHOT`, `ARCHIVE_NAME`, `MODULE_COUNT`, `SAMPLE_FILES` ve `PORTING_NOTE` desenini kullanir.

Ornek:
- `src/assistant/__init__.py`

Kaynaklar:
- [src/assistant/__init__.py#L8](/home/eren/Desktop/claw-code/src/assistant/__init__.py#L8)

Snapshot tabanli paketler:
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
- [src/assistant/__init__.py](/home/eren/Desktop/claw-code/src/assistant/__init__.py)
- [src/bootstrap/__init__.py](/home/eren/Desktop/claw-code/src/bootstrap/__init__.py)
- [src/bridge/__init__.py](/home/eren/Desktop/claw-code/src/bridge/__init__.py)
- [src/buddy/__init__.py](/home/eren/Desktop/claw-code/src/buddy/__init__.py)
- [src/cli/__init__.py](/home/eren/Desktop/claw-code/src/cli/__init__.py)
- [src/components/__init__.py](/home/eren/Desktop/claw-code/src/components/__init__.py)
- [src/constants/__init__.py](/home/eren/Desktop/claw-code/src/constants/__init__.py)
- [src/coordinator/__init__.py](/home/eren/Desktop/claw-code/src/coordinator/__init__.py)
- [src/entrypoints/__init__.py](/home/eren/Desktop/claw-code/src/entrypoints/__init__.py)
- [src/hooks/__init__.py](/home/eren/Desktop/claw-code/src/hooks/__init__.py)
- [src/keybindings/__init__.py](/home/eren/Desktop/claw-code/src/keybindings/__init__.py)
- [src/memdir/__init__.py](/home/eren/Desktop/claw-code/src/memdir/__init__.py)
- [src/migrations/__init__.py](/home/eren/Desktop/claw-code/src/migrations/__init__.py)
- [src/moreright/__init__.py](/home/eren/Desktop/claw-code/src/moreright/__init__.py)
- [src/native_ts/__init__.py](/home/eren/Desktop/claw-code/src/native_ts/__init__.py)
- [src/outputStyles/__init__.py](/home/eren/Desktop/claw-code/src/outputStyles/__init__.py)
- [src/plugins/__init__.py](/home/eren/Desktop/claw-code/src/plugins/__init__.py)
- [src/remote/__init__.py](/home/eren/Desktop/claw-code/src/remote/__init__.py)
- [src/schemas/__init__.py](/home/eren/Desktop/claw-code/src/schemas/__init__.py)
- [src/screens/__init__.py](/home/eren/Desktop/claw-code/src/screens/__init__.py)
- [src/server/__init__.py](/home/eren/Desktop/claw-code/src/server/__init__.py)
- [src/services/__init__.py](/home/eren/Desktop/claw-code/src/services/__init__.py)
- [src/skills/__init__.py](/home/eren/Desktop/claw-code/src/skills/__init__.py)
- [src/state/__init__.py](/home/eren/Desktop/claw-code/src/state/__init__.py)
- [src/types/__init__.py](/home/eren/Desktop/claw-code/src/types/__init__.py)
- [src/upstreamproxy/__init__.py](/home/eren/Desktop/claw-code/src/upstreamproxy/__init__.py)
- [src/utils/__init__.py](/home/eren/Desktop/claw-code/src/utils/__init__.py)
- [src/vim/__init__.py](/home/eren/Desktop/claw-code/src/vim/__init__.py)
- [src/voice/__init__.py](/home/eren/Desktop/claw-code/src/voice/__init__.py)

## Runtime Yardimci Moduller

Kesin olarak inceledigim runtime yardimci moduller:
- `history.py`: `HistoryEvent` ve `HistoryLog`
- `transcript.py`: `TranscriptStore`
- `query.py`: `QueryRequest` ve `QueryResponse`
- `session_store.py`: `StoredSession`, `save_session`, `load_session`
- `cost_tracker.py`: `CostTracker`
- `costHook.py`: `apply_cost_hook`
- `projectOnboardingState.py`: `ProjectOnboardingState`
- `dialogLaunchers.py`: `DialogLauncher` ve `DEFAULT_DIALOGS`
- `interactiveHelpers.py`: `bulletize`
- `ink.py`: `render_markdown_panel`
- `replLauncher.py`: `build_repl_banner`

Bu dosyalar veri siniflari ve basit yardimci metodlar icerir.

Kaynaklar:
- [src/history.py#L6](/home/eren/Desktop/claw-code/src/history.py#L6)
- [src/transcript.py#L6](/home/eren/Desktop/claw-code/src/transcript.py#L6)
- [src/query.py#L6](/home/eren/Desktop/claw-code/src/query.py#L6)
- [src/session_store.py#L8](/home/eren/Desktop/claw-code/src/session_store.py#L8)
- [src/cost_tracker.py](/home/eren/Desktop/claw-code/src/cost_tracker.py)
- [src/costHook.py](/home/eren/Desktop/claw-code/src/costHook.py)
- [src/projectOnboardingState.py](/home/eren/Desktop/claw-code/src/projectOnboardingState.py)
- [src/dialogLaunchers.py](/home/eren/Desktop/claw-code/src/dialogLaunchers.py)
- [src/interactiveHelpers.py](/home/eren/Desktop/claw-code/src/interactiveHelpers.py)
- [src/ink.py](/home/eren/Desktop/claw-code/src/ink.py)
- [src/replLauncher.py](/home/eren/Desktop/claw-code/src/replLauncher.py)

## Alias ve Sarmalayici Dosyalar

`src/QueryEngine.py`, `QueryEnginePort` uzerine `QueryEngineRuntime` sinifini ekler ve route sonucunu Markdown olarak dondurur.

`src/Tool.py`, iki sabit `ToolDefinition` nesnesi iceren kucuk bir tanim dosyasidir.

`src/__init__.py`, port manifest, parity audit, runtime, session store ve command/tool backlog yuzeylerini package export olarak disari acar.

Kaynaklar:
- [src/QueryEngine.py](/home/eren/Desktop/claw-code/src/QueryEngine.py)
- [src/Tool.py](/home/eren/Desktop/claw-code/src/Tool.py)
- [src/__init__.py](/home/eren/Desktop/claw-code/src/__init__.py)

## Kesin Sorunlu Alan

`src/task.py` ve `src/tasks.py` dosyalari `PortingTask` sinifina baglidir. `src/task.py` dosyasinda kendi icinden kendine import vardir ve repo icinde `PortingTask` tanimi yoktur.

Kaynaklar:
- [src/task.py#L3](/home/eren/Desktop/claw-code/src/task.py#L3)
- [src/tasks.py#L3](/home/eren/Desktop/claw-code/src/tasks.py#L3)
