1. Contare quanti iscritti ci sono stati ogni anno

SELECT
COUNT(`id`) AS `iscrizioni`,
YEAR(`enrolment_date`) AS `anno_iscrizione`
FROM
`students`
GROUP BY
`anno_iscrizione`

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT
COUNT(`id`),
`office_address`
FROM
`teachers`
GROUP BY
`office_address`;

3. Calcolare la media dei voti di ogni appello d'esame

SELECT
`exam_id`,
AVG(`vote`)
FROM
`exam_student`
GROUP BY
`exam_id`

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT
COUNT(`id`) AS `numero_corsi`,
`department_id`
FROM
`degrees`
GROUP BY
`department_id`
