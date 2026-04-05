# Static Shape

## Kisa Ozet

Kok seviyedeki Python modullerinin buyuk bolumu cok kisadir. En buyuk merkez dosyalar `main.py`, `query_engine.py`, `runtime.py` ve `parity_audit.py` dosyalaridir.

## En Buyuk Kok Moduller

Satir sayisina gore en buyuk kok moduller:
- `src/main.py`: 213 satir
- `src/query_engine.py`: 193 satir
- `src/runtime.py`: 192 satir
- `src/parity_audit.py`: 138 satir
- `src/tools.py`: 96 satir
- `src/commands.py`: 90 satir
- `src/setup.py`: 77 satir

Kaynaklar:
- [src/main.py](/home/eren/Desktop/claw-code/src/main.py)
- [src/query_engine.py](/home/eren/Desktop/claw-code/src/query_engine.py)
- [src/runtime.py](/home/eren/Desktop/claw-code/src/runtime.py)
- [src/parity_audit.py](/home/eren/Desktop/claw-code/src/parity_audit.py)

## Cok Kisa Kok Moduller

Su kok moduller 15 satir veya daha kisadir:
- `src/interactiveHelpers.py`
- `src/replLauncher.py`
- `src/task.py`
- `src/ink.py`
- `src/costHook.py`
- `src/projectOnboardingState.py`
- `src/tasks.py`
- `src/cost_tracker.py`
- `src/query.py`
- `src/Tool.py`
- `src/dialogLaunchers.py`

Bu dosyalarin cogu tek helper, tek veri sinifi veya sabit tanim modulu olarak yazilmistir.

Kaynaklar:
- [src/interactiveHelpers.py](/home/eren/Desktop/claw-code/src/interactiveHelpers.py)
- [src/replLauncher.py](/home/eren/Desktop/claw-code/src/replLauncher.py)
- [src/task.py](/home/eren/Desktop/claw-code/src/task.py)
- [src/Tool.py](/home/eren/Desktop/claw-code/src/Tool.py)

## Import Merkezi

Import listesine gore en yogun merkez baglanti noktasi `src/main.py` dosyasidir. `src/runtime.py` ve `src/query_engine.py` ikinci merkezlerdir.

Kaynaklar:
- [src/main.py#L5](/home/eren/Desktop/claw-code/src/main.py#L5)
- [src/runtime.py#L5](/home/eren/Desktop/claw-code/src/runtime.py#L5)
- [src/query_engine.py#L7](/home/eren/Desktop/claw-code/src/query_engine.py#L7)

## Net Kırık Bag

`src/task.py` kendi icinden kendini import eder. Bu, kok moduller arasindaki tek acik self-import sorunudur.

Kaynak:
- [src/task.py#L3](/home/eren/Desktop/claw-code/src/task.py#L3)
