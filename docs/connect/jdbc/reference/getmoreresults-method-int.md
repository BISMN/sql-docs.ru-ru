---
title: Метод getMoreResults (int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMoreResults (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6419e5a8-8b3a-4d5b-8226-95865c52c723
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 08760680774b2e760b66d9e210c4ef939872444e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981777"
---
# <a name="getmoreresults-method-int"></a>Метод getMoreResults (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Переходит к следующему результату этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) и обрабатывает все открытые объекты результирующего набора в соответствии с инструкциями, заданными указанным режимом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final boolean getMoreResults(int mode)  
```  
  
#### <a name="parameters"></a>Параметры  
 *mode*  
  
 Значение **int**, указывающее порядок обработки открытых объектов результирующего набора. Это должна быть одна из следующих констант:  
  
 CLOSE_CURRENT_RESULT  
  
 KEEP_CURRENT_RESULT (не поддерживается драйвером JDBC)  
  
 CLOSE_ALL_RESULTS  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если возвращенный результат — это результирующий набор. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getMoreResults задается методом getMoreResults в интерфейсе Java. SQL. Statement.  
  
 Если метод getMoreResults вызван перед получением результатов, то он работает в соответствии со значением аргумента *mode* и переходит к следующему результату.  
  
> [!NOTE]  
>  Драйвер JDBC не поддерживает использование константы KEEP_CURRENT_RESULT. Если эта константа используется, вызывается исключение.  
  
## <a name="see-also"></a>См. также:  
 [Метод getMoreResults (SQLServerStatement)](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
