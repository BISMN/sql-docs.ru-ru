---
title: Метаданные (вкладка «браузер», конструктор кубов) (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.metadatapane.f1
ms.assetid: a1ace545-488d-4645-8330-56408a5e8abd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e4aade575cdcb8260865d4a1fe9ab6f4b7941fe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66077845"
---
# <a name="metadata-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Метаданные (вкладка «Браузер», конструктор кубов) (службы Analysis Services — многомерные данные)
  Панель **Метаданные** на вкладке **Браузер** в конструкторе кубов предназначена для просмотра структур куба и связанных мер, а также для просмотра и создания измерений. В ней можно выполнять детализацию углублением иерархий, просматривать список доступных мер и ключевых показателей эффективности, а также копировать полные имена объектов.  
  
 Объекты и иерархии также можно перетаскивать с панели **Метаданные** в область построения запросов для создания новых запросов или экспорта данных в Excel для просмотра.  
  
## <a name="options"></a>Параметры  
 **Метаданные**  
 Отображает доступные в текущем представлении метаданные. Представление (то есть выбранную в текущий момент перспективу или куб) можно изменить, щелкнув значок куба и выбрав в диалоговом окне **Выбор куба** новый куб или перспективу. Также можно нажать кнопку **Группа мер**и выбрать из раскрывающегося списка новую группу мер, по которой будут фильтроваться доступные на панели **Метаданные** объекты.  
  
 Чтобы отобразить данные для выделенного элемента, перетащите его на панель фильтра, данных, строк или столбцов элемента управления PivotTable (сводная таблица) [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 11.0 на панели **Отчет** .  
  
 **Функции**  
 Отображает список всех функций, операторов и констант, которые могут использоваться для создания запросов или представлений данных в **браузере**. Чтобы использовать функцию, найдите нужную функцию и перетащите ее в область запросов. Синтаксис определения добавляется к тексту  
  
> [!WARNING]  
>  Список **Функция** недоступен при работе в режиме графического конструирования.  
  
 При работе с табличной моделью список функций включает и функции многомерных выражений, и функции DAX. В противном случае список включает только многомерные выражения. В многомерной модели нельзя непосредственно использовать функции DAX, но можно включить выражение DAX в определение объекта.  
  
 Совет. Папки, которые содержат функции DAX, перечислены в верхнем регистре. Все остальные папки содержат функции многомерных выражений. Например имеется две папки статистических функций: **СТАТИСТИЧЕСКИЕ** содержит соответствующие функции DAX.  
  
## <a name="context-menu"></a>Контекстное меню  
 Следующие пункты доступны в контекстном меню, которое появляется при щелчке правой кнопкой мыши по элементу, отображаемому на панели **Метаданные** :  
  
|Параметр|Описание|  
|------------|-----------------|  
|**Добавить запрос**|Нажмите, чтобы добавить выбранный объект на нижнюю панель области построения запроса.|  
|**Добавить в фильтр**|Нажмите, чтобы добавить выделенное измерение, атрибут, иерархию или уровень в область фильтра **браузера**.<br /><br /> Примечание. Этот параметр становится доступен только в том случае, если измерение, атрибут, иерархию или уровень выбран.|  
|**Копировать**|Выберите этот пункт, чтобы копировать выделенный элемент в буфер обмена.<br /><br /> Примечание. Этот параметр копирует полное имя объекта.|  
  
## <a name="see-also"></a>См. также  
 [Панель инструментов &#40;вкладка «браузер», конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Анализ в Excel &#40;вкладка «браузер», конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Запрос и фильтр &#40;вкладка «браузер», конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Браузер &#40;конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
