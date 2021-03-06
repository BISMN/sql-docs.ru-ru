---
title: Добавление прямоугольника или контейнера (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10061"
- sql12.rtp.rptdesigner.rectangleproperties.general.f1
ms.assetid: f905c35f-754d-4d02-80f3-85e29ddda826
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f1f9750813d305834fe36f2c6ab7abfaa1d95075
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106771"
---
# <a name="add-a-rectangle-or-container-report-builder-and-ssrs"></a>Добавление прямоугольника или контейнера (построитель отчетов и службы SSRS)
  Прямоугольник добавляется к отчету, если нужно разделить различные области отчета с помощью графического элемента, выделить области отчета или установить фон для одного или нескольких элементов отчета. Прямоугольники используются также в качестве контейнеров, помогающих управлять подготовкой к просмотру областей данных в отчете. Внешний вид прямоугольника можно настроить, изменяя его свойства, например цвета фона и границ. Дополнительные сведения об использовании прямоугольника как контейнера см. в разделах [Прямоугольники и линии (построитель отчетов и службы SSRS)](rectangles-and-lines-report-builder-and-ssrs.md) и [Отображение одних и тех же данных в матрице и на диаграмме (построитель отчетов)](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-rectangle"></a>Добавление прямоугольника  
  
1.  На вкладке **Вставка** в группе **Элементы отчета** щелкните **Прямоугольник**.  
  
2.  В области конструктора щелкните место расположения верхнего левого угла прямоугольника и перетащите указатель мыши в место расположения нижнего правого угла.  
  
     Обратите внимание при движении курсора: в момент, когда курсор располагается на одной линии с другими объектами в области конструктора, появляются линии привязки. Это облегчает выравнивание объектов.  
  
### <a name="to-create-a-container"></a>Создание контейнера  
  
1.  Добавьте прямоугольный элемент отчета в отчет.  
  
2.  Перетащите в прямоугольник другие элементы отчета.  
  
    > [!NOTE]  
    >  Прямоугольник является всего лишь контейнером для элементов, которые создаются в прямоугольнике или перетаскиваются в него. Если нарисовать прямоугольник вокруг элемента, уже существующего в области конструктора, прямоугольник не будет функционировать как его контейнер.  
  
### <a name="to-change-rectangle-properties-such-as-color-style-or-weight"></a>Изменение свойств прямоугольника, таких как цвет, стиль или вес  
  
1.  Выберите прямоугольник, а затем выберите параметры цвета, стиля или веса в разделе **Граница** вкладки «Корневая папка».  
  
2.  Для задания того, какие стороны прямоугольника изменять, нажмите стрелку рядом с кнопкой **Граница** .  
  
    > [!NOTE]  
    >  Если установить для линии стиль **двойные** и толщина линии равна 1 1/2 пт или уже, линия может не отображаться двойной при запуске отчета в построителе отчетов, конструктора отчетов или диспетчера отчетов. После экспорта отчета в другие форматы, такие как Microsoft Word и Acrobat PDF, линия будет отображаться двойной.  
  
## <a name="see-also"></a>См. также  
 [Прямоугольники и линии (построитель отчетов и службы SSRS)](rectangles-and-lines-report-builder-and-ssrs.md)   
 [Поведение при подготовке к просмотру (построитель отчетов и службы SSRS)](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
