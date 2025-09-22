# 📊 Bid Ask Spread Indicator для TradingView

[![Pine Script Version](https://img.shields.io/badge/Pine%20Script-v5-blue.svg)](https://www.tradingview.com/pine-script-docs/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/JonNash495/BidAskIndicator.svg)](https://github.com/JonNash495/BidAskIndicator)

Профессиональный индикатор для анализа bid/ask спреда на платформе TradingView с расширенными возможностями статистического анализа.

## 🚀 Основные возможности

- **📈 Визуализация bid/ask** - отображение цен покупки и продажи в реальном времени
- **📊 Анализ спреда** - расчет спреда в процентах и абсолютных значениях
- **🔍 Анализ глубины стакана** - 5/15, 8/30, 15/25, 20/40 уровни анализа
- **💧 Индекс ликвидности** - оценка качества торговых условий (0-100)
- **⚖️ Дисбаланс объема** - анализ соотношения bid/ask объемов
- **🏗️ Обнаружение стен** - поиск крупных заявок на уровнях
- **📉 Статистические инструменты** - скользящие средние, стандартное отклонение, экстремумы
- **🔔 Система алертов** - уведомления о резких изменениях спреда
- **🎨 Настраиваемый интерфейс** - полная кастомизация цветов и стилей
- **⏱️ Множественные таймфреймы** - работает на всех временных интервалах

## 📁 Структура проекта

```
├── 📁 src/                          # Исходный код
│   ├── 📄 BidAskIndicator.pine      # Основной индикатор
│   ├── 📄 BidAskAdvanced.pine       # Расширенная версия
│   ├── 📄 BidAskMarketDepth.pine    # Анализ глубины стакана
│   ├── 📄 BidAskUtils.pine          # Библиотека утилит
│   └── 📄 MarketDepthUtils.pine     # Утилиты для анализа стакана
├── 📁 examples/                     # Примеры использования
│   ├── 📄 SimpleUsage.pine          # Простой пример
│   ├── 📄 AdvancedUsage.pine        # Расширенный пример
│   └── 📄 MarketDepthExample.pine   # Пример анализа стакана
├── 📁 docs/                         # Документация
│   ├── 📄 README.md                 # Подробная документация
│   └── 📄 MarketDepthGuide.md       # Руководство по анализу стакана
├── 📄 config.json                   # Конфигурация
└── 📄 INSTALL.md                    # Инструкция по установке
```

## ⚡ Быстрый старт

### 1. Установка
1. Скопируйте код из `src/BidAskIndicator.pine`
2. Откройте TradingView → Pine Editor
3. Вставьте код и нажмите "Add to Chart"

### 2. Основные настройки
```pine
// Основные параметры
show_bid_line = true      // Показать линию Bid
show_ask_line = true      // Показать линию Ask  
show_spread = true        // Показать спред
enable_spread_alert = true // Включить алерты
```

## 📊 Скриншоты

### Основной индикатор
- Линии bid/ask с цветовой кодировкой
- Значения спреда в реальном времени
- Информационная таблица

### Расширенная версия
- Статистический анализ спреда
- Полосы волатильности
- Дополнительные индикаторы (RSI, MACD)

## 🛠 Использование

### Простой пример
```pine
//@version=5
include BidAskUtils.pine

// Получение bid/ask цен
bid_price = f_get_bid_price(close, "NORMAL")
ask_price = f_get_ask_price(close, "NORMAL")

// Расчет спреда
spread_percent = f_get_spread_percent(bid_price, ask_price, close)

// Отображение
plot(bid_price, "Bid", color=color.blue)
plot(ask_price, "Ask", color=color.red)
```

### Расширенный анализ
```pine
// Статистический анализ
spread_ma = f_get_spread_ma(spread_percent, 20)
spread_std = f_get_spread_std(spread_percent, 20)
spread_type = f_get_spread_type(spread_percent, spread_ma, spread_std)

// Алерты
if f_is_spread_anomaly(spread_percent, spread_ma, spread_std, 2.0)
    alert("Аномальный спред!", alert.freq_once_per_bar)
```

## 📈 Поддерживаемые инструменты

- ✅ **Forex** - валютные пары
- ✅ **Crypto** - криптовалютные пары  
- ✅ **Stocks** - акции
- ✅ **Indices** - индексы
- ✅ **Commodities** - товары

## ⚙️ Конфигурация

### Для начинающих
```json
{
  "show_bid_line": true,
  "show_ask_line": true,
  "show_spread": true,
  "enable_spread_alert": false
}
```

### Для опытных трейдеров
```json
{
  "show_bid_line": true,
  "show_ask_line": true,
  "show_spread": true,
  "show_spread_percent": true,
  "enable_spread_alert": true,
  "spread_threshold": 0.5,
  "show_spread_ma": true,
  "ma_length": 20
}
```

## 📚 Документация

- [📖 Подробная документация](docs/README.md)
- [🚀 Инструкция по установке](INSTALL.md)
- [⚙️ Конфигурация](config.json)

## 🤝 Вклад в проект

Мы приветствуем вклад в развитие проекта! Пожалуйста:

1. Форкните репозиторий
2. Создайте ветку для новой функции (`git checkout -b feature/AmazingFeature`)
3. Зафиксируйте изменения (`git commit -m 'Add some AmazingFeature'`)
4. Отправьте в ветку (`git push origin feature/AmazingFeature`)
5. Откройте Pull Request

## 📝 Лицензия

Этот проект распространяется под лицензией MIT. См. файл [LICENSE](LICENSE) для подробностей.

## ⚠️ Отказ от ответственности

Данный индикатор предназначен для образовательных и аналитических целей. Всегда проводите дополнительный анализ перед принятием торговых решений. Авторы не несут ответственности за любые финансовые потери.

## 📞 Поддержка

- 🐛 **Баги и проблемы**: [Issues](https://github.com/JonNash495/BidAskIndicator/issues)
- 💡 **Предложения**: [Discussions](https://github.com/JonNash495/BidAskIndicator/discussions)
- 📧 **Email**: [Связаться с автором](mailto:your-email@example.com)

## 🌟 Звезды

Если проект был полезен, поставьте звезду ⭐ - это мотивирует нас развивать его дальше!

---

**Создано с ❤️ для торгового сообщества**
