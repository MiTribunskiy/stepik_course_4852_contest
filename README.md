# Описание

Здесь представлен baseline для [соревнования](https://stepik.org/lesson/226979/step/1?unit=199528), 
который дается в конце курса ["Введение в Data Science и машинное обучение"](https://stepik.org/course/4852/) на stepic.

За основу взять признаки которые создавали в течении курса. ROC_AUC = 0.8792.

**Структура проекта**
* **model-baseline.ipynb** - блокнот для тренировки модели и генерации прогноза
* **libs** - папка с код для генерации признаков(_data_iter1.py_) и вспомогательными модулями
* **data** - папка с данными 
* **reports** - в эту папку складывается прогноз 

# Соревнование

Задача нам уже знакома - нужно предсказать, сможет ли пользователь успешно закончить онлайн курс Анализ данных в R.
Мы будем считать, что пользователь успешно закончил курс, если он правильно решил больше 40 практических заданий.

В данных:

* submission_data_test.csv
* events_data_test.csv

хранится информация о решениях и действиях для 6184 студентов за первые два дня прохождения курса. 
Это 6184 студентов, которые проходили курс в период с мая 2018 по январь 2019. 


Используя данные о первых двух днях активности на курсе вам нужно предсказать, наберет ли пользователь более 40 баллов на курсе или нет.

В этих данных, вам доступны только первые дня активности студентов для того, чтобы сделать предсказание. 
На самом деле, используя эти данные, вы уже можете сделать прогноз. 
Например, если пользователь за первые два дня набрал 40 баллов, скорее всего он наберет более 40 баллов в дальнейшем. 
Чтобы подкрепить такие гипотезы, вы можете использовать [данные](http://stepik.org/lesson/222124/step/3?unit=195045), на которые мы исследовали в первых двух модулях курса, где для всех пользователей представлены все данные об их активности на курсе.

# Оформление результатов

Итогом вашей работы должен стать csv файл c предсказанием для каждого студента из тестовых данных. 
Пример предсказания выглядит [следующим образом](https://stepik.org/media/attachments/course/4852/submission_example.csv).

Чтобы узнать точность ваших предсказаний, в качестве решения этого шага отпраьте файл с предсказаниями для каждого студента в указанном выше формате.

Убедитесь, что вы сформировали файл с предсказаними для всех 6184 студентов, для каждого студента должна быть предсказана вероятность, что он наберет более 40 баллов за курс. У вас есть 20 попыток засабмитить решения, в зачет пойдет наилучший вариант.

Результатом проверки этого задания будет значение ROC AUC score, именно по этому показателю мы и отберем победителей, успехов!

Завершение соревнования - 1 июня.

# Описание данных

* [events_train.csv](https://stepik.org/media/attachments/course/4852/event_data_train.zip) - данные о действиях, которые совершают студенты со стэпами
    * **step_id** - id стэпа
    * **user_id** - анонимизированный id юзера
    * **timestamp** - время наступления события в формате unix date
    * **action** - событие, возможные значения:
        * _discovered_ - пользователь перешел на стэп
        * _viewed_ - просмотр шага,
        * _started_attempt_ - начало попытки решить шаг, ранее нужно было явно нажать на кнопку - начать решение, перед тем как приступить к решению практического шага
        * _passed_ - удачное решение практического шага

* [submissions_train.csv](https://stepik.org/media/attachments/course/4852/submissions_data_train.zip) - данные о времени и статусах сабмитов к практическим заданиям
    * **step_id** - id стэпа
    * **timestamp** - время отправки решения в формате unix date
    * **submission_status** - статус решения
    * **user_id** - анонимизированный id юзера