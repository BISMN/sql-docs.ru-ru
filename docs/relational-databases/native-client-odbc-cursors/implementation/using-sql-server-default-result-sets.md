---
title: Использование SQL Server результирующих наборов по умолчанию | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dfd3ef8ec56f458bb57b1898a1bf7212534b7af1
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73784485"
---
# <a name="using-sql-server-default-result-sets"></a>Использование результирующих наборов по умолчанию в SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Атрибутами курсора ODBC по умолчанию являются:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Каждый раз, когда для этих атрибутов заданы значения по умолчанию, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует результирующий набор по умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Результирующие наборы по умолчанию могут использоваться для любой инструкции SQL, поддерживаемой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], и являются самым эффективным методом передачи всего результирующего набора клиенту.  
  
 в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] появилась поддержка режима MARS; у приложений теперь может быть несколько активных результирующих наборов по умолчанию для каждого подключения. По умолчанию режим MARS не включен.  
  
 До версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] принимаемые по умолчанию результирующие наборы не поддерживали несколько активных инструкций для одного соединения. После выполнения инструкции SQL для соединения сервер не принимает команд от клиента в этом соединении до тех пор, пока не будут обработаны все строки результирующего набора. Исключение составляют запросы на отмену оставшейся части результирующего набора. Чтобы отменить оставшуюся часть частично обработанного результирующего набора, вызовите [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) или [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md) , указав для параметра *параметром fOption* значение SQL_CLOSE. Чтобы завершить частично обработанный результирующий набор и проверить наличие другого результирующего набора, вызовите [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md). Если приложение ODBC пытается выполнить команду в обработчике соединения до того, как результирующий набор по умолчанию будет полностью обработан, вызов создает SQL_ERROR и вызов **SQLGetDiagRec** возвращает:  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Способы реализации курсоров](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
