---
title: Синтаксис литерала интервала | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], interval
- interval literals [ODBC]
- ODBC literals [ODBC], interval
ms.assetid: 2f2d22c1-51d6-4055-9f5a-53bc31e9fea0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6352a5ae894adb09f714a78386bfecfa3ce1df77
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041622"
---
# <a name="interval-literal-syntax"></a>Синтаксис литерала интервала
Для интервала литералы в ODBC используется следующий синтаксис.  
  
 *interval-literal ::= INTERVAL* [+ *&#124;* -] *interval-string interval-qualifier*  
  
 *interval-string* ::= *quote* { *year-month-literal* &#124; *day-time-literal* } *quote*  
  
 *year-month-literal* ::= *years-value* &#124; [*years-value* -] *months-value*  
  
 *day-time-literal* ::= *day-time-interval* &#124; *time-interval*  
  
 *день интервала* :: = *значение дней* [*значение часов* [:*значение минут*[:*значение секунд*]]]  
  
 *time-interval* ::= *hours-value* [:*minutes-value* [:*seconds-value* ] ]  
  
 &#124;*значение минут* [:*значение секунд* ]  
  
 &#124;*значение секунд*  
  
 *years-value* ::= *datetime-value*  
  
 *months-value* ::= *datetime-value*  
  
 *days-value* ::= *datetime-value*  
  
 *hours-value* ::= *datetime-value*  
  
 *minutes-value* ::= *datetime-value*  
  
 *seconds-value* ::= *seconds-integer-value* [.[*seconds-fraction*] ]  
  
 *seconds-integer-value* ::= *unsigned-integer*  
  
 *seconds-fraction* ::= *unsigned-integer*  
  
 *datetime-value* ::= *unsigned-integer*  
  
 *interval-qualifier* ::= *start-field* TO *end-field* &#124; *single-datetime-field*  
  
 *поле начала* :: = *не секунду поля даты и времени* [(*интервал начальные поля точности* )]  
  
 *end-field* ::= *non-second-datetime-field* &#124; SECOND[(*interval-fractional-seconds-precision*)]  
  
 *поля для даты и времени одного* :: = *не секунду поля даты и времени —* [(*интервал начальные поля точности*)] &#124; второй [(*интервал начальные поля точности*  [, (*интервал--секунд — точность в долях секунды*)]  
  
 *datetime-field* ::= *non-second-datetime-field* &#124; SECOND  
  
 *не секунду поля даты и времени* :: = год &#124; месяц &#124; день &#124; час &#124; МИНУТУ  
  
 *interval-fractional-seconds-precision* ::= *unsigned-integer*  
  
 *interval-leading-field-precision* ::= *unsigned-integer*  
  
 *quote* ::= '  
  
 *unsigned-integer* ::= *digit...*
