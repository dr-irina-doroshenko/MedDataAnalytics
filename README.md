# MedDataAnalytics

Automated non-parametric statistical analysis pipeline for medical data / 
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
   - Optional steps (configured in code): missing values imputation with median (continuous) or «нет данных» string (categorical); creation of additional variables (e.g., age groups); data filtering (e.g., by age) / По необходимости (настраивается в коде): заполнение пропусков медианой (количественные) или строкой «нет данных» (категориальные), создание дополнительных переменных (пример — возрастная группа), фильтрация наблюдений (пример — по возрасту).

6. **Important / Важно**
   - Categorical variables must be selected manually by column index. Relative frequencies are calculated by default based on the number of filled cells per column, but can be switched to group size (e.g., only males) or total database size via the `expected_n` parameter /Категориальные переменные выбираются вручную по индексу столбца. Относительные величины по умолчанию рассчитываются от числа заполненных ячеек в столбце, но могут быть переключены на размер группы целевой переменной (например, только мужчины) или общее число пациентов в базе через параметр `expected_n`.

7. **Reporting / Формирование отчёта**
   - Only statistically significant results (p < 0.05) are included in the report / В отчёт выводятся только статистически значимые результаты (p < 0.05)
   - Output format: Microsoft Word (.docx) / Формат выходного файла: Microsoft Word (.docx)

## Installation / Установка

```bash
pip install -r requirements.txt
```