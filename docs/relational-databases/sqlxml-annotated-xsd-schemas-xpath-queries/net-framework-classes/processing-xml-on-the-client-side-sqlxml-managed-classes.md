---
title: Обработка XML на стороне клиента (управляемые классы SQLXML) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d6133cbedb01dce5cb4d868e79e52e236e773f4b
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909170"
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a>Обработка XML-кода на стороне клиента (управляемые классы SQLXML)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом примере показано использование свойства Клиентсидексмл. Приложение выполняет хранимую процедуру на сервере. Результат хранимой процедуры (набор строк из двух столбцов) обрабатывается на стороне клиента для создания XML-документа.  
  
 Следующая хранимая процедура "связи" возвращает " **FirstName** " и " **LastName** " сотрудников в таблице Person. Contact в базе данных AdventureWorks.  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 Это C# приложение выполняет хранимую процедуру и ЗАДАЕТ параметр FOR XML AUTO в указании значения CommandText. В приложении свойству Клиентсидексмл объекта SqlXmlCommand присваивается значение true. Это позволяет выполнять существующие хранимые процедуры, возвращающие наборы строк, и применить к ним преобразование XML на стороне клиента.  
  
> [!NOTE]  
>  В коде необходимо задать имя экземпляра Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
    static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.ClientSideXml = true;  
         cmd.CommandText = "EXEC GetContacts ? FOR XML NESTED";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         using (Stream strm = cmd.ExecuteStream())   
         {  
            using (StreamReader sr = new StreamReader(strm))  
                  {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
  
public static int Main(String[] args)  
{  
    testParams();  
    return 0;  
}  
}  
```  
  
 Чтобы проверить этот пример, необходимо установить на компьютер платформу [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.  
  
### <a name="to-test-the-application"></a>Тестирование приложения  
  
1.  Создайте хранимую процедуру.  
  
2.  Сохраните в папке код C# (файл DocSample.cs), приведенный в этом примере. Измените этот код, указав нужные имя входа и пароль.  
  
3.  Скомпилируйте код. Чтобы скомпилировать код из командной строки, введите следующую команду.  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Будет создан исполняемый файл (DocSample.exe).  
  
4.  Запустите файл DocSample.exe из командной строки.  

