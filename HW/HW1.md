## Домашнее задание 1

**Дедлайн: 27 сентября 23:59**

После дедлайна задание **не принимается**. Но если вы понимаете заранее, что обстоятельства непреодолимой силы не позволят вам сдать работу вовремя, напишите нам об этом, и мы договоримся об индивидуальном переносе дедлайна. Домашние задания не пересдаются.

Работы присылайте на daria.ryzhova@mail.ru, daschapopowa@gmail.com и milenakamskaia@gmail.com (на все три адреса!).

В этом задании мы будем создавать аналог системы CLICS на основе небольшого фрагмента онтологии WordNet, т.е. возьмем из WordNet данные о колексификациях значений (в этом случае - синсетов) и построим по ним взвешенный граф. 

### Шаг 1 (0.3 балла)
В базе WordNet возьмите синсет 'search.v.01'. Из всех языков, которые есть в базе, извлеките списки лемм, относящихся к этому синсету.

**NB!** Если вы возьмете в качестве стартового не этот синсет, а любой другой, это принесет вам 1 бонусный балл. Но будьте внимательны: в этом случае вам нужно будет самостоятельно регулировать ограничения на количество колексификаций из шага 2 так, чтобы в итоговом графе было не меньше 30 и не больше 60 узлов. 

### Шаг 2 (0.7 балла)
Теперь, наоборот, для каждой леммы из каждого языка составьте список синсетов, к которым она относится. Из этих синсетов выберите такие, к которым относится больше 3 лемм из нашего изначального списка (надеемся, что это поможет нам выделить более устойчивые и надежные связи). Оставшиеся синсеты и станут узлами нашего графа.

### Шаг 3 (1 балл)
Теперь строим ребра. Ребро между двумя синсетами ставьте в том случае, если хотя бы в одном языке есть хотя бы одна лемма, которая относится к ним обоим. Пусть граф будет взвешенным: вес ребра будет отражать количество лемм, относящихся к обоим узлам пары.

**NB!** На этом шаге мы уже забываем про исходный список лемм из шага 1 (он нам нужен был только для отбора синсетов) и учитываем все леммы, относящиеся к отобранным узлам.

**Критерии**: 0.5 балла - ребра, 0.5 балла - вес ребер

### Шаг 4 (3 балла)
Проанализируйте получившийся граф. Сколько получилось связных компонент? Какая у этого графа плотность? Как распределились (взвешенные) степени узлов? Какие узлы оказались центральными (попробуйте несколько метрик, например, degree centrality и eigencentrality, прокомментируйте результат)? Разбейте граф на сообщества (поиграйте с несколькими алгоритмами) и прокомментируйте результаты.

**Критерии**: 0.5 - связные компоненты, 0.5 - плотность графа, 1 - степени и центральность узлов, 1 - сообщества

### Шаг 5 (2 балла)
Постройте точно такой же граф, только теперь ставьте ребра только в том случае, если пару синсетов объединяет не менее 5 лемм (убираем все ребра с небольшим весом в поисках наиболее устойчивых связей). Проанализируйте этот граф по той же схеме (см. шаг 4). Что изменилось? Какой из графов кажется вам более содержательным и почему?

**Критерии**: 0.5 - обновленный граф, 0.5 - подсчет всех метрик заново, 1 - комментарий

### Шаг 6 (1 балл)
Подведите небольшой теоретический итог. Какие выводы о колексификациях в зоне глаголов поиска позволяют сделать эти два графа?

### Шаг 7 (бонусный, 1 балл)
Сравните ваши графы с подграфом LOOK FOR из базы CLICS. Что общего, в чем отличия? С чем эти отличия могут быть связаны? Если у вас был свой стартовый синсет, а не search.v.01, выберите в CLICS максимально близкий к нему по значению кластер.
