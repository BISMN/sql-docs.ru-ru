---
title: sys. dm_resource_governor_configuration (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_resource_governor_configuration_TSQL
- dm_resource_governor_configuration
- sys.dm_resource_governor_configuration
- sys.dm_resource_governor_configuration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_configuration dynamic management view
ms.assetid: c89aab6a-0434-4ce6-af8c-f8a1a3284e38
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d37a6ad94056007dd7c941d53ce52b4b84498a9
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983301"
---
# <a name="sysdm_resource_governor_configuration-transact-sql"></a>sys.dm_resource_governor_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку, содержащую текущее состояние конфигурации, хранимой в памяти, для регулятора ресурсов.  
  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**int**|Идентификатор функции-классификатора, используемой в настоящий момент регулятором ресурсов. Возвращает значение 0, если ни одна функция не используется. Не допускает значение NULL.<br /><br /> **Примечание.** Эта функция используется для классификации новых запросов и использует правила для маршрутизации этих запросов в соответствующую группу рабочей нагрузки. Дополнительные сведения см. в разделе [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) (Регулятор ресурсов).|  
|is_reconfiguration_pending|**бит**|Указывает, что изменения в группе или пуле внесены с помощью инструкции ALTER RESOURCE GOVERNOR RECONFIGURE, но не были применены к конфигурации, хранимой в памяти. Возвращается одно из следующих значений.<br /><br /> 0 — Инструкция перенастройки не требуется.<br /><br /> 1 — Для применения изменений конфигурации, находящихся в статусе ожидания, необходима инструкция перенастройки или перезапуск сервера.<br /><br /> **Примечание.** Возвращаемое значение всегда равно 0, если Resource Governor отключено.<br /><br /> Не допускает значение NULL.|  
|max_outstanding_io_per_volume|**int**|**Область применения**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и более поздних версий.<br /><br /> Максимальное число невыполненных операций ввода-вывода в расчете на том.|  
  
## <a name="remarks"></a>Remarks  
 Данное динамическое административное представление отображает конфигурацию, хранимую в памяти. Чтобы просмотреть сохраненные метаданные конфигурации, используйте соответствующее представление каталога.  
  
 Следующий пример иллюстрирует получение и сравнение хранимых значений метаданных и значений из памяти настройки регулятора ресурсов.  
  
```  
USE master;  
go  
-- Get the stored metadata.  
SELECT   
object_schema_name(classifier_function_id) AS 'Classifier UDF schema in metadata',   
object_name(classifier_function_id) AS 'Classifier UDF name in metadata'  
FROM   
sys.resource_governor_configuration;  
go  
-- Get the in-memory configuration.  
SELECT   
object_schema_name(classifier_function_id) AS 'Active classifier UDF schema',   
object_name(classifier_function_id) AS 'Active classifier UDF name'  
FROM   
sys.dm_resource_governor_configuration;  
go  
```  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW SERVER STATE.  
  
## <a name="see-also"></a>См. также статью  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys. resource_governor_configuration &#40;  Transact-&#41; SQL](../../relational-databases/system-catalog-views/sys-resource-governor-configuration-transact-sql.md)  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)  
  
  

