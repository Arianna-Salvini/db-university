***Selezionare tutti gli studenti nati nel 1990 (160)***

> SELECT * FROM students WHERE year(date_of_birth) = 1990;  -> Mostro le righe 0 - 159 (160 del totale)
> SELECT * FROM students WHERE date_of_birth BETWEEN '1990-01-01' AND '1990-12-31'; -> Mostro le righe 0 - 159 (160 del totale)
> SELECT * FROM students WHERE EXTRACT(YEAR FROM date_of_birth) = 1990; -> Mostro le righe 0 - 159 (160 del totale)
> SELECT * FROM students WHERE date_of_birth LIKE '1990-%-%'; -> Mostro le righe 0 - 159 (160 del totale)
