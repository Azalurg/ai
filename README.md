# Rozpoznawanie Komórek Krwi na Zdjęciach przy Pomocy AI

## 🎯 Cel Projektu

Celem projektu jest stworzenie modelu opartego na sztucznej inteligencji, zdolnego do rozpoznawania i klasyfikacji różnych typów komórek krwi na podstawie obrazów mikroskopowych. Model ten może wspierać diagnostykę medyczną, pomagając w wykrywaniu chorób krwi poprzez automatyczną klasyfikację komórek.

## 🔬 Tło i Motywacja

Analiza komórek krwi jest kluczowym elementem diagnostyki wielu schorzeń, takich jak białaczka czy anemia. Obecnie klasyfikacja komórek dalej często odbywa się ręcznie przez specjalistów, co może być czasochłonne i podatne na błędy ludzkie. Automatyzacja tego procesu przy pomocy głębokiego uczenia może poprawić precyzję diagnozy oraz usprawnić pracę lekarzy.

## 🏗 Opis Rozwiązania

Projekt koncentruje się na stworzeniu oraz wytrenowaniu konwolucyjnej sieci neuronowej (CNN) do klasyfikacji obrazów komórek krwi. Dwa modele o różnej złożoności zostaną porównane pod względem skuteczności i czasu trenowania.

## 🛠 Technologie i Narzędzia

- **Język programowania**: Python
- **Biblioteki**: TensorFlow, Keras, NumPy, OpenCV, Matplotlib
- **Środowisko**: Jupyter Notebook / Google Colab

## 📊 Zbór Danych

Zbór danych pochodzi z: [Blood Cell Images](https://www.kaggle.com/datasets/paultimothymooney/blood-cells) i zawiera obrazy mikroskopowe komórek krwi w formacie RGB (320x240 px)

4 klasy komórek:

- **EOSINOPHIL**
- **LYMPHOCYTE**
- **MONOCYTE**
- **NEUTROPHIL**

## 🏗 Budowa Modelu

1. Warstwa wejściowa przetwarzająca obrazy (240x240 px, RGB)
2. Trzy bloki warstw konwolucyjnych z filtrami i warstwami poolingowymi
3. Warstwa spłaszczającej (Flatten)
4. Gęsta warstwa w pełni połączona (Dense)
5. Warstwa wyjściowa (4 klasy, softmax)

---

1. Warstwa wejściowa przetwarzająca obrazy (240x240 px, RGB)
2. Dwa bloki warstw konwolucyjnych z filtrami i warstwami poolingowymi
3. Warstwa spłaszczającej (Flatten)
4. Gęsta warstwa w pełni połączona (Dense)
5. Warstwa odrzucająca połowę wyników (Dropout)
6. Warstwa wyjściowa (4 klasy, softmax)

## 🔧 Trenowanie Modelu

Modele trenowane są przez 10 epok na zestawie treningowym, a do ewaluacji wykorzystywane są metryki dokładności (accuracy) oraz funkcja straty (loss). Dopasowywanie pierwszego modelu zajmuje ok 16.5 min, a drugiego (mniejszego) ok 8 min. Wykorzystywany sprzęt: **Intel® Core™ Ultra 7 Processor 165H - laptop**

## 📉 Porównanie Modeli

- **Model 1 (większy):**
  - Dokładność: **58.5%**
  - Strata: **4.23**
- **Model 2 (mniejszy, szybszy):**
  - Dokładność: **24.9%**
  - Strata: **1.39**

**Wnioski**
Model 1 (większy) osiągnął dokładność 58.5%, ale jego strata jest wysoka (4.23). Oznacza to, że model może mieć problem z dobrze dopasowanymi predykcjami, ale mimo to klasyfikuje lepiej niż losowo.
Model 2 (mniejszy) ma niższą stratę (1.39), ale jego dokładność jest niska (24.9%). Oznacza to, że model jest zbyt prosty i nie nauczył się wystarczająco dobrze.

## 📈 Możliwe Ulepszenia

Dalsze prace nad modelem mogłyby obejmować dodanie kolejnych warstw sieci neuronowej, zwiększenie zbioru danych treningowych oraz zastosowanie augmentacji obrazów poprzez zmiany nasycenia czy jasności. Użycie technik transfer learningu, takich jak pretrenowane modele ResNet, mogłoby również znaczną poprawić wyniki klasyfikacji. Aby uniknąć przetrenowania, warto byłoby także wdrożyć mechanizmy regularyzacji, takie jak dropout czy L2.

## 📌 Podsumowanie

Projekt pokazuje możliwości wykorzystania AI w diagnostyce medycznej, jednak osiągnięte wyniki wskazują na konieczność dalszych optymalizacji. Lepsze modele osiągają nawet **98.5%** dokładności ([przykład](https://www.kaggle.com/code/mohamedgobara/blood-cell-images-using-cnn-model-98-5)), co sugeruje, że dalsza praca nad architekturą modelu może przynieść znacznie lepsze rezultaty.

## 🚀 Dalszy Rozwój Projektu

W przyszłości możliwa jest integracja modelu z aplikacją webową umożliwiającą diagnostykę online oraz testowanie modelu na nowych zbiorach danych. Ponadto implementacja sieci Transformer mogłaby poprawić jakość klasyfikacji komórek krwi.

---

📝 Autor: *Patryk Wawrzyniak*  
📅 Data: *2025-02-26*
