# Projenin Mantigi

Bu repo, tam bitmis bir son kullanici uygulamasi olmaktan cok, Python ile kurulmus bir **porting workspace**'tir.

Buradaki ana fikir su:

Bir referans sistem var. Bu referans sistemin TypeScript tarafindaki komutlari, tool'lari, klasor yapisi ve modulleri alinmis. Sonra bunlar Python tarafinda yeniden organize edilmis. Bu isleme bu repo icinde fiilen "port" deniyor.

Yani bu repo:
- referans sistemin yapisini kaydediyor
- bu yapinin Python tarafindaki karsiliklarini olusturuyor
- Python tarafinin referans sisteme ne kadar yaklastigini olcuyor
- bu yuzeyi CLI uzerinden okunabilir hale getiriyor

## Bu Repo Tam Olarak Ne Ise Yariyor

Bu repo, referans alinan agent/harness sistemini Python tarafinda modellemek icin kullaniliyor.

Bunu su sekilde yapiyor:

1. Referans sistemin komut listesini kaydediyor.
2. Referans sistemin tool listesini kaydediyor.
3. Referans sistemin klasor ve modul yuzeyini kaydediyor.
4. Python tarafinda bunlara karsilik gelen paketleri ve modulleri aciyor.
5. Python tarafinin referans yuzeye ne kadar uydugunu parity audit ile hesapliyor.

Buradaki onemli nokta su:

Bu repo sadece "bir seyi calistirmak" icin yazilmamis. Ayni zamanda "bir sistemin yapisini tasimak, temsil etmek ve belgelemek" icin yazilmis.

## Ana Mantik Nerede Kurulu

Bu repo tek bir merkezden aciliyor: [src/main.py](/home/eren/Desktop/claw-code/src/main.py)

Bu dosya:
- CLI parser'i kuruyor
- alt komutlari tanimliyor
- ilgili modullere yonlendiriyor

Yani repo icindeki ana giris kapisi burasi.

Bunun altinda en onemli merkez moduller sunlar:
- [src/main.py](/home/eren/Desktop/claw-code/src/main.py)
- [src/runtime.py](/home/eren/Desktop/claw-code/src/runtime.py)
- [src/query_engine.py](/home/eren/Desktop/claw-code/src/query_engine.py)
- [src/commands.py](/home/eren/Desktop/claw-code/src/commands.py)
- [src/tools.py](/home/eren/Desktop/claw-code/src/tools.py)
- [src/parity_audit.py](/home/eren/Desktop/claw-code/src/parity_audit.py)

Bu dosyalar bir araya geldiginde repo'nun ana mantigi ortaya cikiyor.

## Snapshot Nedir

Bu repoda "snapshot", referans sistemin kaydedilmis yuzeyidir.

Ornek olarak:
- hangi komutlar var
- hangi tool'lar var
- hangi klasorler var
- kac dosya var

Bu bilgi Python kodunun icine tek tek yazilmamis. Bunun yerine JSON dosyalarina kaydedilmis.

En onemli snapshot dosyalari sunlar:
- [src/reference_data/commands_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/commands_snapshot.json)
- [src/reference_data/tools_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/tools_snapshot.json)
- [src/reference_data/archive_surface_snapshot.json](/home/eren/Desktop/claw-code/src/reference_data/archive_surface_snapshot.json)

Yani repo once referans sistemi bir veri katmani olarak tutuyor, sonra Python kodu bu veriyi okuyarak ustune bir temsil katmani kuruyor.

## Port Nedir

Bu repoda "port", referans sistemin Python tarafina tasinmasidir.

Bu tasima her zaman "birebir ayni runtime" anlamina gelmiyor.

Bu repo icinde port daha cok su alanlarda yapiliyor:
- klasor yapisi
- modul adlari
- komut yuzeyi
- tool yuzeyi
- raporlar
- parity olcumu
- CLI uzerinden bu yapinin sunulmasi

Yani burada "Python portu" dedigimiz sey:

"Referans alinan TypeScript sistemin Python tarafinda yeniden kurulmus yapisal ve kismen davranissal karsiligi"

## Parity Nedir

Bu repoda "parity", Python tarafinin referans sisteme ne kadar yaklastiginin olcusudur.

Bu su sorulari cevaplar:
- referans sistemdeki kok dosyalarin Python karsiliklari var mi
- referans sistemdeki ust klasorlerin Python karsiliklari var mi
- command entry sayisi ne durumda
- tool entry sayisi ne durumda
- toplam dosya yuzeyi ne kadar karsilanmis

Bunu yapan kod:
- [src/parity_audit.py](/home/eren/Desktop/claw-code/src/parity_audit.py)

Bu dosya referans arsiv yoluna ve snapshot dosyalarina bakip oranlar hesapliyor.

Yani parity, "Python tarafi ne kadar benzemis" sorusunun cevabi.

## Commands ve Tools Katmani Ne Yapiyor

Burasi repo'nun en kritik noktalarindan biri.

[src/commands.py](/home/eren/Desktop/claw-code/src/commands.py) ve [src/tools.py](/home/eren/Desktop/claw-code/src/tools.py), komut ve tool listelerini JSON snapshot'lardan yukluyor.

Bu moduller:
- entry'leri okuyor
- `PortingModule` nesnelerine ceviriyor
- filtreleme yapiyor
- listeleme yapiyor
- tekil lookup yapiyor

Ama en onemli gercek su:

`execute_command` ve `execute_tool` gercek komut ya da gercek tool calistirmiyor. Bunlar temsil metni donduruyor.

Yani bu katmanin isi:
"Bu komut/tool burada temsil ediliyor"
demek.

Bu nedenle repo genis bir komut ve tool yuzeyi gosterse de, bu yuzeyin onemli bir bolumu metadata tabanli.

## Runtime ve Query Engine Ne Yapiyor

[src/query_engine.py](/home/eren/Desktop/claw-code/src/query_engine.py) ve [src/runtime.py](/home/eren/Desktop/claw-code/src/runtime.py), bu metadata katmanini daha "uygulama benzeri" bir akis icine koyuyor.

`query_engine.py`:
- workspace bilgisi aliyor
- command backlog ve tool backlog bilgisi topluyor
- oturum kimligi uretiyor
- mesaj/turn ozetleri cikartiyor
- session verisini `.port_sessions` altina yazabiliyor

`runtime.py`:
- context kuruyor
- setup bilgisini aliyor
- system init metni olusturuyor
- prompt icindeki kelimelere gore komut/tool eslestirmesi yapiyor
- bootstrap session raporu cikartiyor
- turn-loop mantigi kuruyor

Yani bu iki dosya, snapshot katmanini bir "temsil runtime'i" haline getiriyor.

## Eslestirme Mantigi Nasil Calisiyor

Bu repo icinde route mantigi akilli bir semantic engine degil.

[src/runtime.py](/home/eren/Desktop/claw-code/src/runtime.py) icinde gorulen haliyle:
- prompt token'lara ayriliyor
- command/tool metadata'si icindeki isimler, source hint'ler ve responsibility metinleri taraniyor
- eslesenler puanlaniyor

Yani eslestirme mantigi keyword tabanli.

Bu da repo'nun amacinin agirlikli olarak "temsil ve haritalama" oldugunu tekrar gosteriyor.

## Alt Paketler Neden Var

`src/` altinda cok sayida paket gorunuyor:
- `assistant`
- `bridge`
- `components`
- `services`
- `skills`
- `utils`
- vb.

Ama bunlarin buyuk bolumu gercek alt modullerle dolu degil.

29 alt paket sadece `__init__.py` tabanli placeholder paket olarak yazilmis. Bu `__init__.py` dosyalari kendi `subsystems/*.json` snapshot dosyasini okuyup su sabitleri uretiyor:
- `ARCHIVE_NAME`
- `MODULE_COUNT`
- `SAMPLE_FILES`
- `PORTING_NOTE`

Yani bu paketlerin temel isi su:

"Referans sistemde bu alt sistem vardi; Python tarafinda da burada temsil ediliyor."

Bu paketler genis bir mimari yuzeyin Python tarafinda yer tutuculari gibi kullaniliyor.

## reference_data Neden Bu Kadar Onemli

`src/reference_data/` bu repo'nun merkezi veri katmanidir.

Burada:
- command snapshot'lari
- tool snapshot'lari
- archive surface snapshot'i
- subsystem snapshot'lari
tutuluyor.

Yani repo'nun "bildigi seylerin" buyuk bolumu burada.

Kod tarafi ise bu verileri okuyup:
- rapor
- ozet
- parity sonucu
- command/tool listesi
- placeholder package bilgisi
uretiyor.

Bu nedenle bu repo icinde asagidaki cumle dogrudur:

"Kodun onemli bir kismi behavior-first degil, metadata-first yazilmis."

## Testler Ne Yapiyor

Test yuzeyi tek dosya:
- [tests/test_porting_workspace.py](/home/eren/Desktop/claw-code/tests/test_porting_workspace.py)

Bu test dosyasi:
- CLI komutlarini
- summary/parity/setup benzeri ciktilari
- snapshot sayilarini
- command/tool registry davranisini
kontrol ediyor.

Yani testler "bu yuzey var mi, beklenen metni donduruyor mu?" sorusunu iyi kontrol ediyor.

Bu da repo'nun ana hedefiyle uyumlu:
yuzeyin, temsillerin ve porting workspace'in tutarli kalmasi.

## Bu Repo Neden Ilginc

Bu repo siradan bir Python uygulamasi degil.

Ilginc cunku:
- sadece bir uygulama sunmuyor
- bir sistemin nasil yeniden kuruldugunu gosteriyor
- bir referans arsivin Python tarafinda nasil haritalandigini gosteriyor
- parity mantigi ile "ne kadar tasinmis" sorusunu olcuyor

Yani bu repo hem kod tabani, hem de teknik harita gibi calisiyor.

## Bu Repo Su Anda Ne Degil

Bu repo su anda:
- tam uretim runtime'i degil
- gercek command executor degil
- gercek tool executor degil
- tam dolu alt paket agaci degil

Bunu koddan net olarak biliyoruz cunku:
- command/tool execution temsil metni donduruyor
- prefetch katmani simule edilmis
- mode katmanlari placeholder rapor donduruyor
- alt paketlerin buyuk bolumu placeholder package

## Kesin Problemli Nokta

Repo icinde dogrudan gorulen net bir kirik alan var:

- [src/task.py#L3](/home/eren/Desktop/claw-code/src/task.py#L3)

Bu dosya kendi kendini import ediyor:
- `from .task import PortingTask`

`src/tasks.py` de ayni bagimliliga sahip.

Repo icinde `PortingTask` sinif tanimi gorunmuyor.

Bu, su anda eldeki kod icinde acik bir kirik bagdir.

## Tek Cumlede Ozet

Bu repo, referans alinan bir TypeScript agent/harness sisteminin Python tarafinda yeniden kurulmus, snapshot verileriyle yonlendirilen, parity odakli bir porting workspace'idir.
