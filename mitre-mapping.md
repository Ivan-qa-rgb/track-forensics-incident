# MITRE ATT&CK Mapping — Wilfred workstation incident

## Overview

Маппинг действий атакующего и связанных артефактов на тактики и техники MITRE ATT&CK.

## Table

| Тактика (TACTIC)             | Техника (TECHNIQUE)                                           | ID          | Артефакты / действия                                                                 |
|----------------------------- |---------------------------------------------------------------|-------------|--------------------------------------------------------------------------------------|
| Initial Access               | Phishing: Spearphishing Attachment                            | T1566.001   | Запуск `Refund_form.lnk` из `Downloads` (UserAssist, NTUSER.DAT, счётчик = 1).       |
| Execution                    | Command and Scripting Interpreter: PowerShell                 | T1059.001   | `powershell.exe -noP -sta -w 1 -enc ...` (pstree, Updater.bat).                      |
| Persistence                  | Logon Script (Windows)                                        | T1037.001   | `UserInitMprLogonScript = C:\Users\Wilfred\AppData\Roaming\Identities\Updater.bat`.  |
| Command and Control / Exfil  | Application Layer Protocol: HTTP/HTTPS                        | T1071.001   | TCP `192.168.1.74` → `192.168.1.71:80`, `240.115.119.185:443` (memory network scan). |
| Discovery                    | System Owner/User Discovery                                   | T1033       | Использование утилит для сбора информации о пользователе и системе (Amcache, reg.exe и др.).|
| Discovery                    | Process Discovery                                             | T1057       | Запуски утилит, анализ процессов, использование `taskmgr.exe`.                       |
| Execution                    | Command and Scripting Interpreter (generic)                   | T1059       | BAT‑файлы (`111.bat`, `2.bat`, `3.bat`) и командная строка.                          |
| Persistence / Priv Esc       | Scheduled Task/Job                                            | T1053       | Использование `schtasks.exe` (по данным Amcache.hve).                                |
| Defense Evasion / Persistence| Modify Registry                                               | T1112       | Изменения реестра (`regedit.exe`, `reg.exe`, записи профиля пользователя).           |
| Execution                    | Command and Scripting Interpreter: Windows Command Shell      | T1059.003   | BAT‑скрипты, временные файлы в `C:\Windows\Temp`, работа через cmd.exe.              |
| Defense Evasion              | Masquerading                                                  | T1036       | Нестандартный путь `C:\da790f6476e06f24c6ada9\setup.exe`.                            |
| Collection                   | Data from Local System                                        | T1005       | Создание дампа памяти (RamCapture.exe) и образа диска (FTK Imager.exe).              |

## Notes

- Техники сгруппированы по тактикам, но в отчёте они рассматриваются в хронологическом порядке развития инцидента.
- В ряде случаев одна утилита участвует сразу в нескольких техниках (например, PowerShell и BAT‑скрипты — Execution, C2, Discovery).
