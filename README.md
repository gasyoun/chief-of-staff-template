# File-based Chief of Staff — public template / Файловый chief of staff — публичный шаблон

_EN below · Русский ниже_

## EN

A minimal, file-based chief-of-staff for a solo owner: an AI agent of any harness
(opencode, Codex, Claude Code, …) runs a daily/weekly loop over plain Markdown files.
No server, no app — a repo is the product. Skills are files, so any agent can execute them:
`Read skills/brief/SKILL.md and execute it`.

This is a **sanitized public snapshot**: the personal context directory `me/` and the
vendored `upstream/` copy of the original template are excluded by design.

**Attribution:** the idea and the loop come from
[dx-dzbor/chief-of-staff](https://github.com/dx-dzbor/chief-of-staff) (MIT). The original
repo is **not** republished here — use the link. Everything in this repository is the
author's own reimplementation over their own estate, MIT-licensed (see `LICENSE`).

### Layout

| Path | Purpose |
|---|---|
| `AGENTS.md` | The working contract every agent reads first. |
| `CONTEXT.md` | File formats and write boundaries — including the `me/` file spec. |
| `me/` | **Yours to create** — all personal context: profile, current drives, weekly goals, decisions, waiting-on, sources map, briefs, logs. |
| `skills/` | Six skills: `brief` (morning), `debrief` (evening), `weekly-status`, `os-review` (read-only audit), `fleet-check` (read-only), `fleet-act` (commands with explicit owner confirmation). |

### The loop

| When | Skill | Output |
|---|---|---|
| Morning | `skills/brief/SKILL.md` | One-page day brief: priority, decisions, overdue waits, overnight news — into `me/briefs/`. |
| Evening | `skills/debrief/SKILL.md` | Day dumped verbatim into `me/log/`, updates to decisions/waits after confirmation. |
| Weekly | `skills/weekly-status/SKILL.md` | Draft status digest from briefs and the log. |
| Weekly | `skills/os-review/SKILL.md` | Read-only audit: what rotted, what was forgotten, where the gaps are. |
| On event | `skills/fleet-check/SKILL.md` | Read-only look at the automation fleet: dead lanes, stale heartbeats. |
| On event | `skills/fleet-act/SKILL.md` | Fleet commands: proposal first, execution only after the owner's explicit "yes". |

### How to adapt

1. Copy this repository (it carries no personal data — that's the point).
2. Create the `me/` files exactly as specified in `CONTEXT.md`.
3. Fill `me/sources.md` with **your** live paths (GTD board, handoff registry, wiki, chat logs) —
   the skills read tails and numbers from real paths, not hand-entered status.
4. Keep the boundaries in `CONTEXT.md`: drafts are never sent automatically, `os-review`
   and `fleet-check` are read-only, destructive actions need the owner's explicit yes.
5. The estate-specific paths inside the skills (`Uprava`, `sprint-watch`, `hermes`, …) are the
   author's own worked example — point them at your equivalents or delete them.

### Glossary (kept from the original repo, bilingual)

- **PR (pull request)** — a merge request: changes go in through review, not directly.
- **Uprava** — the estate's shared "management" repository: task board (GTD board), work registry with acceptance criteria, fleet lane registry.
- **Lane** — an agent's recurring piece of work with its own schedule and a freshness deadline (heartbeat).
- **Foreman** — the daily agent-foreman: checks lanes against the schedule and assembles the morning summary.
- **Дренаж / Drain** — nightly processing of the task queue by agents in waves.
- **Хендофф / Handoff** — the local format of a task for an agent: mission, acceptance criteria, required evidence.

## RU

Минималистичный файловый chief of staff для одного владельца: агент любого харнесса
(opencode, Codex, Claude Code, …) гоняет утренне-недельный луп по обычным Markdown-файлам.
Ни сервера, ни приложения — репозиторий и есть продукт. Скилл — это файл, его выполняет
любой агент: `Read skills/brief/SKILL.md and execute it`.

Это **выхолощенный публичный снимок**: личный контекст `me/` и вендоренная копия
оригинального шаблона `upstream/` исключены намеренно.

**Атрибуция:** идея и луп — из
[dx-dzbor/chief-of-staff](https://github.com/dx-dzbor/chief-of-staff) (MIT). Оригинальный
репозиторий здесь **не переиздается** — работайте по ссылке. Все в этом репозитории —
собственная реализация автора поверх своего хозяйства, лицензия MIT (см. `LICENSE`).

### Устройство

| Путь | Назначение |
|---|---|
| `AGENTS.md` | Рабочий контракт, который агент читает первым. |
| `CONTEXT.md` | Форматы файлов и границы записи — включая спецификацию `me/`. |
| `me/` | **Создаете сами** — весь личный контекст: профиль, активные фронты, цели недели, решения, ожидания, карта источников, брифы, логи. |
| `skills/` | Шесть скиллов: `brief` (утро), `debrief` (вечер), `weekly-status`, `os-review` (read-only ревизия), `fleet-check` (read-only), `fleet-act` (команды с явным «да» владельца). |

### Луп

| Когда | Скилл | Что на выходе |
|---|---|---|
| Утро | `skills/brief/SKILL.md` | Бриф дня: приоритет, решения, просроченные ожидания, новое за ночь — в `me/briefs/`. |
| Вечер | `skills/debrief/SKILL.md` | День в `me/log/` сырым дампом, обновления решений и ожиданий после подтверждения. |
| Неделя | `skills/weekly-status/SKILL.md` | Черновик статус-дайджеста из брифов и лога. |
| Неделя | `skills/os-review/SKILL.md` | Ревизия read-only: что протухло, что забыто, где разрывы. |
| По событию | `skills/fleet-check/SKILL.md` | Смотр автоматизационного флота: мертвые лейны, просроченные heartbeat'ы. |
| По событию | `skills/fleet-act/SKILL.md` | Команды флоту: сначала предложение, исполнение только после явного «да» владельца. |

### Как приспособить под себя

1. Скопируйте репозиторий (он не несет персональных данных — в этом смысл).
2. Создайте файлы `me/` ровно как указано в `CONTEXT.md`.
3. Впишите в `me/sources.md` **свои** живые пути (GTD-борд, реестр задач, вики, логи чатов) —
   скиллы читают хвосты и числа из реальных путей, а не из ручного статуса.
4. Держите границы из `CONTEXT.md`: черновики не отправляются автоматически, `os-review`
   и `fleet-check` — read-only, разрушительные действия требуют явного «да» владельца.
5. Хозяйственно-специфичные пути внутри скиллов (`Uprava`, `sprint-watch`, `hermes`, …) —
   это проработанный пример самого автора: направьте на свои аналоги или удалите.

### Словарик для внешнего читателя

- **PR (pull request)** — запрос на слияние: так в Git вносят правки через ревью, а не напрямую.
- **Uprava** — общий репозиторий-управа хозяйства: доска задач (GTD-борд), реестр работ с критериями приемки, реестр лейн флота.
- **Лейн (lane)** — закрепленная повторяющаяся работа агента со своим расписанием и сроком «свежести» (heartbeat).
- **Foreman** — дневной агент-бригадир: сверяет лейны с расписанием и собирает утреннюю сводку.
- **Дренаж** — ночная обработка очереди задач агентами волнами.
- **Хендофф** — формат задачи для агента: миссия, критерии приемки, доказательства.

## License / Лицензия

MIT — see [`LICENSE`](LICENSE). Based on
[dx-dzbor/chief-of-staff](https://github.com/dx-dzbor/chief-of-staff).
