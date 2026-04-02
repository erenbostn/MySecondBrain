- **Class:**  
- **Date:** 2026-04-02  
- **Topics:** #agent #subagent #skill

En doğru yaklaşım şu ayrımı net koymak:

- `AGENTS.md`: Codex’in repo içinde nasıl davranacağını belirler.
- `agents.<name>`: özel alt ajan rolleri tanımlar.
- `SKILL.md`: tekrar eden bir işi, gerektiğinde devreye girecek şekilde paketler.

**Agent**
Kendi “agent”ını oluştururken önce `AGENTS.md` ile başla. Resmi dokümana göre burası repo düzeni, çalıştırma komutları, test/lint, mühendislik kuralları, yasaklar ve “done” kriteri için doğru yer. `/init` bunun için başlangıç dosyası üretir. Ayrıca `AGENTS.md` katmanlı çalışır: `~/.codex` altındaki global dosya, repo seviyesi dosya ve daha iç klasörlerdeki dosyalar birleştirilir; çalışma dizinine daha yakın olan kurallar daha baskın olur. Bu yüzden genel davranışı globale, repo kurallarını köke, servis/alt-modül özel kuralları ilgili klasöre koymak en temiz model.  
Kaynaklar: [AGENTS.md best practices](https://developers.openai.com/codex/learn/best-practices/#make-guidance-reusable-with-agentsmd), [AGENTS.md discovery order](https://developers.openai.com/codex/guides/agents-md/#how-codex-discovers-guidance)

Eğer gerçekten ayrı bir “rol agent” tanımlayacaksan bunu `~/.codex/config.toml` içinde `agents.<name>` ile yaparsın. Resmi config’e göre bunun üç temel alanı var: `description` rolün ne zaman seçileceğini anlatır, `config_file` o role özel ek TOML katmanını bağlar, `nickname_candidates` ise görünen isimler içindir. Pratikte en önemli alan `description`; kısa ama seçim yapmayı kolaylaştıran bir rol tanımı yaz.  
Kaynak: [config.toml agent role fields](https://developers.openai.com/codex/config-reference/#configtoml)

**Skill**
Skill oluştururken resmi öneri önce `$skill-creator` kullanmak. Dokümana göre creator sana skill’in ne yaptığını, ne zaman tetikleneceğini ve sadece instruction mı yoksa script de içerip içermeyeceğini sorar. Manuel kuracaksan klasör + `SKILL.md` yeterli; en kritik parça frontmatter’daki `name` ve özellikle `description`. Çünkü skill iki şekilde çalışır: sen `$skill` ile açıkça çağırırsın ya da Codex açıklamaya bakıp kendisi seçer.  
Kaynaklar: [Create a skill](https://developers.openai.com/codex/skills/#create-a-skill), [How Codex uses skills](https://developers.openai.com/codex/skills/#how-codex-uses-skills)

Skill’i iyi yapmak için resmi pratikler şunlar:
- Tek işi çözsün; her şeyi yapan mega-skill yapma.
- 2-3 somut kullanım örneğiyle tasarla.
- `description` içine “ne yapar” ve “ne zaman kullanılmalı/kullanılmamalı” bilgisini koy.
- `SKILL.md` içinde nasıl çalıştırılır, beklenen çıktı, gotcha’lar ve sınırlar olsun.
- Routing kararsızsa önce isim/açıklama/örnekleri düzelt.
- Script varsa küçük CLI gibi tasarla: deterministik çıktı versin, hata durumunda net bozulsun, dosya yolları belli olsun.
- Ağ erişimi gerekiyorsa çok dikkatli ol; allowlist mantığı kullan.
Kaynaklar: [Turn repeatable work into skills](https://developers.openai.com/codex/learn/best-practices/#turn-repeatable-work-into-skills), [Skills operational best practices](https://developers.openai.com/cookbook/examples/skills_in_api/#operational-best-practices)

**En doğru kısa reçete**
1. Repo davranışı için önce `/init` ile `AGENTS.md` oluştur.
2. Aynı hata tekrar edince `AGENTS.md`’yi güncelle.
3. Tekrarlanan workflow gördüğünde onu skill’e çevir.
4. Skill için önce `$skill-creator` kullan.
5. `description` alanını tetikleme mantığına göre çok net yaz.
6. Sadece gerçekten gerekiyorsa script/assets ekle.
7. Alt ajan rolü gerekiyorsa en son `agents.<name>` tanımla.

İstersen bir sonraki mesajda sana doğrudan:
- örnek bir `AGENTS.md`
- örnek bir `agents.reviewer` tanımı
- örnek bir `SKILL.md`

üçünü birlikte, kopyalanabilir şekilde çıkarayım.