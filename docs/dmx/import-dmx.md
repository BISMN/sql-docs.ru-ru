---
title: IMPORT (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2141a4f8ccc6e34ec3010ad3ce8e8e3789d09132
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892756"
---
# <a name="import-dmx"></a>IMPORT (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Загружает модель или структуру интеллектуального анализа данных из файла резервной копии служб Analysis Services (ABF) на сервер.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IMPORT FROM <filename>  
```  
  
## <a name="arguments"></a>Аргументы  
 *файлов*  
 Строка с именем и расположением файла для импорта.  
  
## <a name="remarks"></a>Примечания  
 Если объекты не указаны, то загружается все содержимое DMB-файла. Если в DMB-файле содержится ссылка на несуществующую на сервере базу данных, то указанная база данных будет создана.  
  
 Только администратор базы данных или сервера имеет право экспортировать и импортировать объекты.  
  
## <a name="import-from-file-example"></a>Импорт из образца файла  
 В следующем примере выполняется импорт всего содержимого файла с моделью взаимосвязей и структурой на текущий сервер.  
  
```  
IMPORT FROM 'C:\TEMP\Association_NEW.dmb'  
```  
  
## <a name="see-also"></a>См. также  
 [Расширения &#40;интеллектуального анализа&#41; данных инструкции расширений интеллектуального анализа данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения &#40;интеллектуального анализа&#41; данных инструкции DMX-операций с данными](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по DMX &#40;&#41; -инструкциям расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-statements.md)   
 [ЭКСПОРТ &#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&#41;](../dmx/export-dmx.md)   
 [Экспорт и импорт объектов интеллектуального анализа данных](https://docs.microsoft.com/analysis-services/data-mining/export-and-import-data-mining-objects)  
  
  
