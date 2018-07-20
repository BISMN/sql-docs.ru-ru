---
title: Запросы FOR XML AUTO возвращают ссылки на производные таблицы в режиме совместимости 90 и выше | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR XML AUTO [SQL Server]
ms.assetid: 10c32f06-f7e1-40e0-8f79-6d921f2bef1d
caps.latest.revision: 15
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 578222ffcdfe7d9b73205e64528441a8300f1959
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321744"
---
# <a name="for-xml-auto-queries-return-derived-table-references-in-90-or-later-compatibility-modes"></a>Запросы в режиме FOR XML AUTO возвращают ссылки на производные таблицы в режиме совместимости 90 и выше
  В режиме совместимости базы данных 90 и выше запросы FOR XML, выполняемые в режиме AUTO, возвращают ссылки на псевдонимы производных таблиц. В режиме совместимости базы данных 80 запросы FOR XML AUTO возвращают ссылки на базовые таблицы, определяющие производную таблицу.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Например, рассмотрим следующую таблицу.  
  
```  
CREATE TABLE Test(id int);  
INSERT INTO Test VALUES(1);  
INSERT INTO Test VALUES(2);  
```  
  
 Следующий запрос, содержащий производную таблицу, при уровнях совместимости 80, 90 и выше вернет разные результаты.  
  
```  
SELECT * FROM   
   (SELECT a.id AS a, b.id AS b   
    FROM Test a JOIN Test b ON a.id=b.id)  
AS DerivedTest   
FOR XML AUTO;  
```  
  
 При уровне совместимости 80 запрос возвращает следующие результаты. Результат содержит ссылки на псевдонимы базовой таблицы `a` и `b` производной таблицы, а не на псевдоним производной таблицы.  
  
```  
<a a="1"><b b="1"/></a><a a="2"><b b="2"/></a>  
```  
  
 При уровне совместимости 90 и выше запрос возвращает ссылки на псевдоним производной таблицы `DerivedTest`, а не на базовую таблицу.  
  
```  
<DerivedTest a="1" b="1"/><DerivedTest a="2" b="2"/>  
```  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Внесите в приложения необходимые изменения, чтобы учесть изменения в результатах запросов FOR XML AUTO, содержащих производные таблицы и выполняемых на уровне совместимости 90 и выше.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  