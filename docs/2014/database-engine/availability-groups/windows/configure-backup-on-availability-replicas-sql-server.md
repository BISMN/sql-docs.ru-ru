---
title: Настройка резервного копирования в репликах доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 74bc40bb-9f57-44e4-8988-1d69c0585eb6
caps.latest.revision: 30
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b3b35cb41610f490b4a12f8deba77e9d34cc7185
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328444"
---
# <a name="configure-backup-on-availability-replicas-sql-server"></a>Настройка резервного копирования в репликах доступности (SQL Server)
  В этом разделе описывается настройка резервной копии вторичной реплики для группы доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Введение в резервное копирование во вторичных репликах, см. в разделе [ активные вторичные реплики: резервное копирование на вторичных репликах (группы доступности AlwaysOn)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).  
  
 
  

  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Необходимо подключиться к экземпляру сервера, на котором размещена первичная реплика.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
  
|Задача|Разрешения|  
|----------|-----------------|  
|Настройка резервного копирования во вторичных репликах при создании группы доступности|Требуется членство в фиксированной роли сервера **sysadmin** и одно из разрешений: CREATE AVAILABILITY GROUP, ALTER ANY AVAILABILITY GROUP или CONTROL SERVER.|  
|Изменение группы доступности или реплики доступности|Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.|  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Настройка резервного копирования во вторичных репликах**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена первичная реплика, и щелкните имя сервера, чтобы развернуть его дерево.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Щелкните группу доступности, для которой нужно задать параметры резервного копирования, и выберите команду **Свойства** .  
  
4.  В диалоговом окне **Свойства групп доступности** перейдите на страницу **Настройки резервного копирования** .  
  
5.  На панели **Где должно происходить резервное копирование?** выберите один из способов автоматизированного резервного копирования для группы доступности:  
  
     **Предпочтение вторичной**  
     Указывает, что резервное копирование должно выполняться на вторичной реплике, за исключением тех случаев, когда в режиме «в сети» находится только первичная реплика. В этом случае резервное копирование будет выполняться на первичной реплике. Это параметр по умолчанию.  
  
     **Только вторичная**  
     Указывает, что резервное копирование никогда не выполняется на первичной реплике. Если первичная реплика является единственной репликой, находящейся в режиме «в сети», резервное копирование не будет выполняться.  
  
     `Primary`  
     Указывает, что резервное копирования должно всегда выполняться на первичной реплике. Данный параметр является полезным, если вам требуются такие функции резервного копирования, как создание разностных резервных копий, которые не поддерживаются при выполнении резервного копирования на вторичной реплике.  
  
    > [!IMPORTANT]  
    >  Если планируется использовать доставку журналов для подготовки баз данных-получателей для группы доступности, задайте параметру автоматизированного резервного копирования значение `Primary` до тех пор, пока все базы данные-получатели не будут подготовлены и присоединены к группе доступности.  
  
     **Любая реплика**  
     Указывает, что вы предпочитаете, чтобы задания резервного копирования пропускали реплики доступности при выборе реплики для создания резервных копий. Примечание. Задания резервного копирования могут учитывать другие факторы, например приоритет резервного копирования каждой реплики доступности в сочетании с ее состоянием работоспособности и подключения.  
  
    > [!IMPORTANT]  
    >  Принудительного применения параметра автоматического резервного копирования не существует. Интерпретация данного приоритета зависит от логики (при ее наличии), которая внесена в задания резервного копирования для баз данных в указанной группе доступности. Параметр автоматического резервного копирования не влияет на выполнение нерегламентированного резервного копирования. Дополнительные сведения см. в разделе [Дальнейшие действия. После настройки резервного копирования во вторичных репликах](#FollowUp) ниже в этой статье.  
  
6.  Сетка **Настройки резервного копирования реплики** позволяет изменить приоритет резервного копирования для группы доступности. В этой сетке отображается текущий приоритет резервного копирования каждого экземпляра сервера, на котором размещена реплика, входящая в данную группу доступности. Сетка содержит следующие столбцы.  
  
     **Экземпляр сервера**  
     Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , в котором размещается группа доступности.  
  
     **Приоритет резервного копирования (низкий = 1, высокий = 100)**  
     Указывает приоритет выполнения резервного копирования на данной реплике по отношению к другим репликам из той же группы доступности. Значение представляет собой целое число в диапазоне от 0 до 100. 1 указывает минимальный приоритет, 100 — наивысший приоритет. Если **Backup Priority** = 1, реплика доступности будет выбрана для создания резервных копий только в случае, если реплики доступности с более высоким приоритетом отсутствуют.  
  
     **Исключить реплику**  
     Установите этот параметр, чтобы реплика никогда не выбиралась для выполнения резервного копирования. Этот параметр может быть полезным, например, для исключения удаленной реплики доступности, создание резервных копий на которой нежелательно.  
  
7.  Для фиксации изменений нажмите кнопку **ОК**.  
  
 **Альтернативные пути доступа к странице настройки резервного копирования**  
  
-   [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Использование мастера добавления реплики в группу доступности (среда SQL Server Management Studio)](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Настройка резервного копирования во вторичных репликах**  
  
1.  Подключитесь к экземпляру сервера, на котором находится первичная реплика.  
  
2.  Для новой группы доступности используйте инструкцию [CREATE AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/create-availability-group-transact-sql). При добавлении или изменении существующей группы доступности воспользуйтесь инструкцией [ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql).  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Настройка резервного копирования во вторичных репликах**  
  
1.  Значение по умолчанию (`cd`) к экземпляру сервера, на котором размещена первичная реплика.  
  
2.  При необходимости настройте приоритет каждой реплики доступности, которую необходимо добавить или изменить. Этот приоритет используется экземпляром сервера, на котором размещается первичная реплика, при принятии решения о том, какая реплика должна обработать запрос автоматического резервного копирования для базы данных в группе доступности (выбирается реплика с максимальным приоритетом). Значением приоритета может быть любое целое число от 0 до 100 включительно. Приоритет 0 указывает, что реплика не должна считаться кандидатом на обработку запросов резервного копирования.  Значение по умолчанию — 50.  
  
     При добавлении реплики доступности в группу доступности воспользуйтесь командлетом `New-SqlAvailabilityReplica`. При изменении существующей реплики доступности воспользуйтесь командлетом `Set-SqlAvailabilityReplica`. В любом случае укажите `BackupPriority` *n* параметр, где *n* представляет собой значение от 0 до 100.  
  
     Например, следующая команда задает приоритет резервного копирования реплики доступности `MyReplica` для `60`.  
  
    ```  
    Set-SqlAvailabilityReplica -BackupPriority 60 `  
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
3.  Также настройте приоритет автоматического резервного копирования для группы доступности, которая создается или изменяется. Этот параметр указывает, как задание резервного копирования вычисляет первичную реплику при выборе места для создания резервных копий. Значение по умолчанию предпочитают вторичные реплики.  
  
     При создании группы доступности используйте командлет `New-SqlAvailabilityGroup`. При изменении существующей группы доступности, воспользуйтесь `Set-SqlAvailabilityGroup` командлета. В любом случае укажите `AutomatedBackupPreference` параметра.  
  
     где  
  
     `Primary`  
     Указывает, что резервное копирования должно всегда выполняться на первичной реплике. Данный параметр является полезным, если вам требуются такие функции резервного копирования, как создание разностных резервных копий, которые не поддерживаются при выполнении резервного копирования на вторичной реплике.  
  
    > [!IMPORTANT]  
    >  Если планируется использовать доставку журналов для подготовки баз данных-получателей для группы доступности, задайте параметру автоматизированного резервного копирования значение `Primary` до тех пор, пока все базы данные-получатели не будут подготовлены и присоединены к группе доступности.  
  
     `SecondaryOnly`  
     Указывает, что резервное копирование никогда не выполняется на первичной реплике. Если первичная реплика является единственной репликой, находящейся в режиме «в сети», резервное копирование не будет выполняться.  
  
     `Secondary`  
     Указывает, что резервное копирование должно выполняться на вторичной реплике, за исключением тех случаев, когда в режиме «в сети» находится только первичная реплика. В этом случае резервное копирование будет выполняться на первичной реплике. Это поведение по умолчанию.  
  
     `None`  
     Указывает, что вы предпочитаете, чтобы задания резервного копирования пропускали реплики доступности при выборе реплики для создания резервных копий. Примечание. Задания резервного копирования могут учитывать другие факторы, например приоритет резервного копирования каждой реплики доступности в сочетании с ее состоянием работоспособности и соединения.  
  
    > [!IMPORTANT]  
    >  Параметр `AutomatedBackupPreference` не вводится в действие принудительно. Интерпретация данного приоритета зависит от логики (при ее наличии), которая внесена в задания резервного копирования для баз данных в указанной группе доступности. Параметр автоматического резервного копирования не влияет на выполнение нерегламентированного резервного копирования. Дополнительные сведения см. далее в разделе [Дальнейшие действия. После настройки резервного копирования во вторичных репликах](#FollowUp) .  
  
     Например, следующая команда задает свойству `AutomatedBackupPreference` группы доступности `MyAg` значение `SecondaryOnly`. Автоматическое резервное копирование баз данных в этой группе доступности никогда не будет выполняться в первичной реплике, а будет перенаправляться на вторичную реплику с наивысшим приоритетом резервного копирования.  
  
    ```  
    Set-SqlAvailabilityGroup `  
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `  
    -AutomatedBackupPreference SecondaryOnly  
    ```  
  
> [!NOTE]  
>  Чтобы просмотреть синтаксис командлета, используйте `Get-Help` командлет в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] среде PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Получение справок по SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки резервного копирования во вторичных репликах  
 Чтобы настройка автоматического резервного копирования учитывалась для данной группы доступности на каждом экземпляре сервера, где размещена реплика доступности, приоритет резервного копирования которой больше нуля (>0), необходимо создать скрипты заданий резервного копирования для баз данных в группе доступности. Чтобы определить, является ли текущая реплика предпочитаемой репликой резервного копирования, выполните функцию [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) в скрипте резервного копирования. Если реплика доступности, размещенная на текущем экземпляре сервера, является предпочтительной для резервного копирования, эта функция возвращает значение 1. В противном случае функция возвращает значение 0. С помощью простого скрипта для каждой реплики доступности, который запрашивает эту функцию, можно определить, какая реплика должна выполнять данное задание резервного копирования. Например, типичный фрагмент скрипта задания резервного копирования выглядит следующим образом:  
  
```  
IF (NOT sys.fn_hadr_backup_is_preferred_replica(@DBNAME))  
BEGIN  
      Select ‘This is not the preferred replica, exiting with success’;  
      RETURN 0 – This is a normal, expected condition, so the script returns success  
END  
BACKUP DATABASE @DBNAME TO DISK=<disk>  
   WITH COPY_ONLY;  
```  
  
 Написание скрипта с подобной логикой для задания резервного копирования позволяет планировать запуск задания на каждой реплике доступности по одинаковому расписанию. Каждое из данных заданий обращается к одним и тем же данным для определения того, какие задания следует выполнить, поэтому для создания резервной копии фактически обрабатывается только одно запланированное задание.  В случае отработки отказа не приходится изменять ни один из скриптов или заданий. Кроме того, если перенастроить группу доступности для добавления реплики доступности, то для управления заданиями резервного копирования потребуется просто скопировать или запланировать задание. В случае удаления реплики доступности просто удалите задание резервного копирования с экземпляра сервера, на котором размещалась эта реплика.  
  
> [!TIP]  
>  Если задание резервного копирования создается в[мастере планов обслуживания](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md), то в это задание автоматически включается логика скрипта, которая вызывает и проверяет функцию **sys.fn_hadr_backup_is_preferred_replica** . Однако задание резервного копирования не будет возвращать сообщение «Это не предпочтительная реплика». Необходимо создать задания для каждой базы данных доступности на каждом экземпляре сервера, на котором размещена реплика доступности этой группы доступности.  
  
##  <a name="ForInfoAboutBuPref"></a> Получение сведений о параметрах настройки резервного копирования  
 Ниже приводятся способы получения информации, имеющей отношение к резервному копированию во вторичных репликах.  
  
|Просмотр|Сведения|Соответствующие столбцы|  
|----------|-----------------|----------------------|  
|[sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)|Является ли текущая реплика предпочитаемой репликой резервного копирования?|Неприменимо.|  
|[sys.availability_groups](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)|параметр автоматического резервного копирования|**automated_backup_preference**<br /><br /> **automated_backup_preference_desc**|  
|[sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)|Приоритет резервного копирования данной реплики доступности|**backup_priority**|  
|[sys.dm_hadr_availability_replica_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)|Является реплика локальной по отношению к экземпляру сервера?<br /><br /> Текущая роль.<br /><br /> Состояние работы<br /><br /> Состояние подключения<br /><br /> Исправность синхронизации реплики доступности|**is_local**<br /><br /> **role**, **role_desc**<br /><br /> **operational_state**, **operational_state_desc**<br /><br /> **connected_state**, **connected_state_desc**<br /><br /> **synchronization_health**, **synchronization_health_desc**|  
  
##  <a name="RelatedContent"></a> См. также  
  
-   [Microsoft SQL Server AlwaysOn Solutions Guide for высокий уровень доступности и аварийного восстановления](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [Блог группы AlwaysOn SQL Server: Официальный блог SQL Server AlwaysOn Team](http://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [ Активные вторичные реплики: Резервное копирование во вторичных репликах (группы доступности AlwaysOn)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
  
  