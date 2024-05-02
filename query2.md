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

SELECT `exam_id`,  AVG(`vote`) AS `average_vote` 
FROM `exam_student` 
GROUP BY `exam_id`;

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
