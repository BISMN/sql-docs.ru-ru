---
title: Диалоговое окно "Добавление таблицы" в конструкторе базы данных (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 37b3207009e12b506f0ae80d9cdb0f1039442438
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253376"
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a>Диалоговое окно «Добавление таблицы» (конструктор базы данных) (визуальные инструменты для баз данных)
  Позволяет добавлять таблицы в конструкторе базы данных.  
  
> [!NOTE]  
>  Если таблица опубликована для репликации, то изменения схемы следует проводить при помощи инструкции языка Transact-SQL [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) или объектов SMO. При изменении схемы с помощью конструктора таблиц или конструктора диаграмм баз данных конструктор пытается удалить и затем вновь создать таблицу. Но поскольку удалять опубликованные объекты нельзя, изменения схемы не будут применены.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Обновить**  
 Обновляет список таблиц для соответствия текущему состоянию базы данных.  
  
 **Добавить**  
 Добавляет выбранную таблицу или таблицы.  
  
> [!NOTE]  
>  Если нужно добавить несколько таблиц к диаграмме, можно выбрать их все, а затем нажать кнопку **Добавить**. Или можно дважды щелкнуть каждую таблицу, которую нужно добавить, а затем, по окончании, нажать кнопку **Закрыть** .  
  
 **Закрыть**  
 Закрывает диалоговое окно без дальнейшего добавления таблиц.  
  
## <a name="see-also"></a>См. также  
 [Добавление таблиц в диаграммы (визуальные инструменты для баз данных)](visual-database-tools.md)  
  
  