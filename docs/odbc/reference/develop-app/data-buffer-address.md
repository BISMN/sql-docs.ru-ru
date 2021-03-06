---
title: Адрес буфера данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7cd157edd6111dec29ae238a1c383879e66ac0b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067430"
---
# <a name="data-buffer-address"></a>Адрес буфера данных
Приложение передает адрес буфера данных драйвера в аргументе, часто с именем *ValuePtr* или таким же именем. Например, в вызове **SQLBindCol**, приложение указывает адрес *даты* переменной:  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Как упоминалось в [распределение и освобождение буферов](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) разделе адрес отложенного буфера должен оставаться действительным, пока буфер не связан.  
  
 Если он запрещен в частности, адрес буфера данных может быть пустым указателем. Для буферов, используемых для отправки данных в драйвер в результате драйвер пропустили информацию, обычно содержащихся в буфере. Для буферов, используемых для получения данных от драйвера в результате драйвер не будет возвращать значение. В обоих случаях драйвер пропускает соответствующего аргумента длина буфера данных.
