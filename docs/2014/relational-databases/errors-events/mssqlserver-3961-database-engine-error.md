---
title: MSSQLSERVER_3961 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f12e70423905a78eddecb93a8b4623c96a6f0322
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62914086"
---
# <a name="mssqlserver3961"></a>MSSQLSERVER_3961
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3961|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|XACT_METADATA_INVALID|  
|Текст сообщения|Ошибка транзакции в режиме изоляции моментального снимка в базе данных «%.*ls»: объект, к которому производится обращение в данной инструкции, был изменен инструкцией DDL другой, параллельной транзакции после начала данной транзакции.  Это запрещено, поскольку управление версиями метаданных не поддерживается. Одновременное обновление метаданных может привести к несогласованности при совместном использовании с режимом изоляции моментального снимка.|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка может произойти при запросе метаданных в режиме изоляции моментального снимка при одновременном обновлении этих метаданных параллельной инструкцией DDL. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает управление версиями метаданных. Поэтому не все операции DDL могут выполняться в явной транзакции, работающей с уровнем изоляции моментального снимка. Неявная транзакция, по определению, — это единственная инструкция, для которой возможно выполнение семантики изоляции моментального снимка, даже для инструкций DDL. Следующие инструкции DDL не разрешены в режиме изоляции моментального снимка после инструкции BEGIN TRANSACTION: ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME или любые инструкции DDL среды выполнения (CLR). Эти инструкции разрешены к использованию в неявных транзакциях, работающих при уровне изоляции моментального снимка. Неявная транзакция, по определению, — это единственная инструкция, для которой возможно выполнение семантики изоляции моментального снимка, даже для инструкций DDL.  
  
## <a name="user-action"></a>Действие пользователя  
 Перед запросом метаданных измените уровень изоляции моментального снимка на другой уровень изоляции, например на уровень изоляции зафиксированной операции чтения.  
  
  
