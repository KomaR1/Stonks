## Курсовой проект по дисциплине "Проектирование информационных систем"

## Сыпачев А., ИДБ-17-07

### Определение требований к модели [✋](https://github.com/stankin/design-part-2/wiki/LR-1)

**Тема ВКР:** Создание web-приложения оформления заказов на изготовление изделий с применением современных технологий.

**Объект исследований:**  процесс формирования и отслеживания заявок на изготовление изделий с помощью аддитивных технологий.

**Предмет исследований:** формализация и автоматизация процесса приема заявок.

**Процессы верхнего уровня:** [✋](https://github.com/stankin/design-part-2/wiki/sem1)
* **А1** Управлять обработкой данных
* **А2** Обработать запрос
* **А3** Создать личный кабинет
* **А4** Войти в систему
* **А5** Обработать заявку
* **А6** Выполнить заказ

**Точка зрения:** ИТ-директор

**Цель моделирования:** Определение процессов повышения качества обработки приема заявок на производство аддитивной продукции

### 2. Функциональное моделирование процессов (IDEF0) [✋](https://github.com/stankin/design-part-2/wiki/LR-1)

* **Диаграмма А0**

![none](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/01_A0.png)

* **Диаграмма А1-А6**

![none](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/02_A0.png)

* **Диаграмма А31-А34**

![none](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/03_A3.png)

* **Диаграмма A41-A43**

![none](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/05_A4.png)

* **Диаграмма А51-А53**

![none](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/07_A5.png)

### 3. Функциональное моделирование программных и информационных средств (DFD) [✋](https://github.com/stankin/design-part-2/wiki/LR-2)

**Конфигурация технических средств:** Visual Studio, ПК с любой операционной системой с поддержкой GUI, PostgreSQL

**Конфигурация программных средств:** многоуровневые

**Допустимые виды хранилищ и их размещение:** БД под управлением PostgreSQL, файлы формата .stl, .obj, .stp

* **Автоматизация процесса А34**

![none](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/04_A34.png)

* **Автоматизация процесса А44**

![none](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/06_A44.png)

### 4. Описание выбранного процесса [✋](https://github.com/stankin/design-part-2/wiki/LR-3) в формате прецедента (Use Case) [✋](https://github.com/stankin/design-part-2/wiki/LR-4)

[Диаграмма UML Use Case](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/UML-Usecase.PNG)

**4.1 Идентификатор прецедента:** A5

**4.2 Название прецедента:** Обработать заявку

**4.3 Контекст:** Обработка данных (данные пользователя, файл с моделью), указанных в заявке на изготовление изделий

**4.4 Участники (actors) и цели (goals):**

| Участник  | Категория  | Цель (goal) |
|---|---|---|
| Покупатель | Основной  | Составить и отправить заявку на изготовление изделия |
| Оператор | Основной | Получить, обработать и записать данные в БД |
| Приложение | Инструмент | Обработать, сформировать и записать данные в БД |

**4.5 Предусловия (pre-conditions):**

* Условие наличия потока управления: Запрос на создания заявки

* Условие наличия входного потока: Заполненная заявка (данные о покупателе, модель изделия)

* Условие наличия потока исполнителя: Оператор предприятия

* Условие наличия потока механизма: Приложение

**4.6 Постусловия (post-conditions):**

* Выходной поток: Обработанная заявка (принята или отклонена)

**4.7 Основной поток выполнения (main flow)**:

| Участник  | Действие (activity)  | Ожидаемый результат |
|---|---|---|
| Покупатель | Регистрируется | Поступление данных в систему |
| Покупатель | Вводит данные личного кабинета | Наделение пользователя правами на создание заявки печати 3D объекта |
| Покупатель | Отправляет заявку с 3D моделью | Поступление запроса в систему, начало обработки запроса |
| Оператор | Авторизуется | Наделение пользователя правами оператора |
| Оператор | Обрабатывает заявку | Обработанная заявка |
| Оператор | Контролирует состояние выполнения заявки | Уведомление покупателя о состоянии заявки (заявка принята/отклонена/оплачена/в работе/выполнена) |


**4.8 Исключения (exceptions):**

| Условие (риск) | Последствия | Реакция |
|---|---|---|
| Ввод некорректных данных | Сбой в работе приложения | Сообщить покупателю о некорректности введенных данных |
| Отправка некорректного файла | Сбой в работе приложения | Сообщить покупателю о проблеме с файлом |
| Сбой в работе или недоступность сервера | Прекращение функицонирования приложения | Сообщить пользователю о временных технических неполадках и при наличии интернет соединения отправить администратору сообщение о сбое |

**4.9 Альтернативы (alternates):**

| Участник  | Действие (activity)  | Ожидаемый результат |
|---|---|---|
| Администратор | Масштабирование вычислительных мощностей | Стабильная работа приложения |

**4.10 Временные параметры:**

* **Триггер:** Обращение пользователя (составление заявки)

* **Номинальная частота повторения прецедента:** 20 в сутки

* **Продолжительность прецедента:** 40 минут

### 5. Описание структуры объекта [✋](https://github.com/stankin/design-part-2/wiki/LR-3) в формате ERD (Class) [✋](https://github.com/stankin/design-part-2/wiki/LR-5)

* **Описываемый объект:** База данных приложения

* [**Диаграмма UML Class:**](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/ERD.txt)

<p align="center">
  <img src="http://www.plantuml.com/plantuml/png/lPB1Ri8m38RFv2bodiGBS6Bi0IPDcdQiJEAr4KdSESwcQkBTbz823N3UgUqNk__lFzuc0POSl4e75tjW2DfuI4d_gjKEpA5boj6-a2VM7vqJLAjdPlgPoCwNab98R96NwAWwPr4RnyRZz1vGEh99gUd_xmbvLD5QEzjalT5xrnRcm8_CK-jYWKdOnNOaVUcg01Y39nHps2EFwDDHtTDHn49S56nBoN4MV-sHGOZJF-kFgEI3rwAZEbjYYrS_Ski7iX1NMZJFK0bQ46mCOtbiJXzNIA7tkCICYJ8RhAVwoX35oL1f9O4Mbw2UOYI6ajHXz304ZDB8q6Dj4htxHXxkJuh9iIKzoEVjulQS4Tzc525WK-SHG4x7TrQR7hbf6K9b-U7mzpSsxUvw_JJVcfhtgOONnqkunMXpy7y0">
</p>

### 6. Описание алгоритма [✋](https://github.com/stankin/design-part-2/wiki/LR-3) в формате UML (Sequence) [✋](https://github.com/stankin/design-part-2/wiki/LR-6)

* **Описываемые процессы и потоки данных:** А1 "Обработать запрос", А2 "Создать личный кабинет", А3 "Войти в систему"

* [**Диаграмма UML Sequence:**](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/UML6.txt)

![p6](http://www.plantuml.com/plantuml/png/jLFDRjDW4Bn_Jx7g7N7dW7WGBfzhHqIGf79ipgwZ5X154QWI4WT-40_Wc9eOD_do2hjlnAnT9r-jm8rBcqyxExCxituoJsoSf9CNPlvyF3spiPtGP3QTdJwBPvE8aZYDZB6doImc_iItN7F5Myd9pYarW2VZq_6PdIPqmZyaOwT5XV3DYM960ynxUSUDLmzCQ1CRs7caHIvupGNn3NvimVHMBbfKQ4nA3nxJY1uHVqHnfr9oJa0L9EUGNNTDEj_JAM_OuLtfl3hy-ALD8imosfDynfIDP538vGeC-9Tr_N8f2p2KSj5o50zHgFWdrpr8BY5IatBBAtGu51qw6lIlKDfo1V824_jYkvQ_v6Qmt_4L1kmq9FSs-Q9MWBYIh2ClkTJ91pfTHz2EmojWbSz9tYEuyk2jXpkmtCeLnbBwGcF5UtdmCp21SeP7Gy7BcqiMWwLBGjhN1wxGXFUvr6yautTraA1tLAbpWiQAP043TtY_RXtxJRpkERWsOUJ917lZlcEVHaEzss_Pdu5J7_ske3ClrQvlx5HItd3LH-MwPH6EB2LNVRYtLaRDMn7rCE0QY7ydxEkF_FF_q1scMWXITKc3sSZ2EtGlx6iluFyPgH_byPpmHpF_MnnVzUENJ4CyMAko_QVeXQ2qxkwAV-tHQeKkfTU0FY-2Mjto3DyCxQxksVq7)

### 7. Описание состава [✋](https://github.com/stankin/design-part-2/wiki/LR-3) в формате UML (Component) [✋](https://github.com/stankin/design-part-2/wiki/LR-7)

* **Описываемый объект:** Компоненты web-приложения оформления заказов на изготовление изделий с применением современных аддитивных технологий

* **Диаграмма UML Component:**

![p7](http://www.plantuml.com/plantuml/png/HOz12i9034NtSuhGVQyWLRfn8HIAgz95R6CfT39b4WKH3-EDF9BfEE0cX7pU-wGInQWtlpWE8q5He-85XQ2bUATOmDC1r0SeeRDvGiQ9FB52-n0btxkNo-IHho5wr3bm3XEST-CtDJGn32GoyzHRrcKBbENEMlwovlF-qMUXk9NlrtMPXsHFu7PFMFORMX6FziWN)

### 8. Демонстрация реализации (личная страница)

Личная страница на [**Github**](https://github.com/KomaR1/Stonks/wiki/%D0%9A%D1%83%D1%80%D1%81%D0%BE%D0%B2%D0%BE%D0%B9-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82)

### 9. Подготовка к интерпретации построенных моделей

**9.1 Используемые паттерны проектирования и разработки [✋](https://github.com/stankin/design-part-2/wiki/sem2):**

* **Процессная модель для сравнения:**

Процессная модель для сравнения представляет собой систему, в которой реализовано уменьшение роли оператора и большее взаимодействие самого клиента непосредственно с системой для наиболее эффективной обработки данных

Для реализации подобной системы нет необходимости менять процессную модель (состав и последовательность процессов P-D-C остаются прежними)
**Задача:** Необходимо повысить эффективность обработки данных
**Решение задачи при помощи методологии PDCA:**

1.**Этап Plan**(Планирование):

 1.1 Выявленные проблемы:

 * чрезмерные затраты времени на оформление новых клиентов (данные абонентов вводятся непосредственно в офисе оператора, это существенно повышает время);
 * чрезмерные затраты времени на обработку данных абонентов;

 1.2 Цель: оптимизировать временные затраты на обработку данных;

 1.3 Требования: уменьшить время обработки данных без увеличения количества сотрудников.

 1.4 Ожидаемый результат: повышение эффективности обработки данных;

 1.5 Ресурсы, необходимые для достижения ожидаемого результата: необходима информационная система обработки данных (web-приложение, БД, сервер);

 1.6 Процессы (запланированные действия):

 * Проектирование
 * Создание макета дизайна web-приложения
 * Проектирование и разработка БД
 * Программная настройка

 2.**Этап Do** (Выполнение):

Сотрудники выполняют поставленные задачи

 3.**Этап Check** (Проверка):

По итогу внедрения разработанного web-приложения производится оценка эффективности

 4.**Этап Act** (Улучшение):

Если запланированные действия начинают выдавать ожидаемый результат (уменьшается время обработки), то web-приложение принимается за основу и внедряется с последующей доработкой.

 * Используемые в разработке паттерны и фреймворки:

Для работы с Python в качестве фреймворка был использован Django с HTML/CSS-фреймворком Bootstrap, который включает в себя также готовые стили и плагины.

**9.2 Используемые паттерны выявления проблем [✋](https://github.com/stankin/design-part-2/wiki/sem3):**
* Муда: Потеря времени из-за огромного потока клиентов, который приводит к столпотворению
* Мура: Выполнение скопившейся за день работы за пару часов до окончания рабочего дня
* Мури: Очередь к оператору

**9.3 Возможные антипаттерны [✋](https://github.com/stankin/design-part-2/wiki/sem4):**

| Категория  | Антипаттерн (риск) | Действие по избежанию |
|---|---|---|
| Разработка | Спагетти-код — слабо структурированная и плохо спроектированная система, запутанная и очень сложная для понимания. Такой код так же очень часто содержит в себе множество примеров анти-паттерна программирования копи-пастом. Подобный код в будущем не сможет разобрать даже его автор. В ООП спагетти-код может быть представлен в виде небольшого количества объектов с огромными, по размеру кода, методами. | Рефактор спагетти-кода, переписывание функций.|
| Архитектура | Божественный объект (God Object) - такой объект берет на себя слишком много функций и/или хранит в себе практически все данные. В итоге мы имеем непереносимый код, в котором, к тому же, сложно разобраться. Так же, подобный код довольно сложно поддерживать, учитывая, что вся система зависит практически только от него | Разбивать задачи на подзадачи, с возможностью решения этих подзадач различными разработчиками |
| Организация | Scope creep: Неконтролируемо разрастание или “расползание” границ проекта, приводящее к срыву сроков, перерасходу бюджета или снижению качества, чтобы удержаться в границах проекта | Держать под контролем масштабы проекта |
| Среда | Чрезмерное усложнение: Расходы ресурсов, что делает проект более устойчивым и сложным, чем это необходимо | Четко установить задачи и ограничения в ТЗ |

### 10. Интерпретация построенных моделей

**10.1 Определение числовых показателей для поставленной цели моделирования:**

Стандарт цели: определение процессов требующих повышения качества.

![none](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/UFP.PNG)

Способ получения: извлечение из диаграмм IDEF0 и DFD.

**10.2 Определение числовых показателей для цели потенциального проекта автоматизации: [✋](https://github.com/stankin/design-1/wiki/interpret_process)**

Одним из важных числовых показателей является временные затраты клиента на оформление заявки.

**10.3 Расчет потенциального эффекта от автоматизации:**

Предположим, что клиент в среднем на оформление заявки, от начала до отправки, тратит 40 минут. За сутки клиент может обратиться к заявке примерно 20 раз, либо корректируя её, либо изменяя, либо проверяя статус заявки. В целом это действие может занять 13-14 часов свободного времени, подобное распределение возможностей нецелесообразно. Внедрение web-приложения, в данный процесс, позволит оптимизировать планирование времени, сократить его, что увеличит продуктивность продуктивность аддитивного производства.

После внедрения информационной системы на оформление одной заявки понадобится 20 минут, при условии первоначального создания личного кабинета, а впоследствии время на оформление одной заявки сократится до 15 минут и те же 20 обращений к системе за сутки:
(15 * 20) / 60 = 5 часов.

Рассмотрим период в 1 месяц: 30 суток и 30 клиентов.

Итого экономия времени составит: 14ч-5ч=9 часов, в месяц 9ч * 30 дней = 270 часов. При наличии 30 клиентов, которые обращаются к системе 24 часа в сутки, ежемесечная экономия времени будет: 270 * 30 = 8100 человеко-часов в месяц.

**10.4 Определение числовых показателей и расчет трудозатрат на разработку программных средств:**

**Расчет сложности разработки методом FPA IFPUG:**

![none](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/FPA.PNG)

**Расчет трудозатрат на разработку «с нуля» методом COCOMO II:**

![none](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/COCOMO.PNG)

**10.5 План-факт сравнение для затрат на реализацию:**

Исходя из расчетов п. 10.4 можно сформировать следующую таблицу:

![none](https://github.com/KomaR1/Stonks/blob/main/%D0%A0%D0%B8%D1%81%D1%83%D0%BD%D0%BA%D0%B8/final.PNG)

Из расчета: SLOC = 4464 строк кода

PM (Трудозатраты) = 322 человеко-часы

TDEV (Полный срок разработки, месяцы) = 4,4 месяца

Эффект от автоматизации (человеко-часы в месяц): 270 * 30 = 8100 человеко-часов в месяц

Исходя из значений по факту: SLOC = 3571 строк кода

PM (Трудозатраты) = 257 человеко-часы

TDEV (Полный срок разработки) = 0,9 месяца

Готовность = 80%

**ВЫВОДЫ**

Исходя из результатов таблицы п.10.5 можно сделать вывод, что за счет использования готовых библиотек, патернов разработки удалось сократить строки кода в 1,01 раза. Также, за счет сокращения сокращение функциональных требований, удалось сократить срок разработки с 4,4 месяцев до 0,9. Срок окупаемости составляет ~1 недели. На данный момент работа выполнена на 80%, и на остаток реализации по расчету осталось 168 часов, поэтому выполнение ВКР в срок осуществимо.
