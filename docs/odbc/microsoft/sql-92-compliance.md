---
title: Соответствие SQL-92 | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5d8ed2818b466d16591be8b70478221d7ac84df
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063371"
---
# <a name="sql-92-compliance"></a>Соответствие SQL-92
Драйверы для баз данных ODBC рабочего стола и базового ядра Microsoft Jet не соответствует SQL-92. Они поддерживают множество функций, которые были определены в SQL-92. Некоторые функции, поддерживаемые в драйвере не поддерживаются в SQL-92. Дополнительные сведения см. в разделе *Microsoft Jet Database Engine Programmer's Guide*. Ниже приведены основные различия между ними.  
  
-   SQL, используемые драйверы для баз данных Desktop поддерживает более мощные выражения, чем SQL-92.  
  
-   Предикат BETWEEN подчиняются разным правилам.  
  
-   SQL, используемые драйверы для баз данных рабочего стола и ANSI SQL поддерживает разные ключевые слова.  
  
 Следующие функции SQL-92 не поддерживаются Microsoft Jet SQL:  
  
-   Инструкции безопасности, такие как предоставление и БЛОКИРОВКУ.  
  
-   Ключевое слово DISTINCT со ссылками на агрегатной функции.  
  
 Усовершенствования в SQL, используемое драйверами Desktop базы данных, которые не указаны, SQL-92, имеют следующие возможности:  
  
-   Оператор ПРЕОБРАЗОВАНИЯ, предоставление поддержки для перекрестных запросов.  
  
-   Дополнительные статистические функции (**StDev** и **VarP**).  
  
> [!NOTE]  
>  Драйверы для баз данных Desktop поддерживает стандартный синтаксис ANSI для % (в процентах) и _ (символ подчеркивания), не * (звездочка) и? (вопросительный знак).
