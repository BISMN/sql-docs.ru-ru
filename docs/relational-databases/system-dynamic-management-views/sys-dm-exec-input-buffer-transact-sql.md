---
title: sys. dm_exec_input_buffer (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_input_buffer
- sys.dm_exec_input_buffer _tsql
- dm_exec_input_buffer
- dm_exec_input_buffer_tsql
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_input_buffer dynamic management function
ms.assetid: fb34a560-bde9-4ad9-aa96-0d4baa4fc104
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4e18f635b7bbdd8fa96a565fef6aef5be5bde87f
ms.sourcegitcommit: 0c40843c13f67ba7d975f4fedb9d20d70747f66d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2019
ms.locfileid: "74097870"
---
# <a name="sysdm_exec_input_buffer-transact-sql"></a>sys. dm_exec_input_buffer (Transact-SQL)

[!INCLUDE[tsql-appliesto-2014sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2014sp2-asdb-xxxx-xxx-md.md)]

Возвращает сведения о инструкциях, отправленных в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="syntax"></a>Синтаксис

```
sys.dm_exec_input_buffer ( session_id , request_id )
```

## <a name="arguments"></a>Аргументы

*session_id* Идентификатор сеанса, в котором будет выполняться поиск пакета. *session_id* имеет **smallint**. *session_id* можно получить из следующих объектов DMO:

- [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
- [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)
- [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)

*request_id* Request_id из [sys. dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md). *request_id* имеет **тип int**.

## <a name="table-returned"></a>Возвращаемая таблица

|Имя столбца|Data type|Описание|
|-----------------|---------------|-----------------|
|**event_type**|**nvarchar(256)**|Тип события во входном буфере для данного SPID.|
|**parameters**|**smallint**|Любые параметры, предоставленные для инструкции.|
|**event_info**|**nvarchar(max)** ;|Текст инструкции во входном буфере для данного SPID.|

## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если пользователь имеет разрешение VIEW SERVER STATE, он увидит все сеансы выполнения на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; в противном случае пользователь увидит только текущий сеанс.

> [!IMPORTANT]
> Выполнение этого динамического административного представления вне SQL Server Management Studio от SQL Server без разрешения VIEW SERVER STATE (например, в триггере, хранимой процедуре или функции) вызывает ошибку разрешения в базе данных master.

На [!INCLUDE[ssSDS](../../includes/sssds-md.md)], если пользователь является владельцем базы данных, он увидит все выполненные сеансы на [!INCLUDE[ssSDS](../../includes/sssds-md.md)]; в противном случае пользователь увидит только текущий сеанс.

> [!IMPORTANT]
> Выполнение этого динамического административного представления вне SQL Server Management Studio в базе данных SQL Azure без разрешений владельца (например, в триггере, хранимой процедуре или функции) вызывает ошибку разрешения в базе данных master.

## <a name="remarks"></a>Remarks

Эту функцию динамического управления можно использовать в сочетании с sys. dm_exec_sessions или sys. dm_exec_requests, выполняя **CROSS APPLY**.

## <a name="examples"></a>Примеры

### <a name="a-simple-example"></a>A. Простой пример

В следующем примере показано, как передать в функцию идентификатор сеанса (SPID) и идентификатор запроса.

```sql
SELECT * FROM sys.dm_exec_input_buffer (52, 0);
GO
```

### <a name="b-using-cross-apply-to-additional-information"></a>б. Использование перекрестного применения к дополнительным сведениям

В следующем примере перечисляются Входные буферы для сеансов с ИДЕНТИФИКАТОРом сеанса больше 50.

```sql
SELECT es.session_id, ib.event_info
FROM sys.dm_exec_sessions AS es
CROSS APPLY sys.dm_exec_input_buffer(es.session_id, NULL) AS ib
WHERE es.session_id > 50;
GO
```

## <a name="see-also"></a>См. также статью

- [Динамические административные представления и функции, связанные с выполнением (Transact-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)
- [sys.dm_exec_sessions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)
- [sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
- [DBCC INPUTBUFFER (Transact-SQL)](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)
