---
title: Snapshots.fn_trace_getdata (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- snapshots.fn_trace_getdata
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots.fn_trace_getdata function
ms.assetid: ac28ef48-f4f4-4bf2-ba22-d44e1be88172
author: rothja
ms.author: jroth
ms.openlocfilehash: a85a911d4c9f5cd4565e9839f3be44a4e2366079
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067755"
---
# <a name="snapshotsfntracegetdata-transact-sql"></a>snapshots.fn_trace_getdata (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает все события, собранные для заданной трассировки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
snapshots.fn_trace_gettable ( trace_info_id, start_time, end_time )  
```  
  
## <a name="arguments"></a>Аргументы  
 *trace_info_id*  
 Уникальный идентификатор первичного ключа в таблице snapshots.trace_info данные управления база данных хранилища. *trace_info_id* — **int**.  
  
 *start_time*  
 Время начала трассировки. *start_time* — **datetime**.  
  
 *end_time*  
 Время завершения трассировки. *end_time* — **datetime**.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|\<Все трассировочные столбцы >|\<Зависит от >|Данные трассировки из таблицы snapshots.trace_data в базе данных хранилища данных управления.<br /><br /> Список столбцов для заданной трассировки можно получить, выполнив следующий запрос:<br /><br /> `SELECT * FROM sys.trace_columns`<br /><br /> **Примечание.** Столбцы, возвращаемые функцией snapshots.fn_trace_gettable соответствуют значениям в столбце name системного представления sys.trace_columns. Единственным различием является столбец GroupID, не возвращаемый функцией.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для mdw_reader.  
  
## <a name="see-also"></a>См. также  
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
