
#### Diabetes 130-US hospitals readmission (Kaggle)
- [https://www.kaggle.com/datasets/brandao/diabetes](https://www.kaggle.com/datasets/brandao/diabetes)
- Сущность: пациент (`patient_nbr`)
- Событие: readmission (повторная госпитализация)
- Время: admission/discharge time (можно перевести id в дату)
- Повторяемость: пациенты могут возвращаться много раз

#### Recidivism of Prisoners Released (BJS dataset)
- https://www.kaggle.com/datasets/slonnadube/recidivism-for-offenders-released-from-prison?select=prison_recidivists_with_recidivism_type_only.csv
- ~400k освобождённых
- наблюдение 3–5 лет
- события: повторные аресты
✔ есть интервалы времени до повторных преступлений (но нет самих id)

#### GDELT (глобальная база событий)
- Ссылка: https://www.gdeltproject.org/data.html#rawdatafiles
  (документация: http://data.gdeltproject.org/documentation/GDELT-Data_Format_Codebook.pdf)
  Сами файлы: http://data.gdeltproject.org/events/index.html (по дням)
- Масштаб: миллиарды событий по всему миру (новости, политика, конфликты)
- Каждое событие включает:
    - timestamp
    - тип события (CAMEO код)
    - actors, location, tone
    - контекстные признаки (есть ссылки на источники новостей)
Можно агрегировать по субъекту → получить последовательность событий для каждого актора/страны.

#### OpenForecast (новый крупный датасет событий)
- Датасет: **OpenForecast**
- Масштаб: **43k сложных событий (1950–2024)**
- Содержит:
    - временную эволюцию событий
    - последовательные шаги развития
    - атрибуты и контекст
Подходит для **long-term event evolution prediction** и моделирования цепочек событий.

#### [Deep Recurrent Survival Analysis (DRSA)](https://github.com/songhwanjun/drsa/tree/367b63a31834e45d6b2db3379d19ea7d212268d6?tab=readme-ov-file#deep-recurrent-survival-analysis-drsa)
- Ссылка на [статью](https://arxiv.org/pdf/1809.02403)
- Много медицинских [наборов данных](https://hbiostat.org/data/)(support2csv.zip)
- Набор музыкальных исполнителей 1. [lastfm-dataset-1K](https://github.com/eifuentes/lastfm-dataset-1K/tree/master): [preprocessing](https://github.com/eifuentes/lastfm-dataset-1K/blob/master/preprocessing.ipynb) - только исполнители и их песни с timestamp
- bidding: [https://github.com/wnzhang/make-ipinyou-data](https://github.com/wnzhang/make-ipinyou-data) - странные признаки
- SAS: https://psiaims.github.io/CAMIS/SAS/recurrent_events.html
- https://arxiv.org/html/2503.23050v1 + [GitHub](https://github.com/TheeChris/hospital_readmission?tab=readme-ov-file) (MIMIC)