---
title: Последовательность записей состояния | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 0e0436cc-230f-44b0-b373-04a57e83ee76
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 67eac22a630305f32f141ea18861e5638445f19b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094351"
---
# <a name="sequence-of-status-records"></a>Последовательность записей состояния
Если два или более состояние записи, диспетчер драйверов и драйверов ранжировать согласно следующим правилам. Запись с наивысшим рангом является первой записью. Источник записи (диспетчера драйверов, драйвер, шлюза и т. д.) не считается когда ранжирование записей.  
  
-   **Ошибки** записи состояния, которые описывают ошибки имеют наивысший ранг. Помимо записи об ошибках записи, которые указывают на сбой транзакции или возможных транзакций сбоя outrank все остальные записи. Если две или более записей описать то же условие ошибки, SQLSTATE, определенных в спецификации Open CLI группы (классы 03 через ГЦ) outrank SQLSTATE, определенных для ODBC и определяемые драйвером.  
  
-   **Значения данных нет определенной реализацией** записи состояния, которые описывают значения определенное драйвером нет данных (класс 02) имеют второй наивысшим рангом.  
  
-   **Предупреждения** записи состояния, описывающих предупреждения (класс 01) имеют низкий ранг. Если две или более записей описывают то же условие предупреждение, предупреждение SQLSTATE, определенных в спецификации Open CLI группы outrank SQLSTATE, определенных для ODBC и определяемые драйвером.  
  
 Если два или несколько записей с наивысшим рангом, не определено, какая запись является первой записью. Не определен порядок других записей. В частности поскольку предупреждения появляются перед ошибки, приложения необходимо проверять все записи о состоянии, если функция возвращает значение, отличное от SQL_SUCCESS.
