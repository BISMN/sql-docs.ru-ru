---
title: sys. dm_column_encryption_enclave (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: system-objects
ms.topic: language-reference
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: d10bef0df04501c177086b6c89b3f67dec3bab10
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73599247"
---
# <a name="sysdm_column_encryption_enclave-transact-sql"></a>sys. dm_column_encryption_enclave (Transact-SQL)
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

Возвращает счетчики производительности для безопасного анклава для Always Encrypted. Дополнительные сведения см. в статье [Always Encrypted с безопасными анклавами](../security/encryption/always-encrypted-enclaves.md).

Если анклава настроен и правильно инициализирован после последнего перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], представление содержит ровно одну строку. Если анклава не настроен или не был правильно инициализирован, представление не возвращает никаких строк. 

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|current_enclave_session_count|**int**|Текущее количество клиентских сеансов, использующих анклава.|  
|current_column_encryption_key_count|**int**|Число ключей шифрования столбцов, которые в настоящее время содержатся в анклава.|  
|current_memory_size_kb|**bigint**|Размер памяти анклава в КБ|  
|total_evicted_session_count|**bigint**|Общее число сеансов анклава, удаленных с момента последнего перезапуска сервера.|   
  
## <a name="permissions"></a>Разрешения  
Требуется разрешение `VIEW SERVER STATE`.   
  
## <a name="examples"></a>Примеры  
 
```sql  
SELECT * FROM sys.dm_column_encryption_enclave;  
GO  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Настройка параметра конфигурации "тип анклава" для сервера Always Encrypted](../../database-engine/configure-windows/configure-column-encryption-enclave-type.md)
  
  
