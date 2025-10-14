# Self-supervised learning

В этом задании мы хотим познакомить Вас с методами `Self-supervised learning`.

Мы не хотим ограничивать Вас в творчестве и выборе методов.

Для решения данного ДЗ можно использовать любой из методов `Self-supervised learning`:
* метод предсказания относительного положения патчей внутри одного изображения из статьи ([ссылка](https://arxiv.org/pdf/1505.05192.pdf))
* методы Contrastive Learning
...
* и др.

В разделе `Дополнительные материалы по теме` ниже вы найдете много интересных идей и методов.

## Задание

Берем за основу ДЗ 1. С помощью техники [Self-supervised learning](https://arxiv.org/pdf/1505.05192.pdf), разобранной на лекции, 
нужно провести следующие эксперименты для N = 100, N = 50, N = 10:

1. Повторить ДЗ1, используя N% размеченной выборки
2. Предобучить feature extractor вашей архитектуры на всем датасете с помощью Self-supervised learning без использования разметки
3. Использовать предобученный feature extractor в архитектуре сети для обучения на N% размеченной выборки, сравнить: 
   - как быстро менялись лоссы в обучении без feature extractor (в ДЗ 1) и с предобученным feature extractor
   - как быстро менялись метрики без feature extractor и с ним
   - какая из сетей достигла плато быстрее
   - какие максимальные метрики

## Дополнительные материалы по теме

[Progress_and_Thinking_on_Self_Supervised_Learning_Methods_in_Computer.pdf](Progress_and_Thinking_on_Self_Supervised_Learning_Methods_in_Computer.pdf)

[Colorization as a Proxy Task for Visual Understanding](https://ar5iv.labs.arxiv.org/html/1703.04044)
