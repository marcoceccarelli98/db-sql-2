1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT \*
FROM
`degrees`
INNER JOIN `students` ON `students`.`degree_id` = `degrees`.`id`
WHERE
`degrees`.`name` = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
   Neuroscienze

SELECT \*
FROM
`degrees`
INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE
`departments`.`name` = "Dipartimento di Neuroscienze" AND `degrees`.`level` = "magistrale"

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT \*
FROM
`teachers`
JOIN `courses` ON `teachers`.`id` = `courses`.`id`
WHERE
`teachers`.`id` = "44"

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
   sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
   nome

   SELECT
   `students`.`surname`,
   `students`.`name`,
   `degrees`.\*,
   `departments`.`name`
   FROM
   `students`
   JOIN `degrees` ON `students`.`id` = `degrees`.`id`
   JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
   ORDER BY
   `students`.`surname`

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT
`degrees`.`name`,
`courses`.`name`,
`teachers`.`name`,
`teachers`.`surname`
FROM
`degrees`
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `teachers` ON `courses`.`id` = `teachers`.`id`

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
   Matematica (54)

SELECT DISTINCT
`teachers`.`name` AS `teacher_name`,
`teachers`.`surname` AS `teacher_surname`
FROM
`departments`
JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id`
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE
`departments`.`name` = 'Dipartimento di Matematica';

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
   per ogni esame, stampando anche il voto massimo. Successivamente,
   filtrare i tentativi con voto minimo 18.
