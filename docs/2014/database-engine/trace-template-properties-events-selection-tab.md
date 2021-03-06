---
title: Свойства шаблона (вкладка «Выбор событий») трассировки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetemplateproperties.eventsselection.f1
helpviewer_keywords:
- Trace Template Properties dialog box
ms.assetid: 5b202457-ab42-4902-8012-7f3f40aa09f5
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8d86515646236916a9c651c7fa02923b88b995cd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66089548"
---
# <a name="trace-template-properties-events-selection-tab"></a>Свойства шаблона трассировки (вкладка «Выбор событий»)
  С помощью вкладки **Выбор событий** в окне **Свойства шаблона трассировки** просмотрите, измените или задайте классы событий и столбцы данных, которые будут включены в шаблон трассировки приложения [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] .  
  
## <a name="options"></a>Параметры  
 Столбец**События**  
 С помощью установки или снятия флажка в столбце событий укажите события для трассировки. События упорядочиваются по категориям событий.  
  
 Если выбран параметр **Использовать существующий шаблон в качестве основы** на вкладке **Общие** , то события автоматически выбираются в соответствии с указанным шаблоном. Дополнительные сведения о классах событий см. в разделе [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
 Столбцы данных  
 С помощью установки флажка, соответствующего нужному событию и столбцу данных, укажите столбцы данных для трассировки. Для каждого трассируемого события по умолчанию выбираются все соответствующие столбцы событий, если установлен флажок, соответствующий этому событию. Если установлен флажок **Использовать существующий шаблон в качестве основы** на вкладке **Общие** , то столбцы данных и фильтры автоматически выбираются в соответствии с указанным шаблоном.  
  
 Для определения фильтра щелкните заголовок столбца данных и введите критерии фильтра. Отфильтрованные столбцы данных отображаются значком фильтра слева от метки столбца в диалоговом окне **Изменение фильтра** .  
  
 **Показать все события**  
 Показать все доступные события. Этот параметр включен по умолчанию при создании нового шаблона, не основанного на существующем шаблоне. Снимите флажок, чтобы скрыть все события, не выбранные в сетке **Выбор событий** .  
  
 **Показать все столбцы**  
 Показать все доступные столбцы данных. Этот параметр включен по умолчанию при создании нового шаблона, не основанного на существующем шаблоне. Снимите флажок, чтобы скрыть все столбцы данных, не выбранные в сетке **Выбор событий** .  
  
 **Фильтры столбцов**  
 Открывает окно **Изменение фильтра**, в котором слева от метки столбца данных показан значок фильтра. Используйте диалоговое окно **Изменение фильтра** для изменения фильтров столбцов.  
  
 **Систематизировать столбцы**  
 Изменяет порядок следования столбцов в трассировке и группирует результаты по одному или нескольким столбцам.  
  
## <a name="see-also"></a>См. также  
 [Указание столбцов событий и данных для файла трассировки (приложение SQL Server Profiler)](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Упорядочивание столбцов, отображаемых в трассировке &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)   
 [Фильтрация событий в трассировке &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)   
 [Просмотр сведений фильтров (приложение SQL Server Profiler)](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)   
 [Изменение фильтра &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)   
 [Шаблоны и разрешения приложения SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Приложение SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
