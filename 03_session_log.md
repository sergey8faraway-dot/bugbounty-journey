# Session Log

## Шаблон записи
- Дата:
- Время (мин):
- Фокус:
- Что сделал:
- Что получилось:
- Что не получилось:
- Следующий шаг:
- EN-блок (что написал на английском):
- Self-score (0-2): Understanding / Practice / Reporting / English

---

## Entry 1
- Дата: 2026-05-05
- Время (мин): 50
- Фокус: IDOR foundation (PortSwigger Apprentice)
- Что сделал: Перехватил `POST /download-transcript`, извлек `Location` с именем transcript-файла, перебрал соседние `.txt` в Repeater.
- Что получилось: Получил доступ к чужому transcript (`/download-transcript/1.txt`) и извлек пароль, затем вошел как `carlos` и закрыл lab.
- Что не получилось: Сначала было неочевидно, где смотреть response в Burp.
- Следующий шаг: Следующий Apprentice IDOR lab; повторить тот же шаблон: object reference -> mutation -> response diff -> impact.
- EN-блок (что написал на английском): I found an object reference in the transcript filename. By changing the filename, I accessed another user’s chat log. The server returned unauthorized data instead of blocking access. This confirms an IDOR vulnerability. Impact: an attacker can read sensitive chat data and take over accounts.
- Self-score (0-2): 2 / 2 / 1 / 1
