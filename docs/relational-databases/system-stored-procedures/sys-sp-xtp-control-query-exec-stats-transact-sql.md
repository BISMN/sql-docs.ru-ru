---
title: sys.sp_xtp_control_query_exec_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_query_exec_stats_TSQL
- sys.sp_xtp_control_query_exec_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_control_query_exec_stats
ms.assetid: 4838125d-ad1e-479e-b7d2-42655e8f4f02
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd8ee38dc4ac1a8fd3a729d94744d3fd98f78875
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017848"
---
# <a name="sysspxtpcontrolqueryexecstats-transact-sql"></a>sys.sp_xtp_control_query_exec_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Включает сбор статистики запросов для всех скомпилированных в собственном коде хранимых процедур экземпляра или определенных, скомпилированных в собственном коде хранимых процедур.  
  
 При включении сбора статистики производительность снижается. Если требуется устранить неполадки только одной или нескольких скомпилированных в собственном коде хранимых процедур, то включить сбор статистики можно только для этих хранимых процедур.  
  
 Чтобы включить сбор статистики на уровне процедуры для всех скомпилированных хранимых процедур, см. в разделе [sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_xtp_control_query_exec_stats [ [ @new_collection_value = ] collection_value ],  
[ [ @database_id = ] database_id   
[ , [ @xtp_object_id = ] procedure_id ] ,   
[ @old_collection_value] ]  
```  
  
## <a name="arguments"></a>Аргументы  
 @new_collection_value = *значение*  
 Определяет, включен (1) или выключен (0) сбор статистики на уровне процедуры.  
  
 @new_collection_value имеет значение ноль Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] начинается.  
  
 @database_id == *database_id*, @xtp_object_id = *procedure_id*  
 Идентификатор базы данных и идентификатор объекта для скомпилированной в собственном коде хранимой процедуры. Если сбор статистики включен для экземпляра ([sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md)), собираются Статистика по скомпилированной хранимой процедуры. При отключении сбора статистики для экземпляра сбор статистики для отдельных, скомпилированных в собственном коде хранимых процедур не отключается.  
  
 Используйте [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md), [sys.procedures &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md), [DB_ID &#40;Transact-SQL&#41;](../../t-sql/functions/db-id-transact-sql.md), или [OBJECT_ID &#40;Transact-SQL&#41; ](../../t-sql/functions/object-id-transact-sql.md) для получения идентификаторов базы данных и хранимую процедуру.  
  
 @old_collection_value = *значение*  
 Возвращает текущее состояние.  
  
## <a name="return-code"></a>Код возврата  
 0 — успешное завершение. Ненулевое значение — ошибка.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли sysadmin.  
  
## <a name="code-sample"></a>Образец кода  
 В следующем примере кода показано, как включить сбор статистики для всех скомпилированных в собственном коде хранимых процедур экземпляра, а затем для определенной процедуры.  
  
```sql   
DECLARE @c bit  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1;  
  
EXEC sp_xtp_control_query_exec_stats @old_collection_value=@c output;  
SELECT @c AS 'collection status';  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1,   
@database_id = 5, @xtp_object_id = 341576255;  
  
EXEC sp_xtp_control_query_exec_stats @database_id = 5,   
@xtp_object_id = 341576255, @old_collection_value=@c output;  
  
SELECT @c AS 'collection status';  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
