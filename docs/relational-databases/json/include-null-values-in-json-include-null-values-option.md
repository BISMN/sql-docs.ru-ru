---
title: INCLUDE_NULL_VALUES для включения значений Null в JSON
ms.date: 06/02/2016
ms.prod: sql
ms.reviewer: genemi
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- INCLUDE_NULL_VALUES (FOR JSON)
ms.assetid: 06873768-3778-4ed8-a1db-61758726bda0
author: jovanpop-msft
ms.author: jovanpop
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2cbb9f2dc30ab02f77fafadf39d8c1c6426de708
ms.sourcegitcommit: 15fe0bbba963d011472cfbbc06d954d9dbf2d655
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2019
ms.locfileid: "74095752"
---
# <a name="include-null-values-in-json---include_null_values-option"></a>INCLUDE_NULL_VALUES для включения значений Null в JSON
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Чтобы выходные данные JSON предложения **FOR JSON** содержали значения NULL, укажите параметр **INCLUDE_NULL_VALUES** .  
  
 Если параметр **INCLUDE_NULL_VALUES** не указан, в выходные данные JSON не будут включены те свойства, для которых в результатах запроса указаны значения NULL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показаны выходные данные предложения **FOR JSON** с параметром **INCLUDE_NULL_VALUES** и без него.  
  
|Без параметра **INCLUDE_NULL_VALUES**|С параметром **INCLUDE_NULL_VALUES**|  
|--------------------------------------------------|-----------------------------------------------|  
|`{    "name": "John",    "surname": "Doe" }`|`{    "name": "John",    "surname": "Doe",    "age": null,    "phone": null }`|  
  
 Вот другой пример предложения **FOR JSON** с параметром **INCLUDE_NULL_VALUES** .  
  
 **Запрос**  
  
```sql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO, INCLUDE_NULL_VALUES    
```  
  
 **Результат**  
  
```json  
[{
    "name": "John",
    "surname": null
}, {
    "name": "Jane",
    "surname": "Doe"
}] 
```  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующих видео.

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 и поддержка JSON)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Использование JSON в SQL Server 2016 и базе данных SQL Azure)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON как мост между NoSQL и реляционными решениями)

## <a name="see-also"></a>См. также:  
 [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  
