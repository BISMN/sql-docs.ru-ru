---
title: Метод getCharacterStream (long, long) (SQLServerNClob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5a8028bc-c877-4668-b662-0746d462040e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 10cd57cff29c73a2b99d1489eb122eed37859768
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953272"
---
# <a name="getcharacterstream-method-long-long-sqlservernclob"></a>Метод getCharacterStream (long, long) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает данные **NCLOB** в виде объекта **Reader** или потока символов с указанной позицией и длиной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                  long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *POS*  
  
 Значение **long**, определяющее смещение до первого символа извлекаемого фрагмента значения.  
  
 *length*  
  
 Значение **long**, определяющее длину в символах для извлекаемого фрагмента значения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Reader, содержащий данные **NCLOB**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getCharacterStream задается методом getCharacterStream в интерфейсе Java. SQL. NClob.  
  
## <a name="see-also"></a>См. также:  
 [Метод getCharacterStream (SQLServerNClob)](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
