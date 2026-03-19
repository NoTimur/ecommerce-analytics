# E-Commerce A/B Test & Analytics
### О проекте:
Комплексный аналитический проект основанный на [eCommerce данных](https://www.kaggle.com/datasets/mkechinov/ecommerce-behavior-data-from-multi-category-store/data) за 2 месяца включающий 285 млн. юзеров.
В рамках проекта была создана локальная аналитическая система DWH + BI и проведен A/B тест для тестирования продуктовой гипотезы.
### Стек:
<div align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas"/>
  <img src="https://img.shields.io/badge/Statsmodels-EE4C2C?style=for-the-badge&logo=python&logoColor=white" alt="Statsmodels"/>
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter"/>
  <img src="https://img.shields.io/badge/ClickHouse-FFCC01?style=for-the-badge&logo=clickhouse&logoColor=black" alt="ClickHouse"/>
  <img src="https://img.shields.io/badge/Apache_Superset-00A699?style=for-the-badge&logo=apache&logoColor=white" alt="Superset"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker"/>
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="SQL"/>
</div>

---

### Результаты A/B тестирования
В тесте приняло участие 1.88M уникальных пользователей.

| Метрика | Группа A (Control) | Группа B (Test) | Uplift | Стат. значимость (p-value) |
| :--- | :--- | :--- | :--- | :--- |
| Conversion Rate (CR) | 5.39% | 7.87% | +20.41% | < 0.05 (Z-test) |

Продуктовый вывод: Внедрение кнопки статистически значимый прирост конверсии. Анализ в разрезе брендов показал, что эффект стабилен на топ-10 брендов (Apple, Samsung, Xiaomi и т.п). **Рекомендация: раскатить фичу на 100% пользователей.**

---

### Дашборды (Apache Superset)
### 1. Результаты A/B теста
![A/B Test Dashboard](images/ab_res.png)

### 2. Аналитический обзор маркетплейса
![Marketplace Overview](images/anal1.png)
![Marketplace Overview2](images/anal2.png)


### Архитектура данных
1. ETL-процесс: Сырые логи обрабатываются чанками с помощью pandas, очищаются от пустых значений и приводятся типы.
2. Сплитование: Пользователи разделены на группы А и B (50/50).
3. Хранилище: Обработанные датафреймы загружаются в колоночную СУБД **ClickHouse**.
4. Визуализация: ClickHouse подключен к **Apache Superset**, где написаны SQL-запросы для создания витрин и дашбордов.
