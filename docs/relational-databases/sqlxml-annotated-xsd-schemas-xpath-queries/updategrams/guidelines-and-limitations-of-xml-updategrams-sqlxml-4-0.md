---
title: "Рекомендации и ограничения диаграмм обновления XML (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a8396c837707ad9560aebb2e86617df8bfb2b69
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Правила и ограничения диаграмм обновления XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
При использовании диаграмм обновления XML следует помнить следующее.  
  
-   При использовании диаграммы обновления для операции вставки с единственной парой из  **\<перед >** и  **\<после >** блоки,  **\<перед >** можно опустить блок. И наоборот, при операции удаления  **\<после >** можно опустить блок.  
  
-   При использовании диаграммы обновления с несколькими  **\<перед >** и  **\<после >** блоков в  **\<синхронизации >** тег, оба  **\<перед >** блоки и  **\<после >** блоки должен быть указан в виде  **\<перед >** и  **\<после >** пары.  
  
-   Обновления в диаграммах обновления применяются к XML-представлению, предоставленному схемой XML. Поэтому для успешного сопоставления по умолчанию следует либо указать имя файла схемы в диаграмме обновления, либо, если имя файла не указано, имена элемента и атрибута должны совпадать с именами таблицы и столбца базы данных.  
  
-   SQLXML 4.0 требует, чтобы все значения столбцов в диаграмме обновления были бы явно сопоставлены в схеме (XDR или XSD), предоставленной для создания XML-представления для дочерних элементов. Это поведение отличается от более ранних версиях SQLXML, в которой допустимое значение для столбца не сопоставлены в схеме, если оно являлось частью внешнего ключа в **SQL: Relationship** заметки. (Следует отметить, что подобное изменение не повлияет на распространение значений первичного ключа на дочерние элементы, которое по-прежнему происходит в SQLXML 4.0, если явно не указано значение для дочернего элемента.  
  
-   При использовании диаграммы обновления для изменения данных в двоичном столбце (такие как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **изображения** тип данных), необходимо предоставить схему сопоставления, в котором [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных (например, **SQL: DataType = «изображения»** ) и тип данных XML (например, **DT: Type = «binhex»** или **DT: Type = "binbase64**) должен быть указан. Данные для двоичного столбца должно быть указано в диаграмме обновления; **заметки SQL: URL-encode** заметка, указанная в схеме сопоставления учитывается в диаграмме обновления.  
  
-   При написании схемы XSD, если значение, заданное для **SQL: Relation** или **SQL: field** заметка содержит специальный символ, такой как символ пробела (например, в «Order Details» Имя таблицы), это значение должно быть заключено в скобки (например, «[Order Details]»).  
  
-   При использовании диаграмм обновления цепочки связей не поддерживаются. Например, если таблицы А и С связаны через цепочку связей, которая использует таблицу В, при попытке запустить и выполнить диаграмму обновления возникнет следующая ошибка:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Даже если как схема, так и диаграмма обновления верны и правильно оформлены, эта ошибка возникнет, если имеется цепочка связей.  
  
-   Диаграммы обновления не допускают передачи **изображения** тип данных в качестве параметров во время обновления.  
  
-   Типы больших двоичных объектов (BLOB) как **text, ntext** и изображения не должен использоваться в  **\<перед >** блока в при работе с диаграммами обновления, так как это будет включать их для использования в Управление параллелизмом. Это может вызвать проблемы в работе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из-за ограничений, налагаемых на сравнение для типов больших двоичных объектов. Например, ключевое слово LIKE используется в предложении WHERE для сравнения столбцов **текст** типа данных; Однако такое сравнение завершится ошибкой в случае с типами больших двоичных ОБЪЕКТОВ, где размер данных больше, чем 8 КБ.  
  
-   Специальные символы в **ntext** данных может вызвать проблемы с SQLXML 4.0 из-за ограничений, налагаемых на сравнение типов больших двоичных ОБЪЕКТОВ. Например, использование «[Serializable]» в  **\<перед >** блок диаграмм обновления при проверке столбца параллелизма **ntext** типа будут завершаться следующей SQLOLEDB Описание ошибки:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности диаграмм обновления &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  