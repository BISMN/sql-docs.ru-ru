---
title: Выберите из &lt;модели&gt;. ВАРИАНТЫ (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5f0334c37eeedafee7066f01d61745fcb82d1629
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892845"
---
# <a name="select-from-ltmodelgtcases-dmx"></a>Выберите из &lt;модели&gt;. ВАРИАНТЫ (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Поддерживает детализацию и возвращает объекты, которые использовались для обучения модели. Кроме того, можно возвращать столбцы структуры, не включенные в модель, если и в структуре, и в модели интеллектуального анализа данных включена детализация и пользователь обладает необходимыми разрешениями.  
  
 Если детализация для модели интеллектуального анализа данных не включена, выполнение данной инструкции завершится ошибкой.  
  
> [!NOTE]  
>  Для расширений интеллектуального анализа данных активировать детализацию можно только при создании модели. Добавить детализацию в существующую модель можно с помощью среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], однако, прежде чем будет можно просматривать варианты и выполнять к ним запросы, необходимо выполнить повторную обработку модели.  
  
 Дополнительные сведения о том, как включить детализацию, см. в статьях [Создание &#40;расширений&#41;](../dmx/create-mining-model-dmx.md)интеллектуального анализа данных, [ &#40;выбор&#41;](../dmx/select-into-dmx.md)расширений интеллектуального анализа данных и DMX- [структуры &#40;&#41;интеллектуального](../dmx/alter-mining-structure-dmx.md)анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *n*  
 Необязательный параметр. Целое число, указывающее количество возвращаемых строк.  
  
 *список выражений*  
 Список выражений с разделителями-запятыми. Выражение может включать в себя идентификаторы столбцов, определяемые пользователем функции, функции VBA и пр.  
  
 Чтобы включить столбец структуры, не включенный в модель интеллектуального анализа данных, используйте функцию `StructureColumn('<structure column name>')`.  
  
 *model*  
 Идентификатор модели.  
  
 *выражение условия*  
 Условие ограничения значений, возвращаемых из списка столбцов.  
  
 *expression*  
 Необязательный параметр. Выражение, возвращающее скалярное значение.  
  
## <a name="remarks"></a>Примечания  
 Если детализация включена как для модели, так и для структуры интеллектуального анализа данных, пользователи, являющиеся членами роли с разрешением на детализацию модели и структуры, могут обращаться к столбцам в структуре интеллектуального анализа данных, которые не включены в модель. Таким образом, чтобы защитить конфиденциальные данные или персональные данные, необходимо создать представление источника данных для маскирования персональных данных и предоставить **AllowDrillthrough** разрешение для структуры интеллектуального анализа данных только в том случае, если это необходимо.  
  
 Функция [Lag &#40;для&#41; расширений интеллектуального анализа данных](../dmx/lag-dmx.md) может использоваться с моделями временных рядов для возврата или фильтрации временной задержки между каждым вариантом и начальным временем.  
  
 Использование функции [IsInNode &#40;расширений&#41; интеллектуального анализа данных](../dmx/isinnode-dmx.md) в предложении **WHERE** возвращает только те варианты, которые связаны с узлом, указанным в столбце NODE_UNIQUE_NAME набора строк схемы.  
  
## <a name="examples"></a>Примеры  
 Приведенные ниже примеры основаны на целевой корреспонденции структуры интеллектуального анализа [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]данных, основанной на базе и связанных с ней моделях интеллектуального анализа. Дополнительные сведения см. в разделе [учебник по основам интеллектуального анализа данных](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
### <a name="example-1-drillthrough-to-model-cases-and-structure-columns"></a>Пример 1. Детализация до вариантов модели и столбцов структуры  
 В следующем примере возвращаются столбцы для всех вариантов, использованных для проверки модели «Целевая рассылка». Если структура интеллектуального анализа данных, на основе которой построена модель, не имеет контрольного проверочного набора данных, данный запрос не возвращает вариантов. Кроме того, можно использовать список выражений, чтобы возвращать только необходимые столбцы.  
  
```  
SELECT * FROM [TM Decision Tree].Cases  
WHERE IsTestCase();  
```  
  
### <a name="example-2-drillthrough-to-training-cases-in-a-specific-node"></a>Пример 2. Детализация обучающих вариантов в определенном узле  
 В следующем примере возвращаются только столбцы, использованные для обучения кластера 2. Узел кластера 2 имеет значение «002» в столбце NODE_UNIQUE_NAME. Кроме того, в этом примере возвращается один столбец структуры [Customer Key], который не входил в модель интеллектуального анализа данных. Этому столбцу присваивается псевдоним `CustomerID`. Обратите внимание, что имя столбца структуры передается как строковое значение, поэтому его следует заключать в кавычки, а не в скобки.  
  
```  
SELECT StructureColumn('Customer Key') AS CustomerID, *   
FROM [TM_Clustering].Cases  
WHERE IsTrainingCase()  
AND IsInNode('002')  
```  
  
 Чтобы вернуть столбец структуры, необходимы разрешения на детализацию как для модели, так и для структуры интеллектуального анализа данных.  
  
> [!NOTE]  
>  Детализация поддерживается не всеми типами моделей интеллектуального анализа данных. Дополнительные сведения о моделях, поддерживающих детализацию, см. в статье [запросы &#40;детализации интеллектуальный анализ&#41;данных](https://docs.microsoft.com/analysis-services/data-mining/drillthrough-queries-data-mining).  
  
## <a name="see-also"></a>См. также  
 [ВЫБОР &#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&#41;](../dmx/select-dmx.md)   
 [Расширения &#40;интеллектуального анализа&#41; данных инструкции расширений интеллектуального анализа данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения &#40;интеллектуального анализа&#41; данных инструкции DMX-операций с данными](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
