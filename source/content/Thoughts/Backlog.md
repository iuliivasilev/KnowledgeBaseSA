1. Log-rank с конкурирующими событиями
2. Модели с повторяющимися событиями
3. Детектирование мультимодальности
4. Мульти-доменность моделей (Hardware, CRM, Medicine)
5. Beran estimator: https://ieeexplore.ieee.org/abstract/document/10858699
6. Генерация событий (SMOTE): может работать как виртуальные события в деревьях (схожее признаковое пространство в листах)
7. Получение эмбеддинга из TV и построение Time-Invariant моделей
8. Модификация CoxPH/AFT с базовой функцией на виртуальных событиях
9. Построение моделей, устойчивых к дисбалансу (есть наработки)
10. Федеративное обучение (CMC, медицинские данные пациентов)
11. Сравнение OneClass/Binary и SA при анализе логов (фиксируем окно до события длины h и прогнозируем оценку события SA как $P(failure~in~[t,~t+h]) = 1 - S(t+h) / S(t)$). Исследование при разных h?
    Метрики: AUC, IBS (сортировать изначальные наблюдения по аномальности, брать KM по ближайшим 20: 10 с двух сторон от оценки аномальности)?
12. Разработка настоящих метрик качества: перенос digital-метрик на другие области?

ПО:
1. Разработка приложения для визуализации деградации оборудования в реальном времени. За основу можно посмотреть Flutter (относительно новая библиотека, на ней написан [PathScribe](https://www.pathscribe.ru/news/icbsp-2023/)). Пишется один код для desktop/web/mobile приложений и всё легко масштабируется. PathScribe работал со сверхбольшими изображениями.
   Примеры: Alibaba, Google Pay, Google Earth
2. Внедрение моделей Time-Varying/Competing Risks в survivors