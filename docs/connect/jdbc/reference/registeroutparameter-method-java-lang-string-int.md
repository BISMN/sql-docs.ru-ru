---
title: Метод registerOutParameter для ввода | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d00242c-4d9c-42cc-86bb-b76f5ef876b8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cdd197be6327b84a6c299239f1198fe005dff0f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975904"
---
# <a name="registeroutparameter-method-javalangstring-int"></a>Метод registerOutParameter (java.lang.String, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Регистрирует параметр OUT с указанным именем для заданного типа JDBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n)  
```  
  
#### <a name="parameters"></a>Параметры  
 *s*  
  
 Значение типа **String**, содержащее имя параметра.  
  
 *n*  
  
 Код типа JDBC, определенный в java.sql.Types.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод registerOutParameter задается методом registerOutParameter в интерфейсе Java. SQL. CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод registerOutParameter (SQLServerCallableStatement)](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
