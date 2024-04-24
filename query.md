*** Selezionare tutti gli studenti nati nel 1990 (160) ***
> SELECT * FROM students WHERE year(date_of_birth) = 1990;  -> Mostro le righe 0 - 159 (160 del totale)
> SELECT * FROM students WHERE date_of_birth BETWEEN '1990-01-01' AND '1990-12-31'; -> Mostro le righe 0 - 159 (160 del totale)
> SELECT * FROM students WHERE EXTRACT(YEAR FROM date_of_birth) = 1990; -> Mostro le righe 0 - 159 (160 del totale)
> SELECT * FROM students WHERE date_of_birth LIKE '1990-%-%'; -> Mostro le righe 0 - 159 (160 del totale)

*** Selezionare tutti i corsi che valgono più di 10 crediti (479) ***
> SELECT * FROM courses WHERE cfu > 10; -> Mostro le righe 0 - 478 (479 del totale)


*** Selezionare tutti gli studenti che hanno più di 30 anni ***
> SELECT * FROM students WHERE TIMESTAMPDIFF( YEAR, date_of_birth, CURDATE()) > 30; -> Mostro le righe 0 - 24 (3541 del totale)

*** Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286) *** 

> SELECT * FROM courses WHERE period = 'I semestre' AND year = 1; -> Mostro le righe 0 - 24 (286 del totale)

