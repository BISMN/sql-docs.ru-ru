---
title: Метод Precision (SQLServerParameterMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getPrecision
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8bd79484-bab6-423b-978f-d7ec7132ebeb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b0c6b7d8c69e1cc6bc4a9e8d239c3a47c24573d9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980778"
---
# <a name="getprecision-method-sqlserverparametermetadata"></a>Метод getPrecision (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает число десятичных разрядов для указанного параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getPrecision(int param)  
```  
  
#### <a name="parameters"></a>Параметры  
 *param*  
  
 Значение **int**, указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, указывающее точность заданного параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод метода Precision задается методом ParameterMetaData в интерфейсе Java. SQL.  
  
 Для числовых типов этот метод возвращает число десятичных разрядов. Для символьных типов он возвращает максимальную длину в символах. Для двоичных типов он возвращает максимальную длину в байтах. Если число разрядов неизвестно, этот метод возвращает значение 0.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Элементы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Класс SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
