## Итоговое задание по Проекту 4. Компьютер говорит "Нет"
![alt-текст](https://memegenerator.net/img/instances/82954367.jpg)
### 1. Описание проекта:
1. Проект выполнен на Kaggle.
2. Автор: [Pavel Begunov](https://www.kaggle.com/pavelbegunov).
3. [Ссылка](https://www.kaggle.com/pavelbegunov/pavel-begunov-sf-credit-scoring) на ноутбук на Kaggle.
4. Достигнутое в соревновании значении метрики [ROC_AUC](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html?highlight=roc_auc#sklearn.metrics.roc_auc_score):
   * Максимальное значение: 0.73650
   * На котором решил остановиться: 0.73164  
### 2. Цель: 
Построить скоринговую модель предсказания дефолта клиентов банка.
#### Задачи:
   1. Провести предварительную очистку данных.
   2. Провести оценку и преобразование данных.
   3. Сформулировать выводы относительно качества данных и тех признаков, которые будут использоваться в дальнейшем построении модели.
   4. Построить и обучить модель. Найти наилучшие параметры модели.
   5. Использовать различные метрики для оценки качества модели.         
### 3. Краткая информация о данных:
Датасет содержит информацию из анкетных данных о заемщиках, которые уже брали кредиты (повторных клиентов) и факт наличия дефолта.
Первоначальная версия датасета состоит из девятнадцати столбцов, содержащих следующую информацию:
  * client_id: идентификатор клиента;
  * education: уровень образования;
  * sex: пол заёмщика;
  * age: возраст заёмщика;
  * car: флаг наличия автомобиля;
  * car_type: флаг автомобиля-иномарки;
  * decline_app_cnt: количесвто отказанных прошлых заявок;
  * good_work: флаг наличия "хорошей" работы;
  * bki_request_cnt: количество запросов в БКИ (Бюро кредитных историй);
  * home_adress: категоризатор домашнего адреса;
  * work_adress: категоризатор рабочего адреса;
  * income: доход заёмщика;
  * foreign_passport: наличие загранпаспорта;
  * sna: связь заемщика с клиентами банка;
  * first_time: давность наличия информации о заемщике;
  * score_bki: скоринговый балл по данным из БКИ;
  * region_rating: рейтинг региона;
  * app_date: дата подачи заявки;
  * default: наличие дефолта;
### 4. Этапы работы над проектом.
1. Был проведен первичный анализ данных. В котором были определены типы данных, количество строк и столбцов, наличие пропусков и дубликатов.
2. Проведен анализ данных по группам признаков.
3. Заполнены пропуски и минимизированы выбросы.
4. Созданы новые признаки на основе имеющихся данных.
5. Отобраны признаки, которые влияют на конечный результат.
6. Данные преобразованы в вид, пригодный для модели.
7. Построена и обчена модель, подобраны гиперпараметры.
8. Использованы различные метрики для оценки качества модели.
### 5. Особенности работы:
1. Работу выполнял один.
2. Во время работы прибегнул к использованию:
    * Различных методов кодирования данных из библиотеки sklearn.preprocessing: [LabelEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html?highlight=labelencoder#sklearn.preprocessing.LabelEncoder), [OneHotEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html#sklearn.preprocessing.OneHotEncoder).
    * Методу PCA для декомпозиции сильноскоррелированных признаков.
    * Различным видам стандартизации данных: [StandardScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html?highlight=standard%20scaler#sklearn.preprocessing.StandardScaler)*, [MinMaxScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html?highlight=minmaxscaler#sklearn.preprocessing.MinMaxScaler), [RobustScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html?highlight=minmaxscaler#sklearn.preprocessing.MinMaxScaler).
    * Различным методам [Undersampling](https://imbalanced-learn.org/dev/references/under_sampling.html) и [Oversampling](https://imbalanced-learn.org/dev/references/over_sampling.html)* для балансировки данных.
    * Различным метрикам, которые применимы к задачам классификации.
    * Подбору гиперпараметров для модели с помощью [GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html?highlight=gridsearchcv#sklearn.model_selection.GridSearchCV).
3. Получил максимальное значение ROC_AUC в четвертой версии ноутбука, однако все остальные метрики имели очень малые значения, что указало на слабость модели. Поэтому решил сделать модель более рабочей (шестая версия), хоть это и снизило значение метрики ROC_AUC. Но несмотря на это значения всех остальных метрик увеличились, и значимо снизилась ошибка 2 рода.
4. Добавил пару исправлений в проект и доработал оформление:
    * Вместо удаления признака car, сделал декомпозицию car и car_type, это привело к улучшению модели и увеличению значений метрик.
    * Изменил описание некоторых функций;
    * Добавил REDME в формате md.
  - *методы, которые использовались. Для Oversamling лучше всего показал себя метод **[ADASYN](https://imbalanced-learn.org/dev/references/generated/imblearn.over_sampling.ADASYN.html)**.
