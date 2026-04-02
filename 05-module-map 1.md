# Module Map

## Merkez Moduller

Kok seviyede birbirine baglanan merkez moduller sunlardir:
- `src/main.py`
- `src/runtime.py`
- `src/query_engine.py`
- `src/commands.py`
- `src/tools.py`

`src/main.py`, bu modullerin cogu dahil olmak uzere CLI akisinin merkez baglanti noktasi olarak yazilmistir.

Kaynaklar:
- [src/main.py#L5](/home/eren/Desktop/claw-code/src/main.py#L5)
- [src/runtime.py#L5](/home/eren/Desktop/claw-code/src/runtime.py#L5)
- [src/query_engine.py#L7](/home/eren/Desktop/claw-code/src/query_engine.py#L7)

## Kisa Veri ve Helper Modulleri

Asagidaki moduller kisa veri yapisi veya helper fonksiyon icerir:
- `src/query.py`: `QueryRequest` ve `QueryResponse`
- `src/history.py`: `HistoryEvent` ve `HistoryLog`
- `src/transcript.py`: `TranscriptStore`
- `src/cost_tracker.py`: `CostTracker`
- `src/costHook.py`: `apply_cost_hook`
- `src/interactiveHelpers.py`: `bulletize`
- `src/ink.py`: `render_markdown_panel`
- `src/projectOnboardingState.py`: `ProjectOnboardingState`

Kaynaklar:
- [src/query.py#L6](/home/eren/Desktop/claw-code/src/query.py#L6)
- [src/history.py#L6](/home/eren/Desktop/claw-code/src/history.py#L6)
- [src/transcript.py#L6](/home/eren/Desktop/claw-code/src/transcript.py#L6)
- [src/cost_tracker.py#L6](/home/eren/Desktop/claw-code/src/cost_tracker.py#L6)
- [src/costHook.py#L6](/home/eren/Desktop/claw-code/src/costHook.py#L6)
- [src/interactiveHelpers.py#L4](/home/eren/Desktop/claw-code/src/interactiveHelpers.py#L4)
- [src/ink.py#L4](/home/eren/Desktop/claw-code/src/ink.py#L4)
- [src/projectOnboardingState.py#L6](/home/eren/Desktop/claw-code/src/projectOnboardingState.py#L6)

## Placeholder veya Sabit Tanim Modulleri

Asagidaki moduller sabit veya cok kisa placeholder davranisi icerir:
- `src/Tool.py`: iki adet `ToolDefinition` ile varsayilan arac listesi
- `src/dialogLaunchers.py`: iki adet `DialogLauncher` ile varsayilan dialog listesi
- `src/replLauncher.py`: etkileşimli olmayan REPL banner metni
- `src/remote_runtime.py`: `remote`, `ssh`, `teleport` rapor nesneleri
- `src/direct_modes.py`: `direct-connect` ve `deep-link` rapor nesneleri
- `src/bootstrap_graph.py`: sabit bootstrap stage listesi

Kaynaklar:
- [src/Tool.py#L6](/home/eren/Desktop/claw-code/src/Tool.py#L6)
- [src/dialogLaunchers.py#L6](/home/eren/Desktop/claw-code/src/dialogLaunchers.py#L6)
- [src/replLauncher.py#L4](/home/eren/Desktop/claw-code/src/replLauncher.py#L4)
- [src/remote_runtime.py#L16](/home/eren/Desktop/claw-code/src/remote_runtime.py#L16)
- [src/direct_modes.py#L16](/home/eren/Desktop/claw-code/src/direct_modes.py#L16)
- [src/bootstrap_graph.py#L16](/home/eren/Desktop/claw-code/src/bootstrap_graph.py#L16)

## Paket Disa Aktarma Katmani

`src/__init__.py`, bu paketin disa actigi ana sembolleri bir araya getirir. Bu dosya bos degildir; parity, manifest, runtime, query engine, session store ve tool/command backlog sembollerini re-export eder.

Kaynak:
- [src/__init__.py#L3](/home/eren/Desktop/claw-code/src/__init__.py#L3)

## Kirik Moduller

`src/task.py` kendi icinden kendini import eder. `src/tasks.py` de ayni importa baglidir. Repo icinde `PortingTask` tanimi yoktur.

Kaynaklar:
- [src/task.py#L3](/home/eren/Desktop/claw-code/src/task.py#L3)
- [src/tasks.py#L3](/home/eren/Desktop/claw-code/src/tasks.py#L3)
