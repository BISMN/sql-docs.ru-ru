---
title: Поведение курсора | Документация Майкрософт
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- version-based optimistic concurrency
- cursors [ODBC], cursor behaviors
- ODBC applications, cursors
- SQL_ATTR_CURSOR_SENSITIVITY option
- SQL_ATTR_CURSOR_SCROLLABLE option
- sensitivity behavior of cursor
- ODBC cursors, cursor behaviors
ms.assetid: 742ddcd2-232b-4aa1-9212-027df120ad35
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 06a19a173fdd6f70b19e9a63c214616909708eec
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73784730"
---
# <a name="cursor-behaviors"></a>Режимы работы курсоров
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC поддерживает параметры ISO, предназначенные для указания поведения курсоров, задавая их прокручиваемость и чувствительность. Эти поведения задаются путем установки параметров SQL_ATTR_CURSOR_SCROLLABLE и SQL_ATTR_CURSOR_SENSITIVITY для вызова [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реализует эти параметры, запрашивая серверные курсоры со следующими характеристиками.  
  
|Параметры режима работы курсоров|Запрошенные характеристики серверного курсора|  
|------------------------------|---------------------------------------------|  
|SQL_SCROLLABLE и SQL_SENSITIVE|Курсор, управляемый набором ключей, и основанный на версии оптимистический параллелизм|  
|SQL_SCROLLABLE и SQL_INSENSITIVE|Статический курсор и параллелизм в режиме «только чтение»|  
|SQL_SCROLLABLE и SQL_UNSPECIFIED|Статический курсор и параллелизм в режиме «только чтение»|  
|SQL_NONSCROLLABLE и SQL_SENSITIVE|Однопроходный курсор и основанный на версии оптимистический параллелизм|  
|SQL_NONSCROLLABLE и SQL_INSENSITIVE|Результирующий набор по умолчанию (последовательный доступ, только чтение)|  
|SQL_NONSCROLLABLE и SQL_UNSPECIFIED|Результирующий набор по умолчанию (последовательный доступ, только чтение)|  
  
 Для оптимистичного параллелизма на основе версий требуется столбец **отметок времени** в базовой таблице. Если для таблицы, не имеющей столбца **timestamp** , запрашивается управление оптимистичным параллелизмом на основе версий, то сервер использует оптимистичный параллелизм на основе значений.  
  
## <a name="scrollability"></a>Прокручиваемость  
 Если SQL_ATTR_CURSOR_SCROLLABLE имеет значение SQL_SCROLLABLE, курсор поддерживает все различные значения параметра *Фетчориентатион* [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Если SQL_ATTR_CURSOR_SCROLLABLE имеет значение SQL_NONSCROLLABLE, курсор поддерживает только значение *фетчориентатион* , равное SQL_FETCH_NEXT.  
  
## <a name="sensitivity"></a>Чувствительность  
 Если параметр SQL_ATTR_CURSOR_SENSITIVITY имеет значение SQL_SENSITIVE, курсор отражает изменения данных, произведенные текущим пользователем или зафиксированные другими пользователями. Если параметр SQL_ATTR_CURSOR_SENSITIVITY имеет значение SQL_INSENSITIVE, курсор не отражает изменения данных.  
  
## <a name="see-also"></a>См. также раздел  
 Использование [свойств курсора](properties/cursor-properties.md) [(ODBC)](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md) 
  
  
