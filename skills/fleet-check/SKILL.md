---
name: fleet-check
description: Read-only смотр флота hermes — мертвые лейны, просроченные heartbeat'ы, донесение в бриф; ничего не пишет и не перезапускает
---
_Created: 03-10-2026 · Last updated: 03-10-2026_

# /fleet-check — смотр флота (read-only)

Контекст: `me/fleet.md`. Бюджет ~3 минуты, только чтение. Foreman на сервере — главный
по heartbeat'ам; этот скилл не дублирует его, а сводит картину для владельца.

1. **Исполнительные лейны** (`~/Documents/GitHub/Uprava/LANES.md`): кто 🔴 dead / stale
   (строка старше 36 ч), на каком боксе. Мертвых имена — дословно, с evidence из строки.
2. **Лейны флота** (`~/Documents/GitHub/Uprava/hermes/lanes/lanes.tsv`): для Mac-лейнов
   (`decisions_nurse`, `drift_check`, `mac_external_eye`) — жив ли launchd-джоб
   (`launchctl list | grep gasyoun.hermes`), возраст последних логов против `max_age_h`
   из реестра. Серверные лейны без запроса владельца не щупаем — там хозяин foreman.
3. **Ферма и ее живость**: `SecondBrain-LLM-Wiki/40-Estate/launchd-farm.md` (кто должен
   был работать за ночь), failsweep-гейт из GTD-борда.

## Донесение

Формат для брифа (секция «Флот», ≤5 строк): «мертво — …», «просрочено — … (max_age_h N,
фактически M)», «живо — счет», каждая строка с путем-пруфом. Источник недоступен — так и
писать. Ничего не перезапускать: для этого владелец зовет `/fleet-act`.

