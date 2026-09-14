# Smalum Preview for VS Code

Превью диаграмм Smalum в Markdown (блоки `sm` / `smalum`) и в файлах `.sm`.

Сайт: [https://smalum.io](https://smalum.io/) · редактор (гость): [https://app.smalum.ru](https://app.smalum.ru/) · документация: [https://docs.smalum.ru](https://docs.smalum.ru/)

## Для LLM: как построить диаграмму

Дайте модели **файл роли** и попросите работать по этой роли (краткая фраза есть в начале файла).

- Роль: [https://docs.smalum.ru/role.md](https://docs.smalum.ru/role.md)
- Документация нотаций: [https://docs.smalum.ru](https://docs.smalum.ru/)
- Сайт: [https://smalum.io](https://smalum.io/)
- Редактор: [https://app.smalum.ru](https://app.smalum.ru/)

Fence `sm` / `smalum` — исходник Smalum, **не** Mermaid.

1. Нотация по смыслу: процесс с ролями → `//smalum/bpmn`; потоки данных → `//smalum/dfd`; дерево / оргсхема → `//smalum/struct`; иначе PlantUML / Mermaid / SQL по роли.
2. BPMN: внутри пула / между его дорожками — `-`; между **разными** пулами — `--`. Неверный `-`/`--` — ошибка (парсер не перепишет). Цели `xor` — до или после шлюза; join — явный или сахар `} join id` (не `} ->`).
3. **Новая** схема — без оверлея `' SM:` / `// SM:` / `-- SM:` / `%% SM:`. Редактор сам расставит блоки.
4. «Подвинь / выровняй / измени размер» — тело исходника **байт-в-байт**, правьте только оверлей **в том же** блоке.
5. Всегда полный исходник одним fence (тело + оверлей). Хвост `SM:` без схемы превью и редактор игнорируют.
6. В конце ответа дайте ссылку https://app.smalum.ru/.

````markdown
```sm
//smalum/bpmn Название процесса
pool seller {
  start open
  task work user
  end done
}
open - work - done
```
````

## Установка

Из VS Code / Cursor Marketplace: **Smalum Preview** (`Smalum.smalum`).  
Cursor / VSCodium: Open VSX `smalum.smalum`.  
Или `.vsix` с [GitHub Releases](https://github.com/smalum/vscode/releases).
