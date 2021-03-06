---
title: Печать отчетов из других приложений (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 58fee2cf31601dc638eebd69a13727a805408ac0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66107739"
---
# <a name="print-reports-from-other-applications-report-builder-and-ssrs"></a>Печать отчетов из других приложений (построитель отчетов и службы SSRS)
  Построитель отчетов поддерживает возможность экспорта, которая позволяет просматривать отчеты в других приложениях. При открытии отчета в браузере или в веб-приложении в его верхней части появляется панель инструментов отчета, в которой доступна команда `Export`. Экспорт обеспечивает просмотр отчетов в других приложениях (например, экспортированный в [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]отчет открывается именно в этом приложении). Рекомендуется экспортировать отчет для печати только в том случае, если это дает существенные преимущества при распечатывании.  
  
 Приложение, в которое производится экспорт отчета, должно быть установлено на компьютере. Например, при экспортировании в формат Adobe Acrobat Reader (PDF) необходимо сначала установить указанное приложение. При экспортировании в формат TIFF сервер отчетов открывает полученный файл с помощью приложения для просмотра, ассоциированного с файлами указанного формата. Использование какого-либо приложения зависит от используемой версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Обычно для указанных целей используется приложение Windows Picture and Fax Viewer. По умолчанию при просмотре используется разрешение экрана 96 точек на дюйм (dpi). При использовании Windows Picture and Fax Viewer можно увеличить разрешение до 300 либо 600 dpi (в зависимости от возможностей принтера). Дополнительные сведения об изменении разрешения см. в документации по продукту Windows.  
  
 При экспортировании в формат веб-архива (более известного как MHTML) отчет открывается в программе браузера, выбранного по умолчанию. При распечатывании отчета из браузера внизу каждой страницы добавляется информация о месторасположении отчета. В большинстве случаев указанную функцию браузера добавления информации о местоположении отчета можно отключить. Дополнительные сведения см. в документации по используемому веб-браузеру.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Печать отчета (построитель отчетов и службы SSRS)](print-a-report-report-builder-and-ssrs.md)   
 [Печать отчетов из браузера с помощью элемента управления печатью (построитель отчетов и службы SSRS)](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)   
 [Экспорт отчетов &#40;построитель отчетов и службы SSRS&#41;](export-reports-report-builder-and-ssrs.md)   
 [Экспорт отчета в файл другого типа (построитель отчетов и службы SSRS)](../export-a-report-as-another-file-type-report-builder-and-ssrs.md)   
 [Поиск, просмотр отчетов и управление ими (построитель отчетов и службы SSRS)](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
