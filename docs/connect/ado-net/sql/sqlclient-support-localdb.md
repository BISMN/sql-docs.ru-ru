---
title: Поддержка поставщика SqlClient для LocalDB
description: Описывает поддержку SqlClient для баз данных LocalDB.
ms.date: 08/15/2019
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 14cbe4ccf227c9462d2a2dc19fb42d913ca7bc5a
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451972"
---
# <a name="sqlclient-support-for-localdb"></a>Поддержка поставщика SqlClient для LocalDB

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Начиная с SQL Server Code Name Denali, будет доступна упрощенная версия SQL Server, именуемая LocalDB. В этом разделе описывается подключение к базе данных LocalDB.  
  
## <a name="remarks"></a>Remarks  
Дополнительные сведения о LocalDB, включая способы его установки и настройки, см. в электронной документации на SQL Server.  
  
Чтобы получить сводные сведения о том, что можно сделать с LocalDB, выполните следующие действия.  
  
- Создание и запуск экземпляров LocalDB с помощью SqlLocalDB. exe или файла App. config.  
  
- Для добавления и изменения баз данных в локальном экземпляре LocalDB можно воспользоваться программой sqlcmd.exe. Например, `sqlcmd -S (localdb)\myinst`.  
  
- Используйте ключевое слово строки подключения `AttachDBFilename`, чтобы добавить базу данных в экземпляр LocalDB. Если при использовании `AttachDBFilename` не указано имя базы данных в ключевом слове строки подключения `Database`, то база данных будет удалена из экземпляра LocalDB при закрытии приложения.  
  
- Чтобы указать экземпляр LocalDB в строке подключения, выполните указанные ниже действия. Например, имя экземпляра `myInstance`, строка подключения будет включать:  
  
```console
server=(localdb)\\myInstance  
```  
  
`User Instance=True` не разрешены при подключении к базе данных LocalDB.  
  
Базу данных LocalDB можно скачать из [пакета дополнительных компонентов Microsoft SQL Server 2012](https://www.microsoft.com/download/en/details.aspx?id=29065). Если необходимо изменение данных в экземпляре LocalDB с помощью программы sqlcmd.exe, то необходимо пользоваться версией sqlcmd из SQL Server 2012. Эту программу можно также получить из пакета дополнительных компонентов SQL Server 2012.  
  
## <a name="programmatically-create-a-named-instance"></a>Программное создание именованного экземпляра  
Приложение может создать именованный экземпляр и указать базу данных следующим образом:  
  
- Укажите экземпляры LocalDB для создания в файле App. config, как показано ниже.  Номер версии экземпляра должен совпадать с номером версии установки LocalDB.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- Укажите имя экземпляра с помощью ключевого слова строки подключения `server`.  Имя экземпляра, указанное в ключевом слове строки подключения `server`, должно соответствовать имени, указанному в файле app.config.  
  
- Используйте ключевое слово строки подключения `AttachDBFilename`, чтобы указать. MDF.  
  
## <a name="next-steps"></a>Следующие шаги
- [Функции SQL Server и ADO.NET](sql-server-features-adonet.md)
