1. Selezionare tutti gli studenti nati nel 1990 (160)
    SELECT * 
    FROM `students`
    WHERE YEAR(`date_of_birth`) = 1990;

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
    SELECT * 
    FROM `courses`
    WHERE `cfu` > 10;

3. Selezionare tutti gli studenti che hanno più di 30 anni
    SELECT (YEAR(CURDATE()) - YEAR(`date_of_birth`))
    FROM `students`
    WHERE (YEAR(CURDATE()) - YEAR(`date_of_birth`)) > 30;

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)
    SELECT * 
    FROM `courses`
    WHERE `year` = 1 AND `period` = 'I semestre';

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)
    SELECT *
    FROM `exams`
    WHERE `date` = '2020-06-20' AND `hour` BETWEEN '14:00:00' AND '23:59:59';

6. Selezionare tutti i corsi di laurea magistrale (38)
    SELECT * 
    FROM `degrees`
    WHERE `level` LIKE 'm%';

7. Da quanti dipartimenti è composta l'università? (12)
    SELECT COUNT(*)
    FROM `departments`;

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
    SELECT * 
    FROM `teachers`
    WHERE `phone` IS NOT NULL;


------------------------------------------------------------------------------------------------------
- JOIN
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
    SELECT `students`.*, `degrees`. `name` AS `nome_corso` 
    FROM `students`
    INNER JOIN `degrees`
    ON `degrees`. `id` = `students`.`degree_id`
    WHERE `degrees`. `name`= 'Corso di Laurea in Economia';
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

--------------------------------------------------------------------------------------------------------
- GROUPBY
1. Contare quanti iscritti ci sono stati ogni anno
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
3. Calcolare la media dei voti di ogni appello d'esame
4. Contare quanti corsi di laurea ci sono per ogni dipartimento