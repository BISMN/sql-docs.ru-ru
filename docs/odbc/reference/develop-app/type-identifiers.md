---
title: Введите идентификаторы | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 79aa4de5d722208195477f7ffef53cac6c61a2de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093024"
---
# <a name="type-identifiers"></a>Идентификаторы типов
Для описания типов данных SQL и C, ODBC определяет два набора *введите идентификаторы*. Идентификатор типа описывает тип SQL столбца или C буфера. Это **#define** значение и является обычно передается в качестве аргумента функции или возвращены в метаданных.  
  
 Например, следующий вызов **SQLBindParameter** связывает переменной типа SQL_DATE_STRUCT параметр даты в инструкции SQL. Идентификатор типа C SQL_C_TYPE_DATE указывает тип *даты* переменной и идентификатор типа SQL SQL_TYPE_DATE тип динамического параметра.  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
