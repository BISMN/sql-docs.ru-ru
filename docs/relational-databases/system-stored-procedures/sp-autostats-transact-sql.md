---
title: sp_autostats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_autostats_TSQL
- sp_autostats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_autostats
ms.assetid: d1df8c15-ee73-49eb-9d13-6e98943c3e38
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e3fdb095ed869ba2e8f060bdba7a3dc9db81a405
ms.sourcegitcommit: 8c1c6232a4f592f6bf81910a49375f7488f069c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2019
ms.locfileid: "70026250"
---
# <a name="sp_autostats-transact-sql"></a>Хранимая процедура sp_autostats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отображает или изменяет параметр автоматического обновления статистики AUTO_UPDATE_STATISTICS для индекса, объекта статистики, таблицы или индексированного представления.  
  
 Дополнительные сведения о параметре AUTO_UPDATE_STATISTICS см. в разделе [ &#40;параметры ALTER DATABASE SET Transact-&#41; SQL](../../t-sql/statements/alter-database-transact-sql-set-options.md) и [Statistics](../../relational-databases/statistics/statistics.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_autostats [ @tblname = ] 'table_or_indexed_view_name'   
    [ , [ @flagc = ] 'stats_flag' ]   
    [ , [ @indname = ] 'statistics_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @tblname = ] 'table_or_indexed_view_name'`Имя таблицы или индексированного представления, для которого отображается параметр AUTO_UPDATE_STATISTICS. *table_or_indexed_view_name* имеет тип **nvarchar (776)** и не имеет значения по умолчанию.  
  
`[ @flagc = ] 'stats_flag'`Обновляет параметр AUTO_UPDATE_STATISTICS на одно из следующих значений:  
  
 **ВКЛ** . = ВКЛ.  
  
 **ВЫКЛ** . = ВЫКЛ.  
  
 Если *stats_flag* не указан, отобразится текущее значение параметра AUTO_UPDATE_STATISTICS. *stats_flag* имеет тип **varchar (10)** и значение по умолчанию NULL.  
  
`[ @indname = ] 'statistics_name'`Имя статистики для вывода или обновления параметра AUTO_UPDATE_STATISTICS в. Чтобы отобразить статистику для индекса, можно использовать имя индекса. Имя индекса совпадает с именем соответствующего объекта статистики.  
  
 *statistics_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если указан параметр *stats_flag* , **sp_autostats** сообщает о выполненном действии, но не возвращает результирующий набор.  
  
 Если *stats_flag* не указан, **sp_autostats** возвращает следующий результирующий набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Index Name**|**varchar (60)**|Имя индекса или статистики.|  
|**АВТОСТАТИСТИКА**|**varchar (3)**|Текущее значение параметра AUTO_UPDATE_STATISTICS.|  
|**Последнее обновление**|**datetime**|Дата последнего обновления статистики.|  
  
 Результирующий набор для таблицы или индексированного представления включает статистику, созданную для индексов, статистику по отдельным столбцам, созданную с помощью параметра AUTO_CREATE_STATISTICS и статистики, созданной с помощью инструкции [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) .  
  
## <a name="remarks"></a>Примечания  
 Если указанный индекс отключен или указанная таблица имеет отключенный кластеризованный индекс, выводится сообщение об ошибке.  
  
 Параметр AUTO_UPDATE_STATISTICS всегда имеет значение OFF для таблиц с оптимизацией памяти.  
  
## <a name="permissions"></a>Разрешения  
 Для изменения параметра AUTO_UPDATE_STATISTICS требуется членство в предопределенной роли базы данных **db_owner** или разрешение ALTER для *table_name*. Для вывода параметра AUTO_UPDATE_STATISTICS требуется членство в роли **Public** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-display-the-status-of-all-statistics-on-a-table"></a>A. Отображение состояния всей статистики по таблице  
 Следующий код выводит состояние всей статистики по таблице `Product`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_autostats 'Production.Product';  
GO  
```  
  
### <a name="b-enable-auto_update_statistics-for-all-statistics-on-a-table"></a>Б. Включение параметра AUTO_UPDATE_STATISTICS для всей статистики по таблице  
 Следующий код включает параметр AUTO_UPDATE_STATISTICS для всей статистики по таблице `Product`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_autostats 'Production.Product', 'ON';  
GO  
```  
  
### <a name="c-disable-auto_update_statistics-for-a-specific-index"></a>В. Отключение параметра AUTO_UPDATE_STATISTICS для конкретного индекса  
 В следующем примере отключается параметр AUTO_UPDATE_STATISTICS для индекса `AK_Product_Name` по таблице `Product`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_autostats 'Production.Product', 'OFF', AK_Product_Name;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Статистика](../../relational-databases/statistics/statistics.md)   
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [Ядро СУБД хранимых &#40;процедур TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS (Transact-SQL)](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_createstats (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS (Transact-SQL)](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
