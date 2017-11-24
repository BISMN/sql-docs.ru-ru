---
title: "sysmail_mailattachments (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_mailattachments_TSQL
- sysmail_mailattachments
dev_langs: TSQL
helpviewer_keywords: sysmail_mailattachments database mail view
ms.assetid: aee87059-a4c1-459a-a95c-641b4e3f0e73
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 382106752e64701d0e31d7a41056a66767750b1d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailmailattachments-transact-sql"></a>sysmail_mailattachments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого вложения, полученного компонентом Database Mail. Это представление следует использовать в том случае, когда необходима информация о вложениях, принятых компонентом Database Mail. Для просмотра всех электронных писем, обработанных с помощью компонента Database Mail [sysmail_allitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**attachment_id**|**int**|Идентификатор вложения.|  
|**mailitem_id**|**int**|Идентификатор письма, содержавшего вложение.|  
|**Имя файла**|**nvarchar(520)**|Имя файла вложения. Когда **attach_query_result** -1 и **query_attachment_filename** имеет значение NULL, компонент Database Mail создает произвольное имя файла.|  
|**размер файла**|**int**|Размер вложения в байтах.|  
|**вложение**|**varbinary(max)**|Содержимое вложения.|  
|**last_mod_date**|**datetime**|Дата и время последнего изменения строки.|  
|**last_mod_user**|**sysname**|Пользователь, внесший последнее изменение в строку.|  
  
## <a name="remarks"></a>Замечания  
 Это представление следует использовать для просмотра свойств вложений при устранении неполадок в работе компонента Database Mail.  
  
 Хранение вложений в системных таблицах может привести к **msdb** рост базы данных. Используйте **sysmail_delete_mailitems_sp** для удаления писем и связанных с ними вложений. Дополнительные сведения см. в разделе [создания задания агента SQL Server для архива сообщения компонента Database Mail и журналов событий](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md).  
  
## <a name="permissions"></a>Permissions  
 Предоставленные **sysadmin** предопределенной роли сервера и **DatabaseMailUserRole** роли базы данных. При выполнении членом **sysadmin** предопределенной роли сервера, в этом представлении отображаются все вложения. Все остальные пользователи могут видеть только вложения, отправленные ими самими.  
  
## <a name="see-also"></a>См. также:  
 [sysmail_allitems &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)   
 [sysmail_faileditems &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)   
 [sysmail_sentitems &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md)   
 [sysmail_unsentitems &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md)   
 [sysmail_event_log (Transact-SQL)](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)  
  
  