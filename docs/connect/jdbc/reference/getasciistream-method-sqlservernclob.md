---
title: Метод getAsciiStream (SQLServerNClob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ff1d47e4-572a-4169-a631-ac261f7642b3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22177442dcec9fb873d4a824b73845ce6fc9bfdf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954122"
---
# <a name="getasciistream-method-sqlservernclob"></a>Метод getAsciiStream (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение **NCLOB** , обозначенное этим объектом **NCLOB** как поток ASCII.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.InputStream getAsciiStream()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект InputStream, содержащий данные NCLOB.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getAsciiStream задается методом getAsciiStream в интерфейсе Java. SQL. SQLServerNClob.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
