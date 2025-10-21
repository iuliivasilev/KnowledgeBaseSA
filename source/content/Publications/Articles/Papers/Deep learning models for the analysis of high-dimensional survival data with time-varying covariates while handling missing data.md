---
Title: Deep learning models for the analysis of high-dimensional survival data with time-varying covariates while handling missing data
Link: "[Link](https://link.springer.com/article/10.1007/s44163-025-00429-z)"
Year: 2025
Direction:
  - "[[Time Varying]]"
  - "[[DeepLearning]]"
Code:
Type: Research
Overview:
Datasets:
Metrics:
  - CITD
  - IBSTD
Reviewer: dvarfe
Source:
---
Статья не предлагает кардинально новых подходов, скорее занимается сравнением существующих подходов.
# Тема исследования
Исследование направлено на решение следующих проблем при прогнозировании времени до наступления события(инцидент ВИЧ):
1. **Высокая размерность данных:** Наличие большого количества признаков (48 цитокинов + 24 базовых переменных).
2. **Наличие изменяющихся во времени ковариат:** цитокиновые профили.
3. **Пропущенные данные:** Часть наблюдений содержит пропуски.
4. **Неспособность традиционных моделей** (например, регрессии Кокса) учитывать сложные нелинейные взаимодействия и динамические изменения признаков.
# Предложенное решение
1. Для решение проблемы высокой размерности предлагается использовать нейросетевые архитектуры, которые должны хорошо справляться с извлечением признаков из высокоразмерных данных. 
2. Для учёта изменяющихся во времени ковариат используется модель [[Dynamic-DeepHit: A Deep Learning Approach for Dynamic Survival Analysis with Competing Risks based on Longitudinal Data|Dynamic DeepHit]]. В ней используется RNN-блок, который позволяет обрабатывать последовательности, а также механизм внимания.
3. Для работы с пропусками используется MissForest, способ заполнения пропусков на основе RandomForest.
# Наборы данных  
Набор данных представляет собой  данные клинического исследования CAPRISA 004, включающие 812 ВИЧ-отрицательных женщин из Южной Африки, среди которых за 30 месяцев наблюдения было зафиксировано 96 случаев инфицирования. Данные содержат 24 статические базовые характеристики и 48 динамически измеряющихся во времени цитокиновых профиля.
 
# Экспериментальные исследования
 В качестве метрик используются Time-Dependent варианты CI и IBS.
 
<table>
  <thead>
    <tr>
      <th rowspan="2">Model</th>
      <th rowspan="2">Covariate</th>
      <th colspan="2">Before Imputation (N=139)</th>
      <th colspan="2">After Imputation (N=162)</th>
    </tr>
    <tr>
      <th>C<sup>td</sup>-index</th>
      <th>BS<sup>td</sup></th>
      <th>C<sup>td</sup>-index</th>
      <th>BS<sup>td</sup></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="2">DeepSurv</td>
      <td>Mean</td>
      <td>0.6175</td>
      <td>0.1318</td>
      <td>0.6870</td>
      <td>0.1141</td>
    </tr>
    <tr>
      <td>Difference</td>
      <td>0.6246</td>
      <td>0.1206</td>
      <td>0.7022</td>
      <td>0.1038</td>
    </tr>
    <tr>
      <td rowspan="2">DeepHit</td>
      <td>Mean</td>
      <td>0.6318</td>
      <td>0.1245</td>
      <td>0.6976</td>
      <td>0.1223</td>
    </tr>
    <tr>
      <td>Difference</td>
      <td>0.6714</td>
      <td>0.1101</td>
      <td>0.7135</td>
      <td>0.0979</td>
    </tr>
  </tbody>
</table>

<table>
  <caption>Table 2 — C-index — Before imputation (N=139)</caption>
  <thead>
    <tr>
      <th>Prediction \ Eval (months)</th>
      <th>Three</th><th>Six</th><th>Nine</th><th>Twelve</th><th>Fifteen</th>
    </tr>
  </thead>
  <tbody>
    <tr><th>Three</th><td>0.6851</td><td>0.6851</td><td>0.8326</td><td>0.5692</td><td>0.5692</td></tr>
    <tr><th>Six</th>  <td>0.6851</td><td>0.8316</td><td>0.5692</td><td>0.5736</td><td>0.6190</td></tr>
    <tr><th>Nine</th> <td>0.9764</td><td>0.7248</td><td>0.7248</td><td>0.7544</td><td>0.7544</td></tr>
    <tr><th>Twelve</th><td>0.7847</td><td>0.7843</td><td>0.8121</td><td>0.8121</td><td>0.8121</td></tr>
    <tr><th>Fifteen</th><td>0.7958</td><td>0.8173</td><td>0.8173</td><td>0.8173</td><td>0.8173</td></tr>
  </tbody>
</table>

<table>
  <caption>Table 2 — C-index — After imputation (N=162)</caption>
  <thead>
    <tr>
      <th>Prediction \ Eval (months)</th>
      <th>Three</th><th>Six</th><th>Nine</th><th>Twelve</th><th>Fifteen</th>
    </tr>
  </thead>
  <tbody>
    <tr><th>Three</th><td>0.8432</td><td>0.8213</td><td>0.8350</td><td>0.8098</td><td>0.7990</td></tr>
    <tr><th>Six</th>  <td>0.8331</td><td>0.8298</td><td>0.8000</td><td>0.7990</td><td>0.7990</td></tr>
    <tr><th>Nine</th> <td>0.8276</td><td>0.8001</td><td>0.7968</td><td>0.7968</td><td>0.7968</td></tr>
    <tr><th>Twelve</th><td>0.8501</td><td>0.8501</td><td>0.8501</td><td>0.8501</td><td>0.8501</td></tr>
    <tr><th>Fifteen</th><td>0.8551</td><td>0.8551</td><td>0.8551</td><td>0.8544</td><td>0.8544</td></tr>
  </tbody>
</table>

<table>
  <caption>Table 3 — Brier Score — Before imputation (N=139)</caption>
  <thead>
    <tr>
      <th>Prediction \ Eval (months)</th>
      <th>Three</th><th>Six</th><th>Nine</th><th>Twelve</th><th>Fifteen</th>
    </tr>
  </thead>
  <tbody>
    <tr><th>Three</th><td>0.0013</td><td>0.0032</td><td>0.0056</td><td>0.0135</td><td>0.0167</td></tr>
    <tr><th>Six</th>  <td>0.0016</td><td>0.0059</td><td>0.0124</td><td>0.0163</td><td>0.0376</td></tr>
    <tr><th>Nine</th> <td>0.0064</td><td>0.0109</td><td>0.0143</td><td>0.0259</td><td>0.0326</td></tr>
    <tr><th>Twelve</th><td>0.0111</td><td>0.0155</td><td>0.0255</td><td>0.0322</td><td>0.0410</td></tr>
    <tr><th>Fifteen</th><td>0.0189</td><td>0.0252</td><td>0.0317</td><td>0.0433</td><td>0.0415</td></tr>
  </tbody>
</table>

<table>
  <caption>Table 3 — Brier Score — After imputation (N=162)</caption>
  <thead>
    <tr>
      <th>Prediction \ Eval (months)</th>
      <th>Three</th><th>Six</th><th>Nine</th><th>Twelve</th><th>Fifteen</th>
    </tr>
  </thead>
  <tbody>
    <tr><th>Three</th><td>0.0081</td><td>0.0098</td><td>0.0171</td><td>0.0267</td><td>0.0523</td></tr>
    <tr><th>Six</th>  <td>0.0091</td><td>0.0165</td><td>0.0279</td><td>0.0467</td><td>0.0574</td></tr>
    <tr><th>Nine</th> <td>0.0148</td><td>0.0264</td><td>0.0419</td><td>0.0579</td><td>0.0693</td></tr>
    <tr><th>Twelve</th><td>0.0299</td><td>0.0427</td><td>0.0573</td><td>0.0682</td><td>0.0766</td></tr>
    <tr><th>Fifteen</th><td>0.0429</td><td>0.0569</td><td>0.0691</td><td>0.0751</td><td>0.0777</td></tr>
  </tbody>
</table>

Dynamic DeepHit показывает себя лучше, чем обычный DeepHit или DeepSurv. Заполнение пропусков положительно влияет на CI, но отрицательно сказывается на IBS.
# Выводы  
Учёт временно-зависимо ковариат и импутация пропусков положительно сказываются на ранжировании. При этом, заполнение пропусков может ухудшать качество прогнозирования.

# Примечания
