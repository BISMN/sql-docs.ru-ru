---
title: Метод getTrustStore (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getTrustStore Method (SQLServerDataSource)
apilocation:
- getTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 8f5850e4-8627-49a8-ba0e-b1f4014322a5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f35a71cc741411f3aad3408d366f3f70218fecdf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67978519"
---
# <a name="gettruststore-method-sqlserverdatasource"></a>Метод getTrustStore (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает путь к файлу сертификата trustStore (включая имя файла).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getTrustStore()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**, содержащее путь к файлу сертификата trustStore (включая имя файла), или значение NULL, если значение не задано.  
  
## <a name="remarks"></a>Remarks  
 Если свойство trustStore не задано, то метод [getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md) возвращает значение NULL.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
