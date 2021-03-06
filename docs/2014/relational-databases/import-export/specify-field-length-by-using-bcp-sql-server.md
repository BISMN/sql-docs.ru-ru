---
title: Указание длины поля с помощью программы bcp (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- default field lengths
- field length [SQL Server]
- data formats [SQL Server], field length
- bcp utility [SQL Server], field length
ms.assetid: 240f33ca-ef4a-413a-a4de-831885cb505b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: abb451611f7e102e9167561ef2c3a4b64e00fb12
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66011843"
---
# <a name="specify-field-length-by-using-bcp-sql-server"></a>Указание длины поля с помощью программы bcp (SQL Server)
  Длина поля указывает максимальное количество символов, необходимых для представления данных в символьном формате. Длина поля известна заранее, если данные хранятся в собственном формате, например значение типа `int` занимает 4 байта. Если указано значение 0 в качестве значения длины префикса **bcp** команда запрашивает длину поля, длины поля по умолчанию и влияние длины поля на хранении данных в файлах данных, которые содержат `char` данных.  
  
## <a name="the-bcp-prompt-for-field-length"></a>Запрос командой bcp значения длины поля  
 Если интерактивная команда **bcp** содержит параметр **in** или **out** без параметра файла форматирования ( **-f**) либо параметра формата данных ( **-n**, **-c**, **-w** или **-N**), то команда запрашивает длину каждого поля данных следующим образом:  
  
 `Enter length of field <field_name> [<default>]:`  
  
 Пример этого запроса в контексте см. в разделе [Указание форматов данных для совместимости с помощью программы bcp (SQL Server)](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).  
  
> [!NOTE]  
>  После интерактивного заполнения всех полей в команде **bcp** появится запрос на сохранение введенных ответов для каждого поля в файле форматирования в формате, отличном от XML. Дополнительные сведения о файлах форматирования в формате, отличном от XML, см. в разделе [Файлы формата, отличные от XML (SQL Server)](xml-format-files-sql-server.md).  
  
 Будут ли командные строки **bcp** выводить запросы для указания значений длины полей, зависит от нескольких факторов, как указано ниже.  
  
-   Если происходит копирование данных таких типов, которые не имеют постоянной длины, и задана длина префикса, равная 0, то **bcp** выводит приглашения для указания длины полей.  
  
-   Если происходит преобразование несимвольных данных в символьные данные, то **bcp** предлагает по умолчанию длину поля, достаточно большую для сохранения данных.  
  
-   Если по своему типу хранилище файлов не является символьным, то команда **bcp** не выводит приглашения для указания длины полей. Данные хранятся в собственном представлении данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (в собственном формате).  
  
## <a name="using-default-field-lengths"></a>Использование значения длины поля по умолчанию  
 В общем случае [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует принимать значения по умолчанию для длины полей, предлагаемые командой **bcp**. Использование значений длины поля по умолчанию при создании файла символьных данных помогает избежать усечения данных и возникновения ошибок переполнения.  
  
 При указании некорректного значения длины поля могут возникнуть проблемы. Например, если при копировании числовых данных была задана слишком малая длина поля, программа **bcp** выдает сообщение о переполнении, а копирование данных не выполняется. Кроме того Если вы экспортируете `datetime` данных и задана длина поля меньше, чем 26 байт для символьной строки, **bcp** производит усечение данных без сообщения об ошибке.  
  
> [!IMPORTANT]  
>  При использовании размера, заданного по умолчанию, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] считывает всю строку. В некоторых случаях использование значения длины поля по умолчанию приводит к возникновению ошибки «неожиданный конец файла». Как правило, эта ошибка происходит при `money` и `datetime` типы данных, когда происходит только часть ожидаемого поля в файле данных; например, если `datetime` значение *мм*/*дд*  / *гг* указано без компонента времени и, следовательно, меньше, чем длина 24 символов `datetime` значение в `char` формате. Чтобы избежать указанной ошибки типов, необходимо использовать признаки конца поля или файлы данных фиксированной длины, либо изменить значение длины поля по умолчанию.  
  
### <a name="default-field-lengths-for-character-file-storage"></a>Значения длины поля по умолчанию для файлов символьных данных  
 В представленной ниже таблице приведены значения длины поля для данных, хранимых в символьной форме. Данные, которые могут и не могут принимать значение NULL, имеют одинаковую длину поля.  
  
|Тип данных|Длина по умолчанию (в символах)|  
|---------------|-----------------------------------|  
|`char`|Длина, определенная для столбца|  
|`varchar`|Длина, определенная для столбца|  
|`nchar`|Удвоенная длина, определенная для столбца|  
|`nvarchar`|Удвоенная длина, определенная для столбца|  
|`Text`|0|  
|`ntext`|0|  
|`bit`|1|  
|`binary`|Удвоенная длина, определенная для столбца + 1|  
|`varbinary`|Удвоенная длина, определенная для столбца + 1|  
|`image`|0|  
|`datetime`|24|  
|`smalldatetime`|24|  
|`float`|30|  
|`real`|30|  
|`int`|12|  
|`bigint`|19|  
|`smallint`|7|  
|`tinyint`|5|  
|`money`|30|  
|`smallmoney`|30|  
|`decimal`|41*|  
|`numeric`|41*|  
|`uniqueidentifier`|37|  
|`timestamp`|17|  
|`varchar(max)`|0|  
|`varbinary(max)`|0|  
|`nvarchar(max)`|0|  
|определяемый пользователем тип|Длина столбца определенного пользователем типа (UDT)|  
|XML|0|  
  
 \*Дополнительные сведения о `decimal` и `numeric` типов данных, см. в разделе [decimal и numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).  
  
> [!NOTE]  
>  Столбец данных типа `tinyint` может содержать целые значения от 0 до 255; максимальное количество символов, необходимых для представления чисел данного диапазона, равно 3 (для записи чисел от 100 до 255).  
  
### <a name="default-field-lengths-for-native-file-storage"></a>Значения длины поля по умолчанию для файлов собственных данных  
 В представленной ниже таблице приведены значения длины поля для данных, хранимых в собственном формате. Данные, которые могут и не могут принимать значение NULL, имеют одинаковую длину поля, а символьные данные всегда хранятся в собственном формате.  
  
|Тип данных|Длина по умолчанию (в символах)|  
|---------------|-----------------------------------|  
|`bit`|1|  
|`binary`|Длина, определенная для столбца|  
|`varbinary`|Длина, определенная для столбца|  
|`image`|0|  
|`datetime`|8|  
|`smalldatetime`|4|  
|`float`|8|  
|`real`|4|  
|`int`|4|  
|`bigint`|8|  
|`smallint`|2|  
|`tinyint`|1|  
|`money`|8|  
|`smallmoney`|4|  
|`decimal` <sup>1</sup>|<sup>*</sup>|  
|`numeric` <sup>1</sup>|<sup>*</sup>|  
|`uniqueidentifier`|16|  
|`timestamp`|8|  
  
 <sup>1</sup> Дополнительные сведения о `decimal` и `numeric` типов данных, см. в разделе [decimal и numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).  
  
 Во всех перечисленных случаях для создания файла данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , занимающего наименьшее количество памяти, необходимо использовать префикс, задающий тип файлов и длину поля по умолчанию.  
  
## <a name="see-also"></a>См. также  
 [Программа bcp](../../tools/bcp-utility.md)   
 [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)   
 [Определение признаков конца поля и строки (SQL Server)](specify-field-and-row-terminators-sql-server.md)   
 [Определение длины префикса в файлах данных с помощью программы bcp (SQL Server)](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)   
 [Указание типа файлового хранилища с помощью программы bcp (SQL Server)](specify-file-storage-type-by-using-bcp-sql-server.md)   
 [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
  
