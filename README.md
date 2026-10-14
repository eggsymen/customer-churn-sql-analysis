CREATE TABLE bank_churn (
    rownumber INT PRIMARY KEY,
    customerid INT,
    surname VARCHAR(100),
    creditscore INT,
    geography VARCHAR(100),
    gender VARCHAR(50),
    age INT,
    tenure INT,
    balance NUMERIC,
    numofproducts INT,
    hascrcard INT,
    isactivemember INT,
    estimatedsalary NUMERIC,
    exited INT
);
SELECT 
    ROUND(COUNT(CASE WHEN exited = 1 THEN 1 END) * 100.0 / COUNT(*), 2) AS churn_rate_percent
FROM bank_churn;

SELECT 
    ROUND(COUNT(CASE WHEN exited = 1 THEN 1 END) * 100.0 / COUNT(*), 2) AS churn_rate_percent 
FROM bank_churn;

SELECT 
    geography, 
    COUNT(*) AS total_customers,
    COUNT(CASE WHEN exited = 1 THEN 1 END) AS churned_customers,
    ROUND(COUNT(CASE WHEN exited = 1 THEN 1 END) * 100.0 / COUNT(*), 2) AS churn_rate_percent
FROM bank_churn
GROUP BY geography
ORDER BY churn_rate_percent DESC;

SELECT 
    gender, 
    ROUND(COUNT(CASE WHEN exited = 1 THEN 1 END) * 100.0 / COUNT(*), 2) AS churn_rate_percent
FROM bank_churn
GROUP BY gender;

На основе выполненных SQL-запросов были получены следующие важные инсайты о поведении клиентов банка:
1.Общий уровень оттока клиентов
Составляет (20.38%). Это означает, что банк теряет каждого пятого клиента, что указывает на острую необходимость внедрения CRM-стратегий по удержанию пользователей.
2.Географические особенности оттока:
Германия является самым проблемным регионом с критическим уровнем оттока — 32.44% (ушел 814 из 2509 клиентов).
Испания-демонстрирует уровень оттока в 16.67%.
Франция-имеет самый низкий и стабильный показатель — 16.17%, несмотря на то, что это самый крупный рынок по общему числу клиентов (5014 человек).
Вывод:Руководству необходимо провести локальный аудит работы филиалов в Германии, чтобы выявить локальные причины недовольства клиентов (например, тарифы или качество сервиса).
3.Гендерные различия пользователей:
Женщины уходят из банка значительно чаще — уровень оттока среди(Female составляет 25.07%), в то время как среди (Male этот показатель равен всего 16.47%).
Вывод:Маркетинговым кампаниям и продуктовым предложениям банка стоит уделить больше внимания женской аудитории и адаптировать под них программы лояльности.

