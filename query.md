*** Selezionare tutti gli studenti nati nel 1990 (160) ***
> SELECT * FROM students WHERE year(date_of_birth) = 1990;  -> Mostro le righe 0 - 159 (160 del totale)
> SELECT * FROM students WHERE date_of_birth BETWEEN '1990-01-01' AND '1990-12-31'; -> Mostro le righe 0 - 159 (160 del totale)
> SELECT * FROM students WHERE EXTRACT(YEAR FROM date_of_birth) = 1990; -> Mostro le righe 0 - 159 (160 del totale)
> SELECT * FROM students WHERE date_of_birth LIKE '1990-%-%'; -> Mostro le righe 0 - 159 (160 del totale)

*** Selezionare tutti i corsi che valgono più di 10 crediti (479) ***
> SELECT * FROM courses WHERE cfu > 10; -> Mostro le righe 0 - 478 (479 del totale)


*** Selezionare tutti gli studenti che hanno più di 30 anni ***
> SELECT * FROM students WHERE TIMESTAMPDIFF( YEAR, date_of_birth, CURDATE()) >= 30; -> Mostro le righe 0 - 24 (3702 del totale)

*** Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286) *** 

> SELECT * FROM courses WHERE period = 'I semestre' AND year = 1; -> Mostro le righe 0 - 24 (286 del totale)

*** Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21) ***
> SELECT * FROM exams WHERE date = '2020-06-20' AND TIME(hour) > '14:00:00'; -> Mostro le righe 0 - 20 (21 del totale)

*** Selezionare tutti i corsi di laurea magistrale (38) ***
> SELECT * FROM degrees WHERE level = 'magistrale'; ->  Mostro le righe 0 - 37 (38 del totale)

*** Da quanti dipartimenti è composta l'università? (12) ***
> SELECT COUNT(*) as tot_departments FROM departments; -> 

| tot_departments |
|:-------------:|
|12             |

*** Quanti sono gli insegnanti che non hanno un numero di telefono? (50) ***
> SELECT COUNT(*) AS teachers_no_number FRom teachers WHERE phone IS null; 

| teachers_no_number |
|:------------------:|
|50                  |