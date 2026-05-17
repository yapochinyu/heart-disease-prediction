# ❤️ Heart Disease Prediction

Проект по предсказанию наличия сердечно-сосудистых заболеваний на основе клинических данных пациента.

Модель обучена на объединённом датасете (918 наблюдений, 11 признаков) и обёрнута в API для получения предсказаний.

---

## Описание задачи

Сердечно-сосудистые заболевания — одна из главных причин смертности в мире.  
Цель проекта — построить модель, которая по характеристикам пациента оценивает вероятность наличия заболевания.

---

## Данные

Датасет содержит следующие признаки:

- `Age` — возраст
- `Sex` — пол
- `ChestPainType` — тип боли в груди
- `RestingBP` — артериальное давление в покое
- `Cholesterol` — уровень холестерина
- `FastingBS` — повышенный сахар натощак (>120 mg/dl)
- `RestingECG` — результаты ЭКГ
- `MaxHR` — максимальный пульс
- `ExerciseAngina` — стенокардия при нагрузке
- `Oldpeak` — депрессия ST
- `ST_Slope` — наклон сегмента ST

Целевая переменная:

- `HeartDisease` — наличие заболевания (1 — да, 0 — нет)

---

## Этапы проекта

1. Первичное ознакомление с данными
2. Предобработка:
   - проверка пропусков
   - анализ дубликатов
   - выявление аномалий
3. EDA (исследовательский анализ)
4. Подготовка признаков
5. Обучение моделей:
   - Logistic Regression
   - Random Forest
   - XGBoost
   - LightGBM
6. Кросс-валидация и выбор лучшей модели
7. Сохранение пайплайна (preprocessing + модель)
8. Разработка API

---

## Модели

Оценка проводилась по метрикам:

- ROC AUC
- Recall
- F1-score

Лучшая модель: **Random Forest**

---

## Используемые технологии

- Python 3.11
- pandas, numpy
- scikit-learn
- xgboost, lightgbm
- matplotlib, seaborn
- FastAPI
- joblib

---

## Структура проекта

```
│   heart-disease-prediction.ipynb
│   heart.csv
│   README.md
├───api
│   └───app.py
│
├───envs
│       heart-api.yml
│       heart-disease-research-env.yml
│
└───models
        RandomForest_pipeline.pkl
```
---

## Установка и запуск

### 1. Клонирование репозитория

```bash
git clone https://github.com/yapochinyu/heart-disease-prediction.git
cd heart-disease-prediction
```

2. Создание окружения
```powershell
conda env create -f environment.yml
conda activate heart-api
```
3. Запуск API
```powershell
uvicorn api.app:app --reload
```
4. Открыть документацию
```http://127.0.0.1:8000/docs```

Пример запроса
```JSON
{
  "Age": 54,
  "Sex": "M",
  "ChestPainType": "ATA",
  "RestingBP": 130,
  "Cholesterol": 250,
  "FastingBS": 0,
  "RestingECG": "Normal",
  "MaxHR": 150,
  "ExerciseAngina": "N",
  "Oldpeak": 1.0,
  "ST_Slope": "Up"
}
```
Ответ API
```JSON
{
  "prediction": 1,
  "probability": 0.87
}
```


**Важно**
Модель ожидает данные в том же формате, что и при обучении
Все категориальные значения должны совпадать с обучающими
Обработка данных встроена в pipeline

**Возможные улучшения**
- Добавление новых признаков.
- Добавление тестов.
- Добавление обработки единиц измерения в api.

Источник данных

```https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction/data```

**Проект выполнен в учебных и практических целях.**