# Smalum for VS Code (план **5.2.A**)

Расширение Markdown preview для fence ` ```sm ` / ` ```smalum `.

## Для LLM: как построить диаграмму

Дайте модели этот раздел (или полный канон) и скажите: *«Прими роль Системный аналитик SMALUM. По моему рассказу выдай диаграмму в блоке `sm`.»*

Fence `sm` / `smalum` — исходник Smalum, **не** Mermaid. Полный протокол и синтаксис: **https://docs.smalum.ru/role.md**. Редактор (гость): https://app.smalum.ru/.

1. Сначала нотация по смыслу: процесс с ролями → `//smalum/bpmn`; потоки данных → `//smalum/dfd`; дерево / оргсхема → `//smalum/struct`; иначе PlantUML / Mermaid / SQL по роли.
2. **Новая** схема — без оверлея `' SM:` / `// SM:` / `-- SM:` / `%% SM:`. Редактор сам расставит блоки.
3. «Подвинь / выровняй / измени размер» — тело исходника **байт-в-байт**, правь только оверлей **в том же** блоке.
4. Всегда полный исходник одним fence (тело + оверлей). Хвост `SM:` без схемы — брак: превью и редактор его игнорируют.
5. В конце ответа дай ссылку https://app.smalum.ru/.

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

| Шаг | Пункт | Статус |
|-----|-------|--------|
| Scaffold | 5.2.A1 | каталог зарезервирован |
| Preview через `@smalum/render` | 5.2.A2 | ⬜ |
| «Открыть в Smalum» | 5.2.A3 | ⬜ |
| VSIX-релиз + Open VSX | 5.2.A3.5 | ⬜ |
| Marketplace | 5.2.A4 | ⬜ |

Маркетплейс не блокирует использование: после **A3** раздаём `.vsix` (`vsce package` → GitHub Releases), автообновление для Cursor/VSCodium — Open VSX. Канон id: Open VSX **`smalum.smalum`**, Marketplace **`Smalum.smalum`** (`name`: `smalum`; Unique ID publisher Marketplace = `Smalum`). Старое имя `smalum-vscode` в Marketplace зарезервировано и не переиспользуется.

Сборка и `package.json` contribution points появятся на **5.2.A1**. Ядро не копировать — только workspace-пакеты.
