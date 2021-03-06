---
title: Поля дескриптора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], fields
- header fields [ODBC]
- record fields [ODBC]
ms.assetid: f38623c8-fdd4-4601-b1f0-97c593d31177
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5025bf5eee4b0b65342e7ce47cbbde4ae9ef6b7e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106174"
---
# <a name="descriptor-fields"></a>Поля дескриптора
Содержать дескрипторы *заголовок* и *записи* поля, полностью описывающие столбцов или параметров.  
  
 Дескриптор содержит копию одного из следующих полей заголовка. Изменение поля заголовка, влияет на все столбцы или параметры.  
  
|||  
|-|-|  
|SQL_DESC_ALLOC_TYPE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_COUNT|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Дескриптор содержит ноль или более записей дескриптора. Каждая запись описывает столбец или параметр, в зависимости от типа дескриптора. При привязке параметра или столбца, новая запись добавляется в дескриптор. Если столбца или параметра отсутствует привязка, запись удаляется из дескриптора. Каждая запись содержит копию одного из следующих полей:  
  
|||  
|-|-|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_DESC_LOCAL_TYPE_NAME|  
|SQL_DESC_BASE_COLUMN_NAME|SQL_DESC_NAME|  
|SQL_DESC_BASE_TABLE_NAME|SQL_DESC_NULLABLE|  
|SQL_DESC_CASE_SENSITIVE|SQL_DESC_OCTET_LENGTH|  
|SQL_DESC_CATALOG_NAME|SQL_DESC_OCTET_LENGTH_PTR|  
|SQL_DESC_CONCISE_TYPE|SQL_DESC_PARAMETER_TYPE|  
|SQL_DESC_DATA_PTR|SQL_DESC_PRECISION|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_DESC_SCALE|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQL_DESC_SCHEMA_NAME|  
|SQL_DESC_DISPLAY_SIZE|SQL_DESC_SEARCHABLE|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_DESC_TABLE_NAME|  
|SQL_DESC_INDICATOR_PTR|SQL_DESC_TYPE|  
|SQL_DESC_LABEL|SQL_DESC_TYPE_NAME|  
|SQL_DESC_LENGTH|SQL_DESC_UNNAMED|  
|SQL_DESC_LITERAL_PREFIX|SQL_DESC_UNSIGNED|  
|SQL_DESC_LITERAL_SUFFIX|SQL_DESC_UPDATABLE|  
  
 Многие атрибуты инструкции соответствуют поле заголовка дескриптора. Установка этих атрибутов посредством вызова **SQLSetStmtAttr** и соответствующее поле заголовка дескриптора, вызвав **SQLSetDescField** дают одинаковый результат. То же самое касается **SQLGetStmtAttr** и **SQLGetDescField**, каждый из которых получить эти сведения. Вызов функций инструкции вместо функций дескриптора преимущество дескриптора не поддерживает требуется получить.  
  
 Можно задать следующие поля заголовка, задав атрибуты инструкции.  
  
|||  
|-|-|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Число записей](../../../odbc/reference/develop-app/record-count.md)  
  
-   [Связанные записи дескриптора](../../../odbc/reference/develop-app/bound-descriptor-records.md)  
  
-   [Отложенные поля](../../../odbc/reference/develop-app/deferred-fields.md)  
  
-   [Проверка согласованности](../../../odbc/reference/develop-app/consistency-check.md)
