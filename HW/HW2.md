
# Домашнее задание 2. Кластеризация векторного пространства

## Входные данные
Входные данные содержатся в файле [HW2_change.txt](https://github.com/dashapopova/CompSem2024/blob/main/HW/HW2_change.txt).
Это глаголы и список существительных, которые входят в первые 50 их устойчивых коллокаций по версии НКРЯ (коллокации формата "глагол *заменить / сменить / поменять / изменить* + существительное на расстоянии от -3 до 3 от глагола").
**NB!** Можно взять свой датасет, см. пункт 7 в задачах.

## Задачи
1. Взять [любую предобученную векторную модель для русского языка](http://vectors.nlpl.eu/repository/) и извлечь оттуда вектор для каждого глагола и каждого существительного из списка. [Здесь](https://github.com/dashapopova/CompSem2024/blob/main/CompSem_word2vec_24.ipynb) лежит хендаут по word2vec, который может вам пригодиться.
2. На основе этих векторов построить репрезентацию для каждой пары «глагол + существительное» с помощью простой аддитивной модели композиции.
> Примечание. Если каждый вектор – это объект типа array в модуле numpy, то можно просто сложить эти два объекта, используя оператор «+».
3. Собрать все векторные представления пар в единую матрицу и кластеризовать их двумя способами:
* методом иерархической кластеризации;
* методом К-средних, см. [хендаут](https://github.com/dashapopova/CompSem2024/blob/main/CompSemClustering.ipynb).<br/>
В первом случае количество кластеров определяется автоматически (но задается значение порога t), во втором случае количество кластеров нужно задать вручную.
Возьмите то значение каждого из этих параметров, которое вам кажется наиболее удачным и обоснуйте свое решение (одного-двух предложений будет вполне достаточно).
Все остальные параметры в обоих случаях можно не менять и использовать настройки по умолчанию.
4. Для каждого кластера определите центр и выберите по три элемента, наиболее к нему близких (по метрике косинусной близости).
Центр можно определить как среднее арифметическое среди всех элементов кластера по каждому измерению (например, с помощью метода numpy.mean).
Кластеры, размер которых не превышает двух элементов, не учитывайте совсем. 
5. Оформите результат в виде набора групп из трех словосочетаний, например:  

идти_дождь, идти_снег, идти_град <br/>
идти_часы, идти_время, идти_урок <br/>
…  

6. Подготовьте очень краткий (буквально на абзац) анализ результатов. Однородные ли, на ваш взгляд, получились группы? Получается ли выявить сходства и различия в семантике глаголов?

**NB!** Шаги 4-6 нужно проделать с результатами обеих кластеризаций: и иерархической, и методом К-средних.

**7. (бонус на 10)**. Вместо предложенного датасета возьмите свой: выберите несколько предикатов и по любому корпусу составьте список существительных - их наиболее частотных аргументов (в списке должно быть 100-200 словосочетаний). Максимально четко опишите процедуру подготовки датасета: какой использовался корпус, как был составлен сам список.

## NB!
На основе этого задания можно написать итоговое эссе. Для этого можно пойти по одному из следующих путей: обсудить возможные варианты строгой оценки качества полученных результатов; предложить свою модификацию алгоритма; обсудить варианты выбора количества кластеров для алгоритма К-средних; поэкспериментировать с различными параметрами (взять другую языковую модель; попробовать другие модели композиции; поменять настройки алгоритма кластеризации и т.п.) и обсудить результат. А можно предложить свой вариант развития сюжета. 

## Как и когда сдавать
Выполненную работу (или ссылку на работу в открытом репозитории на гитхабе, или ссылку на работу в колабе) нужно послать Милене (milenakamskaia@gmail.com), Даше П. (daschapopowa@gmail.com) и Даше Р. (daria.ryzhova@mail.ru) - всем троим! - **до 23:59 16 октября**. После дедлайна работы не принимаются. По уважительной причине дедлайн можно перенести в индивидуальном порядке. Для этого напишите нам заранее (хотя бы за сутки до дедлайна), и мы с вами обо всем договоримся.  

## Критерии оценивания
Каждый элемент задания имеет свой вес:
* пункт 1 - 1 балл
* пункт 2 - 1 балл
* пункт 3 - 4 балла (по одному за метод и по одному за обоснование выбора порогового значения для иерархической кластеризации и числа кластеров для метода К-средних)
* пункт 4 - 1.5 балла (1 балл - определение центров, 0.5 балла - выбор трех элементов, наиболее к ним близких)
* пункт 5 - 0.5 балла
* пункт 6 - 1 балл
* пункт 7 - 1 балл
