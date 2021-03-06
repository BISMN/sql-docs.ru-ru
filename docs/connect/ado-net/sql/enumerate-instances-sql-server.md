---
title: Перечисление экземпляров SQL Server (ADO.NET)
description: Описание перечисления активных экземпляров SQL Server.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: d6c83ffd407a9b27a04b254fb3e9e5673a600417
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452200"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Перечисление экземпляров SQL Server (ADO.NET)

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server позволяет приложениям находить SQL Server экземпляров в текущей сети. Класс <xref:System.Data.Sql.SqlDataSourceEnumerator> предоставляет эти сведения разработчику приложения, предоставляя <xref:System.Data.DataTable>, содержащий сведения обо всех видимых серверах. Эта возвращенная таблица содержит список экземпляров серверов, доступных в сети, который совпадает со списком, предоставляемым при попытке пользователя создать новое соединение, и дополняет раскрывающийся список, содержащий все доступные серверы, в диалоговом окне **Свойства соединения**. Отображаемые результаты не всегда завершаются.  
  
> [!NOTE]
>  Как и в большинстве служб Windows, рекомендуется запускать службу обозреватель SQL с минимально возможными привилегиями. Дополнительные сведения о службе браузера SQL и о том, как управлять ее работой, см. в электронной документации на SQL Server.  
  
## <a name="retrieving-an-enumerator-instance"></a>Получение экземпляра перечислителя  
Чтобы получить таблицу с данными о доступных экземплярах SQL Server, вначале необходимо получить перечислитель с помощью общего и (или) статического свойства <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A>:  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
После получения статического экземпляра можно вызвать метод <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A>, который возвращает <xref:System.Data.DataTable>, содержащий сведения о доступных серверах:  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
Таблица, возвращенная из вызова метода, содержит следующие столбцы, которые содержат `string` значения:  
  
|Столбец|Описание|  
|------------|-----------------|  
|**ServerName**|Имя сервера.|  
|**InstanceName**|Имя экземпляра сервера. Пусто, если сервер работает как экземпляр по умолчанию.|  
|**IsClustered**|Указывает, является ли сервер частью кластера.|  
|**Версия**|Версия сервера. Пример:<br /><br /> -9.00.x (SQL Server 2005)<br />-10.0. XX (SQL Server 2008)<br />-10.50.x (SQL Server 2008 R2)<br />-11.0. XX (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Ограничения перечисления  
Все доступные серверы могут быть указаны или отсутствовать в списке. Список может различаться в зависимости от таких факторов, как время ожидания и сетевой трафик. Это может привести к тому, что список будет отличаться для двух последовательных вызовов. Будут перечислены только серверы в одной сети. Широковещательные пакеты обычно не проходят через маршрутизаторы, поэтому сервер может не отображаться в списке, но он будет стабильным во всех вызовах.  
  
Перечисленные серверы могут содержать дополнительные сведения, такие как `IsClustered` и версия. Это зависит от того, как был получен список. В списках серверов, полученных с помощью службы браузера SQL Server, присутствует больше сведений, чем в списках серверов, найденных с помощью инфраструктуры Windows и содержащих только имена.  
  
> [!NOTE]
>  Перечисление серверов доступно только при выполнении в режиме полного доверия. Сборки, работающие в среде с частичным доверием, не смогут использовать их, даже если у них есть разрешение <xref:Microsoft.Data.SqlClient.SqlClientPermission> доступа к коду (CAS).  
  
В SQL Server сведения для <xref:System.Data.Sql.SqlDataSourceEnumerator> предоставляются с использованием внешней службы Windows, называемой браузером SQL. Эта служба включена по умолчанию, но администраторы могут отключить ее или отключить, делая этот экземпляр сервера невидимым для этого класса.  
  
## <a name="example"></a>Пример  
Следующее консольное приложение получает сведения обо всех видимых экземплярах SQL Server и отображает эти сведения в окне консоли.  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)
