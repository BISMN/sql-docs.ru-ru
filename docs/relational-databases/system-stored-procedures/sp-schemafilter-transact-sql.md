---
title: sp_schemafilter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_schemafilter_TSQL
- sp_schemafilter
helpviewer_keywords:
- sp_schemafilter
ms.assetid: 199e869b-2cd2-44ee-b2ee-69edb06a1bc4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 231796d1678a19106eb89f3039cd755e8385082c
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633019"
---
# <a name="sp_schemafilter-transact-sql"></a>sp_schemafilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет и отображает сведения о схеме, исключенной при построении списка таблиц Oracle, подходящих для публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_schemafilter [ @publisher = ] 'publisher'   
   [ , [ @schema = ] 'schema' ]   
   [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` — имя издателя, не являющегося [!INCLUDE[msCoName](../../includes/msconame-md.md)]ом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @schema = ] 'schema'` — имя схемы. *Schema* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @operation = ] 'operation'` — это действие, выполняемое с этой схемой. *Операция* имеет тип **nvarchar (4)** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**включить**|Добавляет указанную схему в список схем, не подходящих для публикации.|  
|**тени**|Удаляет указанную схему из списка схем, не подходящих для публикации.|  
|**Справка**|Возвращает список схем, которые не подходят для публикации.|  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**SchemaName**|**sysname**|Имя схемы, не подходящей для публикации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Замечания  
 **sp_schemafilter** следует использовать только для разнородных издателей.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** на распространителе могут выполнять **sp_schemafilter**.  
  
## <a name="see-also"></a>См. также раздел  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
