# Test Surface

## Test Yapisi

Repo icinde tek test dosyasi vardir:
- `tests/test_porting_workspace.py`

Bu dosya `unittest.TestCase` tabanli bir sinif icerir.

Kaynaklar:
- [tests/test_porting_workspace.py#L15](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L15)

## Test Edilen Basliklar

Bu test dosyasi su alanlari kapsar:
- port manifest
- query engine summary
- `summary` CLI
- `parity-audit` CLI
- snapshot boyutlari
- `commands` ve `tools` CLI
- subsystem package metadata exportlari
- `route`, `show-command`, `show-tool` CLI
- bootstrap/session akislari
- `exec-command`, `exec-tool` CLI
- setup report ve registry filtreleri
- session yukleme
- tool permission filtering
- turn loop
- remote/ssh/teleport modlari
- transcript flush
- command graph ve tool pool
- deferred init alanlari
- execution registry
- bootstrap graph ve direct mode'lar

Kaynaklar:
- [tests/test_porting_workspace.py#L16](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L16)
- [tests/test_porting_workspace.py#L57](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L57)
- [tests/test_porting_workspace.py#L81](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L81)
- [tests/test_porting_workspace.py#L123](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L123)
- [tests/test_porting_workspace.py#L176](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L176)
- [tests/test_porting_workspace.py#L196](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L196)
- [tests/test_porting_workspace.py#L229](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L229)

## Kesin Sayilar ve Esikler

Test dosyasinda dogrudan yazili esikler:
- manifest toplam Python dosyasi `>= 20`
- komut snapshot boyutu `>= 150`
- tool snapshot boyutu `>= 100`
- archive varsa directory coverage `>= 28`
- archive varsa command entry coverage `>= 150`
- archive varsa tool entry coverage `>= 100`

Kaynaklar:
- [tests/test_porting_workspace.py#L16](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L16)
- [tests/test_porting_workspace.py#L45](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L45)
- [tests/test_porting_workspace.py#L53](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L53)

## Test Dosyasinin Net Ozelligi

Test dosyasi dogrudan `subprocess.run([sys.executable, '-m', 'src.main', ...])` kullanan cok sayida CLI testi icerir.

Kaynaklar:
- [tests/test_porting_workspace.py#L27](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L27)
- [tests/test_porting_workspace.py#L57](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L57)
- [tests/test_porting_workspace.py#L186](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L186)
- [tests/test_porting_workspace.py#L238](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py#L238)
