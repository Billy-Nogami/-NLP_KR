# NLP Classification Results

Проект сравнивает пять подходов к классификации текстов: классические TF-IDF признаки, RNN-модели, Transformers, LoRA/full fine-tuning и LLM pipeline с zero-shot/few-shot режимами.

## Распределение работы

| Участник | Часть проекта |
|---|---|
| Андрей | TF-IDF и классические ML-модели |
| Роман | RNN: BiLSTM и BiGRU |
| Георгий | Transformers |
| Анна | LoRA vs full RoBERTa fine-tune |
| Илья | LLM pipeline: zero-shot и few-shot |

## Сводная таблица результатов

| Метод | Model | Accuracy | Precision macro | Recall macro | F1 macro | Precision weighted | Recall weighted | F1 weighted | Комментарий |
|---|---|---:|---:|---:|---:|---:|---:|---:|---|
| TF-IDF classic NLP | Logistic Regression | 0.9145 | 0.914680 | 0.9145 | 0.914311 |  |  |  | Исходные precision/recall/f1 перенесены в macro-колонки |
| TF-IDF classic NLP | XGBoost | 0.8360 | 0.838273 | 0.8360 | 0.835810 |  |  |  | Исходные precision/recall/f1 перенесены в macro-колонки |
| RNN | BiLSTM | 0.9050 | 0.905080 | 0.9050 | 0.904689 |  |  |  |  |
| RNN | BiGRU | 0.9065 | 0.906676 | 0.9065 | 0.906537 |  |  |  |  |
| Transformers |  |  |  |  |  |  |  |  | Место под результаты |
| LoRA finetune | base_model | 0.2525 | 0.201671 | 0.2525 | 0.105273 |  |  |  |  |
| LoRA finetune | lora_peft | 0.9260 | 0.925965 | 0.9260 | 0.925967 |  |  |  |  |
| LoRA finetune | full_finetune | 0.9365 | 0.936628 | 0.9365 | 0.936515 |  |  |  |  |
| LLM pipeline | Zero-shot | 0.8450 | 0.8451 | 0.8450 | 0.8448 | 0.8451 | 0.8450 | 0.8448 |  |
| LLM pipeline | Few-shot | 0.8860 | 0.8864 | 0.8860 | 0.8860 | 0.8864 | 0.8860 | 0.8860 |  |

## Краткие выводы

Лучший результат среди заполненных экспериментов показал `full_finetune` с `F1 macro = 0.936515` и `accuracy = 0.9365`. LoRA fine-tuning также дал высокий результат: `F1 macro = 0.925967`.

Среди подходов без fine-tuning хорошо показали себя TF-IDF с Logistic Regression (`F1 macro = 0.914311`) и RNN-модель BiGRU (`F1 macro = 0.906537`). В LLM pipeline few-shot режим оказался лучше zero-shot: `F1 macro = 0.8860` против `0.8448`.

Excel-файл со сводной таблицей: `nlp_results_summary.xlsx`.
