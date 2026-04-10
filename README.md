# Классификация тональности рецензий Кинопоиска

Бинарная классификация тональности рецензий с Кинопоиска на фильмы:
сравнение `TF-IDF/Word2Vec/FastText` с моделями `FFNN`, `RNN`, `LSTM` по качеству `F1` и времени обучения.

## Что в репозитории
- `kinopoisk_sentiment_research.ipynb` — ноутбук исследования.
- `output/jupyter-notebook/artifacts/model_comparison.csv` — сводная таблица качества и времени.
- `output/jupyter-notebook/artifacts/test_predictions_all_models.csv` — предсказания всех моделей.
- `output/jupyter-notebook/artifacts/best_model_test_predictions.csv` — предсказания лучшей модели.
- `train.csv` - обучающая выборка.
- `test.csv` - тестовая выборка.
- `requirements.txt` — зависимости для запуска.

## Условия исследования
- Зафиксирован `SEED`.
- Подбор гиперпараметров только на split внутри `train.csv`.
- `test.csv` не используется для обучения и тюнинга.
- Основная метрика: `f1_score`.

## Ключевые результаты
| Модель | best_val_f1 | test_f1 | total_time_sec |
|---|---:|---:|---:|
| TFIDF+FFNN | 0.8152 | **0.8213** | **79.34** |
| FASTTEXT+FFNN | 0.6868 | 0.6843 | 232.06 |
| W2V+FFNN | 0.6723 | 0.6815 | 126.99 |
| LSTM | 0.6452 | 0.6476 | 1148.15 |
| RNN | 0.5424 | 0.5553 | 1061.34 |

Вывод: `TF-IDF + FFNN` дал лучший F1 и лучший баланс по времени.

## Как запустить
1. Установить зависимости:
   - `pip install -r requirements.txt`
2. Положить `train.csv` и `test.csv` в корень проекта.
3. Запустить Jupyter и открыть `kinopoisk_sentiment_research.ipynb`.
4. Выполнить ячейки сверху вниз.
