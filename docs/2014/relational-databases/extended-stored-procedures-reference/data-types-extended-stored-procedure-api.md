---
title: Типы данных (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 715cdc343e3a73781c06977fdb3d3d829d6bf533
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62511654"
---
# <a name="data-types-extended-stored-procedure-api"></a>Типы данных (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Для использования типов данных API расширенных хранимых процедур необходимо включить в программу файл заголовка Srv.h.  
  
|Тип данных|Тип данных SQL Server|Описание|  
|---------------|--------------------------|-----------------|  
|SRVBIGBINARY|`binary`|Данные типа `binary` с длиной от 0 до 8000 байт.|  
|SRVBIGCHAR|`char`|Данные типа `character` с длиной от 0 до 8000 байт.|  
|SRVBIGVARBINARY|`varbinary`|Данные типа `binary` с переменной длиной от 0 до 8000 байт.|  
|SRVBIGVARCHAR|`varchar`|Данные типа `character` с переменной длиной от 0 до 8000 байт.|  
|SRVBINARY|`binary`|Тип данных `binary`.|  
|SRVBIT|`Bit`|Тип данных `bit`.|  
|SRVBITN|`bit null`|Данные типа `bit`, значения NULL допускаются.|  
|SRVCHAR|`char`|Тип данных `character`.|  
|SRVDATETIME|`datetime`|8-байтовые данные типа `datetime`.|  
|SRVDATETIM4|`smalldatetime`|4-байтовое `smalldatetime` тип данных.|  
|SRVDATETIMN|**datetime null**|Данные типа `smalldatetime` или `datetime`, значения NULL допускаются.|  
|SRVDECIMAL|`decimal`|Тип данных `decimal`.|  
|SRVDECIMALN|`decimal null`|Данные типа `decimal`, значения NULL допускаются.|  
|SRVFLT4|`real`|4-байтовое `real` тип данных.|  
|SRVFLT8|`float`|8-байтовые данные типа `float`.|  
|SRVFLTN|`real` &#124; `float null`|Данные типа `real` или `float`, значения NULL допускаются.|  
|SRVIMAGE|`image`|Тип данных `image`.|  
|SRVINT1|`tinyint`|1-байтовое `tinyint` тип данных.|  
|SRVINT2|`smallint`|2-байтовые `smallint` тип данных.|  
|SRVINT4|`int`|4-байтовое `int` тип данных.|  
|SRVINTN|`tinyint` &#124; `smallint` &#124; `int null`|Данные типа `tinyint`, `smallint` или `int`, значения NULL допускаются.|  
|SRVMONEY4|`smallmoney`|4-байтовое `smallmoney` тип данных.|  
|SRVMONEY|`money`|8-байтовые данные типа `money`.|  
|SRVMONEYN|`money` &#124; `smallmoney null`|Данные типа `smallmoney` или `money`, значения NULL допускаются.|  
|SRVNCHAR|**nchar**|Данные типа `character` в Юникоде.|  
|SRVNTEXT|`ntext`|Данные типа `text` в Юникоде.|  
|SRVNUMERIC|`numeric`|Тип данных `numeric`.|  
|SRVNUMERICN|`numeric null`|Данные типа `numeric`, значения NULL допускаются.|  
|SRVNVARCHAR|**nvarchar**|Тип данных Юникода `character` с переменной длиной.|  
|SRVTEXT|`text`|Тип данных `text`.|  
|SRVVARBINARY|`varbinary`|Тип данных `binary` с переменной длиной.|  
|SRVVARCHAR|`varchar`|Тип данных `character` с переменной длиной.|  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409 https://msdn.microsoft.com/security/).  
  
  
