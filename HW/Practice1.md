## Practice 1: Natural Language Inference

#### Задача 1

Исследуем варьирование комитмента в зависимости от оператора (отрицания, условия, модального оператора, вопроса) и глагола (*think*, *know*, *believe* etc.). Работаем с [дейтасетом](https://github.com/mcdm/CommitmentBank/blob/master/CommitmentBank-items.csv) английского [CommmitmentBank](https://github.com/mcdm/CommitmentBank/tree/master).

[Hofmann et al. 2023](https://github.com/dashapopova/CompSem2024/blob/main/NLI/Hofmann-etal_SuB28.pdf) исследовали варьирование комитмента в английском в зависимости от оператора (отрицания, условия, модального оператора, вопроса) и предиката и установили, что условный контекст более проективен (чаще сохраняет следствия), чем вопросительный, который, в свою очередь, более проективен, чем контекст отрицания и модального оператора, также они отметили варьирование по предикату. 
Ранее Sieker & Solstad 2022 установили, что для немецкого языка контекст отрицания -- самый проективный контекст. 

Посчитайте средний рейтинг комитмента по предикату (*think*, *know*, *believe* etc.) и по оператору (modal, negation, conditional, question) из [дейтасета](https://github.com/mcdm/CommitmentBank/blob/master/CommitmentBank-items.csv), приведите релевантный код и постройте график, аналогичный Figure 1 в [Hofmann et al. 2023](https://github.com/dashapopova/CompSem2024/blob/main/NLI/Hofmann-etal_SuB28.pdf). Кратко прокомментируйте результат: подтвердилась ли на нашем дейтасете гипотеза, что в английском условный контекст более проективен (чаще сохраняет следствия), чем вопросительный, который, в свою очередь, более проективен, чем контекст отрицания и модального оператора?

#### Задача 2

Создаем CommitmentBank для русского: приведите 3 стимула и прокомментируйте рейтинг комитмента, который Вы ставите целевому предложению в каждом из стимулов, какие лингвистические факторы влияют, по Вашему мнению, на рейтинг в каждом случае?

Напоминаем, что стимул состоит из 1) источник (например, НКРЯ, VK); 2) предикат (например, *сказать*, *знать*, *подозревать*); 3) тип оператора (ничего/отрицание/условие/модальный оператор/вопрос); 4) одно/два предложения до целевого; 5) целевое предложение, содержащее предикат; 6) Ваш рейтинг комитмента (от -3 до +3).

Материалы английского [CommmitmentBank](https://github.com/mcdm/CommitmentBank/tree/master), где можно подробнее прочитать про разметку.

#### Задача 3

Переделываем английский [CommitmentBank](https://github.com/mcdm/CommitmentBank/blob/master/CommitmentBank-items.csv) в дейтасет для NLI и тестируем, насколько хорошо с помощью BERT можно предсказать наличие следствия, противоречия или нейтрального отношения на этом дейтасете. 

Примерный алгоритм (можно делать по-другому, но тогда кратко поясните, что и почему Вы делаете):

- приводим изначальный [дейтасет](https://github.com/mcdm/CommitmentBank/blob/master/CommitmentBank-items.csv) к нужному виду: берем средний рейтинг для каждого стимула, средний рейтинг в интервале [1,3] -- следствие (entailment), [0] -- нейтральное отношение (neutral), в интервале [-3,-1] -- противоречие (contradiction), приведите код, который создает из изначального дейтасета файл, который Вы подаете на вход BERT;

- с помощью любой модели семейства BERT ([хендаут про BERT](https://github.com/dashapopova/CompSem2024/blob/main/compsem_bert_Nika_Zykova.ipynb)) предскажите лейбл отношения (entailment, neutral, contradiction) для пары Target+Prompt (подсказка: подумайте, как использовать [CLS] и [SEP]), приведите релевантный код и precision, recall, F1;

- кратко прокомментируйте результат.

Можно посмотреть, как аналогичная задача решалась [тут](https://github.com/dashapopova/CompSem2024/blob/main/NLI/de%20Marneffe_CommitmentBank%20for%20NLI.pdf).
