---
title: sp_replshowcmds (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replshowcmds
- sp_replshowcmds_TSQL
helpviewer_keywords:
- sp_replshowcmds
ms.assetid: 199f5a74-e08e-4d02-a33c-b8ab0db20f44
author: stevestein
ms.author: sstein
ms.openlocfilehash: 96a32ea04fc53f1a0bf3a842a5e68cde5586ac29
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770884"
---
# <a name="spreplshowcmds-transact-sql"></a>sp_replshowcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает команды для транзакций, отмеченных для репликации, в удобочитаемом формате. **sp_replshowcmds** может выполняться, только если клиентские соединения (включая текущее соединение) не считывают реплицированные транзакции из журнала. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replshowcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @maxtrans = ] maxtrans`Число транзакций, о которых возвращаются сведения. *maxtrans* имеет **тип int**и значение по умолчанию **1**, указывающее максимальное количество транзакций, ожидающих репликации, для которых **sp_replshowcmds** возвращает сведения.  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_replshowcmds** — это диагностическая процедура, которая возвращает сведения о базе данных публикации, из которой она выполняется.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**binary(10)**|Последовательный номер команды.|  
|**originator_id**|**int**|Идентификатор инициатора команды, значение всегда **равно 0**.|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя, значение всегда **равно 0**.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**type**|**int**|Тип команды.|  
|**команда**|**nvarchar(1024)**|Команда языка [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## <a name="remarks"></a>Примечания  
 **sp_replshowcmds** используется в репликации транзакций.  
  
 С помощью **sp_replshowcmds**можно просматривать транзакции, которые в настоящее время не распределены (транзакции, оставшиеся в журнале транзакций, которые не были отправлены распространителю).  
  
 Клиенты, выполняющие **sp_replshowcmds** и **sp_replcmds** в одной и той же базе данных, получают ошибку 18752.  
  
 Чтобы избежать этой ошибки, первый клиент должен отключиться или роль клиента в качестве модуля чтения журнала, выполнив процедуру **sp_replflush**. После отключения всех клиентов от средства чтения журнала **sp_replshowcmds** может быть успешно запущен.  
  
> [!NOTE]  
>  **sp_replshowcmds** следует запускать только для устранения неполадок с репликацией.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_replshowcmds**.  
  
## <a name="see-also"></a>См. также  
 [Сообщения об ошибках](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_replcmds (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [хранимая процедура sp_repldone &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
