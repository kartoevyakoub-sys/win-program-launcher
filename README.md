<div align="center">

# Windows Setup Hub (`WinPackApp`)

**Единый хаб и лаунчер для быстрой установки базового софта, утилит диагностики и сетевых клиентов после переустановки или при обслуживании Windows.**

[![GitHub Pages](https://img.shields.io/badge/Web-GitHub%20Pages-1f6feb?style=flat-square&logo=github)](https://krtv-vov.github.io/win-program-launcher/)
[![Vercel](https://img.shields.io/badge/Mirror-Vercel-000000?style=flat-square&logo=vercel)](https://win-program-launcher.vercel.app/)
[![Release](https://img.shields.io/github/v/release/krtv-vov/win-program-launcher?style=flat-square&color=3b82f6&label=WinPackApp.exe)](https://github.com/krtv-vov/win-program-launcher/releases)
[![Platform](https://img.shields.io/badge/Platform-Windows%2010%20%2F%2011-0078D6?style=flat-square&logo=windows)](https://github.com/krtv-vov/win-program-launcher/releases)

</div>

---

## О проекте

После чистой установки Windows, переезда на новый ПК или при удалённой/выездной настройке компьютера приходится тратить время на поиск десятка официальных сайтов и релизов: браузеры, архиваторы, кодеки, мессенджеры, антивирусные сканеры, библиотеки Visual C++ и средства обхода блокировок.

**Windows Setup Hub** закрывает эту задачу в два клика:
1. **Веб-каталог (`index.html`)** — тёмный, быстрый интерфейс без лишней воды, где весь нужный софт разбит по категориям, снабжён фильтрацией, поиском и готовыми профилями под типовые сценарии.
2. **Desktop-лаунчер (`WinPackApp.exe`)** — компактный исполняемый файл для Windows, который сам проверяет доступность площадок (Vercel и GitHub Pages) и открывает каталог в отдельном окне браузера в режиме `--app` без адресной строки и лишних вкладок.

---

## Быстрый старт

### Способ 1 — Скачать готовый `WinPackApp.exe` (удобнее всего)
1. Перейди в раздел **[Releases](https://github.com/krtv-vov/win-program-launcher/releases)**.
2. В блоке **Assets** последнего релиза скачай **`WinPackApp.exe`**.
3. Запусти файл — лаунчер автоматически выберет доступный сервер и откроет окно **Windows Setup Hub**.

### Способ 2 — Открыть прямо в браузере
* **Основное зеркало (Vercel):** https://win-program-launcher.vercel.app/
* **Резервное зеркало (GitHub Pages):** https://krtv-vov.github.io/win-program-launcher/

---

## Что внутри каталога

### Готовые профили в один клик
Чтобы не отмечать программы вручную каждый раз, в шапке доступны пресеты под конкретные задачи:
* **Быстрый старт клиента** — базовый набор на каждый день (`Google Chrome`, `Telegram Desktop`, `WhatsApp`, `AnyDesk`, `7-Zip`, `VLC`, `qBittorrent`, `Kaspersky Free`).
* **Обходы + связь (РФ)** — инструменты для стабильного доступа и общения (`zapret`, `Happ`, `Hiddify Next`, `AmneziaVPN`, `Telegram Desktop`, `AyuGram Desktop`, `Google Chrome`, `7-Zip`).
* **Лечение и проверка ПК** — набор для очистки и диагностики заражённой или забитой системы (`Dr.Web CureIt!`, `Kaspersky Virus Removal Tool`, `Malwarebytes`, `Revo Uninstaller Free`, `WizTree`, `CrystalDiskInfo`).
* **Слабый / старый ПК** — лёгкий софт без лишней нагрузки на ОЗУ и процессор (`Mozilla Firefox`, `MPC-BE`, `AIMP`, `7-Zip`, `GoodbyeDPI`, `AnyDesk`, `CrystalDiskInfo`, `CPU-Z`).
* **Максимум (всё подряд)** — выделяет сразу все позиции каталога.

### Разделы программ и утилит
* **Браузеры:** Google Chrome, Mozilla Firefox, Яндекс Браузер, Brave Browser, Zen Browser.
* **Антивирусы и безопасность:** Kaspersky Free, Dr.Web CureIt!, Malwarebytes, Kaspersky Virus Removal Tool (KVRT).
* **Обход блокировок и VPN:** zapret (Discord / YouTube), GoodbyeDPI, Happ, Hiddify Next, AmneziaVPN, v2rayN.
* **Мессенджеры и удалённый доступ:** Telegram Desktop, AyuGram Desktop, WhatsApp для Windows, AnyDesk, RustDesk.
* **Торренты и медиа:** qBittorrent, VLC Media Player, MPC-BE, AIMP.
* **Архиваторы, системное и диагностика:** 7-Zip, WinRAR, Visual C++ Redistributable (All-in-One), DirectX End-User Runtime, CrystalDiskInfo, CPU-Z, HWMonitor, WizTree, Revo Uninstaller Free.

---

## Как работает `WinPackApp.exe`

Лаунчер написан на Python (`app.py`) и упакован в один автономный `.exe` без консольного окна:
1. **Проверка доступности серверов (Fallback):** по очереди проверяет список адресов `URLS` (сначала Vercel, затем GitHub Pages) лёгким HTTP-запросом с таймаутом `2.5` секунды и берёт первый рабочий.
2. **Запуск в режиме приложения:** ищет установленный **Google Chrome** или **Microsoft Edge** и открывает каталог с флагом `--app=<url>`, чтобы интерфейс выглядел как нативная программа. Если ни один из них не найден — открывает страницу в системном браузере по умолчанию.
3. **Массовое открытие вкладок:** в самом интерфейсе кнопка **«Открыть отмеченные»** открывает выбранные страницы скачивания с небольшой задержкой (`280 мс`), чтобы снизить риск срабатывания блокировщика всплывающих окон. *(Если браузер всё же заблокирует часть вкладок, появится подсказка — достаточно разрешить всплывающие окна для сайта и нажать кнопку повторно.)*

---

## Структура репозитория

```text
win-program-launcher/
├── index.html       # Веб-приложение: вёрстка, стили, база программ, профили и поиск
├── app.py           # Исходный код desktop-лаунчера с проверкой URL и запуском --app
├── icon.ico         # Иконка приложения для сборки WinPackApp.exe
├── images/          # Папка под фавиконку и иконки карточек
└── README.md        # Описание проекта и инструкция по сборке
