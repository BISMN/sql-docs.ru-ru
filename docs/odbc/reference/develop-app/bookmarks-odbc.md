---
title: Закладки (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: 1d7cccc5-f847-4321-b240-28570854ee5c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bab3571ba880658d9f1a2629b899484008428083
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118788"
---
# <a name="bookmarks-odbc"></a>Закладки (ODBC)
Закладка представляет собой значение, используемое для идентификации строки данных. Содержание значения закладки понятно только драйверу или источнику данных. Например, оно может быть простым (номером строки) или сложным (адрес на диске). Закладки в ODBC, немного отличаются от закладки в реальных электронной документации. В реальных книгой средство чтения помещает закладку на конкретной странице, а затем поиск эту закладку, чтобы вернуться на страницу. В ODBC приложение запрашивает закладку для конкретной строки, сохраняет ее и передает обратно курсору для возврата к строке. Таким образом закладки в ODBC похожи на модуль чтения начать записывать номер страницы, запоминать его, а затем выполните поиск страницы.  
  
 Чтобы определить драйверы закладок, приложение вызывает **SQLGetInfo** с параметром SQL_BOOKMARK_PERSISTENCE. Биты в этом значении описывают, какие операции закладки остается после сборки, такие как закладки, по-прежнему действительны ли после закрытия курсора.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Типы закладок](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [Извлечение закладок](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [Прокрутка по закладкам](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [Обновление, удаление или выборка по закладкам](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [Сравнение закладок](../../../odbc/reference/develop-app/comparing-bookmarks.md)
