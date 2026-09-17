# Русский инфостиль для Codex

`ru-infostyle-editor` — навык для редактуры русскоязычных текстов в информационном стиле. Он делает текст яснее, точнее и плотнее, но сохраняет факты, жанр, профессиональную лексику и авторский голос.

Навык не предназначен для обхода AI-детекторов: он не добавляет искусственную разговорность, ошибки или «человеческие шероховатости».

## Что умеет

- Убирать канцелярит, пустые рамки и смысловые повторы.
- Возвращать тексту действие, объект и наблюдаемую конкретику, не выдумывая фактов.
- Перестраивать тяжёлые конструкции, если это не вредит точности и жанру.
- Учитывать особенности сообщений, деловых писем, интерфейсов, инструкций, кейсов, маркетинга и аналитики.
- Сохранять уместные термины, пунктуацию, оговорки и авторскую интонацию.

## Установка

Репозиторий опубликован владельцем [`potatotatoshka`](https://github.com/potatotatoshka).

### ChatGPT и Codex

Проект также упакован как переносимый плагин: [plugin.json](plugin.json) описывает карточку и содержит этот навык. После одобрения OpenAI он появится в общем каталоге плагинов ChatGPT и Codex — пользователь установит плагин, а не отдельный файл `SKILL.md`.

### На всех поддерживаемых платформах

Самый простой способ — установить навык во все совместимые агенты, обнаруженные на компьютере. Нужен Node.js:

```bash
npx skills add https://github.com/potatotatoshka/ru-infostyle-editor --skill ru-infostyle-editor --agent '*' --global
```

Утилита `npx skills` автоматически выбирает правильные каталоги для Codex, Claude Code, Antigravity, Cursor, Windsurf, GitHub Copilot, Gemini CLI и других совместимых агентов. Добавьте `--copy`, если символические ссылки в вашей среде недоступны.

Чтобы установить навык только в несколько платформ:

```bash
npx skills add https://github.com/potatotatoshka/ru-infostyle-editor --skill ru-infostyle-editor --agent codex --agent claude-code --agent antigravity --agent cursor --agent windsurf --agent github-copilot --agent gemini-cli --global
```

Полный и обновляемый список поддерживаемых агентов ведёт проект [`vercel-labs/skills`](https://github.com/vercel-labs/skills).

### Через Codex

Откройте новый чат в Codex и попросите:

```text
Установи скилл из https://github.com/potatotatoshka/ru-infostyle-editor/tree/main/skills/ru-infostyle-editor
```

### Вручную

Скопируйте папку `skills/ru-infostyle-editor` в каталог навыков Codex:

```text
~/.codex/skills/ru-infostyle-editor
```

На Windows это обычно `%USERPROFILE%\.codex\skills\ru-infostyle-editor`. После установки начните новый чат, чтобы Codex обнаружил навык.

### Ручная установка в других агентах

Скопируйте одну и ту же папку `skills/ru-infostyle-editor` в каталог навыков нужной платформы:

| Платформа | Глобальный каталог | Каталог в проекте |
|---|---|---|
| Claude Code | `~/.claude/skills/ru-infostyle-editor` | `.claude/skills/ru-infostyle-editor` |
| Antigravity | `~/.gemini/config/skills/ru-infostyle-editor` | `.agents/skills/ru-infostyle-editor` |
| Cursor | `~/.cursor/skills/ru-infostyle-editor` | `.agents/skills/ru-infostyle-editor` |
| Windsurf | `~/.codeium/windsurf/skills/ru-infostyle-editor` | `.windsurf/skills/ru-infostyle-editor` |
| GitHub Copilot | `~/.copilot/skills/ru-infostyle-editor` | `.agents/skills/ru-infostyle-editor` |
| Gemini CLI | `~/.gemini/skills/ru-infostyle-editor` | `.agents/skills/ru-infostyle-editor` |

Навык намеренно использует только переносимое YAML-ядро `name` и `description`; поэтому один и тот же `SKILL.md` подходит разным агентам. Метаданные в `agents/openai.yaml` нужны только интерфейсу Codex и безвредны для остальных.

## Использование

Вызовите навык явно:

```text
$ru-infostyle-editor
```

Например: «Отредактируй это письмо в информационном стиле, сохрани тон и все условия». Навык также может подключаться автоматически, когда запрос прямо относится к русской редактуре в информационном стиле.

## Структура

```text
skills/ru-infostyle-editor/
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── genre-profiles.md
    ├── patterns-and-edits.md
    └── review-checklist.md
```

## Принципы

Качество правки определяется ясностью, точностью, плотностью и уместностью. Краткость сама по себе не является целью; отдельные тире, двоеточия, вводные слова, повторы или длинные предложения не считаются ошибкой без контекста.

## Лицензия

Проект распространяется по лицензии [MIT](LICENSE).
