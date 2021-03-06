---
title: sys. workload_management_workload_groups (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 76b5b09a07189db127c970e75dac2894fdbea1ae
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633448"
---
# <a name="sysworkload_management_workload_groups-transact-sql"></a>sys. workload_management_workload_groups (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

 Возвращает сведения о группах рабочей нагрузки.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|
|group_id|**int**|Уникальный идентификатор группы рабочей нагрузки. Не допускает значение NULL.||
|имя|**sysname**|Имя группы рабочей нагрузки. Должен быть уникальным для экземпляра.  Не допускает значение NULL.||
|importance|**nvarchar(128)**|— Это относительная важность запроса в этой группе рабочей нагрузки и в группах рабочей нагрузки для общих ресурсов. Не допускает значение NULL.|Low, below_normal, обычная (по умолчанию), above_normal, High||
|min_percentage_resource|**tinyint**|Гарантированный объем ресурсов для запросов в группе рабочей нагрузки. Ресурсы не используются совместно с другими группами рабочей нагрузки. Не допускает значение NULL.||
|cap_percentage_resource|**tinyint**|Жесткое ограничение выделения ресурсов в процентах для запросов в группе рабочей нагрузки. Ограничивает максимальное количество ресурсов, выделенных для указанного уровня. Диапазон допустимых значений — от 1 до 100.||
|request_min_resource_grant_percent|**Decimal (5, 2)**|Указывает минимальный объем ресурсов, выделенных запросу. Допустимый диапазон значений — от 0,75 до 100.||
|request_max_resource_grant_percent |**Decimal (5, 2)**|Указывает максимальный объем ресурсов, выделенных для запроса.||
|query_execution_timeout_sec|**int**|Время выполнения в секундах, которое было разрешено до отмены запроса.  Запросы нельзя отменить после того, как они достигли фазы возврата выполнения.  query_execution_timeout_sec не включает время, затраченное на очередь.|
|query_wait_timeout_sec|**int**|ВНУТРИКЛАСТЕРНЫХ||
|create_time|**datetime**|Время создания группы рабочей нагрузки. Не допускает значение NULL.||
modify_time|**datetime**|Время последнего изменения группы рабочей нагрузки. Не допускает значение NULL.||
|&nbsp;||||
  
## <a name="permissions"></a>Разрешения

Необходимо разрешение VIEW SERVER STATE.

## <a name="next-steps"></a>Следующие шаги

 Список всех представлений каталога для хранилища данных SQL и параллельного хранилища данных см. в статье [представления каталога данных SQL и параллельного](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)хранилища данных. Сведения о создании группы рабочей нагрузки см. в разделе [Создание группы рабочей нагрузки](../../t-sql/statements/create-workload-group-transact-sql.md). Дополнительные сведения о классификации рабочей нагрузки см. в разделе [изоляция рабочей нагрузки](/azure/sql-data-warehouse/sql-data-warehouse-workload-isolation) .
