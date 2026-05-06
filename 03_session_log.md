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

## Entry 2
- Дата: 2026-05-06
- Время (мин): 40
- Фокус: IDOR reporting + English block
- Что сделал: Разбил структуру training report на блоки (`Overview`, `Reproduction`, `Risk & Fix`) и оформил первый IDOR-черновик по этим секциям.
- Что получилось: Подготовлен понятный каркас репорта с шагами воспроизведения, impact и remediation; EN-блок сформулирован в формате PoC.
- Что не получилось: Пока мало вариативности в английских формулировках (повторяются одинаковые конструкции).
- Следующий шаг: Следующий Apprentice IDOR lab + новый report draft с акцентом на более точный impact.
- EN-блок (что написал на английском): I intercepted a request to POST /download-transcript in Burp Suite. The response contained Location: /download-transcript/12.txt, which exposed an object reference. I changed the transcript filename to another value and accessed a different user’s chat log. The server returned sensitive data without proper authorization checks. This is an IDOR vulnerability.
- Self-score (0-2): 2 / 1 / 2 / 1
