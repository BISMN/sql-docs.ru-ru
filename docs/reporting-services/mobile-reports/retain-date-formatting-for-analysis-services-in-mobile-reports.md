---
title: Сохранение форматирования дат для служб Analysis Services в мобильных отчетах | Службы Reporting Services | Документы Майкрософт
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: e9a9a199-40e3-4381-b250-1b99fb83aa62
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4e12b16ecf8df3452d327152638b794c58e2ec67
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62503011"
---
# <a name="retain-date-formatting-for-analysis-services-in-mobile-reports"></a>Сохранение форматирования дат для служб Analysis Services в мобильных отчетах
Для того чтобы даты в источниках данных [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] сохраняли свой тип данных в [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)], добавьте меру в общий набор данных в построителе отчетов.

Для запросов [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] типом возвращаемых данных по умолчанию является строка.  При создании набора данных в построителе отчетов [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] тип "строка" сохраняется и передается на сервер. 

Если же набор данных анализирует обработчик таблиц JSON, он считывает значение столбца как строку и обрабатывает строки.  Когда после этого [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)] получает таблицу, он также видит только строки.

Эту проблему можно обойти, если при создании общего набора данных в построителе отчетов добавить вычисляемый элемент. Это решение подходит и для многомерных, и для табличных моделей [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] .

## <a name="create-a-measure-to-retain-a-date-field-data-type"></a>Создание меры для сохранения тип данных в столбце дат

1. Создайте меру для сохранения значения в соответствующем поле даты, выбрав иерархию или уровень этой даты в поле выражения и добавив **.CurrentMember.MemberValue**. Пример:
 
   [Продажи через Интернет].[Дата отгрузки].CurrentMember.MemberValue
   
   ![ssas-calculated-member-report-builder](../../reporting-services/mobile-reports/media/ssas-calculated-member-report-builder.png)
   
2. Теперь этот вычисляемый элемент можно добавить в набор столбцов, перетащив его из списка "Вычисляемые элементы" в левом нижнем углу в сетку столбцов справа.  

   ![ssas-query-designer-calculated-member-report-builder](../../reporting-services/mobile-reports/media/ssas-query-designer-calculated-member-report-builder.png) 
   
### <a name="see-also"></a>См. также раздел

-  [Data for Reporting Services mobile reports](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md)
-  [Подготовка данных для мобильных отчетов Reporting Services](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
