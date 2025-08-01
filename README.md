# Прогнозирование покупательской активности клиентов

## Описание проекта

Данный проект представляет собой комплексный анализ покупательского поведения клиентов и разработку модели машинного обучения для прогнозирования снижения покупательской активности. Проект включает в себя исследовательский анализ данных, предобработку, моделирование и сегментацию клиентов.

## Цель исследования

Разработка модели классификации для прогнозирования будущей покупательской активности клиентов на основе исторических данных о поведении, предпочтениях и финансовых показателях.

## Структура данных

Анализ проводился на 4 взаимосвязанных датасетах по 1300 уникальным пользователям каждый:

1. **market_file.csv** - действия пользователей на платформе
2. **market_money.csv** - генерируемая выручка  
3. **market_time.csv** - длительность сессий
4. **money.csv** - среднемесячная прибыль за квартал

### Основные признаки:
- **Покупательская активность** (целевая переменная): "Снизилась" / "Прежний уровень"
- **Тип сервиса**: "премиум" / "стандарт"
- **Маркетинговая активность**: показатели за 6 месяцев и текущий месяц
- **Поведенческие метрики**: длительность сессий, глубина просмотра, акционные покупки
- **Финансовые показатели**: выручка по месяцам, прибыль

## Технологический стек

- **Python 3.9**
- **Pandas** - обработка и анализ данных
- **NumPy** - численные вычисления
- **Scikit-learn** - машинное обучение
- **Matplotlib/Seaborn** - визуализация
- **Phik** - корреляционный анализ
- **SHAP** - интерпретация моделей

## Основные этапы работы

### 1. Предобработка данных
- Проверка на дубликаты и пропуски
- Исправление опечаток в категориальных переменных
- Приведение типов данных
- Удаление записей с нулевой выручкой

### 2. Исследовательский анализ данных
- Статистический анализ числовых переменных
- Визуализация распределений (гистограммы, box-plot)
- Анализ категориальных переменных
- Корреляционный анализ с использованием Phik

### 3. Подготовка данных для моделирования
- Объединение таблиц
- Создание пайплайнов для предобработки:
  - OneHotEncoder для категориальных переменных
  - OrdinalEncoder для порядковых переменных
  - StandardScaler/MinMaxScaler для числовых переменных
- Разделение на обучающую и тестовую выборки

### 4. Моделирование
Использован автоматизированный Pipeline с поиском оптимальной модели:
- **DecisionTreeClassifier**
- **KNeighborsClassifier** 
- **LogisticRegression**
- **SVC**

### 5. Оценка качества
- Кросс-валидация (5-fold)
- Метрики: Accuracy, ROC-AUC
- Матрица ошибок

## Результаты

### Лучшая модель
**Логистическая регрессия** с параметрами:
- C = 4
- random_state = 42
- Точность на тестовой выборке: **89.2%**
- ROC-AUC: **91.5%**

### Анализ важности признаков
**Наиболее значимые предикторы:**
- Время, проведенное на сайте
- Глубина просмотра (страницы/категории за сессию)
- Интерес к категории "Бытовая техника и электроника"
- Объем акционных покупок

### Сегментация клиентов
Пользователи разделены на 4 группы по критериям:
- Динамика активности (снижение/стабильность)
- Уровень прибыльности (высокий/низкий)

**Фокус исследования:** сегмент "Снижение активности при высокой прибыльности"

## Бизнес-рекомендации

### Для реактивации целевого сегмента:
1. **Разместить на главной странице акционный блок** с выделением товаров для детей
2. **Учитывать особенности сегмента:**
   - Повышенный интерес к детским товарам (+7% к среднему)
   - Высокая чувствительность к скидкам
   - Ключевая роль времени на сайте и глубины просмотра

### Стратегические меры:
- Усиление вовлеченности через интерактивные элементы
- Приоритизация акционных механик для категории электроники
- Персонализация предложений
- Улучшение UX/UI для увеличения времени сессий

## Установка и запуск

### Требования
```bash
pip install pandas numpy scikit-learn matplotlib seaborn phik shap
```

### Версии библиотек
```
seaborn==0.13.2
matplotlib==3.8.4
scikit-learn==1.6.1
numpy==1.22.4
```

## Структура проекта

```
Git2/
├── Обучение с учителем.ipynb    # Основной Jupyter notebook
└── README.md                    # Документация проекта
```

## Заключение

Разработанное решение позволяет:
- Прогнозировать покупательское поведение с высокой точностью
- Формировать адресные маркетинговые стратегии
- Удерживать экономически значимые клиентские группы
- Оптимизировать пользовательский опыт на основе данных

Модель демонстрирует отличные результаты и может быть использована для автоматизации процессов удержания клиентов в реальном бизнесе. 