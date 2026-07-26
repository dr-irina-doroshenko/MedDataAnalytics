# MedDataAnalytics

Automated non-parametric statistical analysis pipeline for medical data.  
Автоматизированный статистический анализ непараметрических медицинских данных

1. **Descriptive statistics / Описательная статистика** for the whole dataset and by target groups / по всей базе и по группам целевой переменной:
   - *Continuous / Количественные:* mean (M), standard deviation (SD), median (Me), quartiles (Q1–Q3), min–max
   - *Categorical / Категориальные:* absolute frequency (n), relative frequency (%), 95% confidence interval for proportions (95% CI / ДИ)

2. **Correlation analysis / Корреляционный анализ** (whole dataset / по всей базе):
   - Spearman's rank correlation (ρ) — for quantitative and ordinal variables / для количественных и ранговых переменных
   - Kendall's rank correlation (τ) — for ordinal variables / для ранговых переменных

3. **Multiple group comparisons / Множественное сравнение групп** (by target variable / по целевой переменной):
   - Kruskal–Wallis H-test / Краскала–Уоллиса (H) — for continuous variables across ≥2 groups / для количественных переменных между ≥2 группами
   - Chi-squared test / Хи-квадрат (χ²) — for categorical variables / для категориальных переменных
   - Fisher's exact test / Точный тест Фишера — automatically applied if >20% of cells have expected frequency <5 or minimum expected frequency <1 / автоматически, если >20% ячеек с ожидаемой частотой <5 или минимальная ожидаемая частота <1
   - Cramér's V / V Крамера — effect size for χ² / сила связи для χ²

4. **Pairwise comparisons / Попарные сравнения:**
   - Mann–Whitney U-test / U-критерий Манна–Уитни — for continuous variables between 2 groups / для количественных переменных между 2 группами
   - Fisher's exact test / Chi-squared / Точный тест Фишера / Хи-квадрат — for categorical variables / для категориальных переменных

5. **Data preprocessing / Предобработка данных:**
   - Missing values imputed with median (continuous) or "no data" string (categorical) / Заполнение пропусков медианой (количественные) или строкой «нет данных» (категориальные)
   - Only statistically significant results (p < 0.05) are reported / В отчёте выводятся только статистически значимые результаты (p < 0.05)


## Installation / Установка
pip install -r requirements.txt

## Usage / Запуск
# 1 загружаем excel в папку data/ place your Excel file into the data/ folder / 
# 2 меняем "Headache_Sample_DB.xlsx" в INPUT_FILE на имя своего файла / update INPUT_PATH in stat.py to match your filename
# 3 запускаем / run python stat.py
# 4 отчет сохраняется в папке / the report will be saved to output/