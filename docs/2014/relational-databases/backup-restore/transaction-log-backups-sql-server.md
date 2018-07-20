---
title: Резервные копии журнала транзакций (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], transaction logs
- transaction log backups [SQL Server], creating
- log backups [SQL Server[
- transaction log backups [SQL Server], sequencing
ms.assetid: f4a44a35-0f44-4a42-91d5-d73ac658a3b0
caps.latest.revision: 51
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e0a796d00c24f099f6ca96b826eb41e7f0e103e4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37186602"
---
# <a name="transaction-log-backups-sql-server"></a>Резервные копии журналов транзакций (SQL Server)
  Этот раздел относится только к тем базам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые используют модель полного восстановления или модель восстановления с неполным протоколированием. В этом разделе рассматривается создание резервной копии журнала транзакций базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Перед созданием любой резервной копии журнала необходимо создать как минимум одну полную резервную копию. После этого резервное копирование журнала транзакций может выполняться в любое время, кроме времени другого резервного копирования журнала. Рекомендуется периодически производить резервное копирование журнала для снижения вероятности потери результатов работы и для усечения журнала. Обычно администратор базы данных время от времени создает полную резервную копию базы данных (например, еженедельно) и дополнительно создает разностные резервные копии через более короткие интервалы, например ежедневно. Независимо от резервного копирования базы данных администратор создает резервные копии журнала транзакций через еще более короткие интервалы, например каждые 10 минут. При таком подходе к резервному копированию оптимальный интервал между моментами выполнения резервного копирования зависит от множества факторов: важности данных, размера базы данных и рабочей нагрузки сервера.  
  
 **В этом разделе.**  
  
-   [Работа последовательности резервных копий журнала](#LogBackupSequence)  
  
-   [Рекомендации](#Recommendations)  
  
-   [Связанные задачи](#RelatedTasks)  
  
-   [См. также](#RelatedContent)  
  
##  <a name="LogBackupSequence"></a> Работа последовательности резервных копий журнала  
 Последовательность резервных копий *цепочки журналов* транзакций не зависит от резервных копий данных. Например, предположим, что имеется следующая последовательность событий:  
  
|Time|Событие|  
|----------|-----------|  
|8:00|Резервное копирование базы данных.|  
|Полдень|Резервное копирование журнала транзакций.|  
|16:00|Резервное копирование журнала транзакций.|  
|18:00|Резервное копирование базы данных.|  
|20:00|Резервное копирование журнала транзакций.|  
  
 Резервная копия журнала транзакций создана в 20:00, содержит записи журнала транзакций начиная с 16:00 до 20:00, включая время создания полной резервной копии базы данных в 18:00. Последовательность резервных копий журнала транзакций непрерывна, начиная с первого полного резервного копирования базы данных в 8:00 и до последнего резервного копирования журнала в 20:00. Сведения о применении этих резервных копий журналов приводятся в примере в статье [Применение резервных копий журналов транзакций (SQL Server)](transaction-log-backups-sql-server.md).  
  
##  <a name="Recommendations"></a> Рекомендации  
  
-   Если журнал транзакций поврежден, будут потеряны все результаты работы, начиная с момента самого последнего действительного резервного копирования. Поэтому настоятельно рекомендуется помещать файлы журнала в отказоустойчивое хранилище.  
  
-   Если база данных повреждена или требуется восстановить базу данных, рекомендуется создать [резервную копию заключительного фрагмента журнала](tail-log-backups-sql-server.md) , чтобы можно было восстановить базу данных до текущего момента.  
  
-   По умолчанию каждая успешная операция резервного копирования добавляет запись в журнал ошибок служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и в журнал системных событий. Если создание резервной копии журналов производится очень часто, это приводит к быстрому накоплению сообщений об успешном завершении. Это приводит к увеличению журналов ошибок, затрудняя поиск других сообщений. Если работа существующих скриптов не зависит от этих записей, то их можно отключить с помощью флага трассировки 3226. Дополнительные сведения см. в разделе [Флаги трассировки (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Создание резервной копии журнала транзакций**  
  
-   [Создание резервной копии журнала транзакций (SQL Server)](back-up-a-transaction-log-sql-server.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)  
  
 Описание планирования заданий резервного копирования см. в разделе [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).  
  
##  <a name="RelatedContent"></a> См. также  
 Нет.  
  
## <a name="see-also"></a>См. также  
 [Журнал транзакций (SQL Server)](../logs/the-transaction-log-sql-server.md)   
 [Резервное копирование и восстановление баз данных SQL Server](back-up-and-restore-of-sql-server-databases.md)   
 [Резервные копии заключительного фрагмента журнала (SQL Server)](tail-log-backups-sql-server.md)   
 [Применение резервных копий журналов транзакций (SQL Server)](transaction-log-backups-sql-server.md)  
  
  