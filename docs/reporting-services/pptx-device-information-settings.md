---
title: Настройки сведений об устройстве PPTX | Документы Майкрософт
ms.date: 09/11/2015
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- render
- powerpoint
- pptx
- export
ms.assetid: 4dc2045f-8025-41a3-8f9d-5635fb24cf4a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 53f5e080a4ce654eb133aed340034e547f247737
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65503333"
---
# <a name="pptx-device-information-settings"></a>Настройки сведений об устройстве PPTX
  В следующей таблице перечислены настройки сведений об устройстве, предназначенные для подготовки отчетов [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] к просмотру в формате PPTX.  
  
|Настройка|Значение|  
|-------------|-----------|  
|**Столбцы**|Задаваемое число столбцов в отчете. Это значение переопределяет исходные параметры отчета.|  
|**ColumnSpacing**|Интервал между столбцами, который должен быть задан для отчета. Это значение переопределяет исходные параметры отчета.|  
|**DpiX**|Горизонтальное разрешение изображения вывода. Значение по умолчанию — **96**. Применяется к форматам вывода **BMP**, **GIF**, **PNG**и **TIFF** .|  
|**DpiY**|Вертикальное разрешение изображения вывода. Значение по умолчанию — **96**. Применяется к форматам вывода **BMP**, **GIF**, **PNG**и **TIFF** .|  
|**EndPage**|Последняя подготавливаемая к просмотру страница отчета. Значением по умолчанию является значение для **StartPage**.|  
|**MarginBottom**|Задаваемая ширина нижнего поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, **1in**). Это значение переопределяет исходные параметры отчета.|  
|**MarginLeft**|Задаваемая ширина левого поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, **1in**). Это значение переопределяет исходные параметры отчета.|  
|**MarginRight**|Задаваемая ширина правого поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, **1in**). Это значение переопределяет исходные параметры отчета.|  
|**MarginTop**|Задаваемая ширина верхнего поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, **1in**). Это значение переопределяет исходные параметры отчета.|  
|**PageHeight**|Задаваемая высота страницы отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, **11in**). Это значение переопределяет исходные параметры отчета.|  
|**PageWidth**|Задаваемая ширина страницы отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, **8,5in**). Это значение переопределяет исходные параметры отчета.|  
|**StartPage**|Первая подготавливаемая к просмотру страница отчета. Значение **0** указывает, что к просмотру подготовлены все страницы. Значение по умолчанию — **1**.|  
|**UseReportPageSize**|Если UseReportPageSize = **false**, то размер слайда по умолчанию соответствует стандартному значению PowerPoint — 13,333 x 7,5 дюйма (пропорции 16:9). Если UseReportPageSize = true, то размер слайда по умолчанию соответствует заданному размеру страницы отчета.<br /><br /> Значение по умолчанию — **false**.<br /><br /> Обратите внимание, что параметры PageWidth и PageHeight переопределяют стандартную ширину и высоту.|  
  
## <a name="see-also"></a>См. также:  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
