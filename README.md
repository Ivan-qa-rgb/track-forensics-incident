# track-forensics-incident

DFIR case study — судебная экспертиза инцидента на рабочей станции компании «Х».

## О проекте

Расследование инцидента информационной безопасности, связанного с подозрительной сетевой активностью на рабочей станции пользователя Wilfred. Используются дамп оперативной памяти, побитовая копия диска и артефакты Windows для восстановления хронологии событий и маппинга на MITRE ATT&CK.

## Ключевые моменты инцидента

- Фишинговое воздействие: запуск ярлыка `Refund_form.lnk` из каталога `Downloads`.
- Подготовительный этап: использование `7z1900.exe` и временных директорий.
- Living off the Land: активное применение штатных утилит Windows (reg.exe, sc.exe, schtasks.exe, rundll32.exe и др.).
- Запуск PowerShell с закодированными командами (`-enc`) и сценария `Updater.bat` как возможного логон-скрипта.
- Обращения к файлообменнику sendspace.com, работа с временными файлами и батниками `111.bat`, `2.bat`, `3.bat`.
- RDP-активность, использование `netscan.exe` и `iepv.exe` для сетевой и веб-разведки.
- Финальный этап: запуск RamCapture.exe и FTK Imager.exe для фиксации состояния системы (дамп памяти и образ диска).

## MITRE ATT&CK

В полном отчёте инцидент сопоставлен с техниками MITRE ATT&CK, включая:

- T1566.001 — Phishing: Spearphishing Attachment  
- T1059.001 — PowerShell  
- T1037.001 — Logon Script (Windows)  
- T1071.001 — Application Layer Protocol: HTTP/HTTPS  
- T1033, T1057, T1059, T1053, T1112 — использование системных утилит  
- T1059.003 — Windows Command Shell  
- T1036 — Masquerading  
- T1005 — Data from Local System

## Рекомендации

Кратко: обучение пользователей (фишинг), контроль запуска PowerShell/BAT/LNK, аудит механизмов автозапуска, усиление RDP и сетевой защиты, централизованный сбор логов и форензик-аудит.

## Полный отчёт

Полный текст судебной экспертизы:  
[report/track-forensics-full.md](https://github.com/Ivan-qa-rgb/track-forensics-incident/blob/main/report/track-forensics-full.md)











































