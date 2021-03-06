---
title: sys.sp_rda_reconcile_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7ad2fd6c51f5b5463e4e4c10745b2ff245bd691d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083674"
---
# <a name="syssprdareconcilecolumns-transact-sql"></a>sys.sp_rda_reconcile_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Согласовывает столбцы в удаленной таблице Azure со столбцами в таблице с включенным Stretch SQL Server.  
    
  **sp_rda_reconcile_columns** добавляет столбцы на удаленную таблицу, которая существует в таблице с включенным Stretch SQL Server, но не в удаленной таблице. Эти столбцы могут оказаться столбцы, которые случайно удалены из удаленной таблицы. Тем не менее **sp_rda_reconcile_columns** не удалять столбцы из удаленной таблицы, существующие в удаленной таблице, но не в таблице SQL Server.
  
  > [!IMPORTANT]
  > Воссоздавая столбцы, случайно стертые из удаленной таблицы, процедура **sp_rda_reconcile_columns** не восстанавливает данные, которые прежде присутствовали в стертых столбцах.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Аргументы  
 \@objname = " *\@objname*"  
 Имя таблицы SQL Server с поддержкой Stretch.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или > 0 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Требуются права db_owner.  
   
## <a name="remarks"></a>Примечания  
 Если в удаленной таблице Azure есть столбцы, больше не существующие в таблице SQL Server с поддержкой Stretch, они не мешают нормальной работе Stretch Database. При желании вы можете удалить такие столбцы вручную.  
  
## <a name="example"></a>Пример  
 Чтобы согласовать столбцы в удаленной таблице Azure, выполните следующую инструкцию.  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
