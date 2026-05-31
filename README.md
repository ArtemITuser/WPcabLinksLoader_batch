# WPcabLinksLoader_batch v1.3.0

[![Version](https://img.shields.io/badge/version-1.3.0-blue)](https://github.com/ArtemITuser/WPcabLinksLoader_batch/releases)
[![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-lightgrey)](#)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

> 📦 Простой загрузчик CAB-файлов из списка ссылок для восстановления/обновления Windows Phone / Windows 10 Mobile.  
> 📦 Simple CAB downloader for Windows Phone / Windows 10 Mobile restoration and updates.

Источники ссылок: коллекция от @Empyreal96 — https://github.com/Empyreal96/WPCabLinks.db  
Для установки: Universal Updater от @FadilFadz01 — https://github.com/fadilfadz01/Universal_Updater/releases

---

## 🚀 Быстрый старт / Quick Start

### Вариант 1: PowerShell (рекомендуется) / PowerShell (recommended)
```powershell
# 1. Откройте папку со скриптом в проводнике
# 2. ПКМ → "Выполнить с помощью PowerShell" или:
.\WPcab_worker.ps1

# Опционально: указать язык сразу
.\WPcab_worker.ps1 -Lang ru   # Русский
.\WPcab_worker.ps1 -Lang en   # English
```

### Вариант 2: Batch (legacy) / Batch (legacy)
```cmd
:: RU
downloader_1.0.0_RU.bat

:: EN
downloader_1.0.0_EN.bat
```

> ⚠️ Скрипт автоматически запросит права администратора (UAC). Подтвердите запрос.

---

## ✨ Что нового в v1.3.0 / What's New in v1.3.0

| Фича / Feature | Описание / Description |
|----------------|------------------------|
| 🔐 Авто-UAC | Автоматический запрос прав администратора без ручной правки `.bat` |
| 🌐 Двуязычный интерфейс | Переключение RU/EN при запуске или через `-Lang` |
| 🔤 UTF-8 + BOM | Исправлено отображение кириллицы в PowerShell 5.1 и консоли |
| 📦 Валидация CAB | Проверка сигнатуры `MSCF` (4D 53 43 46) перед завершением загрузки |
| 🔄 Retry-логика | До 3 попыток загрузки при сетевых ошибках |
| ⚡ BITS + fallback | Приоритет `BitsTransfer`, резерв — `Invoke-WebRequest` |
| 📁 Timestamped output | Папки вида `CAB_Downloads_YYYYMMDD_HHMMSS` для удобства |
| 📋 Детальный лог | Логи в консоль + файл `download_log_*.txt` с таймстемпами |
| 🎨 Цветной вывод | Статусы с цветовой индикацией (зелёный/красный/жёлтый) |

---

## 📋 Системные требования / System Requirements

| Компонент | Требование |
|-----------|------------|
| **ОС** | Windows 10 (19045+) / Windows 11 (x64, arm64, x86) |
| **PowerShell** | 5.1+ (встроен в Win10/11) |
| **.NET Framework** | 4.5+ (для `System.Windows.Forms.OpenFileDialog`) |
| **Права** | Администратор (для записи в системные пути, опционально) |
| **Сеть** | Доступ к `download.windowsupdate.com` |

> 💡 На Windows 8.1 может потребоваться ручное обновление PowerShell до версии 5.1.

---

## 📁 Структура проекта / Project Structure

```
WPcabLinksLoader_batch/
├── WPcab_worker.ps1          # Основной скрипт (CLI, v1.3.0) ✅ РЕКОМЕНДУЕТСЯ
├── downloader_1.0.0_RU.bat   # Legacy batch (RU)
├── downloader_1.0.0_EN.bat   # Legacy batch (EN)
├── README.md                 # Этот файл
└── LICENSE                   # MIT License
```

---

## 🛠 Использование / Usage

### 1. Подготовка файла со ссылками
Создайте `.txt` файл с одним URL на строку:
```txt
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.data.spku_9505f7ebd89aeca5b3f4d86dbecdfca3587dadf1.cab
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.mainos.spku_ed303665672edd1f522b95c98c439876e2dc0670.cab
```
> ✅ Поддерживаются пустые строки и комментарии (игнорируются).  
> ❌ Не добавляйте не-HTTP ссылки — они будут пропущены.

### 2. Запуск
```powershell
.\WPcab_worker.ps1
```
- Выберите язык (если не указан `-Lang`)
- Разрешите UAC
- Выберите `.txt` файл через диалоговое окно
- Дождитесь завершения

### 3. Результат
```
CAB_Downloads_20260601_143022/
├── microsoft.base.weh.data.spku_....cab
├── microsoft.base.weh.mainos.spku_....cab
└── download_log_20260601_143022.txt
```
📁 Папка автоматически откроется в Проводнике.

---

## 🔍 Лог-файл / Log File

Пример содержимого `download_log_*.txt`:
```[2026-05-31 18:04:29] === WP cab loader v1.3.0 started ===
[2026-05-31 18:04:29] Source : C:\Users\Artem\Desktop\AstoriaPackages.txt
[2026-05-31 18:04:29] Output : C:\Users\Artem\Downloads\Mobile Devices\CAB_Downloads_20260531_180429
[2026-05-31 18:04:29] Language: ru
[2026-05-31 18:04:29] Found URLs: 2
[2026-05-31 18:04:29] [1/2] Downloading: microsoft.ms_projecta.mainos.spkg_9dec9dcfe0f22750e3737e9a484e7a60e193303c.cab
[2026-05-31 18:10:09] [OK] microsoft.ms_projecta.mainos.spkg_9dec9dcfe0f22750e3737e9a484e7a60e193303c.cab  size=109373751
[2026-05-31 18:10:09] [2/2] Downloading: microsoft.ms_projecta.mainos.cbsu_c36c1e67bd04b694a01b65efeb70213ff439be76.cab
[2026-05-31 18:13:07] [OK] microsoft.ms_projecta.mainos.cbsu_c36c1e67bd04b694a01b65efeb70213ff439be76.cab  size=91245425
[2026-05-31 18:15:32] ITOG: OK=2  FAIL=0  TOTAL=2
```

---

## ❓ Устранение неполадок / Troubleshooting

| Проблема / Issue | Решение / Solution |
|------------------|-------------------|
| **"Кракозябры" вместо русского** | Убедитесь, что `WPcab_worker.ps1` сохранён как **UTF-8 with BOM**. Выполните: `[System.IO.File]::WriteAllText("WPcab_worker.ps1", (Get-Content -Raw "WPcab_worker.ps1"), [System.Text.UTF8Encoding]::new($true))` |
| **Ошибка доступа / Access denied** | Запустите от имени администратора или проверьте антивирус/брандмауэр |
| **Файлы скачиваются пустыми** | Проверьте доступ к `download.windowsupdate.com`; возможно, требуется прокси/VPN |
| **Неверная сигнатура CAB** | Файл повреждён или не является CAB. Скрипт автоматически удалит его и повторит загрузку (до 3 раз) |
| **PowerShell не запускается** | Выполните в админ-консоли: `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` |

## Снимки экрана (пример работы программы) / Screenshots

Loadinп successful:
<img width="1710" height="1131" alt="Снимок экрана 2026-05-31 190403" src="https://github.com/user-attachments/assets/062c088a-925b-432a-af36-be609ce283f9" />

Loading failed:
<img width="1710" height="1131" alt="Снимок экрана 2026-05-31 190351" src="https://github.com/user-attachments/assets/ed8ef962-aa03-4dfd-bf86-312f10f83457" />


---

## 🤝 Вклад в проект / Contributing

1. Форкните репозиторий
2. Создайте ветку (`git checkout -b feature/YourFeature`)
3. Внесите изменения + протестируйте
4. Откройте Pull Request с описанием изменений

> 📝 Предпочтительный стиль: комментарии на языке интерфейса (RU/EN), код — на английском.

## 🌐 Локализация / Localization

<details>
<summary><strong>Как добавить новый язык</strong> (нажмите для раскрытия)</summary>

### 1. Добавьте язык в `param()` и хеш-таблицу `$LangMap`

```powershell
param(
    [ValidateSet('ru','en','de')]  # ← Добавьте код языка (двухбуквенный)
    [string]$Lang = ''
)

$LangMap = @{
    # ... существующие ru, en ...
    de = @{  # ← Новый язык
        selectFile  = "Wählen Sie eine Datei mit URL-Liste"
        filter      = "Textdateien (*.txt)|*.txt|Alle Dateien (*.*)|*.*"
        noFile      = "Keine Datei ausgewählt. Beenden."
        notFound    = "Datei nicht gefunden: {0}"
        foundLinks  = "Gefundene URLs: {0}"
        noLinks     = "Keine URLs in der Datei gefunden."
        progress    = "[{0}/{1}] Wird heruntergeladen: {2}"
        retry       = "[{0}/{1}] Wiederholungsversuch {2} für: {3}"
        success     = "[{0}/{1}] Erfolg: {2} [{3} Bytes]"
        errEmpty    = "[{0}/{1}] Fehler: Leere Datei - {2}"
        errFail     = "[{0}/{1}] Download fehlgeschlagen: {2}"
        errSig      = "[{0}/{1}] Fehler: Ungültige CAB-Signatur - {2}"
        skipEmpty   = "[{0}/{1}] Leere Zeile überspringen"
        stats       = "=========== STATISTIK ============"
        s_success   = "Erfolgreich: {0}"
        s_failed    = "Fehlgeschlagen: {0}"
        s_total     = "Gesamt: {0}"
        logSaved    = "Log gespeichert: {0}"
        dirSaved    = "Download-Ordner: {0}"
        openingDir  = "Ordner wird in Explorer geöffnet..."
    }
}
```

### 2. Протестируйте
```powershell
.\WPcab_worker.ps1 -Lang de
```

### 📋 Все ключи для перевода (v1.3.0)
| Ключ | Описание | Пример (RU) |
|------|----------|-------------|
| `selectFile` | Заголовок OpenFileDialog | `Выберите файл со списком URL` |
| `filter` | Фильтр файлов | `Текстовые файлы (*.txt)\|*.txt\|...` |
| `noFile` / `notFound` | Ошибки выбора файла | `Файл не выбран` / `Файл не найден: {0}` |
| `foundLinks` / `noLinks` | Статус поиска URL | `Обнаружено ссылок: {0}` |
| `progress` | Шаблон прогресса | `[{0}/{1}] Загрузка: {2}` |
| `retry` | Повторная попытка | `[{0}/{1}] Повторная попытка {2} для: {3}` |
| `success` | Успешная загрузка | `[{0}/{1}] Успешно: {2} [Размер: {3} байт]` |
| `errEmpty` / `errSig` / `errFail` | Ошибки загрузки | `[{0}/{1}] Ошибка: ...` |
| `skipEmpty` | Пропуск пустой строки | `[{0}/{1}] Пропуск пустой строки` |
| `stats` / `s_success` / `s_failed` / `s_total` | Статистика | `Успешно: {0}` |
| `logSaved` / `dirSaved` / `openingDir` | Итоги | `Лог сохранён: {0}` |

> ⚠️ **Важно:** 
> - Сохраняйте плейсхолдеры `{0}`, `{1}`, `{2}`, `{3}` — они используются для `-f` форматирования.
> - Не переводите технические термины: `CAB`, `BITS`, `URL`, `TLS`.
> - Сохраняйте файл как **UTF-8 with BOM**.

### 📤 Отправка перевода
1. Форкните репозиторий → создайте ветку `i18n/add-XX`
2. Добавьте перевод **только в `$LangMap`** (не меняйте логику скачивания)
3. Протестируйте: `.\WPcab_worker.ps1 -Lang XX`
4. Откройте PR с чеклистом:
   ```markdown
   - [x] Все 20 ключей переведены
   - [x] Протестировано на Win10/11, PowerShell 5.1
   - [x] Файл сохранён как UTF-8 with BOM
   - [x] Плейсхолдеры {0}-{3} сохранены
   ```

💡 **Совет:** Для поиска недостающих ключей используйте:
```powershell
Compare-Object ($LangMap.ru.Keys) ($LangMap.XX.Keys)  # покажет расхождения
```

</details>

---

---

## ⚖️ Лицензия и отказ от ответственности / License & Disclaimer

```
MIT License — см. файл LICENSE

Этот скрипт предоставляется «как есть», без каких-либо гарантий. 
Автор не несёт ответственности за возможные последствия использования.
Вы используете скрипт на свой страх и риск.

This script is provided "AS IS", without warranty of any kind.
The author is not liable for any damages arising from its use.
Use at your own risk.
```

---

## 🙏 Благодарности / Credits

- [@Empyreal96](https://github.com/Empyreal96) — за коллекцию CAB-ссылок [WPCabLinks.db](https://github.com/Empyreal96/WPCabLinks.db)
- [@FadilFadz01](https://github.com/fadilfadz01) — за инструмент [Universal Updater](https://github.com/fadilfadz01/Universal_Updater)

---

## 📬 Контакты / Contact

- 🐙 GitHub Issues: [Сообщить о проблеме](https://github.com/ArtemITuser/WPcabLinksLoader_batch/issues)
- ✈️ Telegram: [@OchkinArtem](https://t.me/OchkinArtem)

> При обращении указывайте: версию скрипта, ОС, текст ошибки и фрагмент лога.

---

*Last updated: June 2026 • v1.3.0 stable* 🚀
