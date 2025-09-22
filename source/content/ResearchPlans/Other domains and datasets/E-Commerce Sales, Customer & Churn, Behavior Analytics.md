##### 1) Открытые датасеты

1. **Online Retail / Online Retail II (UCI)** — транзакционный датасет UK-ритейлера (SKU, customer id, дата/время). Объём > млн строк.
   Задачи: time-to-next-purchase, time-to-churn, когортный LTV. ([archive.ics.uci.edu](https://archive.ics.uci.edu/ml/datasets/online%2Bretail%2BII "Online Retail II - UCI Machine Learning Repository"))
    
2. **Instacart Market Basket Analysis** — данные покупок/корзин ~3M заказов, >200k пользователей; содержит последовательности заказов по пользователям, интервалы между заказами.
   Задачи: time-to-next-purchase и рекуррентные события. ([Kaggle](https://www.kaggle.com/datasets/psparks/instacart-market-basket-analysis "Instacart Market Basket Analysis - Kaggle"))
    
3. **Retailrocket (events + item properties)** — clickstream / события (view/add_to_cart/purchase) и метаданные товаров.
   Задачи: Behavior Analytics (hazard событий покупки/оттока). ([Kaggle](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset "Retailrocket recommender system dataset - Kaggle"))
    
4. **Criteo click / ad logs (большие наборы)** — логи показа/кликов (1TB релиз).
   Задачи: time-to-click, time-to-converse, эффект рекламы на churn/retention. ([Criteo AI Lab](https://ailab.criteo.com/download-criteo-1tb-click-logs-dataset/"))
    
5. REES46 / E-commerce churn datasets 
   Baseline для выравнивания survival-подходов (иногда уже включены бизнес-метки churn). ([Kaggle](https://www.kaggle.com/datasets/fridrichmrtn/e-commerce-churn-dataset-rees46 "E-commerce churn dataset - REES46 - Kaggle"))
    
6. **Amazon Reviews / Product metadata** — большие исторические ревью/покупки; 
   Задачи: time-to-next-purchase, «старение» товара. (используются в рекомендациях). ([GitHub](https://github.com/caserec/Datasets-for-Recommender-Systems "Public Datasets For Recommender Systems - GitHub"))
    
7. **Shopify / public order APIs & sample datasets**
	Задачи: генерация realistic order streams (API / demo datasets для order/payment attempts). Если нужно больше структурированных order-потоков. ([Shopify](https://shopify.dev/docs/api/shopifyql/datasets))
    
#### 2) Постановки задач:

- **Time-to-churn** (время от последней покупки/сессии до «оттока» — нужно задать правило оттока, напр. 90/180 дней без покупок?).
- **Time-to-next-purchase / inter-purchase time** — классическая задача CLV/retention. Instacart.
- **Recurrent events** — многократные покупки по одному пользователю (для продвинутых моделей с многократными рисками).
- **Competing risks** — например, событие «перешёл к конкуренту» vs «удалил приложение» vs «снижение активации» (нужны proxy-метки).
- **Time-to-conversion (from view to purchase)** — из clickstream данных (Retailrocket, Criteo).

#### 3) Идеи исследований

1. Survival с **временными и последовательными ковариатами** (clickstream → hazard)
	- Актуальность: большинство работ смотрят только агрегированные фичи (recency/frequency/monetary), а не полную последовательность событий (можно использовать Retailrocket / Instacart).
	- Построить **RNN/Transformer-survival**: сэмпл — последовательность сессий/событий пользователя; цель — прогноз распределения времени до след. покупки.
	- Сравнить: Cox с time-varying covariates vs DeepSurv/DeepHit vs RNN-based survival (например, RNN-Survival, DeepHit). 
2. Recurrent event survival (анализ повторных покупок)
	- Модель: многокомпонентная модель с учётом уязвимости клиентов (frailty), моделирующая интервалы между покупками и их зависимости.
	- Применение: персонализированные частоты рассылок/акций. Интересно на Instacart/OnlineRetail.
3. **Competing-risks** в e-commerce (churn vs. migration/неактивность)
	- Формализовать разные типы «выхода» (непокупка, жалобы, возвраты) и применить Fine-Gray/competing risks neural models.
	- Практика: для маркетинга — разные стратегии в зависимости от причины ухода.
4. **Causal survival analysis** для маркетинговых акций
	- Оценить влияние кампаний (A/B, купоны) на «время до оттока» — использовать Marginal Structural Models, IPTW в survival setting или g-formula; моделировать time-varying treatment.
	- Интерес: как долго держит клиента скидка и есть ли «переносный» эффект после завершения акции.
5. **Time-aware recommender systems (survival loss)**
	- Вместо стандартной классификации предсказывать hazard того, что пользователь купит товар в следующий период — использовать survival loss (DeepHit) при обучении рекомендатора.
	- Novelty: объединение ranking + survival (ранжировать по ожидаемому времени до покупки).
6. **Interval-censoring / partial observation** (реалистичная проблема)
	- Многие данные имеют только агрегированные даты (например, сессии, а точный момент churn неизвестен). Применить models for interval-censored data (parametric or nonparametric). Это часто упускают.
7. **Transfer learning / domain adaptation**: перенос survival моделей между платформами/странами:
	- Обучать на крупном датасете (Criteo/Instacart) и адаптировать на малых локальных данных (например, локальный Shopify store). Исследовать устойчивость hazard-оценок.
8. Survival explainability / counterfactual hazard explanations
	- Построить интерпретируемые объяснения «почему время до churn увеличилось/уменьшилось»: SHAP-похожая интерпретация для time-dependent survival. Практическая ценность — action-ability для маркетинга.