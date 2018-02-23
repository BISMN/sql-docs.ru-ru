---
title: "sys.dm_column_store_object_pool (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
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
dev_langs:
- TSQL
ms.assetid: a8a58ca7-0a7d-4786-bfd9-e8894bd345dd
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c77d44fd04f328cad314b50c16e6f70970c5e9d8
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmcolumnstoreobjectpool-transact-sql"></a>sys.dm_column_store_object_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Возвращает количество различных типов объектов использование пула памяти для объектов индекса columnstore.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|`database_id`|`int`|Идентификатор базы данных. Уникален в пределах экземпляра базы данных SQL Server или сервер базы данных Azure SQL. |  
|`object_id`|`int`|Идентификатор объекта. Объект является одним из object_types. | 
|`index_id`|`int`|Идентификатор индекса columnstore.|  
|`partition_number`|`bigint`|Номер секции внутри индекса или кучи (нумерация начинается с 1). Каждая таблица или представление имеет по крайней мере одну секцию.| 
|`column_id`|`int`|Идентификатор столбца columnstore. Это значение NULL для DELETE_BITMAP.| 
|`row_group_id`|`int`|Идентификатор группы строк.|
|`object_type`|`smallint`|1 = COLUMN_SEGMENT<br /><br /> 2 = COLUMN_SEGMENT_PRIMARY_DICTIONARY<br /><br /> 3 = COLUMN_SEGMENT_SECONDARY_DICTIONARY<br /><br /> 4 = COLUMN_SEGMENT_BULKINSERT_DICTIONARY<br /><br /> 5 = COLUMN_SEGMENT_DELETE_BITMAP|  
|`object_type_desc`|`nvarchar(60)`|COLUMN_SEGMENT — сегмента столбца. `object_id`Идентификатор сегмента. Сегмент хранит все значения для одного столбца в одну группу строк. Например если таблица содержит 10 столбцов, существует 10 сегментов столбца группы строк. <br /><br /> COLUMN_SEGMENT_PRIMARY_DICTIONARY — глобальные словарь, который содержит сведения о подстановки для всех сегментов столбцов в таблице.<br /><br /> COLUMN_SEGMENT_SECONDARY_DICTIONARY - локальный словарь, связанный с одним столбцом.<br /><br /> COLUMN_SEGMENT_BULKINSERT_DICTIONARY — другое представление глобальных словаря. Это обеспечивает обратный поиск значения dictionary_id. Используется для создания сжатых сегментов в рамках кортежей или массовой загрузки.<br /><br /> COLUMN_SEGMENT_DELETE_BITMAP — удаляет точечного рисунка, который отслеживает сегмента. Нет одного точечного рисунка delete на каждую секцию.|  
|`access_count`|`int`|Число чтения или записи обращается к этому объекту.|  
|`memory_used_in_bytes`|`bigint`|Объем памяти, используемый этим объектом в пул объектов.|  
|`object_load_time`|`datetime`|Часы для время при object_id была переведена в режим в пуле.|  
  
## <a name="permissions"></a>Разрешения  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  

 
## <a name="see-also"></a>См. также  
  
 [Динамические административные представления и функции, связанные с индексами &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Наблюдение и настройка производительности](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  