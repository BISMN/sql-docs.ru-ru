---
title: Связать мастер (клиент интеллектуального анализа данных для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- nested tables, in association models
- association [data mining]
ms.assetid: 4db6462f-93c7-443f-8ff7-39474dc7029e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 15a86cc55e67b2000eabee62d02fa04de4874f59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66062304"
---
# <a name="associate-wizard-data-mining-client-for-excel"></a>Мастер взаимосвязей (клиент интеллектуального анализа данных для Excel)
  ![Мастера взаимосвязей на ленте «Интеллектуальный анализ данных»](media/dmc-associate.gif "Мастер взаимосвязей на ленте Интеллектуальный анализ данных")  
  
 Мастер поможет сопоставить, создать интеллектуального анализа данных модели с помощью [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритм правил взаимосвязей. Такие модели интеллектуального анализа данных особенно полезны для создания *систем рекомендаций*.  
  
 Алгоритм взаимосвязей [!INCLUDE[msCoName](../includes/msconame-md.md)] сканирует набор данных, состоящий из транзакций или событий, и находит частые сочетания. Возможны тысячи сочетаний, но алгоритм можно настроить для поиска большего или меньшего числа сочетаний и сохранения наиболее вероятных из них.  
  
 Анализ взаимосвязей можно применить для решения многих задач. Самое популярное применение этого метода — анализ покупательского поведения, находящий отдельные продукты, которые часто приобретаются вместе. Эту информацию можно использовать для рекомендации товаров клиентам на основе товаров, которые они уже купили.  
  
## <a name="using-the-associate-wizard"></a>Использование мастера взаимосвязей  
  
1.  В **интеллектуального анализа данных** ленты, нажмите кнопку **связать**.  
  
2.  На **Выбор источника данных** странице, выберите диапазон таблицы или данных Excel и нажмите кнопку **Далее**.  
  
     Книга с образцами данных на вкладке «Взаимосвязи» содержит пример того, как данные транзакций обычно упорядочиваются, если, например, имеется несколько товаров в каждой транзакции или несколько записей о покупках в расчете на клиента, которые вы хотите проанализировать.  
  
     Если вы хотите использовать внешние данные для построения модели взаимосвязей с помощью Мастер взаимосвязей, необходимо добавить данные в Excel во-первых, и *сведение* данные. Дополнительные сведения о подготовке данных к построению модели взаимосвязей см. в разделе [вложенные таблицы &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](data-mining/nested-tables-analysis-services-data-mining.md), в электронной документации по SQL Server.  
  
3.  На **ассоциации** выберите столбец, определяющий транзакцию.  
  
     Для моделей покупательского поведения этот идентификатор представляет собой моделируемый элемент. Требуется ли анализировать позиции, которые каждый отдельный клиент приобретает в разное время, или множество транзакций разных пользователей? В первом случае следует выбрать идентификатор клиента, во втором — идентификатор покупки или другой транзакции.  
  
4.  Для **элемент**, выберите столбец, содержащий элементы, между которыми вам нужно найти взаимосвязи.  
  
     Например, в модели покупательского поведения можно выбрать поле товара, чтобы проанализировать, какие товары часто приобретаются вместе. Если отдельных товаров слишком много для эффективного поиска корреляции, можно выбрать категорию или подкатегорию товаров.  
  
5.  В **пороговые значения**, можно задать значения, которые управляют или влияют на выходные данные модели:  
  
    -   **Минимальное несущее множество.** Указывает, сколько раз группа элементов должна появляться, чтобы считаться важной. Алгоритм будет пропускать все сочетания элементов, не отвечающие этому критерию. Например, вас могут интересовать только те наборы элементов, где элементы появляются вместе не менее 10 раз.  
  
    -   **Минимальная вероятность правила**. Задает значение минимальной вероятности, необходимой для сохранения правила. Анализируется весь набор данных для нахождения всех сочетаний, после чего подсчитывается вероятность. Если порог низкий, мастер может ассоциировать элементы со слабой корреляцией. Если порог слишком высокий, некоторые взаимосвязи могут быть пропущены, поскольку их не поддерживает достаточный объем данных.  
  
     В целом при изменении этих значений возникнут следующие результаты.  
  
    -   По мере уменьшения значения несущего множества увеличивается число найденных сочетаний.  
  
    -   При уменьшении максимального значения несущего множества отфильтровываются элементы, встречающиеся настолько часто, что их присутствие не имеет смысла.  
  
    -   По мере понижения вероятности правила понижаются требования, которым должно удовлетворять сочетание, чтобы считаться важным в контексте полного набора данных.  
  
     **Совет.** Рекомендуется создать несколько моделей интеллектуального анализа данных, используются различные сочетания несущего множества и вероятности. Чтобы отслеживать, какие параметры, используемые для каждой модели, можно использовать **модели документов** мастер в клиенте интеллектуального анализа данных для Excel и используйте **Detailed** отчетом. Дополнительные сведения см. в разделе [Документирование модели интеллектуального анализа данных &#40;интеллектуального анализа данных надстройки для Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md).  
  
6.  При необходимости щелкните **параметры** Чтобы изменить параметры алгоритма и настроить поведение модели интеллектуального анализа данных.  
  
     В диалоговом окне «Параметры алгоритма» содержатся все параметры, задаваемые в мастере, а также еще несколько используемых реже обычного, таких как MAXIMUM_SUPPORT. Сведения об использовании этих параметров см. в разделе [Microsoft Association Algorithm Technical Reference](data-mining/microsoft-association-algorithm-technical-reference.md).  
  
7.  На **Готово** введите уникальное имя для набора данных и модели.  
  
8.  В **параметры**, определяют, как вы хотите работать с моделью после ее завершения:  
  
    -   **Обзор**.  Когда модель готова, мастер открывает окно, в котором выводит правила, наборы элементов и диаграмму сети зависимостей с отображением взаимосвязей.  
  
         Дополнительные сведения о том, как интерпретировать данные в средстве просмотра модели взаимосвязей см. в разделе [просмотр модели правил взаимосвязей](browsing-an-association-rules-model.md).  
  
    -   **Включение детализации**. Выберите этот параметр, чтобы получить доступ к базовым данным из модели.  
  
         Детализация полезна, например, если требуется возможность просмотра исходных данных при щелчке на том или ином наборе элементов.  
  
    -   **Использовать временную модель**. Выберите этот параметр, если вы не хотите модели, сохраненные на сервере. Временные модели удаляются при закрытии Excel.  
  
9. Мастер анализирует все возможные сочетания и создает отчет, содержащий наборы элементов и правил.  
  
## <a name="more-about-association-models"></a>Дополнительные сведения о моделях взаимосвязей  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Алгоритм правил взаимосвязей Майкрософт анализирует обучающие данные для поиска элементов, которые отображаются вместе в транзакции. Каждая группа элементов образует *набора элементов*. Затем алгоритм подсчитывает число раз, когда появляется каждый набор элементов, и подсчитывает относительную важность каждого набора элементов во всех транзакциях.  
  
 Алгоритм использует эти сведения о наборах элементов для формирования правил, которые могут быть использованы для прогноза взаимосвязей или формирования рекомендаций. Например, правило может гласить: «если пользователь приобрел книгу автора 1 и книгу автора 2, то он, вероятнее всего, также приобретет книгу автора 3». Каждой рекомендации присваивается вероятность на основе прочности взаимосвязей.  
  
### <a name="requirements"></a>Требования  
 Чтобы использовать мастер взаимосвязей, необходимо соединение с базой данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Исходные данные могут быть организованы в виде таблицы транзакций. Исходные данные должны содержать один столбец с идентификаторами транзакций. Этот столбец определяет каждую группу элементов. Столбец транзакций должен иметь связь типа «один ко многим» со вторым столбцом, идентификатором элементов, в котором хранятся имена или идентификаторы отдельных элементов в группе.  
  
 Возможно, понимание этого облегчит сравнение с покупательской корзиной. Покупательской корзине присваивается идентификатор, который служит идентификатором транзакции. Каждый элемент в покупательской корзине, например пакет картошки или молока, является членом этой транзакции. Алгоритм взаимосвязей может отслеживать элементы в транзакции: например, чтобы определить, сколько раз картошка и Молоко появляются в транзакции.  
  
 Источник данных должен быть отсортирован по столбцу идентификатора транзакций.  
  
## <a name="see-also"></a>См. также  
 [Создание модели интеллектуального анализа данных](creating-a-data-mining-model.md)   
 [Просмотр модели правил взаимосвязей](browsing-an-association-rules-model.md)   
 [Анализ покупательского поведения &#40;таблиц средства анализа для Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)   
 [Пошаговое руководство по диаграмме сети зависимостей &#40;надстройки интеллектуального анализа данных&#41;](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
  
