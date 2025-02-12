# Детекция аномалий

Имеются изображения технологического процесса разлива металлических цилиндров. Есть риск нарушения технологии: когда стенки цилиндра не успевают застывать и трескаются, незастывший металл выливается, не образуя требуемую заготовку. Необходимо оперативно определить лунку, где произошел пролив, при этом пролив - довольно редкое явление, гораздо больше изображений без пролива в лунке.

Задача: построить модель на основе автоэнкодера, определяющую состояние лунки: 
- пролив
- не пролив.

## Датасет
Данные - вырезанные с фото изображения лунок. 
[Ссылка на датасет](https://drive.google.com/file/d/1DHuQ3DBsgab6NtZIZfAKUHS2rW3-vmtb/view)

![img.png](img/img.png)

![img_1.png](img/img_1.png)
![img_2.png](img/img_2.png)

```
dataset
├── proliv  # изображения с проливами
|       ├── 000.jpg
│       ├── 001.jpg
│       │   └── ...
|
├── test  # тестовая выборка где перемешаны проливы и не_проливы
│       ├── imgs
│       │   ├── 000.jpg
│       │   ├── 001.jpg
│       │   └── ...
│       └── test_annotation.txt
|
├── train  #  обучающая выборка из не_проливов
|       ├── 000.jpg
│       ├── 001.jpg
│       └── ...
```

## План решения

1. Имплементировать или найти автоэкодер.
2. Обучить автоэнкодер на не проливах (dataset\train).

    Если через такой автоэнкодер прогнать изображение пролива, то MSE между входным изображением и выходным будет больше, чем если прогнать изображение без пролива. Следовательно, если определить некоторое пороговое значение MSE, можно классифицировать изображение на классы пролив\не_пролив. (MSE между входной картинкой и выходной больше фиксированного порога - пролив).
    В качестве loss функции используем MSE (как минимум для baseline).

3. Написать метод классификации лунок в зависимости от порога. Для определения порога используем изображения из dataset\proliv.
4. На изображениях из dataset\test протестировать качество: посчитать True_positive_rate и True_negative_rate (нужно получить более 95% по каждой).

### Для выполнения ДЗ можно также выбрать один из датасетов:
1. https://www.kaggle.com/datasets/wardaddy24/marble-surface-anomaly-detection-2
2. https://www.kaggle.com/datasets/ipythonx/mvtec-ad
3. https://www.kaggle.com/datasets/trainingdatapro/brain-anomaly-detection
4. https://www.kaggle.com/datasets/belkhirnacim/textiledefectdetection