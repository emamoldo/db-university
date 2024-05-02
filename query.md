1. Selezionare tutti gli studenti nati nel 1990 (160):
    SELECT * FROM `students` WHERE date_of_birth BETWEEN '1990-01-01' AND '1990-12-31';

2. Selezionare tutti i corsi che valgono più di 10 crediti (479):
    SELECT * FROM `courses` WHERE cfu > '10';


3. Selezionare tutti gli studenti che hanno più di 30 anni
    SELECT * FROM `students` WHERE date_of_birth > '1993-12-31';

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea 
(286)
    SELECT * FROM `courses` WHERE period = 'I semestre' AND year = '1';

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)
    SELECT * FROM `exams` WHERE date = '2020-06-20' AND hour > '14:00';


6. Selezionare tutti i corsi di laurea magistrale (38)
    SELECT * FROM `degrees` WHERE level = 'magistrale';

7. Da quanti dipartimenti è composta l'università? (12)
    SELECT * FROM `departments` name;

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
    SELECT * FROM `teachers` WHERE phone IS NULL;




## Group by:

1. Contare quanti iscritti ci sono stati ogni anno
    SELECT COUNT(id) FROM `students` WHERE `enrolment_date` GROUP BY `enrolment_date`;

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
    SELECT COUNT(id), office_address FROM `teachers` GROUP BY `office_address`;

3. Calcolare la media dei voti di ogni appello d'esame
    SELECT COUNT(vote) FROM `exam_student` WHERE `vote` GROUP BY `vote`; --> need to check

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
    SELECT COUNT(id) FROM `departments` GROUP BY `name`;