1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students`.`name`, `students`.`surname`, `students`.`degree_id`, `degrees`.`name`
FROM `students` 
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` 
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';




2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT `degrees`.`department_id`,`degrees`.`level`,`degrees`.`name`, `departments`.`name`
FROM `degrees`
JOIN `departments` ON `departments`.`id`
AND `departments`.`name` = 'Dipartimento di Neuroscienze'
WHERE LEVEL = 'magistrale';


3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT *
FROM `course_teacher` 
JOIN `teachers` ON `id` = `course_teacher`.`teacher_id` 
WHERE `course_teacher`.`teacher_id` = '44';


4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il
relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT `students`.`surname` AS cognome_studente,`students`.`name`AS nome_studente, `degrees`.`id`, `degrees`.`department_id`,`degrees`.`name`

FROM`students`
JOIN `degrees` ON `degree_id` = `students`.`degree_id`
ORDER BY cognome_studente,nome_studente


5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT `degrees`.`name` as `degree_name`, `courses`.`name` as `course_name`, `teachers`.`name` as `teacher_name`, `teachers`.`surname` as `teacher_surname`

FROM `course_teacher` 

JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` 

JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`

JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id` ORDER BY `degree_name`;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT DISTINCT `teachers`.`name` as `teacher_name`, `teachers`.`surname` as `teacher_surname`, `departments`.`name`

FROM `course_teacher` 

JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` 

JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`

JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`

JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`

WHERE `departments`.`name` = 'Dipartimento di Matematica'


7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami