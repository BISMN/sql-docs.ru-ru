---
title: Операторы (синтаксис многомерных выражений) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5067793ae0f5533a889973e18f7b300914df9092
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892115"
---
# <a name="operators-mdx-syntax"></a>Операторы (синтаксис многомерных выражений)


  В многомерных выражениях операторы выполняют следующие действия:  
  
-   Изменяют данные, постоянно или временно.  
  
-   Выполняют поиск значений или объектов, соответствующих указанному условию.  
  
-   Выполнение операции выбора между значениями или выражениями.  
  
-   Проверяют особые условия перед началом или фиксацией транзакций либо перед выполнением определенных инструкций.  
  
 Многомерные выражения поддерживают операторы, перечисленные в следующей таблице.  
  
|Для выполнения операций этого типа|Использовать|  
|---------------------------------------|---------|  
|Назначения значения переменной или связывания столбцов результирующего набора данных с псевдонимом.|[Операторы присваивания](../mdx/assignment-operators.md)|  
|Сложение, вычитание, умножение, деление.|[Арифметические операторы](../mdx/arithmetic-operators.md)|  
|Проверка истинности условия, такого как AND, OR, NOT и XOR.|[Битовые операторы](../mdx/bitwise-operators.md)|  
|Сравнение значения с другим значением или выражением.|[Операторы сравнения](../mdx/comparison-operators.md)|  
|Или постоянное, или временное объединение двух строк в одну.|[Операторы объединения](../mdx/concatenation-operators.md)|  
|Или постоянное, или временное объединение двух выражений набора в один набор.|[Операторы наборов](../mdx/set-operators.md)|  
|Выполнение операции над одним операндом.|[Унарные операторы](../mdx/unary-operators.md)|  
  
> [!NOTE]  
>  Операции в запросах может выполнять каждый, кто видит в кубе данные, используемые с оператором любого типа. Однако изменить данные невозможно без соответствующих разрешений.  
  
 При использовании нескольких операторов важен порядок, в котором многомерное выражение вычисляет операторы. Подобным образом пользователь операторов может потребовать преобразования одного типа данных в другой тип данных перед вычислением операторов.  
  
## <a name="evaluating-complex-expressions"></a>Вычисление сложных выражений  
 Построить выражение можно, объединив несколько меньших выражений с помощью операторов. В этих сложных выражениях многомерное выражение вычисляет операторы в порядке, основанном на определении приоритета операторов, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]используемого. Многомерное выражение выполняет операторы с высокой очередностью раньше, чем операторы с низкой очередностью.  
  
### <a name="understanding-operator-precedence"></a>Основные сведения об очередности операторов  
 В следующем списке показана очередность операторов, от высшей очередности к низшей. Операторы в одной строке имеют равную очередность и вычисляются слева направо, если иной порядок не задан скобками:  
  
-   IS  
  
-   AS  
  
-   DISTINCT  
  
-   , перечислены ниже.  
  
-   ^  
  
-   /, *  
  
-   +, -  
  
-   EXISTING  
  
-   <>, >=, =, \<=, >, <  
  
-   NOT  
  
-   AND  
  
-   XOR  
  
-   OR  
  
 Дополнительные сведения об операторах в многомерных выражениях см. в разделе [многомерное выражение &#40;&#41;справочника](../mdx/mdx-operator-reference-mdx.md)многомерных выражений.  
  
### <a name="determining-results"></a>Определение результатов  
 При формировании сложного выражения путем объединения простых выражений тип данных результирующего значения определяется правилами для операторов в сочетании с правилами для очередности типов данных.  
  
 Если результатом является символ или значение Юникода, то режим сопоставления результата определяется правилами для операторов в сочетании с очередностью параметров сортировки. Дополнительные сведения о параметрах сортировки см. в разделе [языки и &#40;параметры&#41;сортировки Analysis Services](https://docs.microsoft.com/analysis-services/languages-and-collations-analysis-services).  
  
 Имеются также правила, определяющие точность, масштаб и длину результата на основании данных о точности, масштабе и длине составляющих его простых выражений.  
  
## <a name="converting-data-types"></a>Преобразование типов данных  
 Многомерное выражение неявно преобразует объект в другой тип, если этот объект используется в выражении, требующем данные другого типа. В следующей таблице определены правила преобразования для каждого объекта.  
  
|Исходный тип|Требуемый тип|Преобразование|  
|-------------------|-----------------|----------------|  
|Level|Присвойте параметру|\<уровень >. Members|  
|Иерархия|Член|\<Иерархия >. DefaultMember|  
|Член|Кортеж|(\<> Членов)|  
|Кортеж|Член|\<кортеж >. Item (0)|  
|Кортеж|скалярная|\<кортеж >. Value|  
  
## <a name="see-also"></a>См. также  
 [Многомерное выражение &#40;для ссылки на оператор многомерных выражений&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Многомерные выражения &#40;элементов СИНТАКСИСа многомерных выражений&#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
