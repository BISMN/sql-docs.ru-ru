---
title: На компьютере сервера отчетов обнаружены устаревшие расширения (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 40d245a2-0631-470e-81b3-1feb47e028cb
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 18f90bd6c551a6240a49eed9a0ec39723851bce1
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952069"
---
# <a name="obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor"></a>На компьютере сервера отчетов обнаружены устаревшие модули (советник по переходу)
  Советник по переходу обнаружил один или несколько модулей подготовки отчетов, которые в текущей версии недоступны.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Сервер отчетов настроен для использования одного или нескольких модулей, неподдерживаемых в этой версии. В число неподдерживаемых модулей входят:  
  
-   модуль в формате HTML подготовки отчетов к просмотру для веб-компонентов Office;  
  
-   модуль в формате HTML 3.2. подготовки отчетов к просмотру  
  
 Процесс обновления может быть продолжен, но функции, которые не поддерживаются, на обновленном сервере отчетов доступны не будут.  
  
 Если эти модули все еще необходимы, не выполняйте обновление до тех пор, пока не найдете альтернативного решения. Вероятно, может потребоваться получение или создание пользовательского модуля подготовки отчетов к просмотру, предоставляющего идентичные или схожие функции.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Оцените существующий набор функций служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], чтобы определить, выполняют ли поддерживаемые функции необходимые требования.  
  
## <a name="see-also"></a>См. также  
 [Советник по переходу Reporting Services проблем &#40;обновления&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
