1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT 
    `students`.`name` AS `student_name`,
    `students`.`surname`AS `student_surname`,
    `degrees`.`name` AS `nome_corso`
FROM `students`

INNER JOIN `degrees`
ON `degrees`.`department_id` = `students`.`degree_id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';



2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze

SELECT 
    `level` AS `corso_magistrale`,
    `degrees`.`name` AS `nome_corso`,
    `departments`.`name` AS `nome_dipartimento`
FROM `degrees`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `level` = 'magistrale'  AND `departments`.`name` = 'Dipartimento di Neuroscienze';



3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT 
    `teachers`.`name` AS `nome`, 
    `teachers`.`surname` AS `cognome`,
    `courses`.`name` AS `nome_corso`
FROM `teachers`
INNER JOIN `courses`
ON `courses`.`id`
WHERE `teachers`.`id` = '44';



4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome

SELECT 
    `students`.`name`,
    `students`.`surname`,
    `degrees`.`name` AS `nome_corso`,
    `departments`.`name` AS `nome_dipartimento`
		
FROM `students`

INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`

INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`

ORDER BY `students`.`name`, `students`.`surname`ASC;



5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT
	`degrees`.`name` AS `corso_di_laurea`,
	`courses`.`name`AS `nome_corso`,
	`teachers`.`name` AS `nome_insegnante`,
	`teachers`.`surname` as `cognome_insegnante`
    
FROM `degrees`

INNER JOIN `courses`
ON `degrees`.`id` = `courses`.`degree_id`

INNER JOIN `teachers`
ON `teachers`.`id` = `courses`.`id`;



6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)

SELECT DISTINCT
	`teachers`.`name` AS `nome_docente`,
	`teachers`.`surname` AS `cognome_docente`,
    `departments`.`name` AS `nome_dipartimento`
FROM `teachers`

INNER JOIN `course_teacher`
ON `course_teacher`.`teacher_id` = `teachers`.`id`

INNER JOIN `courses`
ON `course_teacher`.`course_id` = `courses`.`id`

INNER JOIN `degrees`
ON `courses`.`degree_id` = `degrees`.`id`

INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name` = 'Dipartimento di Matematica';



7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.