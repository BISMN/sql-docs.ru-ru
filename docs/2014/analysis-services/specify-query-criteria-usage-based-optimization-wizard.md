---
title: Определение критериев запроса (мастер оптимизации с учетом использования) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.specifyquerycriteria.f1
ms.assetid: 3193adc2-af9f-4234-a4cc-dea0c280a724
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 41690da6a4a87bf79d411e2b467aeddfa56b5f00
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66068214"
---
# <a name="specify-query-criteria-usage-based-optimization-wizard"></a>Определение критериев запросов (мастер оптимизации с учетом использования)
  На странице **Определение критериев запроса** выберите один или несколько параметров фильтрации, чтобы определить запросы, которые следует оптимизировать.  
  
> [!NOTE]  
>  Эта страница отключена, если служба [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] не может подключиться к журналу запросов.  
  
## <a name="options"></a>Параметры  
 **Статистика журнала запросов**  
 Отображает данные о запросах, хранимых в журнале запросов для выбранных секций. Отображаются следующие элементы:  
  
|Термин|Определение|  
|----------|----------------|  
|**Всего запросов**|Отображает суммарное количество запросов, хранимых в журнале запросов для выбранных секций.|  
|**Уникальные запросы**|Отображает количество уникальных запросов, хранимых в журнале запросов для выбранных секций.|  
|**Уникальные пользователи**|Отображает суммарное количество уникальных пользователей, связанных с запросами, хранимыми в журнале запросов для выбранных секций.|  
|**Среднее время отклика**|Отображает среднее время отклика для запросов, хранимых в журнале запросов для выбранных секций.|  
  
 **Дата начала**  
 Фильтрует запросы в журнале запросов на основе даты и времени начала. Выберите или введите дату в раскрывающемся списке.  
  
> [!NOTE]  
>  Если параметр **Дата окончания** не выбран, то рассматриваются все запросы в журнале запросов на дату и время, заданные для данного параметра или после них.  
  
 **Дата окончания**  
 Фильтрует запросы в журнале запросов на основе даты и времени окончания. Выберите или введите дату в раскрывающемся списке.  
  
> [!NOTE]  
>  Если параметр **Дата начала** не выбран, то рассматриваются все запросы в журнале запросов на дату и время, заданные для данного параметра или до них.  
  
 **Пользователи**  
 Фильтрует запросы в журнале запросов на основе заданного набора пользователей. Нажмите кнопку с многоточием ( **...** ) для отображения диалогового окна **Выбор пользователей** и выберите пользователей, по которым необходимо фильтровать запросы. Дополнительные сведения о диалоговом окне **Выбор пользователей** см. в разделе [Диалоговое окно "Выбор пользователей" (службы Analysis Services — многомерные данные)](user-selection-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Наиболее часто выполняемые запросы**  
 Фильтрует запросы в журнале запросов на основе наибольшего процентного количества уникальных запросов, выполняемых наиболее часто для выбранных секций. Выберите или введите процентное значение в текстовое поле.  
  
## <a name="see-also"></a>См. также  
 [Справка F1 мастера оптимизации с учетом использования](usage-based-optimization-wizard-f1-help.md)   
 [Мастера служб Analysis Services &#40;многомерных данных&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
