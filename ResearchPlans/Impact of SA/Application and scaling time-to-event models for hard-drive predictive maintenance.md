План:

1. Введение. Различные постановки задачи, сравнение классических подходов и SA.
   Задача: возможность переноса моделей, обученных на данных разных систем.
1. Методы: дерево выживаемости
1. Наборы: Backblaze (B) и Alibaba (A)
1. Эксперименты: качество Backblaze на Alibaba, наоборот и смеси (пропорции). Метрики
1. Обсуждение: лучшие признаки, интерпретация.

Постановка экспериментов:

1. Сбор backblaze, alibaba
1. Анализ характеристик событий, распределений времени.
1. Выделение из каждого набора тестового набора дисков со стратификацией.
1. Обучение на train, применение к разным test
1. Исследование обучения на смеси

Промежуточные выводы (обучение -> подбор гиперпараметров):

1. A -> A
   Best param A: {'criterion': 'tarone-ware', 'cut': False, 'depth': 8, 'leaf_model': 'base_zero_after', 'min_samples_leaf': 0.005}
   **A**
   IBS: 0.05238
   AUPRC: 0.95108
   IAUC: 0.66186
   **B**
   IBS: 0.30632
   AUPRC: 0.76528
   IAUC: 0.34296
1. A -> B
   Best param B: {'criterion': 'tarone-ware', 'cut': False, 'depth': 8, 'leaf_model': 'base', 'min_samples_leaf': 0.001}
   **A**
   IBS: 0.05129
   AUPRC: 0.94919
   IAUC: 0.67916
   **B**
   IBS: 0.27307
   AUPRC: 0.74131
   IAUC: 0.25476
1. B -> A
   Best param A: {'criterion': 'logrank', 'cut': False, 'depth': 12, 'leaf_model': 'base_zero_after', 'min_samples_leaf': 0.01}
   **A**
   IBS: 0.11061
   AUPRC: 0.87802
   IAUC: 0.32786
   **B**
   IBS: 0.07965
   AUPRC: 0.91866
   IAUC: 0.85943
1. B -> B
   Best param B: {'criterion': 'tarone-ware', 'cut': False, 'depth': 12, 'leaf_model': 'base_zero_after', 'min_samples_leaf': 0.005}
   **A**
   IBS: 0.09321
   AUPRC: 0.90101
   IAUC: 0.43512
   **B**
   IBS: 0.07935
   AUPRC: 0.91914
   IAUC: 0.79691
1. A+B -> A
   Best param A: {'criterion': 'logrank', 'cut': False, 'depth': 12, 'leaf_model': 'base_zero_after', 'min_samples_leaf': 0.001}
   **A**
   IBS: 0.05313
   AUPRC: 0.95075
   IAUC: 0.67883
   **B**
   IBS: 0.07891
   AUPRC: 0.92016
   IAUC: 0.86210
1. A+B -> B
   Best param B: {'criterion': 'tarone-ware', 'cut': False, 'depth': 12, 'leaf_model': 'base_zero_after', 'min_samples_leaf': 0.0005}
   **A**
   IBS: 0.05316
   AUPRC: 0.95324
   IAUC: 0.64785
   **B**
   IBS: 0.08742
   AUPRC: 0.91603
   IAUC: 0.80014
