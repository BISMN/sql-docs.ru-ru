---
title: "sys.dm_fts_memory_buffers (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_memory_buffers
- dm_fts_memory_buffers_TSQL
- dm_fts_memory_buffers
- sys.dm_fts_memory_buffers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_buffers dynamic management view
ms.assetid: 56895fe5-e8df-4d75-9adc-c1f7757cdef8
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 190d564ec27cf7921fbfbd9d6e85fc594b77c2d6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmftsmemorybuffers-transact-sql"></a>sys.dm_fts_memory_buffers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает данные о буферах памяти, принадлежащих конкретному пулу памяти, используемому в качестве части полнотекстового сканирования или диапазона полнотекстового сканирования.  
  
> [!NOTE]
> Следующий столбец будет удален в одном из будущих выпусков [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **row_count**. Не пользуйтесь ими в новых разработках и запланируйте изменение приложений, которые сейчас их используют.  

  
|Столбец|Data type|Описание|  
|------------|---------------|-----------------|  
|**pool_id**|**int**|Идентификатор выделенного пула памяти.<br /><br /> 0 = небольшие буферы<br /><br /> 1 = большие буферы|  
|**memory_address**|**varbinary(8)**|Адрес выделенного буфера памяти.|  
|**name**|**nvarchar(4000)**|Имя общего буфера памяти, для которого было произведено данное выделение.|  
|**is_free**|**бит**|Текущее состояние буфера памяти.<br /><br /> 0 = свободен<br /><br /> 1 = занят|  
|**row_count**|**int**|Число строк, обрабатываемое в данный момент буфером.|  
|**bytes_used**|**int**|Объем памяти, используемой данным буфером, в байтах.|  
|**percent_used**|**int**|Процент использования выделенной памяти.|  
  
## <a name="permissions"></a>Разрешения  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  
 
## <a name="physical-joins"></a>Физические соединения  
 ![Существенные соединения данного динамического административного представления](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-buffers-1.gif "существенные соединения данного динамического административного представления")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|«многие к одному»|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  
