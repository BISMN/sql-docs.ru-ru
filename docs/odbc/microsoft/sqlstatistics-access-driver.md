---
title: SQLStatistics (драйвер для Access) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Access Driver
ms.assetid: 6117ac77-1020-4f0c-8eed-e671c34c1f21
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 523f44924858af182e953aa1ce2b72e20cf97a45
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68047080"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (драйвер для Access)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Путь к файлу базы данных возвращается для Microsoft Access.<br /><br /> Сопоставление шаблонов не поддерживается в *szTableQualifier* аргумент.|  
|TABLE_OWNER|В этом столбце возвращается значение NULL, так как имя владельца не поддерживается.|  
|TABLE_NAME|Имя неразделенный таблицы.<br /><br /> Сопоставление шаблонов не поддерживается в *szTableName* аргумент.|  
|INDEX_QUALIFIER|Всегда возвращается значение NULL.|  
|INDEX_NAME|Зависящих от индекса.|  
|TYPE|Для ТИПА будет возвращаться только SQL_TABLE_STAT или SQL_INDEX_OTHER.|  
|SEQ_IN_INDEX|Зависящих от индекса.|  
|COLUMN_NAME|Зависящих от индекса.|  
|COLLATION|Зависящих от индекса.|  
|CARDINALITY|Возвращается только для Microsoft Access.|  
|PAGES|Всегда возвращается значение NULL.|  
  
 Фильтрация основана на уникальность ( *fUnique* аргумент). *FAccuracy* параметр учитывается.
