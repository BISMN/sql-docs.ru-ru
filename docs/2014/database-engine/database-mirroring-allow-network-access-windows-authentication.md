---
title: Разрешение сетевого доступа к базе данных с использованием проверки подлинности Windows (SQL Server) конечной точки зеркального отображения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
caps.latest.revision: 31
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 29b1cdaeae798a73455df2d99046f3564abd0db6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157105"
---
# <a name="allow-network-access-to-a-database-mirroring-endpoint-using-windows-authentication-sql-server"></a>Разрешение сетевого доступа к конечной точке зеркального отображения базы данных с использованием проверки подлинности Windows (SQL Server)
  При проверке подлинности Windows для соединения с конечными точками зеркального отображения базы данных двух экземпляров [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] необходимо вручную задать учетные записи для входа с учетом следующих факторов.  
  
-   Если экземпляры [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] выполняются как службы под разными учетными записями домена (одного или других доверенных доменов), нужно создать имя входа для каждой учетной записи в базе данных **master** на каждом удаленном экземпляре сервера и предоставить этому имени входа разрешение CONNECT для конечной точки.  
  
-   Если экземпляры [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] выполняются как учетные записи сетевой службы, нужно создать в базе данных **master** на каждом из удаленных экземпляров серверов имя входа для каждой учетной записи главного компьютера (*имя_домена***\\***имя_компьютера$*) и предоставить этому имени входа разрешение CONNECT для конечной точки. Это обусловлено тем, что экземпляр сервера, выполняемый под учетной записью Network Service, выполняет проверку подлинности с помощью учетной записи домена главного компьютера.  
  
> [!NOTE]  
>  Убедитесь, что конечная точка существует для каждого из экземпляров сервера. Дополнительные сведения см. в разделе [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).  
  
### <a name="to-configure-logins-for-windows-authentication"></a>Настройка имен входа для проверки подлинности Windows  
  
1.  Для учетной записи пользователя каждого экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]создайте имя входа в других экземплярах [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Выполняйте инструкцию [CREATE LOGIN](/sql/t-sql/statements/create-login-transact-sql) с предложением FROM WINDOWS.  
  
     Дополнительные сведения см. в разделе [Создание имени входа](../relational-databases/security/authentication-access/create-a-login.md).  
  
2.  Кроме того, чтобы выполнивший вход пользователь гарантированно имел доступ к конечной точке, предоставьте имени входа разрешения на соединение с конечной точкой с помощью инструкции [GRANT](/sql/t-sql/statements/grant-transact-sql) . Обратите внимание, что разрешения на подключение к конечной точке предоставлять не требуется, если пользователь является администратором.  
  
     Дополнительные сведения см. в статье [Grant a Permission to a Principal](../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md).  
  
## <a name="example"></a>Пример  
 В следующем примере [!INCLUDE[tsql](../includes/tsql-md.md)] создается имя входа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для учетной записи пользователя `Otheruser` , которая принадлежит домену `Adomain`. Затем пользователю предоставляются разрешения на подключение к существующей конечной точке зеркального отображения базы данных `Mirroring_Endpoint`.  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Зеркальное отображение базы данных (SQL Server)](database-mirroring/database-mirroring-sql-server.md)   
 [Безопасность транспорта для зеркального отображения базы данных и групп доступности AlwaysOn &#40;SQL Server&#41;](database-mirroring/transport-security-database-mirroring-always-on-availability.md)   
 [Конечная точка зеркального отображения базы данных (SQL Server)](database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  