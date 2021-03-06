---
title: Преобразование "Импорт столбца" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.importcolumntrans.f1
helpviewer_keywords:
- Import Column transformation [Integration Services]
- columns [Integration Services], importing
- importing data, SSIS packages
- inserting data
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 13deb9b423ce20fd77e0853cba9d0f205905ca44
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62770428"
---
# <a name="import-column-transformation"></a>Преобразование «Импорт столбца»
  Преобразование «Импорт столбца» считывает данные из файлов и добавляет данные в столбцы потока данных. С помощью этого преобразования пакет может добавлять в поток данных текст и изображения, хранимые в отдельных файлах. Например, поток данных, загружающий данные в таблицу сведений о продуктах, может содержать преобразование «Импорт столбца», чтобы выполнять импорт отзывов покупателей о каждом продукте из файлов и добавлять обзоры в поток данных.  
  
 Можно настроить преобразование «Импорт столбца» следующим образом:  
  
-   Укажите столбцы, в которые преобразование добавляет данные.  
  
-   Укажите, ожидает ли преобразование отметку порядка байтов (BOM).  
  
    > [!NOTE]  
    >  Отметка порядка байтов предполагается, только если данные принадлежат к типу данных DT_NTEXT.  
  
 Столбец входа преобразования содержит имена файлов, в которых хранятся данные. Каждая строка в наборе данных может указывать на отдельный файл. Когда преобразование «Импорт столбца» обрабатывает строку, оно считывает имя файла, открывает соответствующий файл в файловой системе и загружает содержимое файла в выходной столбец. Тип данных выходного столбца должен быть DT_TEXT, DT_NTEXT или DT_IMAGE. Дополнительные сведения см. в разделе [Integration Services Data Types](../integration-services-data-types.md).  
  
 Это преобразование имеет один вход, один выход и один выход ошибок.  
  
## <a name="configuration-of-the-import-column-transformation"></a>Настройка преобразования «Импорт столбца»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../../common-properties.md)  
  
-   [Пользовательские свойства преобразований](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств компонента см. в разделе [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также  
 [Преобразование «Экспорт столбца»](export-column-transformation.md)   
 [Поток данных](../data-flow.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)  
  
  
