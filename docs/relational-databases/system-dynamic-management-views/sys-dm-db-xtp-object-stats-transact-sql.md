---
title: "sys.dm_db_xtp_object_stats (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_object_stats_TSQL
- sys.dm_db_xtp_object_stats
- dm_db_xtp_object_stats
- sys.dm_db_xtp_object_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_object_stats dynamic management view
ms.assetid: 07300b59-3cab-4d3e-8138-5ea8f584f88f
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7610e24b87a2a6dff0ffefbd5a786acf8191dca5
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmdbxtpobjectstats-transact-sql"></a>sys.dm_db_xtp_object_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Возвращает количество строк, затронутых операциями, выполненными с каждым объектом [!INCLUDE[hek_2](../../includes/hek-2-md.md)] с момента последнего запуска базы данных. Статистика обновляется при выполнении операции независимо от того, была ли транзакция зафиксирована, или выполнен ее откат.  
  
 С помощью sys.dm_db_xtp_object_stats можно определить, какие оптимизированные для памяти таблицы больше всего изменяются. Можно удалить индексы в таблицах, которые не используются или используются редко, поскольку каждый индекс влияет на производительность. При наличии хэш-индексов следует периодически анализировать значение bucket-count. Дополнительные сведения см. в разделе [Determining the Correct Bucket Count for Hash Indexes](http://msdn.microsoft.com/library/6d1ac280-87db-4bd8-ad43-54353647d8b5).  
  
 С помощью sys.dm_db_xtp_object_stats можно определить, в каких оптимизированных для памяти таблицах есть конфликты между операциями записи, которые могут повлиять на производительность приложения. Например, если имеется логика повтора транзакций, одна инструкция может выполняться несколько раз. Кроме того, с помощью этой информации можно определять таблицы (а соответственно, и бизнес-логику), для которых требуется обработка конфликтов операций записи.  
  
 Представление содержит одну строку для каждой таблицы, оптимизированной для памяти, в базе данных.  
  
 Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|Идентификатор объекта.|  
|row_insert_attempts|**bigint**|Количество строк, вставленных в таблицу с момента последнего перезапуска базы данных зафиксированными или прерванными транзакциями.|  
|row_update_attempts|**bigint**|Количество строк, обновленных в таблице с момента последнего перезапуска базы данных зафиксированными или прерванными транзакциями.|  
|row_delete_attempts|**bigint**|Количество строк, удаленных из таблицы с момента последнего перезапуска базы данных зафиксированными или прерванными транзакциями.|  
|write_conflicts|**bigint**|Количество конфликтов записи, возникших с момента последнего перезапуска базы данных.|  
|unique_constraint_violations|**bigint**|Число нарушений ограничений уникальности, произошедших с момента последнего перезапуска базы данных.|  
|object_address|**varbinary(8)**|Только для внутреннего применения.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE на текущую базу данных.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления таблиц, оптимизированных для памяти &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  