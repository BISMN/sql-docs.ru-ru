---
title: Восстановление из резервных копий, хранящихся в Azure | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 6ae358b2-6f6f-46e0-a7c8-f9ac6ce79a0e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1ba9d2e6e607bbfae4ff1232af897145132c9370
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154704"
---
# <a name="restoring-from-backups-stored-in-azure"></a>Восстановление из резервных копий, хранящихся в Azure
  В этом разделе приведены рекомендации по восстановлению базы данных с помощью резервной копии, хранящейся в службе хранилища BLOB-объектов Azure. Это относится к резервным копиям, созданным либо с помощью резервного копирования SQL Server на URL-адрес, либо с помощью служб [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 Рекомендуется просмотреть этот раздел, если резервные копии хранятся в службе хранилища BLOB-объектов Azure, которую планируется восстановить, а затем просмотрите разделы, в которых описаны действия по восстановлению базы данных, которая одинакова для локальных и резервных копий Azure.  
  
## <a name="overview"></a>Обзор  
 Средства и методы, используемые для восстановления базы данных из локальной резервной копии, применимы для восстановления базы данных из облака.  В следующих разделах описываются эти вопросы и все различия, которые следует знать при использовании резервных копий, хранящихся в службе хранилища BLOB-объектов Azure.  
  
### <a name="using-transact-sql"></a>Использование Transact-SQL  
  
-   Так как SQL Server должен подключиться к внешнему источнику данных для получения файлов резервных копий, для проверки подлинности учетной записи хранения используются учетные данные SQL. Соответственно, в инструкции RESTORE необходимо указать параметр WITH CREDENTIAL. Дополнительные сведения см. в статье [SQL Server резервное копирование и восстановление с помощью службы хранилища BLOB-объектов Azure](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
-   Если вы используете [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для управления вашими резервными копиями в облаке, можно просматривать все доступные резервные копии в хранилище с помощью функции **smart_admin.fn_available_backups** . Эта функция возвращает все доступные резервные копии для базы данных в таблице. Поскольку результаты возвращаются в виде таблицы, их можно фильтровать и сортировать. Дополнительные сведения см. в разделе [smart_admin. &#40;FN_AVAILABLE_BACKUPS Transact-&#41;SQL](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql).  
  
### <a name="using-sql-server-management-studio"></a>Использование среды SQL Server Management Studio  
  
-   Для восстановления базы данных из SQL Server Management Studio используется задача восстановления. Страница носитель резервной копии теперь включает параметр **URL-адрес** для отображения файлов резервных копий, хранящихся в службе хранилища больших двоичных объектов Azure. Также необходимо указать учетные данные SQL, которые используются для проверки подлинности учетной записи хранения. Затем сетка **резервные наборы данных для восстановления** заполняется доступными резервными копиями в хранилище BLOB-объектов Azure. Дополнительные сведения см. [в статье восстановление из хранилища Azure с помощью SQL Server Management Studio](sql-server-backup-to-url.md#RestoreSSMS).  
  
### <a name="optimizing-restores"></a>Оптимизация восстановления  
 Чтобы снизить время восстановления, добавьте учетной записи пользователя SQL Server право **Выполнение задач по обслуживанию томов** . Дополнительные сведения см. в разделе [Инициализация файлов базы данных](https://go.microsoft.com/fwlink/?LinkId=271622). Если при включенной быстрой инициализации файлов операция восстановления по-прежнему идет медленно, посмотрите размер файла журнала для экземпляра, где была создана резервная копия базы данных. Если размер журнала очень большой (несколько ГБ), то ожидается, что восстановление будет идти медленно. Во время восстановления файл журнала необходимо обнулить, что занимает значительное количество времени.  
  
 Для сокращения времени восстановления, рекомендуется использовать сжатые резервные копии.  Для резервных копий, чей размер превышает 25 ГБ, используйте [служебную программу AzCopy](https://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx) для загрузки на локальный привод и для последующего выполнения восстановления. За дополнительными рекомендациями относительно резервных копий, обратитесь к [Резервное копирование SQL Server на URL-адрес — рекомендации и устранение неполадок](sql-server-backup-to-url-best-practices-and-troubleshooting.md).  
  
 Также при выполнении восстановления можно включить флаг трассировки 3051, что приведет к формированию подробного журнала. Этот файл журнала помещается в каталог журнала и получает имя в следующем формате: BackupToUrl-\<имя_экземпляра>-\<имя_БД>-action-\<идентификатор_процесса>.log. Файл журнала содержит сведения о каждом цикле обработки в службе хранилища Azure, включая время, которое может быть полезно при диагностике проблемы.  
  
### <a name="topics-on-performing-restore-operations"></a>Разделы об операциях восстановления  
  
-   [Выполнение полного восстановления базы данных (простая модель восстановления)](complete-database-restores-simple-recovery-model.md)  
  
-   [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)  
  
-   [Выполнение полного восстановления базы данных (модель полного восстановления)](complete-database-restores-full-recovery-model.md)  
  
-   [Восстановление файлов (простая модель восстановления)](file-restores-simple-recovery-model.md)  
  
-   [Файлы из резервных копий (модель полного восстановления)](file-restores-full-recovery-model.md)  
  
-   [Поэтапное восстановление (SQL Server)](piecemeal-restores-sql-server.md)  
  
  
