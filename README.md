# hse24_hw5

[Google colab](https://colab.research.google.com/drive/1MAyvgbQSOxWsEbc5gRguvQABhO-fVfvj#scrollTo=ZE3qnOcWI-HZ)

### Описание метода нормализации данных

TPM (Transcripts Per Million) — это метод нормализации данных RNA-seq, который используется для приведения уровней экспрессии генов к единой шкале. Этот метод позволяет учитывать различия в "глубине секвенирования" между клетками или образцами, а также устраняет влияние размеров библиотек. Очень похож на FPKM и RPKM, но в нем сначала нормализуется по длине гена, а затем - по глубине секвенирования. Однако эффект дифференцирования очень силен, поэтому TPM является более точной статистикой при сравнении экспрессии генов в разных образцах так как при использовании TPM сумма всех TPM одинакова в каждом образце, что делает сравнение доли чтений, сопоставленных с геном в каждом образце, очень удобным.
![3](https://github.com/user-attachments/assets/6de1c7b7-d87d-4037-aa17-bbe7312dd794)


### Heatmap для экспрессии маркерных генов и анализ результата 

![Unknown](https://github.com/user-attachments/assets/e6e4ea83-6421-46fa-aabd-6007e7e6eced)

На тепловой карте четко можно увидеть около 5 кластеров:

**Кластер 1**:

- *Ccl21a*
- *Apoe*
- *Ly6a*
- *Ccl21c*

Этот кластер включает клетки с высокой экспрессией генов, связанных с функциями лимфоидной ткани и хемокинами (*Ccl21a*, *Ccl21c*). Вероятно что эти клетки связаны с иммунными функциями (клеточной миграцией или хемотаксисом).

**Кластер 2**:

- *Aire*
- *Hdc*
- *Ubd*

Гены, связанные с центральной толерантностью (*Aire*) и регуляцией аутоиммунных процессов. Этот кластер может представлять клетки, ответственные за презентацию антигенов и удаление аутоактивных T-клеток (например, медуллярные эпителиальные клетки вилочковой железы, mTEC).

**Кластер 3**:

- *Trpm5*
- *Avi*
- *Gnb3*

Клетки этого кластера, вероятно, соответствуют "пучковым" эпителиальным клеткам (tuft cells). *Trpm5* и *Avi* характерны для сенсорных функций и производства цитокинов, например, IL-25.

**Кластер 4**:

- *Prss16*
- *Psmb11*
- *Ascl1*
- *Sox4*

Этот кластер, скорее всего, представлен клетками, вовлечёнными в антиген-презентацию (например, через протеасомы — *Psmb11*) и регуляцию эпителиальной дифференцировки (*Sox4*). Может включать популяции клеток, ответственных за обучение T-клеток в вилочковой железе.

**Кластер 5**:

- *Car8*
- *Lcn2*
- *Pigr*

Эти гены указывают на участие клеток в воспалительных процессах (*Lcn2*) и секреции иммуноглобулинов (*Pigr*). Возможно, клетки этого кластера участвуют в барьерных функциях или локальных иммунных реакциях.

### Полученные визуализации UMAP и PCА и анализ результатов

![Unknown-1](https://github.com/user-attachments/assets/dedd62a1-4556-40cf-b307-714a5679f68f)

На данном графике изображен анализ кластеризации клеток в пространстве главных компонент (PCA) на основе их экспрессии генов.
В результате получилось 5 кластеров:

1. **cTEC (Cortical Thymic Epithelial Cells)** - кортикальные эпителиальные клетки вилочковой железы.
2. **mTEC-I, mTEC-II, mTEC-III, mTEC-IV (Medullary Thymic Epithelial Cells)** - различные подтипы медуллярных эпителиальных клеток вилочковой железы.

**mTEC-I -** являются источником для более зрелых mTEC-II клеток

**mTEC-II -** зрелый подтип медуллярных эпителиальных клеток. Уникальной чертой является высокая экспрессия гена *Aire* (Autoimmune Regulator) соответственно играют ключевую роль в обучении T-клеток толерантности к собственным антигенам.

**mTEC-III -** демонстрируют промежуточные признаки между зрелыми mTEC-II и более специализированными клетками (например, mTEC-IV). Функции менее изучены, однако в статье обсуждается их возможная роль в продукции цитокинов или регуляции локального воспаления.

**mTEC-IV -** имеют характеристики "пучковых клеток" (tuft cells), которые обычно находятся в эпителии кишечника и дыхательных путей. Экспрессируют *IL-25*, что указывает на их участие в активации врожденных лимфоидных клеток второго типа (ILC2). Также могут регулировать локальный иммунный ответ через взаимодействие с ILC2.

![Unknown-2](https://github.com/user-attachments/assets/3d8e2647-5490-46be-806a-c8ac2954611a)

UMAP — это метод нелинейного уменьшения размерности, который широко используется для визуализации высокоразмерных данных. 
Получились те же самые кластеры, более того данный метод визуализации оказался лучше так как чётко разделил все 5 типов клеток и сохранил локальную структуру данных, что важно для анализа кластеров в биологических данных, таких как scRNA-seq.
PCA показал хорошую глобальную структуру данных, но не смог чётко отделить все кластеры, особенно при наличии перекрытий между подтипами mTEC.
Тем временем, тепловая карта также выявила 5 отдельных кластеров. Таким образом результат получился идентичным по всем методам визуализации.

## Результаты выполнения бонусного задания

![Unknown-3](https://github.com/user-attachments/assets/a086fbcd-aea9-43e9-8224-2118866f382d)

График показывает сравнение средних значения TPM из bulk RNA-seq и scRNA-seq для всех маркерных генов из основной части.

Точки, близкие к диагонали, показывают гены, экспрессия которых в bulk и scRNA-seq похожа - в данном случае около 2/3 экспрессий генов +- равны 

![Unknown-4](https://github.com/user-attachments/assets/f28b243d-97e8-4737-97bf-1410797e3b64)

Выбрала 150 наиболее экспрессируемых генов как в bulk RNA-seq, так и в scRNA-seq.
График позволяет сравнить только те гены, которые являются высокоэкспрессированными в обоих наборах данных, однако в данном случае сложно понять какое количество экспрессий примерно равно, но это большинство точек то есть >50%

