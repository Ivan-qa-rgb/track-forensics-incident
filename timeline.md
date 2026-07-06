# Incident Timeline — рабочая станция Wilfred

## Overview

Хронология ключевых событий инцидента на рабочей станции пользователя Wilfred, восстановленная по артефактам UserAssist, TypedURLs/TypedURLsTime, TSClient, ComDlg32, дампу оперативной памяти и другим источникам.

## Timeline

- **2019‑03‑09 14:16:37**  
  Запуск стандартных приложений Windows (GettingStarted, SnippingTool, calc, mspaint, WFS).  
  Статус: нормальная пользовательская активность, признаков компрометации нет.

- **2019‑03‑09 14:29:31**  
  Запуск `7z1900.exe` из кэша Internet Explorer:  
  `C:\Users\Wilfred\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\852CH0Q4\7z1900.exe`  
  Статус: подготовительный этап, использование архиватора/загруженного содержимого.

- **2019‑03‑09 14:31:04**  
  Запуск фишингового ярлыка:  
  `C:\Users\Wilfred\Downloads\Refund_form\Refund_form.lnk` (UserAssist, счётчик = 1).  
  Статус: точка входа инцидента, фишинговое воздействие.

- **2019‑03‑09 16:36:29 — 16:57:13**  
  Серия запусков системных утилит: `msiexec.exe`, `notepad.exe`, `rundll32.exe`, `regedit.exe`.  
  Статус: использование штатных средств ОС для изменения параметров системы и работы с файлами (Living off the Land).

- **2019‑03‑09 (вечер, по артефактам TypedURLs/TypedURLsTime)**  
  Обращения к sendspace.com:  
  - `http://sendspace.com/file/obeywl`  
  - `https://www.sendspace.com/file/0beywl`  
  - `https://www.sendspace.com/`  
  Статус: взаимодействие с внешним файлообменным сервисом.

- **2019‑03‑09 (после появления RDP‑следов)**  
  Запуск Microsoft.Windows.RemoteDesktop, появление записей в TSClient\Servers и TSClient\Default для:  
  - `192.168.1.75`  
  - `192.168.1.72`  
  Статус: RDP‑активность, возможный удалённый доступ к внутренним узлам.

- **2019‑03‑09 (временные каталоги)**  
  Запуски `netscan.exe` и `iepv.exe` из временных директорий.  
  Статус: сетевой сканинг и анализ интернет‑следов (история браузера, пароли, URL‑ы).

- **2019‑03‑09 (последующие действия)**  
  Запуск `111.bat`, `2.bat`, `taskmgr.exe`, повторный `notepad.exe`.  
  Статус: использование BAT‑скриптов и временных файлов в каталоге `C:\Windows\Temp` для постэксплуатации.

- **2019‑03‑10 12:30:35 UTC**  
  Запуск `powershell.exe` с параметрами:  
  `powershell  -noP -sta -w 1 -enc  SQBGACgAJABQAFMAVgBlA`  
  Статус: выполнение закодированной команды PowerShell (Command and Scripting Interpreter).

- **2019‑03‑10 13:03:06 UTC**  
  Запуск RamCapture.exe:  
  `\\Vboxsvr\d_drive\RamCapturer\x86\RamCapture.exe`  
  Статус: создание дампа оперативной памяти, форензик‑фиксация.

- **2019‑03‑10 13:05:52 UTC**  
  Запуск FTK Imager.exe:  
  `\\Vboxsvr\d_drive\Imager_Lite_3.1.1\FTK Imager.exe`  
  Статус: создание образа диска, сохранение цифровых доказательств.

## Summary

Инцидент развивался от одноразового открытия фишингового ярлыка до сложной цепочки постэксплуатационной активности, включающей использование системных утилит, сетевую разведку, взаимодействие с внешними ресурсами и последующую криминалистическую фиксацию состояния системы.
