---
title: Обработка секций в базе данных рабочей области (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3a369705-43fa-4961-9045-32e06fbdde33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 15b9f9203075734dd84d7b601574f66bc401e700
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66066797"
---
# <a name="process-partitions-in-the-workspace-database-ssas-tabular"></a>Обработка секций в базе данных рабочей области (табличные службы SSAS)
  Секции разделяют таблицу на логические части. Каждая секция затем может обрабатываться (обновляться) независимо от других секций. Приведенные в этом разделе задачи описывают обработку секций в базе данных рабочей области модели с помощью диалогового окна **Обработка секций** в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 После развертывания модели в другом экземпляре служб Analysis Services администраторы баз данных могут создавать секции и управлять ими в (развернутой) модели с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], скриптов или пакета служб IS. Дополнительные сведения см. в разделе [Создание секций табличной модели и управление ими (табличные службы SSAS)](partitions-ssas-tabular.md).  
  
###  <a name="bkmk_create_new"></a> Обработка секции  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]выберите в меню **Модель** пункт **Обработать** (Обновить), а затем пункт **Обработать секции**.  
  
2.  В списке **Режим** выберите один из следующих режимов обработки:  
  
    |Режим|Описание|  
    |----------|-----------------|  
    |**Обработка. По умолчанию**|Обнаруживает состояние обработки объекта секции и выполняет обработку, необходимую для перевода необработанных или частично обработанных объектов секции в полностью обработанное состояние. Выполняется загрузка данных для пустых таблиц и секций; иерархии, вычисляемые столбцы и связи строятся или перестраиваются.|  
    |**Обработка. Полная**|Обрабатывает объект секций и все объекты, которые в нем содержатся. Если объект, который обрабатывается методом полной обработки, уже был обработан, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удаляют все данные объекта, а затем обрабатывают его. Этот тип обработки требуется при внесении структурных изменений в объект.|  
    |**Обработка данных**|Выполняется загрузка данных в секцию или таблицу без перестроения иерархий или связей или повторного вычисления вычисленных столбцов и мер.|  
    |**Обработка с очисткой**|Удаляет все данные из секции.|  
    |**Обработка с добавлением**|Постепенно обновляет секцию с включением новых данных.|  
  
3.  В столбце флажков **Обработка** выберите секции для обработки в текущем режиме и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Секции (табличные службы SSAS)](partitions-ssas-tabular.md)   
 [Создание секций и управление ими в базе данных рабочей области (табличные службы SSAS)](workspace-database-ssas-tabular.md)  
  
  
