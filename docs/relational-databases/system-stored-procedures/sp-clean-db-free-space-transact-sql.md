---
title: процедуру sp_clean_db_free_space (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_clean_db_free_space_TSQL
- sp_clean_db_free_space
dev_langs:
- TSQL
helpviewer_keywords:
- sp_clean_db_free_space
- ghost records
ms.assetid: faa96f7e-be92-47b1-8bc5-4dbba5331655
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f6aa21345fe4ba16c06a5ead3381a6e1ccdef8e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070382"
---
# <a name="spcleandbfreespace-transact-sql"></a>sp_clean_db_free_space (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет остаточные данные, оставляемые на страницах базы данных процедурами изменения данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. процедура sp_clean_db_free_space очищает все страницы во всех файлах базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_clean_db_free_space   
[ @dbname ] = 'database_name'   
[ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @dbname=] '*имя_базы_данных*"  
 Имя очищаемой базы данных. *DBName* — **sysname** и не может иметь значение NULL.  
  
 [ @cleaning_delay=] '*delay_in_seconds*"  
 Интервал задержки между операциями очистки страниц. Применение задержки помогает уменьшить нагрузку на систему ввода-вывода. *delay_in_seconds* — **int** значение по умолчанию 0.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Удаляет операции из таблицы или обновляет операции, которые приводят к перемещению строки, что может немедленно освободить пространство на странице путем удаления ссылок на строку. Но при определенных обстоятельствах строка может физически оставаться на странице данных как фантомная запись. Фантомные записи периодически удаляются фоновым процессом. Эти остаточные данные не возвращаются [!INCLUDE[ssDE](../../includes/ssde-md.md)] в ответ на запросы. Но если физическая безопасность данных или файлов резервной копии в рабочей среде подвергается угрозам, то можно использовать процедуру sp_clean_db_free_space для очистки этих фантомных записей.  
  
 Продолжительность времени, необходимого для выполнения процедуры sp_clean_db_free_space, зависит от размера файла, доступного свободного пространства и емкости диска. Тем не менее выполнение процедуры sp_clean_db_free_space может оказать существенное отрицательное влияние на работу подсистемы ввода-вывода, поэтому рекомендуется выполнять эту процедуру не в обычное рабочее время.  
  
 Рекомендуется создать полную резервную копию базы данных, прежде чем выполнить процедуру sp_clean_db_free_space.  
  
 Связанные [sp_clean_db_file_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-file-free-space-transact-sql.md) хранимой процедуры можно очистить отдельный файл.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли базы данных db_owner.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как очистить всю остаточную информацию в базе данных `AdventureWorks2012`.  
  
```  
USE master;  
GO  
EXEC sp_clean_db_free_space   
@dbname = N'AdventureWorks2012' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)
 <br>[Руководство по процессу очистки фантомных записей](../ghost-record-cleanup-process-guide.md) 
  
  
