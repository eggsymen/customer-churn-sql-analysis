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

