
### The count function
    SELECT COUNT(NAME)
    FROM CITY 
    WHERE POPULATION > 100000
    ;

### The sum function

    SELECT SUM(POPULATION)
    FROM CITY 
    WHERE DISTRICT ='California'
    ;

### Averages

    SELECT AVERAGE(POPULATION) 
    FROM CITY 
    WHERE DISTRICT ='California'
    ;

### Averages population

    SELECT ROUND(AVG(POPULATION),1)
    FROM CITY
    ;

### Japan population

    SELECT SUM(POPULATION)
    FROM CITY 
    WHERE COUNTRYCODE ='JPN'
    ;

### Population density difference

    SELECT MAX(POPULATION) - MIN(POPULATION)
    FROM CITY 
    ;

### Top earners

    SELECT MAX(MONTHS * SALARY)
        , COUNT(MONTHS * SALARY) 
    FROM EMPLOYEE 
    WHERE (MONTHS * SALARY) = (SELECT MAX(MONTHS * SALARY) FROM EMPLOYEE)
    ;
### The blunder

    SELECT CEIL(AVG(SALARY) - AVG(TO_NUMBER(REPLACE(TO_CHAR(SALARY),'0')))) 
    FROM EMPLOYEES
    ;

### Weather observation station 2

    SELECT ROUND(SUM(LAT_N),2)
        , ROUND(SUM(LONG_W),2)
    FROM STATION
    ;

### Weather observation station 13

    SELECT ROUND(SUM(LAT_N),4)
    FROM STATION
    WHERE 38.7880 < LAT_N AND LAT_N <137.2345
    ;

### Weather observation station 14

    SELECT ROUND(MAX(LAT_N),4)
    FROM STATION 
    WHERE LAT_N < 137.2345
    ;

### Weather observation station 15

    SELECT ROUND(MAX(LONG_W),4)
    FROM STATION 
    WHERE LAT_N =
        (SELECT (MAX(LAT_N))
        FROM STATION
        WHERE LAT_N <137.2345)
    ;
### Weather observation station 16

    SELECT ROUND((LAT_N),4)
    FROM STATION 
    WHERE LAT_N = 
        (SELECT MIN(LAT_N)
        FROM STATION
        WHERE LAT_N > 38.7780)
    ;
### Weather observation station 17

    SELECT ROUND((LONG_W),4)
    FROM STATION 
    WHERE LAT_N = 
        (SELECT MIN(LAT_N)
        FROM STATION
        WHERE LAT_N > 38.7780)
    ;

### Weather observation station 18

    SELECT ROUND((MAX(LAT_N) - MIN(LAT_N) + MAX(LONG_W) - MIN(LONG_W)), 4) 
    FROM STATION
    ;

### Weather observation station 19

    SELECT ROUND(SQRT (POWER(MAX(LAT_N)-MIN(LAT_N),2)+POWER(MAX(LONG_W)-MIN(LONG_W),2)),4)
    FROM STATION
    ;

### Weather observation station 20

    SELECT ROUND(MEDIAN(LAT_N), 4)
    FROM STATION
    ;

