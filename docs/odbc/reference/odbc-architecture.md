---
title: Архитектура ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 781a214d3ca059a442680c332d79aad48914976c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111224"
---
# <a name="odbc-architecture"></a>Архитектура ODBC
В архитектуре ODBC имеется четыре компонента:  
  
-   **Приложение** выполняет обработку и вызовы функций ODBC для отправки инструкций SQL и получения результатов.  
  
-   **Диспетчер драйверов** загружает и выгружает драйверы от имени приложения. Функция ODBC процессов вызывает или передает их драйверу.  
  
-   **Драйвер** вызывает функции ODBC процессы, отправляет запросы SQL к определенному источнику данных и возвращает результаты в приложение. При необходимости драйвер изменяет запрос приложения, чтобы запрос соответствует синтаксису поддерживаемому связанные СУБД.  
  
-   **Источник данных** Consists данных требуется доступ и операционной системы, СУБД и платформы сети (если таковые имеются) используется для доступа к СУБД.  
  
 Обратите внимание на следующие аспекты архитектуры ODBC. Первый, несколько драйверов и источников данных могут существовать, что позволяет приложению одновременно получить доступ к данным из нескольких источников данных. Во-вторых, API-Интерфейс ODBC используется в двух местах: между приложением и диспетчера драйверов, а также между диспетчера драйверов и каждого драйвера. Интерфейс между диспетчера драйверов и драйверов иногда называется *интерфейс поставщика службы,* или *SPI*. Для ODBC программный интерфейс (API) и интерфейс поставщика службы (SPI) одинаковы; то есть диспетчера драйверов и каждого драйвера имеют один и тот же интерфейс для тех же функций.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Приложения](../../odbc/reference/applications.md)  
  
-   [Диспетчер драйверов](../../odbc/reference/the-driver-manager.md)  
  
-   [Драйверы](../../odbc/reference/drivers.md)  
  
-   [Источники данных](../../odbc/reference/data-sources.md)
