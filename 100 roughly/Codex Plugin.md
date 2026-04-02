- **Class:**  
- **Date:** 2026-04-02  
- **Topics:** #plugin

Bunlarla Codex’i sadece “kod yazan terminal botu” olmaktan çıkarıp **dış servislerle çalışan ajan** haline getirirsin. OpenAI dokümanına göre plugin’ler; **skill + uygulama entegrasyonu + MCP server yapılandırmasını** tek pakette topluyor. Yani plugin kurunca Codex’e yeni yetenekler ve bağlantılar ekleniyor. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/plugins/?utm_source=chatgpt.com "Plugins – Codex"))

Ekrandaki plugin’lerle kabaca şunları yaparsın:

**Gmail**  
Mail okuyabilir, arayabilir, özet çıkarabilir, taslak hazırlayabilir ve yönetebilir. OpenAI örneğinde bunu doğrudan Gmail plugin için söylüyor. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/plugins/?utm_source=chatgpt.com "Plugins – Codex"))

**Google Calendar**  
Takvimi okuyup etkinlikleri yönetmeye yarar; toplantı bakma, uygun saat bulma, event oluşturma gibi işler için. Plugin mantığı uygulama entegrasyonu sağladığı için Calendar da bu kategoriye giriyor. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/plugins/?utm_source=chatgpt.com "Plugins – Codex"))

**Google Drive**  
Drive, Docs, Sheets ve Slides üzerinde çalıştırır. Yani doküman buldurma, özetletme, içerik üzerinden işlem yaptırma tarafında işe yarar. OpenAI docs bunu açıkça örnek veriyor. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/plugins/?utm_source=chatgpt.com "Plugins – Codex"))

**Slack**  
Kanal mesajlarını özetletme, konuşmaları okuma, yanıt taslağı hazırlatma. Bu da OpenAI’nin verdiği doğrudan örneklerden biri. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/plugins/?utm_source=chatgpt.com "Plugins – Codex"))

**Notion**  
Spec, research, meeting notes, knowledge base tarafında Notion içeriğiyle çalıştırırsın. Ekrandaki açıklama da buna uyuyor; plugin’ler bu tarz app workflow’larını paketliyor. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/plugins/?utm_source=chatgpt.com "Plugins – Codex"))

**GitHub**  
PR, issue, CI, release akışlarını ajan üzerinden yönetme tarafında kullanılır. Plugin sistemi zaten uygulama entegrasyonlarını reusable workflow olarak sunuyor. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/plugins/?utm_source=chatgpt.com "Plugins – Codex"))

**Vercel / Netlify / Cloudflare**  
Deploy, release, hosting ve platform işlemlerini Codex içinden yürütmek için. OpenAI’nin use-case sayfasında özellikle Vercel için curated skills + official MCP server yaklaşımı anlatılıyor. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/use-cases/chatgpt-apps/?utm_source=chatgpt.com "Bring your app to ChatGPT | Codex use cases"))

**Figma / Canva / Build Web Apps / Build iOS Apps / Test Android Apps / Game Studio**  
Bunlar daha çok belirli workflow plugin’leri. Yani “tasarımdan koda”, “UI inceleme”, “Android emulator üzerinde issue yeniden üretme”, “oyun prototipleme” gibi dar ama güçlü akışlar verir. Plugin’lerin reusable workflow mantığı buna uygun. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/plugins/?utm_source=chatgpt.com "Plugins – Codex"))

**Linear / Sentry / Stripe / Box / Hugging Face / Jam**  
Linear: issue/project takibi.  
Sentry: error ve event inceleme.  
Stripe: ödeme ve business tools.  
Box: dosya/doküman erişimi.  
Hugging Face: model, dataset, Spaces araştırma.  
Jam: screen recording ve bug context.  
Bunların hepsi ekrandaki kısa açıklamalarla da uyumlu app-specific entegrasyonlar. Plugin sistemi zaten tam bunun için var. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/plugins/?utm_source=chatgpt.com "Plugins – Codex"))

En önemli nokta şu:  
**plugin = tek başına sadece “bir araç” değil.** İçinde skill de olabilir, MCP bağlantısı da olabilir, app mapping de olabilir.  
**MCP ise altyapı protokolü.** Codex’in üçüncü parti tool ve context’e bağlanma standardı. OpenAI dokümanında Codex’in MCP server’larını CLI ve IDE extension’da desteklediği yazıyor. Yani çoğu plugin’in altında aslında MCP de olabilir. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/plugins/?utm_source=chatgpt.com "Plugins – Codex"))

Sana en doğru özet şu:

- **Plugin** = hazır entegrasyon paketi
    
- **MCP** = o entegrasyonun altında çalışabilen standart bağlantı katmanı
    

Senin kullanım tarzında en faydalılar büyük ihtimalle:  
**GitHub, Vercel, Notion, Slack, Google Drive, Gmail**.  
Çünkü bunlar proje, deploy, dokümantasyon ve iletişim akışını direkt hızlandırır. ([OpenAI Geliştiricileri](https://developers.openai.com/codex/plugins/?utm_source=chatgpt.com "Plugins – Codex"))

İstersen bir sonraki mesajda sana bu listedeki plugin’leri **“senin workflow’una göre hangisini kur, hangisini boşver”** diye direkt sıralayayım.

