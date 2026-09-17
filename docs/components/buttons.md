[← Каталог](../design-system.md) · [Основы](../foundations/README.md) · [Компоненты](README.md) · [Блоки](../blocks/README.md) · [Открытые вопросы](../design-system-open-questions.md)

# Кнопки

## 1. Назначение

Кнопки первичного и вторичного действия (CTA), используемые в блоках страницы и в хедере.

## 2. Источник и статус спецификации

Четыре варианта:

- **Primary CTA** (`Buttons / Primary / CTA`) — инстанс из [Top Menu Slider](../blocks/top-menu-slider.md) (alaio-sites, node 190:41107), [Chips Block](../blocks/chips-block.md) (Untitled, node 0:1) и [Header (Figma)](../blocks/header-figma.md) (Untitled, node 28:36775, инстанс 28:36810). Инстанс в Header (Figma) подтверждает, что это один и тот же переиспользуемый компонент, а не отдельная реализация (до разбора [Header (Figma)](../blocks/header-figma.md) это было неясно, кодовая реализация не называла инстанс) — размер и паддинг варьируются по инстансу вместе с длиной текста (см. раздел 4).
- **Secondary** (`Buttons / Secondary / Learn more`) — инстанс из блока [«Partners»](../blocks/partners.md) (Untitled, node 32:1520).
- **Small** (`Buttons / Small`) — круглая кнопка-иконка без заливки; встречена в [Customer Stories Slider](../blocks/customer-stories-slider.md) (Untitled, node 124:3286) в двух ролях: маленькая кнопка-стрелка внутри карточки-кейса и (с другими цветами) — круглая стрелка прокрутки ряда карточек.
- **Tertiary / Icon** (`Buttons / Tertiary / Icon`) — текст + иконка, без фона и без обводки; встречена там же, как ссылка «More customer stories».

## 3. Структура

Каждый вариант — горизонтальный контейнер с центрированным текстом (label); Secondary дополнительно имеет обводку вместо заливки.

## 4. Геометрия

| Вариант | Размер | Радиус | Паддинг |
|---|---|---|---|
| Primary CTA — в Top Menu Slider / Chips Block | 183×54 px | 12 px | 36 / 16 px |
| Primary CTA — в хедере | 167×50 px | 12 px | 28 / 14 px |
| Primary CTA — в Customer Stories Slider | 192×54 px | 12 px | 36 / 16 px |
| Secondary (Learn more) | 286×54 px (ширина — по содержимому текста) | 12 px | 36 / 16 px |
| Small (кнопка-стрелка в карточке) | 34×34 px | 8 px | 5 px |
| Small (стрелка прокрутки ряда) | 46×46 px | 100 px (полный круг) | 5 px |
| Tertiary / Icon | По содержимому (текст + иконка 28×28) | — (нет фона/обводки) | 36 / 16 px |

Радиус 12 px у Primary CTA и Secondary — ступень «Кнопка CTA» из [общей таблицы радиусов](../foundations/radii-strokes.md). Размер и паддинг Primary CTA не фиксированы одним значением — все разобранные инстансы меньше по тексту («Start for free» в хедере, «Start for free» в Customer Stories Slider) получают свой паддинг/размер; это не разные компоненты, а один компонент, подстраивающийся под содержимое. У Small радиус меняется по роли: 8 px у кнопки внутри карточки, полный круг (100 px) у стрелки прокрутки — два разных использования одного названного компонента, не два отдельных радиуса-правила.

## 5. Типографика

- Общий стиль **Button** (см. [Типографика](../foundations/typography.md)): Google Sans Flex Semibold 600, 18 px, line-height **140%**.
- **Primary CTA** (инстанс в хедере): Google Sans Flex Semibold 18 px — совпадает с общим стилем Button; line-height в этом узле отдельно не измерен.
- **Secondary** (блок «Partners»): Google Sans Flex Semibold 600, 18 px — но с line-height **120%**, зафиксированным отдельным решением при описании блока. ⚠ Это расходится с line-height 140% из общего стиля Button — см. [открытые вопросы](../design-system-open-questions.md).
- **Primary CTA и Tertiary/Icon в Customer Stories Slider**: в источнике текст оформлен как `Montserrat Bold` — вместо согласованного стиля Button (Google Sans Flex Semibold). Ранее такое же расхождение (Montserrat вместо Google Sans Flex) встречалось в исходном узле кнопки блока «Партнёры», но там уже зафиксировано решение использовать Button-стиль (см. блок [Partners](../blocks/partners.md)); здесь применяется то же решение. При реализации использовать стиль Button; Montserrat не переносить как правило.

## 6. Цвета и варианты

| Вариант | Заливка | Обводка | Цвет текста |
|---|---|---|---|
| Primary CTA | `accent/yellow` `#FFD972` | Нет | `text/primary` `#251E49` |
| Secondary (Learn more) | Прозрачная (виден фон блока) | 2 px, `text/primary` `#251E49` | `#251E49` |

## 7. Состояния и поведение

- Primary CTA в хедере (по кодовой реализации, [Header (код)](../blocks/header.md)): hover — заливка меняется на `#FFC800`. Figma-источник статичен и это состояние не показывает.
- Для остальных инстансов Primary CTA и для Secondary состояние hover источником не задано.

## 8. Адаптивность

Не задано.

## 9. Правила контента

- Текст лейбла — по смыслу конкретного блока («Find a Bitrix24 Partner» в блоке «Partners» — пример, а не фиксированная надпись).
- Если кнопок две — размещать в отдельном горизонтальном Auto Layout с gap 10 px (см. [Сетка, контейнеры и отступы](../foundations/layout-grid.md)).

## 10. Связанные компоненты и токены

- `accent/yellow` (`#FFD972`), `text/primary` (`#251E49`).
- Радиус: ступень «Кнопка CTA» — [Радиусы и обводки](../foundations/radii-strokes.md).
- Отступ до кнопки/группы кнопок — [Сетка, контейнеры и отступы](../foundations/layout-grid.md).
- Используется в блоках: [Top Menu Slider](../blocks/top-menu-slider.md), [Chips Block](../blocks/chips-block.md), [Card Frame Scroll](../blocks/card-frame-scroll.md), [Partners](../blocks/partners.md), [Header](../blocks/header.md) / [Header (Figma)](../blocks/header-figma.md), [Bullet Slider](../blocks/bullet-slider.md) (Secondary), [Customer Stories Slider](../blocks/customer-stories-slider.md) (Primary CTA, Small, Tertiary/Icon).

## 11. Проверка

- Primary CTA — 183×54 паддинг 36/16 (слайдер/чипы) или 167×50 паддинг 28/14 (хедер), радиус 12 в обоих случаях, `#FFD972`, текст `text/primary`.
- Secondary — 286×54, радиус 12, обводка 2 px `#251E49`, паддинг 36/16, текст Google Sans Flex Semibold 18/120%.
- Hover (`#FFD972` → `#FFC800`) подтверждён только для хедерного инстанса по кодовой реализации.
- Small — 34×34 радиус 8 (в карточке) или 46×46 радиус 100 (стрелка прокрутки), паддинг 5, без заливки, обводка есть только у варианта в карточке.
- Tertiary/Icon — без фона и обводки, паддинг 36/16, иконка 28×28 после текста.
