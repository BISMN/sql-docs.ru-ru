---
title: Метод getConnection (java.lang.String, java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 78db89d6-a8a0-4116-8885-548e627220ed
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87d3dfc2183bdc00261417a024507b41ea5fde28
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952746"
---
# <a name="getconnection-method-javalangstring-javalangstring"></a>Метод getConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Пытается установить соединение с источником данных, представляемым этим объектом [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md), с использованием заданного имени пользователя и пароля.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Connection getConnection(java.lang.String username,  
                                         java.lang.String password)  
```  
  
#### <a name="parameters"></a>Параметры  
 *username*  
  
 Значение типа **String**, содержащее имя пользователя.  
  
 *password*  
  
 Значение типа **String**, содержащее пароль.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Этот метод соединения задается методом соединения в интерфейсе javax. SQL. DataSource.  
  
 Вызов метода соединения с непустым именем пользователя или паролем заменит свойства имени пользователя и пароля, заданные для класса SQLServerDataSource при инициализации объекта SQLServerConnection. Например, если вызывающий объект вызвал методы [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) и [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) в источнике данных, а затем вызывает метод getConnection и передает имя пользователя, отличное от NULL, или пароль, отличный от NULL, то имя пользователя и пароль, заданные методами setUser и setPassword, будут заменены именем пользователя и паролем, переданными в метод getConnection.  
  
> [!NOTE]  
>  Имя пользователя и пароль, которые заданы в URL-адресе путем вызова метода [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md), не будут изменяться в этом случае.  
  
## <a name="see-also"></a>См. также:  
 [Метод getConnection (SQLServerDataSource)](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
