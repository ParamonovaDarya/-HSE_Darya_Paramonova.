# -HSE_Darya_Paramonova.
Final homework SQL 
    Определение таблиц и атрибутов:
  Таблица students:
id (Primary Key) — уникальный идентификатор студента.
full_name — полное имя студента.
birth_date — дата рождения.
contact_info — контактные данные (телефон/электронная почта).
group_id — идентификатор группы (Foreign Key).

  Таблица teachers:
id (Primary Key) — уникальный идентификатор преподавателя.
full_name — полное имя преподавателя.
birth_date — дата рождения.
contact_info — контактные данные.

  Таблица subjects:
id (Primary Key) — уникальный идентификатор предмета.
name — название предмета.
teacher_id — идентификатор преподавателя (Foreign Key).

  Таблица grades:
id (Primary Key) — уникальный идентификатор оценки.
student_id — идентификатор студента (Foreign Key).
subject_id — идентификатор предмета (Foreign Key).
teacher_id — идентификатор преподавателя, который выставил оценку (Foreign Key).
grade — оценка (целое число от 1 до 5).
date — дата выставления оценки.

  Таблица groups:
id (Primary Key) — уникальный идентификатор группы.
name — название группы.
    
    Нормализация данных
Проверим, что каждый атрибут находится в своей таблице и не дублируется.
Таблицы связаны с использованием внешних ключей:
students.group_id → groups.id
subjects.teacher_id → teachers.id
grades.student_id → students.id
grades.subject_id → subjects.id
grades.teacher_id → teachers.id
    
    Создание ограничений на атрибуты
Поля grade в таблице grades — значения от 1 до 5.
Поля name в таблицах students, teachers, subjects и groups должны быть уникальными.
Поля с датами не могут быть пустыми.
   
    Механизмы предотвращения дублирования
Добавим уникальные индексы на поля, где это необходимо.
Внешние ключи обеспечат целостность данных.
 
    Написание запросов
Например, для получения списка студентов по определённому предмету:  
  SELECT s.full_name 
  FROM students s
  JOIN grades g ON s.id = g.student_id
  JOIN subjects sub ON g.subject_id = sub.id
  WHERE sub.name = 'Название предмета';
  (блок кода SQL)
