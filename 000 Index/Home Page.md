## 📁 Klasörler
- [[100 roughly/_index|Rough]]
- [[110 research/_index|Research]]
- [[200 source/_index|Source]]
- [[300 my project/_index|My All Project]]
- [[400 special tech/_index|Special Tech]]
- [[500 templates/_index|Templates]]
- [[600 full notes/_index|All Notes]] || [[610 chatcpt-note/_index|ChatGpt Notes]]
---

## 🚀 Dashboard

```dataview  
TABLE WITHOUT ID
	file.link as "Not",
	choice(length(file.etags) > 0, string(file.etags[0]), "") as "🏷️",
	choice(priority, string(priority), "") as "🔥",
	choice(tarih, string(tarih), "") as "📅",
	join(
		map(etiketler, (e) => "<span class='tag'>" + e + "</span>"),
		" "
	) as "Etiketler"
FROM ""
WHERE file.name != "_index"
AND file.name != "Home Page"
AND !contains(file.folder, "500 templates")
AND file.ext = "md"
SORT number(priority) DESC
LIMIT 15
```




