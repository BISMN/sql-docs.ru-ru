---
title: Метод prepareStatement (java.lang.String, int, int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5bb96dbe-f673-41b5-911b-8f661cca071a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5b192f9055394393c48fa19eda697791ddfe3fa2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976158"
---
# <a name="preparestatement-method-javalangstring-int-int"></a>Метод prepareStatement (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает объект [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), который создает объекты [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) с заданным типом и видом параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sSql,  
                                                   int resultSetType,  
                                                   int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sSql*  
  
 Значение **String**, содержащее инструкцию SQL.  
  
 *resultSetType*  
  
 Значение **int**, указывающее тип результирующего набора.  
  
 *ресултсетконкурренци*  
  
 Значение **int**, указывающее тип параллелизма результирующего набора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект PreparedStatement.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод prepareStatement задается методом prepareStatement в интерфейсе Java. SQL. Connection.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-methods.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
