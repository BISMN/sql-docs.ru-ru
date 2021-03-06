---
title: Изменение фильтра (SQL Server Profiler) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], modifying
- modifying filters, modifying
- filters [SQL Server], traces
ms.assetid: 8b317813-4918-4485-b930-77b1951aa00c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ee101f13c7856b2701a02d1446a0ad8e5a4e2d24
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074899"
---
# <a name="modify-a-filter-sql-server-profiler"></a>изменить фильтр (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Фильтры добавляются в шаблоны трассировки, которые содержат определение трассировки, чтобы ограничить число событий, собираемых трассировкой. Ограничение числа собираемых событий может уменьшить влияние трассировки на производительность. Если были установлены фильтры для шаблона трассировки, и обнаружилось, что трассировка не собирает необходимый вид сведений, то фильтр может быть отредактирован.  
  
### <a name="to-modify-a-filter"></a>Изменение фильтра  
  
1.  В приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]откройте проект шаблона трассировки, который необходимо изменить. В меню **Файл** выберите пункт **Шаблоны**и далее пункт **Изменить шаблон**.  
  
2.  На вкладке **Общие** диалогового окна **Свойства шаблона трассировки** выберите шаблон из списка **Выбор имени шаблона** .  
  
3.  Перейдите на вкладку **Выбор событий** .  
  
     Вкладка **Выбор событий** содержит сетку. Сетка — это таблица, которая содержит каждый из классов событий, доступных для трассировки. На каждый класс событий в таблице приходится по одной строке. Классы событий могут незначительно различаться в зависимости от типа и версии сервера, к которому они подключены. Классы событий идентифицируются в столбце **События**сетки и группируются по категориям событий. В оставшихся столбцах перечислены столбцы данных, которые могут быть возвращены для каждого класса событий.  
  
4.  Выберите пункт **Фильтры столбцов**.  
  
5.  В диалоговом окне **Изменение фильтра** выберите значения рядом с оператором сравнения, которые необходимо изменить, и введите новое значение или удалите существующее. Можно также добавлять дополнительные фильтры.  
  
6.  Нажмите кнопку **ОК** , чтобы сохранить шаблон.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
