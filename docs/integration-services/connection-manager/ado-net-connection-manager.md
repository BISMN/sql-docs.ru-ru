---
title: Диспетчер подключений ADO.NET | Документация Майкрософт
description: Диспетчер подключений ADO.NET позволяет пакету обращаться к источникам данных с помощью поставщика .NET.
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.adonetconnection.f1
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d61b7423bb39267fe4171d661e8fe7a74fbc6faa
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71294492"
---
# <a name="adonet-connection-manager"></a>Диспетчер соединений ADO.NET

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] позволяет пакету обращаться к источникам данных с помощью поставщика .NET. Как правило, этот диспетчер подключений используется для получения доступа к таким источникам данных, как [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Кроме того, он обеспечивает доступ к источникам данных, предоставляемым посредством OLE DB и XML в пользовательских задачах, которые реализованы с помощью управляемого кода с использованием таких языков, как C#.  
  
При добавлении диспетчера подключений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] к пакету [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер подключений, который разрешается как подключение [!INCLUDE[vstecado](../../includes/vstecado-md.md)] во время выполнения. При этом задается свойство диспетчера подключений и диспетчер подключений добавляется в коллекцию **подключений** пакета.  
  
Свойству `ConnectionManagerType` диспетчера соединений присваивается значение `ADO.NET`. Значение `ConnectionManagerType` уточняется: в него включается имя поставщика .NET, используемого диспетчером соединений.  
  
## <a name="adonet-connection-manager-troubleshooting"></a>Устранение неполадок с диспетчером подключений ADO.NET  
В журнал можно записывать вызовы, сделанные диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] к внешним источникам данных. Это позволяет устранять неполадки с подключением к внешним источникам данных, которые устанавливаются диспетчером подключений [!INCLUDE[vstecado](../../includes/vstecado-md.md)]. Чтобы протоколировать вызовы диспетчера подключений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] к внешним поставщикам данных, необходимо разрешить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
При чтении данных диспетчером подключений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] определенные типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формируют результаты, показанные в приведенной ниже таблице.  
  
|Тип данных SQL Server|Результат|  
|--------------------------|------------|  
|**time**, **datetimeoffset**|Выполнение пакета завершается неудачей, если в пакете не используются параметризованные команды SQL. Чтобы применить параметризованные команды SQL, используйте в пакете задачу «Выполнение SQL». Дополнительные сведения см. в разделах [Задача "Выполнение SQL"](../../integration-services/control-flow/execute-sql-task.md) и [Параметры и коды возврата в задаче "Выполнение SQL"](https://msdn.microsoft.com/library/a3ca65e8-65cf-4272-9a81-765a706b8663).|  
|**datetime2**|Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] отбрасывает миллисекунды.|  
  
> [!NOTE]  
>  Дополнительные сведения о типах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их сопоставлении с типами данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md) и [Типы данных службы Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="adonet-connection-manager-configuration"></a>Настройка диспетчера подключений ADO.NET  
  
Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
-   Предоставьте специальную строку подключения, настроенную таким образом, чтобы удовлетворить требования выбранного поставщика .NET.  
  
-   В зависимости от поставщика предоставьте имя источника данных, к которому производится подключение.  
  
-   Предоставьте безопасные учетные данные, соответствующие выбранному поставщику.  
  
-   Укажите, сохраняется ли в среде выполнения подключение, созданное диспетчером подключений.  
  
Многие параметры конфигурации диспетчера соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] зависят от используемого им поставщика .NET.  
  
Дополнительные сведения о свойствах, которые можно задавать в конструкторе [!INCLUDE[ssIS](../../includes/ssis-md.md)], см. в [следующем разделе](../../integration-services/connection-manager/configure-ado-net-connection-manager.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
### <a name="configure-adonet-connection-manager"></a>Настройка диспетчера подключений ADO.NET
С помощью диалогового окна **Настройка диспетчера соединений OLE DB** можно добавлять подключения к источнику данных, доступ к которому можно осуществлять с помощью поставщика данных .NET Framework. Например, с помощью поставщика SqlClient. Диспетчер соединений использует существующее соединение, либо можно создать новое.  
  
 Дополнительные сведения о диспетчере соединений ADO.NET см. в разделе [ADO.NET Connection Manager](../../integration-services/connection-manager/ado-net-connection-manager.md).  
  
#### <a name="options"></a>Параметры  
**Подключения к данным**  
Выберите из списка существующее подключение к данным ADO.NET.  
  
**Свойства подключения к данным**  
Просмотрите свойства и значения выбранного подключения к данным ADO.NET.  
  
**Создать**  
Создание подключения к данным ADO.NET с помощью диалогового окна **Диспетчер соединений** .  
  
**Удаление**  
Выберите подключение и затем удалите его, щелкнув **Удалить**.  
  
#### <a name="managed-identities-for-azure-resources-authentication"></a>Управляемые удостоверения для проверки подлинности ресурсов Azure
При выполнении пакетов служб SSIS в [Azure-SSIS Integration Runtime в Фабрике данных Azure](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime) вы можете использовать [управляемое удостоверение](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity), связанное с вашей фабрикой данных, для проверки подлинности Базы данных SQL Azure (или управляемого экземпляра). С помощью этого удостоверения назначенная фабрика может обращаться к данным и копировать их из вашей базы данных или в нее.

> [!NOTE]
>  При использовании проверки подлинности Azure Active Directory (Azure AD), включая проверку подлинности с помощью управляемого удостоверения, для подключения к Базе данных SQL Azure (или к управляемому экземпляру) могут возникнуть проблемы, связанные со сбоем при выполнении пакета или непредвиденным изменением поведения. Дополнительные сведения см. в разделе о [функциях и ограничениях Azure AD](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication#azure-ad-features-and-limitations).

Чтобы использовать проверку подлинности управляемого удостоверения для базы данных SQL Azure, выполните следующие действия для настройки базы данных:

1. Создайте группу в Azure AD. Сделайте управляемое удостоверение членом группы.
    
   1. [Найдите управляемое удостоверение фабрики данных на портале Microsoft Azure](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity). Перейдите к разделу **Свойства** своей фабрики данных. Скопируйте **идентификатор объекта управляемого удостоверения**.
    
   1. Установите модуль [Azure AD PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2). Войдите с помощью команды `Connect-AzureAD`. Выполните указанные ниже команды, чтобы создать группу и добавить управляемое удостоверение в качестве члена.
      ```powershell
      $Group = New-AzureADGroup -DisplayName "<your group name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "NotSet"
      Add-AzureAdGroupMember -ObjectId $Group.ObjectId -RefObjectId "<your data factory managed identity object ID>"
      ```
    
1. [Подготовьте администратора Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-azure-sql-database-server) для своего сервера SQL Azure на портале Azure, если вы еще этого не сделали. Администратор Azure AD может быть пользователем Azure AD или группой Azure AD. Если вы предоставляете группе с управляемым удостоверением роль администратора, пропустите шаги 3 и 4. Администратор будет иметь полный доступ к базе данных.

1. [Создайте пользователей автономной базы данных](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#create-contained-database-users-in-your-database-mapped-to-azure-ad-identities) для группы Azure AD. Подключитесь к базе данных, откуда или куда вы хотите скопировать данные с помощью таких средств, как SSMS, с используя удостоверение Azure AD, которое имеет по меньшей мере разрешение ALTER ANY USER. Выполните следующий код T-SQL: 
    
    ```sql
    CREATE USER [your AAD group name] FROM EXTERNAL PROVIDER;
    ```

1. Предоставьте группе Azure AD необходимые разрешения, как это обычно делается для пользователей SQL и других служб. Сведения о соответствующих ролях см. в статье [Роли уровня базы данных](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles). Например, выполните следующий код:

    ```sql
    ALTER ROLE [role name] ADD MEMBER [your AAD group name];
    ```

Чтобы использовать проверку подлинности с помощью управляемого удостоверения для управляемого экземпляра Базы данных SQL Azure, выполните следующие действия по настройке базы данных:
    
1. [Подготовьте администратора Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-managed-instance) для своего управляемого экземпляра на портале Azure, если вы еще этого не сделали. Администратор Azure AD может быть пользователем Azure AD или группой Azure AD. Если вы предоставляете группе с управляемым удостоверением роль администратора, пропустите шаги 2–5. Администратор будет иметь полный доступ к базе данных.

1. [Найдите управляемое удостоверение фабрики данных на портале Microsoft Azure](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity). Перейдите к разделу **Свойства** своей фабрики данных. Скопируйте **идентификатор приложения управляемого удостоверения** (не **идентификатор объекта управляемого удостоверения**).

1. Преобразуйте управляемое удостоверение фабрики данных в двоичный тип. Подключитесь к базе данных **master** в своем управляемом экземпляре с помощью таких средств, как SSMS, используя свою учетную запись администратора SQL или Active Directory. Выполните следующий код T-SQL для базы данных **master**, чтобы получить идентификатор приложения управляемого удостоверения в двоичном формате:
    
    ```sql
    DECLARE @applicationId uniqueidentifier = '{your managed identity application ID}'
    select CAST(@applicationId AS varbinary)
    ```

1. Добавьте управляемое удостоверение фабрики данных в качестве пользователя в управляемый экземпляр Базы данных SQL Azure. Запустите следующий код T-SQL для базы данных **master**:
    
    ```sql
    CREATE LOGIN [{a name for the managed identity}] FROM EXTERNAL PROVIDER with SID = {your managed identity application ID as binary}, TYPE = E
    ```

1. Предоставьте управляемому удостоверению фабрики данных необходимые разрешения. Сведения о соответствующих ролях см. в статье [Роли уровня базы данных](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles). Запустите следующий код T-SQL для базы данных, откуда или куда вы хотите скопировать данные:

    ```sql
    CREATE USER [{the managed identity name}] FOR LOGIN [{the managed identity name}] WITH DEFAULT_SCHEMA = dbo
    ALTER ROLE [role name] ADD MEMBER [{the managed identity name}]
    ```

Наконец, настройте проверку подлинности с помощью управляемого удостоверения для диспетчера подключений ADO.NET. Это можно сделать такими способами:
    
- **Настройка во время разработки.** В конструкторе SSIS щелкните диспетчер подключений ADO.NET правой кнопкой мыши и выберите **Свойства**. Установите для свойства `ConnectUsingManagedIdentity` значение `True`.
    > [!NOTE]
    >  Сейчас свойство `ConnectUsingManagedIdentity` диспетчера подключений не оказывает никакого влияния (то есть проверка подлинности с помощью управляемого удостоверения не работает) при выполнении пакета SSIS в конструкторе SSIS или [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.
    
- **Настройка во время выполнения.** При выполнении пакета с помощью [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) или [действия "Выполнить пакет SSIS" Фабрики данных Azure](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity) найдите диспетчер подключений ADO.NET. Установите для его свойства `ConnectUsingManagedIdentity` значение `True`.
    > [!NOTE]
    >  В Azure-SSIS Integration Runtime все остальные методы проверки подлинности (например, встроенная аутентификация и пароль), предварительно настроенные в диспетчере подключений ADO.NET, переопределяются, если для подключения к базе данных используется проверка подлинности с помощью управляемого удостоверения.

> [!NOTE]
>  Чтобы настроить проверку подлинности с помощью управляемого удостоверения для существующих пакетов, рекомендуем как минимум однократно перестроить проект SSIS с использованием [конструктора SSIS последней версии](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt). Повторно разверните этот проект служб SSIS в Azure-SSIS Integration Runtime, чтобы новое свойство `ConnectUsingManagedIdentity` диспетчера подключений автоматически добавилось во все диспетчеры подключений ADO.NET в проекте SSIS. Кроме того, можно непосредственно переопределить свойство, указав при выполнении путь **\Package.Connections[{имя_диспетчера_подключений}].Properties[ConnectUsingManagedIdentity]** .

## <a name="see-also"></a>См. также раздел  
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
