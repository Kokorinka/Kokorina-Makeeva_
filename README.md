Описание задания и полученнные результаты
В рамках задания проведён анализ датасета с молекулярными дескрипторами. Основные этапы включали парсинг дескрипторов, предобработку данных, проведение статистических тестов и визуализацию. Для просмотра задания необходимо открыть файл "Кокорина_курсовое задание.ipynb".

1. Парсинг дескрипторов

С помощью библиотеки rdkit извлекли 210 дескрипторов из исходного датасета.
Для парсинга можно использовать такие библиотеки, как RDKit или другие инструменты для обработки молекулярных структур.
Выполняли перебор дискрипторов по стлобцу "smiles" и записали полученный датафрейм в новый файл data1.csv.
2. Предобработка данных

Считали данные из полученного датафрейма data1.csv.
Выполнили поиск пропусков в датасете с помощью функции DataFrame isnull(). Пропусков не нашлось, поэтому приступили к отбору параметров по дисперсии.
Для начала удалили все столбцы со строковым типом данных в датафрейме и сохранение в новый датафрейм data3.csv.
Вычисляем дисперсию каждого столбца и если она превышает порог в 0.05, то удаляем эти столбцы, а результат сохраняем в новый датафрейм data4.csv.
Вычисляем корреляцию данных в каждом столбце. Находим пары признаков с корреляцией выше 0.7.
Исключаем один признак из каждой сильно коррелирующей пары и записываем результат в новый датафрейм data5.csv.
В результате данной фильтрации удалось сократить количество столбцов до 72.
3. Проведение статистических тестов

Далее провели проверку на нормальность распределения данных на нормальность по тесту Шапиро-Уилка (он сравнивает наблюдаемые данные с ожидаемым нормальным распределением).
Вывели показатели по каждому столбцу, "Статистика теста", "P-значение", после чего пришли к выводу, что данные не похожи на нормальное распределение, что и показал тест Шапиро-Уилка.
4. Визуализация данных

Провели визуализацию данных с помощью seaborn и plotly.
График 1.

Построили точечный график зависимости mu от alpha (дипольный момент от изотропной поляризуемости).
График 1 показывает как происходит уровень значимости alpha влияет на выборку и оценку среднего mu (дипольного момента).
Тенденция такая - чем меньше mu, тем больше alpha.
График 2.

Построили точечный график зависимости u0 от cv (внутреннюю энергию молекулы и теплоёмкость)
График 2 показывает, что молекулы с внутренней энергией от -500 до -300 имеют наибольшую теплоёмкость.
График 3.

Построили гистограмму по SPS (эмпирическая оценка пространственной сложности молекулы).
График 4.

Построили боксплот, который позволяет быстро оценить распределение значений "cv" и идентифицировать центральные тенденции и разброс.
Как можно видеть по графику наблюдаются после фильтрации все еще наблюдаются выбросы до 1-го и после 4-го квартилей.
График 5.

Это визуализации данных, которая сочетает в себе элементы боксплота и плотности распределения.
Высокая частота значений наблюдается от 150-200, значит сложность молекулы в этом пределе наибольшая (BertzCT - индекс, который используется для оценки сложности молекулы).
График 6.

Построили график корреляции данных в итоговом отфильтрованном датафрейме df5.
По графику видно, что у нас наблюдается хаотичная корреляция, как положительная, так и отрицательная по всему датафрейму.