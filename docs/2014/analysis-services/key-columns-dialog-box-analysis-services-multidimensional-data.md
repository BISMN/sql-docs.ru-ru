---
title: Диалоговое окно «столбцы» (службы Analysis Services — многомерные данные) ключа | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.dataitemCollection.f1
helpviewer_keywords:
- DataItem Collection dialog box
ms.assetid: 585f27f2-d5eb-4516-b29a-2084010b7d51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 26eb85c97c970f9fe1cfaf63ca9861c2be0b4695
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66079465"
---
# <a name="key-columns-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Ключевые столбцы» (службы Analysis Services — многомерные данные)
  Используйте диалоговое окно **Ключевые столбцы** , чтобы изменить свойство **KeyColumns** атрибута. Дополнительные сведения см. в разделе [Изменение свойства KeyColumn атрибута](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).  
  
 **Чтобы отобразить диалоговое окно ключевые столбцы**  
  
-   В среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]выберите атрибут, а затем в окне **Свойства** нажмите кнопку с многоточием ( **...** ), связанную со свойством **KeyColumns** этого атрибута.  
  
## <a name="options"></a>Параметры  
 **Исходная таблица**  
 Выберите исходную таблицу, для которой нужно выбрать ключевые столбцы. Можно выбрать исходную таблицу из списка всех таблиц в представлении источника данных.  
  
 **Доступные столбцы**  
 Выберите столбцы, которые нужно использовать как ключевые столбцы. Можно выбрать столбцы из списка столбцов указанной **Исходной таблицы** , которые еще не были выбраны как ключевые.  
  
 Чтобы добавить выбранные столбцы к списку **Ключевые столбцы** , нажмите кнопку **>** .  
  
 **Ключевые столбцы**  
 Определите порядок выбранных ключевых столбцов. Порядок ключевых столбцов важен при определении правильного составного ключа. Чтобы упорядочить или переупорядочить список ключевых столбцов, выберите столбцы, а затем нажмите кнопки **Вверх** или **Вниз** .  
  
 Чтобы удалить столбец из списка **Ключевые столбцы** , выберите столбец и нажмите кнопку **\<** .  
  
 **Вверх**  
 Нажмите, чтобы переместить столбец, выбранный в списке **Ключевые столбцы** , на одну позицию вверх.  
  
> [!NOTE]  
>  Этот параметр доступен, только если список содержит более одного столбца и выбран какой-либо столбец.  
  
 **Вниз**  
 Нажмите, чтобы переместить столбец, выбранный в списке **Ключевые столбцы** , на одну позицию вниз.  
  
> [!NOTE]  
>  Этот параметр доступен, только если список содержит более одного столбца и выбран какой-либо столбец.  
  
 **>**  
 Нажмите, чтобы добавить новый столбец в конец списка **Ключевые столбцы**.  
  
 **<**  
 Нажмите, чтобы удалить выбранный столбец из списка **Ключевые столбцы**.  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
