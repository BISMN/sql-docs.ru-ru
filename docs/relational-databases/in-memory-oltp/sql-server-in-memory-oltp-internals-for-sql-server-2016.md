---
title: Внутренние компоненты выполняющейся в памяти OLTP для SQL Server 2016 | Документация Майкрософт
ms.custom: ''
ms.date: 09/14/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b14da361-a6b8-4d85-b196-7f2f13650f44
author: jodebrui
ms.author: jodebrui
ms.openlocfilehash: ca36f8c9716b9160b4d6eaeee26201bf03b42927
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111746"
---
# <a name="sql-server-in-memory-oltp-internals-for-sql-server-2016"></a>Внутренние компоненты выполняющейся в памяти OLTP SQL Server для SQL Server 2016
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**Сводка** выполняемая в памяти OLTP, которую еще часто называют Hekaton, была представлена в SQL Server 2014.
Эта многофункциональная технология позволяет использовать большие объемы памяти и десятки ядер для повышения производительности операций OLTP в 30–40 раз! SQL Server 2016 продолжает развивать выполняющуюся в памяти OLTP: были сняты многие ограничения, найденные в SQL Server 2014, улучшены внутренние алгоритмы обработки, что позволяет выполняющейся в памяти OLTP предоставлять еще больше лучших возможностей. В этом документе описывается реализация выполняемой в памяти OLTP из SQL Server 2016 в SQL Server 2016 RTM. Используя выполняемую в памяти OLTP, таблицы можно объявить как "оптимизированные для операций в памяти", что позволит использовать возможности выполняемой в памяти OLTP. Таблицы, оптимизированные для обработки в памяти, являются полностью транзакционными, доступ к ним можно получить при помощи Transact-SQL. Хранимые процедуры, триггеры и скалярные UDF Transact-SQL можно скомпилировать в машинном коде, чтобы еще больше повысить производительность таблиц, оптимизированных для обработки в памяти. Подсистема рассчитана на большое число параллельных операций без блокировок.    
  
**Автор:** Кален Деланей (Kalen Delaney)  
  
**Технические редакторы:** Сунил Агарвал (Sunil Agarwal) и Хос де Брюин (Jos de Bruijn)  
  
**Опубликовано:** Июнь 2016 г.  
  
**Применимо к:** SQL Server 2016  
  
Для ознакомления скачайте документ [Внутренние компоненты выполняющейся в памяти OLTP SQL Server для SQL Server 2016](https://download.microsoft.com/download/8/3/6/8360731A-A27C-4684-BC88-FC7B5849A133/SQL_Server_2016_In_Memory_OLTP_White_Paper.pdf) .   
