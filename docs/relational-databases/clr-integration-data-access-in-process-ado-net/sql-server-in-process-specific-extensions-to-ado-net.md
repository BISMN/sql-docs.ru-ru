---
title: Специальные расширения SQL Server в процессе для ADO.NET | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
author: rothja
ms.author: jroth
ms.openlocfilehash: b1ed0cf58c34506ce12dd04bf529a80d44a03d2d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67951681"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>Внутрипроцессные расширения SQL Server для ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Существует четыре основных функциональных расширения для ADO.NET, которые специально предназначены для внутрипроцессного использования. Эти расширения подробно рассматриваются в следующих разделах.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Объект SqlContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
 Этот класс предоставляет доступ к другим расширениям, абстрагируя контекст вызывающего объекта процедуры SQL Server, которая выполняет управляемый внутрипроцессный код.  
  
 [Объект SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)  
 Этот класс содержит процедуры для отправки табличных результатов и сообщений клиенту.  
  
 [Объект SqlTriggerContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)  
 Этот класс предоставляет сведения о контексте, в котором выполняется триггер.  
  
 [Объект SqlDataRecord](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)  
 Класс SqlDataRecord представляет одну строку данных вместе со связанными с ней метаданными, позволяя хранимым процедурам возвращать клиенту пользовательские результирующие наборы.  
  
  
