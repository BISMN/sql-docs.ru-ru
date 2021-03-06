---
title: Вставка или удаление столбца (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9db79e2-7e7d-4359-a706-cb746c94182a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e1d5f5d846a690676942e0d4ffcba0475a35595a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66105679"
---
# <a name="insert-or-delete-a-column-report-builder-and-ssrs"></a>Вставка или удаление столбца (построитель отчетов и службы SSRS)
  Добавить или удалить столбцы можно в области данных табликса. Областью данных табликса может быть таблица, матрица или список. Следующие процедуры не применяются к области данных диаграммы и датчика.  
  
 В области данных табликса можно добавлять столбцы, связанные с группой (внутри группы) или не связанные с группой (вне группы). Столбец, находящийся внутри группы, повторяется один раз для уникального значения группы. Например, столбец в группе, основанной на значении столбца данных и содержащей имена цветов, повторяется один раз для каждого отдельного имени цвета. Что касается вложенных групп, то столбец может находиться вне дочерней группы, но должен находиться в родительской группе. В этом случае строка повторяется один раз для каждого уникального значения в родительской группе.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-select-a-data-region-so-that-the-row-and-column-handles-appear"></a>Выделение области данных с целью отображения маркеров строки и столбца  
  
-   В конструкторе щелкните левый верхний угол области данных табликса, чтобы поверх и рядом с ней появились маркеры столбца и строки.  
  
     Дополнительные сведения об областях данных см. в разделе [перечислены &#40;построитель отчетов и службы SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).  
  
### <a name="to-insert-a-column-in-a-selected-data-region"></a>Вставка столбца в выделенную область данных  
  
-   Щелкните правой кнопкой мыши маркер там, где нужно вставить столбец, выберите команду **Вставить столбец**и укажите **Слева** или **Справа**.  
  
     или  
  
-   Щелкните правой кнопкой мыши ячейку области данных там, где нужно вставить столбец, выберите команду **Вставить столбец**и укажите **Слева** или **Справа**.  
  
### <a name="to-delete-a-column-from-a-selected-data-region"></a>Удаление столбца из выделенной области данных  
  
-   Выделите один или несколько столбцов, которые нужно удалить, щелкните правой кнопкой мыши маркер одного из выделенных столбцов и выберите команду **Удалить столбцы**.  
  
     или  
  
-   Щелкните правой кнопкой мыши ячейку области данных там, где нужно удалить столбец, и выберите команду **Удалить столбцы**.  
  
### <a name="to-insert-a-column-in-a-group-in-a-selected-data-region"></a>Вставка столбца в группу в выделенной области данных  
  
-   Щелкните правой кнопкой мыши ячейку группы столбцов в области данных табликса там, где нужно вставить столбец, выберите команду **Вставить столбец**и укажите **Слева — снаружи группы**, **Слева — внутри группы**, **Справа — внутри группы**или **Справа — снаружи группы**.  
  
     Столбец добавится внутри или снаружи группы, представленной выбранной ячейкой группы столбцов.  
  
### <a name="to-delete-a-column-from-a-group-in-a-selected-data-region"></a>Удаление столбца из группы в выделенной области данных  
  
-   Щелкните правой кнопкой мыши ячейку группы столбцов в области данных табликса там, где нужно удалить столбец, и выберите команду **Удалить столбцы**.  
  
## <a name="see-also"></a>См. также  
 [Основные сведения о группах (построитель отчетов и службы SSRS)](understanding-groups-report-builder-and-ssrs.md)   
 [Область данных табликса (построитель отчетов и службы SSRS)](../tablix-data-region-report-builder-and-ssrs.md)   
 [Таблицы &#40;построитель отчетов и службы SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Матрицы &#40;построитель отчетов и службы SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Списки &#40;построитель отчетов и службы SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Списки (построитель отчетов и службы SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
