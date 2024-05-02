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
    SELECT COUNT(id) FROM `departments` GROUP BY `name`; --> need to check


## Joins:

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
    SELECT `students`.`name` FROM `students` JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id` WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
    SELECT `degrees`.`name` FROM `degrees` JOIN `departments` ON `department_id` WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di Neuroscienze';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
    SELECT * FROM `teachers` JOIN `course_teacher` ON `teacher_id` WHERE `teacher_id` = 44; --> need to check

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
    SELECT `students`.`name`, `students`.`surname` FROM `students` JOIN `degrees` ON `degree_id` WHERE `degree_id` = `department_id` ORDER BY `name`, `surname` ASC;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti


6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)


7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.
