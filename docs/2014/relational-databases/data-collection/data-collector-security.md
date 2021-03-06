---
title: Защита сборщика данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
- security [data collector]
- data collector [SQL Server], security
ms.assetid: e75d6975-641e-440a-a642-cb39a583359a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a7dd2b26662fea95837eabaf61f61e3da04fac69
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62873621"
---
# <a name="data-collector-security"></a>Безопасность сборщика данных
  Сборщик данных использует безопасность на основе ролей, реализованную агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Эта модель позволяет администратору базы данных запускать различные задачи сборщика данных в контексте безопасности, имеющем только те разрешения, которые необходимы для выполнения задачи. Этот подход также используется для операций, затрагивающих внутренние таблицы, доступ к которым можно осуществить только с помощью хранимой процедуры или представления. Внутренним таблицам разрешения не предоставляются. Вместо этого разрешения проверяются у пользователя хранимой процедуры или представления, используемых для доступа к таблице.  
  
> [!IMPORTANT]  
>  Еще одним ключевым аспектом данной модели безопасности являются вложенные разрешения. При использовании вложенных разрешений роли с более широкими правами наследуют разрешения ролей с менее широкими правами на объекты (включая предупреждения, операторы, задания, расписания и учетные записи-посредники). Дополнительные сведения см. в статье [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 В следующих разделах в общих чертах описывается безопасность сбора данных, а также те роли, которые необходимо предоставлять пользователям, чтобы они могли настроить и использовать сборщик данных и осуществлять выполнение задач, связанных с хранилищем управляющих данных.  
  
## <a name="general-security"></a>Общая безопасность  
 Сборщик данных устанавливается в соответствии с документированными стандартами для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
### <a name="network-security"></a>Сетевая безопасность  
 Конфиденциальные данные могут передаваться между целевыми экземплярами, реляционным экземпляром, связанным с сервером конфигурации, на котором работают наборы сбора, и сервером, на котором расположено хранилище управляющих данных.  
  
 Для защиты любых данных, передаваемых по сети, были введены стандартные механизмы безопасности, такие как шифрование протокола для [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="permissions-for-configuring-and-using-the-data-collector"></a>Разрешения для настройки и использования сборщика данных  
 В зависимости от задачи пользователи должны быть участниками одной или нескольких предопределенных ролей базы данных, предоставленных для сборщика данных. В порядке от наиболее привилегированных до наименее привилегированных список ролей выглядит следующим образом.  
  
-   `dc_admin`  
  
-   **dc_operator**  
  
-   **dc_proxy**  
  
 Эти роли хранятся в базе данных msdb. По умолчанию ни один из пользователей ни в одну из этих ролей не входит. Членство в этих ролях необходимо предоставлять явным образом.  
  
 Пользователи, являющиеся членами из `sysadmin` предопределенной роли сервера имеют полный доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента объектам и представлениям сборщика данных. Однако для этого их нужно явно добавить в роли сборщика данных.  
  
> [!IMPORTANT]  
>  Члены роли db_ssisadmin и роли dc_admin могут повышать свои права доступа до sysadmin. Такое повышение права доступа может произойти, так как эти роли могут изменять пакеты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , а пакеты [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могут выполняться [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи контекста безопасности sysadmin агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы предотвратить такое повышение прав при выполнении планов обслуживания, наборов сбора данных и других пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , настройте задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запускающие пакеты, на использование учетной записи-посредника с ограниченными правами или добавьте членов sysadmin в роли db_ssisadmin и dc_admin.  
  
### <a name="dcadmin-role"></a>Роль dc_admin  
 Пользователи, назначенные `dc_admin` роли имеют полный административный доступ (Create, Read, Update и Delete) к конфигурации сборщика данных на экземпляре сервера. Члены этой роли могут выполнять следующие операции:  
  
-   задавать свойства уровня сборщика;  
  
-   добавлять новые наборы сбора;  
  
-   устанавливать новые типы сбора;  
  
-   выполнять все действия, разрешенные роли **dc_operator** .  
  
 `dc_admin` Роли является членом следующих ролей:  
  
-   **SQLAgentUserRole**. Эта роль необходима для создания расписаний и запуска заданий.  
  
    > [!NOTE]  
    >  Учетные записи-посредники, созданные для сборщика данных должны предоставлять доступ к `dc_admin` для их создания и использования их в любых шагах задания, которые требуют учетной записи-посредника.  
  
-   **dc_operator**. Членами `dc_admin` наследуют разрешения, предоставленные для **dc_operator**.  
  
### <a name="dcoperator-role"></a>Роль dc_operator  
 Члены роли **dc_operator** имеют доступ на чтение и обновление. Эта роль поддерживает задачи, связанные с выполнением и настройкой наборов сбора. Члены этой роли могут выполнять следующие операции:  
  
-   запускать или останавливать набор сбора;  
  
-   перечислять существующие наборы сбора;  
  
-   просматривать подробные сведения (например, элементы сбора и частоту сбора), связанные с набором сбора;  
  
-   изменять частоту загрузки для существующих наборов сбора;  
  
-   изменять частоту сбора для элементов сбора, являющихся частью существующего набора сбора.  
  
 Роль **dc_operator** является членом следующих ролей, необходимых для перечисления и просмотра пакетов сборщика данных:  
  
-   **db_ssisltduser**  
  
-   **db_ssisoperator**  
  
 Дополнительные сведения см. в разделе [Роли служб Integration Services (службы SSIS)](../../integration-services/security/integration-services-roles-ssis-service.md).  
  
### <a name="dcproxy-role"></a>Роль dc_proxy  
 Члены роли **dc_proxy** имеют доступ на чтение всех наборов элементов сбора сборщика данных и свойств уровня сборщика. Члены этой роли могут также выполнять задания, владельцами которых они являются, и создавать шаги задания, которые выполняются от имени существующей учетной записи-посредника.  
  
 Члены этой роли могут выполнять следующие операции:  
  
-   просматривать сведения о конфигурации набора сбора (например, входные параметры для элементов сбора и их частоту);  
  
-   получать внутренние зашифрованные данные, доступ к которым можно получить только с помощью подписанной хранимой процедуры (например, сведения о соединении с хранилищем данных, используемым для передачи данных);  
  
-   вести журнал событий времени исполнения наборов сбора.  
  
 Роль **dc_proxy** является членом следующих ролей, необходимых для перечисления и просмотра пакетов сборщика данных.  
  
-   **db_ssisltduser**.  
  
-   **db_ssisoperator**  
  
 Дополнительные сведения см. в разделе [Роли служб Integration Services (службы SSIS)](../../integration-services/security/integration-services-roles-ssis-service.md).  
  
## <a name="permissions-for-configuring-and-using-the-management-data-warehouse"></a>Разрешения для настройки и использования хранилища управляющих данных  
 В зависимости от задачи пользователи должны быть членами одной или нескольких предопределенных ролей базы данных, предоставленных для доступа к хранилищу данных управления. В порядке от наиболее привилегированных до наименее привилегированных список ролей выглядит следующим образом.  
  
-   **mdw_admin**  
  
-   **mdw_writer**  
  
-   **mdw_reader**  
  
 Эти роли хранятся в базе данных msdb. По умолчанию ни один из пользователей ни в одну из этих ролей не входит. Членство в этих ролях необходимо предоставлять явным образом.  
  
 Пользователи, являющиеся членами из `sysadmin` предопределенной роли сервера имеют полный доступ к представлениям сборщика данных. Однако для этого их нужно явно добавить в роли базы данных для выполнения других операций.  
  
### <a name="mdwadmin-role"></a>Роль mdw_admin  
 Члены роли **mdw_admin** имеют доступ на чтение, запись, обновление и удаление данных в хранилище данных управления.  
  
 Члены этой роли могут выполнять следующие операции:  
  
-   изменять при необходимости схему хранилища данных управления (например, добавлять новую таблицу при установке нового типа сбора);  
  
    > [!NOTE]  
    >  В случае изменения схемы пользователь также должен быть членом `dc_admin` роль для установки нового типа сборщика, так как для этого действия требуется разрешение на обновление конфигурации сборщика данных в базе данных msdb.  
  
-   запускать обслуживающие задания для хранилища данных управления, например архивацию или очистку.  
  
### <a name="mdwwriter-role"></a>Роль mdw_writer  
 Члены роли **mdw_writer** могут передавать и записывать данные в хранилище данных управления. Любой сборщик данных, хранящий данные в хранилище данных управления, должен быть членом данной роли.  
  
### <a name="mdwreader-role"></a>Роль mdw_reader  
 Члены роли **mdw_reader** имеют доступ на чтение к хранилищу данных управления. Эта роль предназначена для помощи при устранении неполадок путем предоставления доступа к данным с предысторией. Ее члены не могут просматривать другие элементы схемы хранилища данных управления.  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md)  
  
  
