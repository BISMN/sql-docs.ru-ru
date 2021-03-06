---
title: Запрос и фильтр (вкладка «браузер», конструктор кубов) (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.filterpane.f1
ms.assetid: f5cf0bb1-3afb-4856-a2ef-614deb4e7e49
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d788a4957d7c6b3ea02e407f8b09fa80b957a4b5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66070541"
---
# <a name="query-and-filter-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Запрос и фильтр (вкладка «Браузер», конструктор кубов) (службы Analysis Services — многомерные данные)
  Эта область вкладки **Браузер** в конструкторе кубов содержит область запросов и фильтров, которая помогает выбирать из куба данные, используемые при просмотре или в запросах. Можно добавить любое количество кубов и просмотреть результаты в области данных или экспортировать их в отчет с помощью функции «Анализ в Excel», чтобы получить представление о том, как данные будут выглядеть для конечных пользователей.  
  
> [!WARNING]  
>  При работе с данными в этой области по умолчанию **Браузер** использует режим графического конструирования. В то же время запрос можно изменять и непосредственно с помощью выражений MDX, для этого нажмите кнопку-переключатель **Режим конструирования** . При этом панель, позволяющая разрабатывать фильтры по измерениям, исчезает. При необходимости добавить фильтр переключитесь обратно в режим графического конструирования.  
  
 По умолчанию при выполнении запроса для соединения с источником данных используются учетные данные текущего пользователя, а не указанные на странице **Сведения об олицетворении** . Однако контекст пользователя для запроса или отчета также можно изменить, нажав кнопку **Сменить пользователя** на **Панели инструментов**.  
  
## <a name="options"></a>Параметры  
 **Dimension**  
 Выбрать измерение, в котором произвести срез вложенного куба.  
  
 **Hierarchy**  
 Выбрать иерархию, в которой произвести срез вложенного куба.  
  
 **Оператор**  
 Выберите оператор, определяющий, как выражение в поле **Критерии фильтра** применяется к выбранной иерархии. Нижеприведенная таблица описывает доступные операторы.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**равно**|Результаты ограничены набором, определенным в **Критерии фильтра**.|  
|**Не равно**|Результаты ограничены элементами, исключенными набором, определенным в **Критерии фильтра**.|  
|**In**|Результаты ограничены именованным набором, выбранным в **Критерии фильтра**.|  
|**Не в**|Результаты ограничены элементами, исключенными именованным набором, выбранным в **Критерии фильтра**.|  
|**Содержит**|Результаты ограничены элементами, чьи имена содержат строку в **Критерии фильтра**.|  
|**Начинается с**|Результаты ограничены элементами, чьи имена начинаются со строки в **Критерии фильтра**.|  
|**Диапазон (включая границы)**|Результаты ограничены диапазоном, выбранным в **Критерии фильтра**.|  
|**Диапазон (исключая границы)**|Результаты ограничены элементами, исключенными диапазоном, выбранным в **Критерии фильтра**.|  
|**Многомерное выражение**|Результаты ограничиваются многомерными выражениями, установленными в поле **Критерий фильтра**.|  
  
 **Критерий фильтра**  
 Введите выражение, которое должно быть рассчитано **Оператором**, ограничивающее доступные для просмотра результаты.  
  
> [!NOTE]  
>  Это поле — динамический элемент ввода данных, меняющийся, чтобы отражать типы данных, необходимые для выбранного оператора.  
  
## <a name="see-also"></a>См. также  
 [Конструктор кубов &#40;службы Analysis Services — многомерные данные&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Браузер &#40;конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Панель инструментов &#40;вкладка «браузер», конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Анализ в Excel &#40;вкладка «браузер», конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Метаданные &#40;вкладка «браузер», конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
