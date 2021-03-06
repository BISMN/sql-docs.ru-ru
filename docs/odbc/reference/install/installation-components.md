---
title: Компоненты установки | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
- ODBC [ODBC], component installation
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 34d1b6d143f6f40d73e2feeb0b718f3c3b3248fe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094136"
---
# <a name="installation-components"></a>Компоненты установки
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включена в операционную систему Windows. ODBC следует только явным образом установить в более ранних версиях Windows.  
  
 Начнется процесс установки, когда пользователь запускает программу установки. Программа установки работает в сочетании с *библиотека DLL установщика* и *DLL-файлов установки драйвера* для каждого драйвера. Программа установки и библиотека DLL установщика используйте аргументы в **SQLInstallDriverEx** и **SQLInstallTranslatorEx** функции, чтобы определить, какие файлы для копирования или удаления для каждого компонента. Ниже показана связь между этими компонентами установки.  
  
 ![Связь между компонентами установки](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  Файл Odbc.inf, который использовался в ODBC *2.x* компонент не используется для описания файлы, необходимые для каждого ODBC в ODBC *3.x*. Драйверы, поставляемые ODBC *3.x* компоненты не нужно создавать файл Odbc.inf. Удаление **SQLInstallDriver** и **SQLInstallODBC**и об использовании **SQLInstallTranslator**, к просмотру Odbc.inf ненужные. Сведения о драйвере, который был в разделах слово Driver Odbc.inf теперь предоставляются в *lpszDriver* аргумента в **SQLInstallDriverEx**. Сведения перевода, используются в [ODBC Translator] и разделах спецификации Translator Odbc.inf теперь предоставляются в *lpszTranslator* аргумент **SQLInstallTranslatorEx**. Эти изменения разрешите установщику ODBC можно более пригодным для переноса на другие платформы.  
  
 Дополнительные сведения об этих компонентах см. в следующих разделах, в конце этого раздела.  
  
-   [Программа установки](../../../odbc/reference/install/setup-program.md)  
  
-   [Библиотека DLL установщика](../../../odbc/reference/install/installer-dll.md)  
  
-   [Библиотека DLL программы установки драйвера](../../../odbc/reference/install/driver-setup-dll.md)
