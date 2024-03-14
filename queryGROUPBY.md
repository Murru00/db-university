1. Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(*) as `iscritti_per_anno`, YEAR(`enrolment_date`) AS `anno` 
FROM `students`
GROUP BY YEAR(`enrolment_date`);



2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT COUNT(*) AS `numero_insegnanti`, `office_address` AS `via_ufficio`
FROM `teachers`
GROUP BY `office_address`  
ORDER BY `numero_insegnanti` ASC



3. Calcolare la media dei voti di ogni appello d'esame

SELECT `exam_id` AS `appello`, AVG(`vote`) AS `media_voti` 
FROM `exam_student`
GROUP BY `exam_id`;



4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT `department_id` AS `dipartimento`, COUNT(`name`) AS `numero_corsi` 
FROM `degrees`
GROUP BY `department_id`;