---
title: Метод getClientInfo () | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b06a5ced-b760-4c78-b17e-854ce95a1a5c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a6b68caa4abff00f113176791d06c6361c5da1e9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953118"
---
# <a name="getclientinfo-method-"></a>Метод getClientInfo ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает список, содержащий имя и текущее значение всех свойств данных клиентов, поддерживаемых драйвером JDBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.util.Properties getClientInfo()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Properties, содержащий имя и текущее значение всех свойств данных клиентов, поддерживаемых драйвером JDBC.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getClientInfo задается методом getClientInfo в интерфейсе Java. SQL. Connection.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] не поддерживает свойства сведений о клиенте. В результате этот метод возвращает пустой объект свойств.  
  
 Аналогичным образом приложения могут использовать метод [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) класса [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) для получения списка свойств сведений о клиенте, поддерживаемых драйвером. Метод [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) возвращает пустой результирующий набор.  
  
## <a name="see-also"></a>См. также:  
 [Метод getClientInfo (SQLServerConnection)](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
