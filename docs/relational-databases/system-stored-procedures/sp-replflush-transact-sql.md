---
title: sp_replflush (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replflush
- sp_replflush_TSQL
helpviewer_keywords:
- sp_replflush
ms.assetid: 20809f5f-941d-427f-8f0c-de7a6c487584
author: stevestein
ms.author: sstein
ms.openlocfilehash: a6745589616dec5b129992cc555e1238cd62b545
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771589"
---
# <a name="spreplflush-transact-sql"></a>sp_replflush (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Очищает кэш статьи. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Выполнять эту процедуру вручную нет необходимости. процедуру **sp_replflush** следует использовать только для устранения неполадок репликации, как это было направлено опытным специалистом службы поддержки репликации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replflush  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Процедура **sp_replflush** используется в репликации транзакций.  
  
 Определения статей сохраняются в кэше с целью повышения эффективности. **sp_replflush** используется другими хранимыми процедурами репликации при каждом изменении или удалении определения статьи.  
  
 Только одно соединение с клиентом может иметь доступ к данной базе данных для чтения журнала. Если клиент имеет доступ к базе данных для чтения журнала, выполнение процедуры **sp_replflush** приводит к высвобождению доступа клиентом. Другие клиенты могут затем сканировать журнал транзакций с помощью хранимой процедуры **sp_replcmds** или **sp_replshowcmds**.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять процедуру **sp_replflush**.  
  
## <a name="see-also"></a>См. также  
 [sp_replcmds (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [хранимая процедура sp_repldone &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_repltrans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
