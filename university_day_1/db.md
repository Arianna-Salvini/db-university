# DB_NAME: university

## Table name: departments
- id | INDEX | PK | NN | AI | UNIQUE | BIGINT
- name | VARCHAR(150) | NN
- address | VARCHAR(100) | N 
  
###### Table name: degree 
- id | INDEX | PK | NN | AI | UNIQUE | BIGINT
- title | VARCHAR(255) | NN
- department_id | NN | FK
- length | VARCHAR(15) | N

##### Table name: courses
- id | INDEX | PK | NN | AI | UNIQUE | BIGINT
- title | VARCHAR(150) | NN
- degree_id | FK | 
- hours | TINYINT | N
- start_date | DATE | N
- end_date | DATE | N
- teacher_id | FK

#### Table name: teachers
- id | INDEX | PK | NN | AI | UNIQUE | BIGINT
- name | VARCHAR(100) | NN
- lastname | VARCHAR(100) | NN
- email | VARCHAR(255) | N

### Table name: appeals
- id | INDEX | PK | NN | AI | UNIQUE | BIGINT
- date | DATETIME | NN
- course_id | FK 

# Table name: students
- id | INDEX | PK | NN | AI | UNIQUE | BIGINT
- name | VARCHAR(100) | NN
- lastname | VARCHAR(100) | NN
- birth_date | DATE | NN 
- email | VARCHAR(255) | N
- student_register_number | VARCHAR(6) | NN 
- degree_id | FK  

## Table name: appeals-registration
- id | INDEX | PK | NN | AI | UNIQUE | BIGINT
- student_id | FK 
- appeal_id | FK 
- vote | TINYINT | N



