# GROUP BY

*** Contare quanti iscritti ci sono stati ogni anno ***

> SELECT YEAR(`enrolment_date`) AS `year`, COUNT(`id`) AS `tot_enrolment_by_year`
> GROUP BY YEAR(`enrolment_date`)
> FROM `students`
> ORDER BY YEAR(`enrolment_date`) DESC;

Mostro le righe 0 -  3 (4 del totale, La query ha impiegato 0.0008 secondi.)

|year|tot_enrolment_by_year|
|:--:|:-------------------:|
|2021| 734	               |
|2020| 1645                |	
|2019| 1709                |	
|2018| 912	               |


*** Contare gli insegnanti che hanno l'ufficio nello stesso edificio ***

> SELECT `office_address`, COUNT(*) AS `tot_teachers`
> FROM `teachers`
> GROUP BY `office_address`;

Mostro le righe 0 - 24 (29 del totale, La query ha impiegato 0.0003 secondi.)

|office_address                      |tot_teacher|
|:----------------------------------:|:---------:|
| Borgo Demis 1                      |	1        |	
| Borgo Elga 89                      |	8        |	
| Borgo Elio 234 Piano 4             |	4        |	
| Borgo Ippolito 5 Piano 5           |	1        |	
| Borgo Martino 82 Appartamento 07   |	3        |	
| Contrada Amato 58 Piano 2          |	5        |	
| Contrada Penelope 73               |	4        |	
| Contrada Rita 5 Appartamento 71    |	3        |	
| Contrada Santoro 17 Appartamento 30|	3        |	
| Incrocio Marini 9                  |	3        |	
| Incrocio Testa 142 Piano 7         |	2        |	
| Piazza Aroldo 8 Appartamento 85    |	1        |	
| Piazza Demian 856 Appartamento 63  |	3        |	
| Piazza Ferretti 619                |	3        |	
| Piazza Pellegrino 613 Piano 8      |	2        |	
| Rotonda Carmela 10 Piano 1         |	6        |	
| otonda Martinelli 309              |	9        |	
| Rotonda Teseo 9                    |	2        |	
| Strada Concetta 6                  |	3        |	
| Strada Kociss 997 Piano 8          |	5        |	
| Strada Lino 8                      |	1        |	
| Strada Lombardi 855                |	3        |	
| Strada Neri 577                    |	3        |	
| Strada Vitali 8 Piano 0            |	5        |	
| Via Elga 7 Piano 4                 |	1        |	


*** Calcolare la media dei voti di ogni appello d'esame ***

> SELECT `exam_id`,  AVG(`vote`) AS `average_vote` 
> FROM `exam_student` 
> GROUP BY `exam_id`;

Mostro le righe 0 - 24 (4078 del totale, La query ha impiegato 0.0001 secondi.)

|exam_id|average_vote|	
|:-----:|:----------:|
|1      |16.8824     |
|2      |16.4615     |
|3      |20.3333     |
|4      |27.0000     |
|6      |17.5000     |
|7      |19.6000     |
|8      |6.5000      |
|9      |12.0000     |
|11     |17.4324     |	
|12     |14.8889     |	
|13     |22.0000     |	
|16     |18.0526     |	
|17     |19.0000     |	
|18     |5.5000      |
|19     |22.0000     |	
|21     |16.6176     |	
|22     |15.0000     |	
|23     |12.7500     |	
|24     |12.0000     |	
|25     |3.0000      |
|26     |19.1667     |	
|27     |24.5000     |	
|31     |16.9583     |	
|32     |17.2500     |	
|36     |20.1818     |	


*** Contare quanti corsi di laurea ci sono per ogni dipartimento *** 

> SELECT `department_id`, COUNT(`name`) AS `tot_degrees` 
> FROM `degrees`
> GROUP BY `department_id`  
> ORDER BY `department_id` ASC;

Mostro le righe 0 - 11 (12 del totale, La query ha impiegato 0.0001 secondi.)

| department_id|tot_degrees|	
|:------------:|:---------:|
|1 	           |10         |	
|2	           |4	       |
|3	           |4	       |
|4	           |9	       |
|5	           |4	       |
|6	           |6	       |
|7	           |7          |
|8	           |8          |
|9	           |5          |
|10	           |8          | 
|11	           |3          |	
|12            |7          |        


# JOINS 
 <!-- Desclaimer: I know is best practice to use backticks for names of columns and tables hower from now I'm going to avoid them in order to be more faster in writing queries. -->

*** Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia ***

> SELECT degrees.name AS degree, students.surname AS surname, students.name AS name
> FROM students
> JOIN degrees ON students.degree_id
> WHERE degrees.name="Corso di laurea in Economia"
> ORDER BY surname, name;

Mostro le righe 0 - 24 (5000 totali, 0 nella query, La query ha impiegato 0.0047 secondi.) [surname: AMATO... - AMATO...]

|degree                     |surname|name     |
|:-------------------------:|:-----:|:-------:|
|Corso di Laurea in Economia|Amato  |Brigitta |
|Corso di Laurea in Economia|Amato  |Carlo	  |
|Corso di Laurea in Economia|Amato  |Carlo	  |
|Corso di Laurea in Economia|Amato  |Ciro	  |
|Corso di Laurea in Economia|Amato  |Danuta	  |
|Corso di Laurea in Economia|Amato  |Diamante |
|Corso di Laurea in Economia|Amato  |Diana	  |
|Corso di Laurea in Economia|Amato  |Domingo  |
|Corso di Laurea in Economia|Amato  |Egisto	  |
|Corso di Laurea in Economia|Amato  |Enrica	  |
|Corso di Laurea in Economia|Amato  |Enrica	  |
...


*** Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze ***

> SELECT departments.name AS department, degrees.name AS degree, degrees.level AS level
> FROM degrees
> JOIN departments ON degrees.department_id
> WHERE degrees.level = 'magistrale' AND departments.name = 'Dipartimento di Neuroscienze';

Mostro le righe 0 - 24 (38 del totale, La query ha impiegato 0.0001 secondi.)

|department                   |degree                                                 |
|:---------------------------:|:-----------------------------------------------------:|
|Dipartimento di Neuroscienze |Corso di Laurea Magistrale in Astronomia               |
|Dipartimento di Neuroscienze |Corso di Laurea Magistrale in Bioingegneria|           | 
|Dipartimento di Neuroscienze |Corso di Laurea Magistrale in Biologia evoluzionis...  |
|Dipartimento di Neuroscienze |Corso di Laurea Magistrale in Biologia marina          |
|Dipartimento di Neuroscienze |Corso di Laurea Magistrale in Biologia molecolare      |
|Dipartimento di Neuroscienze |Corso di Laurea Magistrale in Biologia sanitaria       |
|Dipartimento di Neuroscienze |Corso di Laurea Magistrale in Biotecnologie indust...  |
|Dipartimento di Neuroscienze |Corso di Laurea Magistrale in Business Administrat...  |
|Dipartimento di Neuroscienze |Corso di Laurea Magistrale in Chimica                  |
|Dipartimento di Neuroscienze |Corso di Laurea Magistrale in Chimica Industriale      |
...


*** Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44) ***

> SELECT courses.name AS "Courses of Dr. Fulvio Amato", courses.period
> FROM teachers 
> INNER JOIN course_teacher ON teachers.id = course_teacher.teacher_id 
> INNER JOIN courses ON course_teacher.course_id = courses.id WHERE teachers.id = 44;

Mostro le righe 0 - 10 (11 del totale, La query ha impiegato 0.0001 secondi.)

|Courses of Dr. Fulvio Amato|period     |
|:-------------------------:|:---------:|
|impedit et eaque	        |I semestre |	
|explicabo ab voluptas	    |I semestre |	
|ullam ullam dignissimo     |I semestre |	
|aut pariatur a	            |I semestre |	
|alias voluptatibus sed	    |II semestre|	
|facilis adipisci providen  |I semestre |	
|doloribus nemo iure        |I semestre |	
|et quasi enim	            |I semestre |	
|facilis pariatur qui	    |I semestre |	
|dolor repellat dignissimos |II semestre|	
|magni magni omnis	        |I semestre |	


*** Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome ***

> SELECT students.surname AS student_lastname, students.name AS student_name, degrees.name AS degree, departments.name, degrees.level, degrees.address, degrees.email, degrees.website
> FROM students
> JOIN degrees ON students.degree_id 
> JOIN departments ON degrees.department_id
> ORDER BY students.surname, students.name;

Mostro le righe 0 - 24 (4500000 del totale, La query ha impiegato 3.9158 secondi.)

| student_lastname | student_name | degree                                                 | name                     | level      | address                             | email                               | website                                    |
|:-----------------|:-------------|:-------------------------------------------------------|--------------------------|------------|:------------------------------------|:------------------------------------|:-------------------------------------------|
| Amato            | Brigitta     | Corso di Laurea in Biologia                            | Dipartimento di Biologia | triennale  | Contrada Galli 289 Piano 5          | biologia@uni.it                     | www.biologia.uni.it                        |
| Amato            | Brigitta     | Corso di Laurea in Biologia molecolare                 | Dipartimento di Biologia | triennale  | Incrocio Fabbri 3                   | biologia-molecolare@uni.it          | www.biologia-molecolare.uni.it             |
| Amato            | Brigitta     | Corso di Laurea in Biotecnologie                       | Dipartimento di Biologia | triennale  | Rotonda Sasha 74 Appartamento 36    | biotecnologie@uni.it                | www.biotecnologie.uni.it                   |
| Amato            | Brigitta     | Corso di Laurea in Scienze naturali                    | Dipartimento di Biologia | triennale  | Rotonda Ferri 4 Piano 2             | scienze-naturali@uni.it             | www.scienze-naturali.uni.it                |
| Amato            | Brigitta     | Corso di Laurea Magistrale in Biologia evoluzionistica | Dipartimento di Biologia | magistrale | Contrada Fiore 253                  | biologia-evoluzionistica@uni.it     | www.biologia-evoluzionistica.uni.it        |
| Amato            | Brigitta     | Corso di Laurea Magistrale in Biologia marina          | Dipartimento di Biologia | magistrale | Via Colombo 378 Piano 9             | biologia-marina@uni.it              | www.biologia-marina.uni.it                 |
| Amato            | Brigitta     | Corso di Laurea Magistrale in Biologia molecolare      | Dipartimento di Biologia | magistrale | Strada Armando 86 Piano 9           | biologia-molecolare@uni.it          | www.biologia-molecolare.uni.it             |
| Amato            | Brigitta     | Corso di Laurea Magistrale in Biologia sanitaria       | Dipartimento di Biologia | magistrale | Contrada Osvaldo 497 Piano 5        | biologia-sanitaria@uni.it           | www.biologia-sanitaria.uni.it              |
| Amato            | Brigitta     | Corso di Laurea Magistrale in Biotecnologie industriali| Dipartimento di Biologia | magistrale | Rotonda Tommaso 806 Appartamento 21 | biotecnologie-industriali@uni.it    | www.biotecnologie-industriali.uni.it       |
| Amato            | Brigitta     | Corso di Laurea Magistrale in Scienze della natura     | Dipartimento di Biologia | magistrale | Strada Negri 323                    | scienze-della-natura@uni.it         | www.scienze-della-natura.uni.it            |
| Amato            | Brigitta     | Corso di Laurea in Astronomia                          | Dipartimento di Biologia | triennale  | Rotonda De Santis 61                | astronomia@uni.it                   | www.astronomia.uni.it                      |
| Amato            | Brigitta     | Corso di Laurea in Fisica                              | Dipartimento di Biologia | triennale  | Strada Rossi 7 Piano 3              | fisica@uni.it                       | www.fisica.uni.it                          |
| Amato            | Brigitta     | Corso di Laurea Magistrale in Astronomia               | Dipartimento di Biologia | magistrale | Via Samira 39                       | astronomia@uni.it                   | www.astronomia.uni.it                      |
| Amato            | Brigitta     | Corso di Laurea Magistrale in Fisica                   | Dipartimento di Biologia | magistrale | Piazza Nathan 77 Piano 2            | fisica@uni.it                       | www.fisica.uni.it                          |
| Amato            | Brigitta     | Corso di Laurea in Ingegneria Civile                   | Dipartimento di Biologia | triennale  | Rotonda Felicia 485 Piano 1         | ingegneria-civile@



