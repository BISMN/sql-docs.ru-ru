---
title: Подключение и извлечение данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bd4751fe3d1acb7119c87e39ecd8694a0fa83c19
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028218"
---
# <a name="connecting-and-retrieving-data"></a>Подключение к данным и их извлечение

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

При работе с драйвером [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] есть два основных способа установить подключение к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Во-первых, можно задать свойства подключения в URL-адресе подключения, а затем вызвать метод getConnection класса DriverManager для возвращения объекта [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
> [!NOTE]  
> Список свойств подключения, поддерживаемых драйвером JDBC, см. в разделе [Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
По второму методу свойства подключения определяются с помощью методов задания класса [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) и последующего вызова метода [getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md), возвращающего объект SQLServerConnection.  
  
В разделах этой статьи описаны различные способы подключения к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и показаны приемы для извлечения данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
| Раздел                                                                | Описание                                                                                                                                                   |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Пример URL-адреса подключения](../../connect/jdbc/connection-url-sample.md) | Описывает подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по URL-адресу и последующее использование инструкции SQL для извлечения данных. |
| [Пример источника данных](../../connect/jdbc/data-source-sample.md)       | Описывается порядок использования источника данных для соединения с SQL Server и последующего использования хранимой процедуры для извлечения данных.                                                 |
  
## <a name="see-also"></a>См. также раздел

[Примеры приложений JDBC Driver](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
