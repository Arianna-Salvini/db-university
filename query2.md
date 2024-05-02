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
> JOIN course_teacher ON teachers.id = course_teacher.teacher_id 
> JOIN courses ON course_teacher.course_id = courses.id 
> WHERE teachers.id = 44;

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
> JOIN degrees ON students.degree_id = degrees.id
> JOIN departments ON degrees.department_id = departments.id
> RDER BY students.surname, students.name;

Mostro le righe 0 - 24 (5000 del totale, La query ha impiegato 0.0111 secondi.)

student_lastname	student_name	degree	name	level	address	email	website	
Amato	Brigitta	Corso di Laurea Magistrale in Relazioni Internazio...	Dipartimento di Scienze politiche, giuridiche e st...	magistrale	Incrocio Milani 70 Appartamento 93	relazioni-internazionali-e-diplomazia@uni.it	www.relazioni-internazionali-e-diplomazia.uni.it	
Amato	Carlo	Corso di Laurea in Ingegneria per l'Ambiente e il ...	Dipartimento di Ingegneria civile, edile e ambient...	triennale	Borgo Nestore 88 Piano 7	ingegneria-per-lambiente-e-il-territorio@uni.it	www.ingegneria-per-lambiente-e-il-territorio.uni.i...	
Amato	Carlo	Corso di Laurea Magistrale in Informatica	Dipartimento di Matematica	magistrale	Incrocio Eustachio 253 Appartamento 90	informatica@uni.it	www.informatica.uni.it	
Amato	Ciro	Corso di Laurea in Fisioterapia	Dipartimento di Neuroscienze	triennale	Strada Parisi 5	fisioterapia@uni.it	www.fisioterapia.uni.it	
Amato	Danuta	Corso di Laurea Magistrale in Lingue Moderne per l...	Dipartimento di Studi linguistici e letterari	magistrale	Incrocio Donatella 72 Appartamento 53	lingue-moderne-per-la-comunicazione-e-la-cooperazi...	www.lingue-moderne-per-la-comunicazione-e-la-coope...	
Amato	Diamante	Corso di Laurea Magistrale in Cybersecurity	Dipartimento di Ingegneria dell'informazione	magistrale	Piazza Quasimodo 14	cybersecurity@uni.it	www.cybersecurity.uni.it	
Amato	Diana	Corso di Laurea Magistrale in Chimica	Dipartimento di Scienze chimiche	magistrale	Strada Soriana 951	chimica@uni.it	www.chimica.uni.it	
Amato	Domingo	Corso di Laurea Magistrale in Ingegneria dell'Auto...	Dipartimento di Ingegneria dell'informazione	magistrale	Strada Ippolito 684	ingegneria-dellautomazione@uni.it	www.ingegneria-dellautomazione.uni.it	
Amato	Egisto	Corso di Laurea in Fisioterapia	Dipartimento di Neuroscienze	triennale	Strada Parisi 5	fisioterapia@uni.it	www.fisioterapia.uni.it	
Amato	Enrica	Corso di Laurea in Biologia	Dipartimento di Biologia	triennale	Contrada Galli 289 Piano 5	biologia@uni.it	www.biologia.uni.it	
Amato	Enrica	Corso di Laurea in Lettere	Dipartimento di Studi linguistici e letterari	triennale	Rotonda Moretti 6	lettere@uni.it	www.lettere.uni.it	
Amato	Felicia	Corso di Laurea Magistrale in European and Global ...	Dipartimento di Scienze politiche, giuridiche e st...	magistrale	Incrocio Orlando 731	european-and-global-studies@uni.it	www.european-and-global-studies.uni.it	
Amato	Fiorenzo	Corso di Laurea in Infermieristica	Dipartimento di Medicina	triennale	Incrocio Gentile 507 Appartamento 78	infermieristica@uni.it	www.infermieristica.uni.it	
Amato	Genziana	Corso di Laurea Magistrale in Astronomia	Dipartimento di Fisica e astronomia	magistrale	Via Samira 39	astronomia@uni.it	www.astronomia.uni.it	
Amato	Germano	Corso di Laurea Magistrale in Cybersecurity	Dipartimento di Ingegneria dell'informazione	magistrale	Piazza Quasimodo 14	cybersecurity@uni.it	www.cybersecurity.uni.it	
Amato	Giacinto	Corso di Laurea in Ingegneria per l'Ambiente e il ...	Dipartimento di Ingegneria civile, edile e ambient...	triennale	Borgo Nestore 88 Piano 7	ingegneria-per-lambiente-e-il-territorio@uni.it	www.ingegneria-per-lambiente-e-il-territorio.uni.i...	
Amato	Grazia	Corso di Laurea in Biologia	Dipartimento di Biologia	triennale	Contrada Galli 289 Piano 5	biologia@uni.it	www.biologia.uni.it	
Amato	Iacopo	Corso di Laurea Magistrale in Economia e Diritto	Dipartimento di Scienze economiche e aziendali	magistrale	Incrocio Joseph 585 Piano 7	economia-e-diritto@uni.it	www.economia-e-diritto.uni.it	
Amato	Irene	Corso di Laurea Magistrale in Ingegneria Informati...	Dipartimento di Ingegneria dell'informazione	magistrale	Via Milani 9	ingegneria-informatica@uni.it	www.ingegneria-informatica.uni.it	
Amato	Joshua	Corso di Laurea in Biologia	Dipartimento di Biologia	triennale	Contrada Galli 289 Piano 5	biologia@uni.it	www.biologia.uni.it	
Amato	Joshua	Corso di Laurea Magistrale in Bioingegneria	Dipartimento di Ingegneria dell'informazione	magistrale	Contrada Sibilla 626	bioingegneria@uni.it	www.bioingegneria.uni.it	
Amato	Kociss	Corso di Laurea in Scienze naturali	Dipartimento di Biologia	triennale	Rotonda Ferri 4 Piano 2	scienze-naturali@uni.it	www.scienze-naturali.uni.it	
Amato	Loris	Corso di Laurea Magistrale in Scienze della natura	Dipartimento di Biologia	magistrale	Strada Negri 323	scienze-della-natura@uni.it	www.scienze-della-natura.uni.it	
Amato	Luigi	Corso di Laurea in Biologia molecolare	Dipartimento di Biologia	triennale	Incrocio Fabbri 3	biologia-molecolare@uni.it	www.biologia-molecolare.uni.it	
Amato	Manfredi	Corso di Laurea in Diritto dell'Economia	Dipartimento di Scienze politiche, giuridiche e st...	triennale	Strada Miriana 2 Appartamento 06	diritto-delleconomia@uni.it	www.diritto-delleconomia.uni.it	


*** Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti ***

> SELECT degrees.name AS degree, courses.name AS course, teachers.name AS teacher_name, teachers.surname AS teacher_lastname
> FROM degrees
> JOIN courses ON courses.degree_id = degrees.id
> JOIN course_teacher ON course_teacher.course_id=courses.id
> JOIN teachers ON course_teacher.teacher_id = teachers.id;

Mostro le righe 0 - 24 (1317 del totale, La query ha impiegato 0.0021 secondi.)

degree	course	teacher_name	teacher_lastname	
Corso di Laurea Magistrale in Biologia marina	corporis consequatur labore	Artemide	Rizzi	
Corso di Laurea in Ingegneria Civile	est ratione qui	Artemide	Rizzi	
Corso di Laurea in Logopedia	eligendi aut vel	Artemide	Rizzi	
Corso di Laurea Magistrale in Chimica	voluptatem fuga incidunt	Artemide	Rizzi	
Corso di Laurea in Economia	omnis culpa voluptatem	Artemide	Rizzi	
Corso di Laurea Magistrale in Innovazione e Serviz...	nobis vitae reprehenderit	Artemide	Rizzi	
Corso di Laurea Magistrale in Lingue Moderne per l...	saepe quod id	Artemide	Rizzi	
Corso di Laurea in Biologia molecolare	aut consequatur sit	Gianantonio	Battaglia	
Corso di Laurea in Ingegneria per l'Ambiente e il ...	laudantium sunt consequatur	Gianantonio	Battaglia	
Corso di Laurea in Ingegneria Elettronica	corrupti enim praesentium	Gianantonio	Battaglia	
Corso di Laurea Magistrale in Bioingegneria	architecto id cum	Gianantonio	Battaglia	
Corso di Laurea in Infermieristica	rerum reiciendis quam	Gianantonio	Battaglia	
Corso di Laurea in Tecniche di Laboratorio Biomedi...	eius animi atque	Gianantonio	Battaglia	
Corso di Laurea in Educazione Professionale	similique id non	Gianantonio	Battaglia	
Corso di Laurea in Fisioterapia	et in aspernatur	Gianantonio	Battaglia	
Corso di Laurea in Lettere	facilis magnam rem	Gianantonio	Battaglia	
Corso di Laurea in Ingegneria dell'Informazione	placeat mollitia atque	Erminia	Gatti	
Corso di Laurea in Ingegneria Elettronica	officia dolor a	Erminia	Gatti	
Corso di Laurea in Fisioterapia	officia nam pariatur	Erminia	Gatti	
Corso di Laurea in Tecniche di Neurofisiopatologia	illum est ea	Erminia	Gatti	
Corso di Laurea Magistrale in Odontoiatria e Prote...	qui corrupti itaque	Erminia	Gatti	
Corso di Laurea in Chimica Industriale	aut reprehenderit deleniti	Erminia	Gatti	
Corso di Laurea in Chimica Industriale	ea enim voluptatibus	Erminia	Gatti	
Corso di Laurea in Statistica per le Tecnologie e ...	dolores dolor voluptas	Erminia	Gatti	
Corso di Laurea in Lettere	ullam numquam perspiciatis	Erminia	Gatti	


*** Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54) ***

> SELECT DISTINCT departments.name, teachers.name AS teacher_name, teachers.surname AS teacher_lastname
> FROM teachers
> JOIN course_teacher ON course_teacher.teacher_id=teachers.id
> JOIN courses ON course_teacher.course_id = courses.id
> JOIN degrees ON courses.degree_id = degrees.id
> JOIN departments ON degrees.department_id = departments.id
> WHERE departments.name = "Dipartimento di Matematica"
> ORDER BY teachers.surname;

Mostro le righe 0 - 24 (54 del totale, La query ha impiegato 0.0003 secondi.)

name	teacher_name	teacher_lastname	
Dipartimento di Matematica	Loretta	Amato	
Dipartimento di Matematica	Fulvio	Amato	
Dipartimento di Matematica	Guendalina	Barbieri	
Dipartimento di Matematica	Diamante	Barone	
Dipartimento di Matematica	Kristel	Bellini	
Dipartimento di Matematica	Maika	Bellini	
Dipartimento di Matematica	Carmelo	Benedetti	
Dipartimento di Matematica	Concetta	Bianchi	
Dipartimento di Matematica	Elda	Bruno	
Dipartimento di Matematica	Penelope	Bruno	
Dipartimento di Matematica	Prisca	Caputo	
Dipartimento di Matematica	Cira	Caputo	
Dipartimento di Matematica	Valdo	Carbone	
Dipartimento di Matematica	Pablo	Caruso	
Dipartimento di Matematica	Cosetta	Costantini	
Dipartimento di Matematica	Tosca	Donati	
Dipartimento di Matematica	Sarita	Donati	
Dipartimento di Matematica	Maria	Esposito	
Dipartimento di Matematica	Gavino	Fabbri	
Dipartimento di Matematica	Bibiana	Farina	
Dipartimento di Matematica	Marvin	Ferrari	
Dipartimento di Matematica	Noemi	Ferraro	
Dipartimento di Matematica	Rudy	Fontana	
Dipartimento di Matematica	Piererminio	Greco	
Dipartimento di Matematica	Mariagiulia	Guerra	

