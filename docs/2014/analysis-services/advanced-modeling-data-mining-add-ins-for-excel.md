---
title: Расширенное моделирование (надстройки интеллектуального анализа для Excel данных) | Документация Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: 042270a3-6ec7-4b52-b2ba-2adb6c4740d5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 669fa1fcd9e4802a4d4102120a373dd615741017
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66062738"
---
# <a name="advanced-modeling-data-mining-add-ins-for-excel"></a>Расширенное моделирование (надстройки интеллектуального анализа данных для Excel)
  Можно использовать **Дополнительно** параметры моделирования данных для создания пользовательских структур и моделей с параметрами отличаются от тех, которые устанавливают мастера. Два мастера, описание которых содержится в этом разделе, помогут создать полностью новые структуры интеллектуального анализа данных или добавить модели интеллектуального анализа данных к уже существующим структурам интеллектуального анализа данных.  
  
## <a name="create-mining-structure"></a>Создание структуры интеллектуального анализа данных  
 ![Кнопка "создать структуру интеллектуального анализа данных", интеллектуального анализа данных](media/dmc-createstruct.gif "кнопка Create Mining Structure, интеллектуального анализа данных")  
  
 **Мастер создания структуры интеллектуального анализа данных** помогает создавать новую структуру интеллектуального анализа данных. Структура — это набор данных, извлеченный из указанного источника данных.  Структуру интеллектуального анализа данных можно обновить новыми данными в источнике, но при создании структуры определяются имена и типы данных, которые определяют, каким образом данные используются для анализа.  
  
 Следующие источники данных можно использовать для построения структуры: таблицы Excel, диапазона Excel или любые данные в источник внешних данных, который уже был определен как [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] представление источника данных.  
  
 Для каждой структуры существует возможность зарезервировать определенное количество данных, которые будут использоваться при испытаниях и проверках. Создав такой *набора контрольных данных* при настройке источников данных, можно обеспечить, всех моделей, основанных на структуре, могут использовать согласованный набор данных для тестирования.  
  
 После создания структуры интеллектуального анализа данных можно добавить несколько моделей для применения различных методов анализа.  
  
 Дополнительные сведения об использовании **мастер создания интеллектуального анализа данных структуры**, см. в разделе [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md).  
  
## <a name="add-model-to-structure"></a>Добавление модели в структуру  
 ![Добавление модели к структуре кнопку](media/dmc-addmodel.gif "добавления модели к структуре кнопки")  
  
 При добавлении новой модели в структуру происходит анализ данных с помощью различных алгоритмов или параметров. Этот параметр особенно полезен, если нужно создать модель с помощью одного из алгоритмов, не предоставляемых в клиентских средствах интеллектуального анализа данных.  
  
 Например, можно использовать любой из алгоритмов, поддерживаемых службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   Линейная регрессия  
  
-   Кластеризация последовательностей  
  
-   Анализ взаимосвязей для вложенных наборов данных  
  
 Чтобы узнать, что вид структуры интеллектуального анализа данных доступны, можно просматривать модели и структуры, сохраненные в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , щелкнув пункт **Управление моделями** или **Обзор**.  
  
 Отображаются структуры интеллектуального анализа данных, которые были созданы в течение текущего сеанса, или структуры интеллектуального анализа данных, сохраненных в экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Дополнительные сведения см. в разделе [добавить модель к структуре &#40;интеллектуального анализа данных надстройки для Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).  
  
## <a name="see-also"></a>См. также  
 [Управление моделями &#40;надстройки интеллектуального анализа данных SQL Server&#41;](manage-models-sql-server-data-mining-add-ins.md)   
 [Просмотр моделей в Excel &#40;надстройки интеллектуального анализа данных SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
