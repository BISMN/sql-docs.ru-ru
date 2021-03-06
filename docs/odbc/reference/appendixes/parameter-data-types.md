---
title: Типы данных параметров | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.openlocfilehash: 5140c69184332b1760859421b7e802a5163a0f09
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100598"
---
# <a name="parameter-data-types"></a>Типы данных параметров
Несмотря на то, что каждый параметр указан с **SQLBindParameter** имеет определенный тип данных SQL, параметры в инструкции SQL с помощью имеют внутренний тип данных. Таким образом маркеры параметров могут быть включены в инструкцию SQL, только в том случае, если их типы данных может быть выведен из другой операнд в инструкции. Например в арифметического выражения, такие как? + COLUMN1, тип данных параметра может быть определено из тип данных именованного столбца, представленного COLUMN1. Приложение не может использовать маркер параметра, если невозможно определить тип данных.  
  
 В следующей таблице описаны как определяется типом данных для нескольких типов параметров, в соответствии с SQL-92. Более полную спецификацию на вывод типа тип параметра, если используются другие предложения SQL см. в спецификации SQL-92.  
  
|Расположение параметра|Предполагается, что тип данных|  
|---------------------------|-----------------------|  
|Один из операндов бинарного оператора сравнения или арифметических операций|Так же, как другой операнд|  
|Первый операнд в **BETWEEN** предложение|Так же, как второй операнд|  
|Второй или третий операнд в **BETWEEN** предложение|Так же, как первый операнд|  
|Выражение, используемое с **IN**|Так же, как первое значение или столбец результата вложенного запроса|  
|Значение, используемое в **IN**|Так же, как выражение или первого значения, если имеется маркер параметра в выражении|  
|Значение шаблона, используемого с **как**|VARCHAR|  
|Значение обновлений с **обновления**|Так же, как столбец обновления|
