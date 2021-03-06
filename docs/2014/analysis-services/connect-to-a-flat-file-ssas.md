---
title: Подключение к неструктурированному файлу (SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connflatfile.f1
ms.assetid: a365991e-eded-4cd8-89c0-0daf6d658d15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b6eeb17662c0cac290a7a455d0925cd05560e5e0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66087362"
---
# <a name="connect-to-a-flat-file-ssas"></a>Подключение к неструктурированному файлу (SSAS)
  Эта страница **мастера импорта таблиц** используется для соединения с неструктурированным файлом (TXT), файлом с разделителями в виде символов табуляции (TAB) или файлом с разделителями-запятыми (CSV). Для доступа к мастеру из [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]выберите пункт **Импорт из источника данных** в меню **Модель**.  
  
 Для соединения с неструктурированным файлом необходимо, чтобы на компьютере был установлен поставщик ACE. Дополнительные сведения см. в разделе [Поддерживаемые источники данных (табличные службы SSAS)](tabular-models/data-sources-supported-ssas-tabular.md).  
  
> [!NOTE]  
>  При выборе файла на этой странице используются учетные данные текущего пользователя. Тем не менее импорт не будет успешным, если пользователь, указанный на странице сведений об олицетворении, не имеет достаточных прав для чтения из выбранного файла.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Понятное имя соединения**  
 Введите уникальное имя для соединения с источником данных. Это поле является обязательным.  
  
 **Путь к файлу**  
 Укажите полный путь к файлу.  
  
 **Обзор**  
 Перейдите в папку, в которой находится файл.  
  
 **Разделитель столбцов**  
 Выберите из списка разделитель столбцов. Выберите разделитель, который вряд ли встретится в тексте.  
  
|Значение|Описание|  
|-----------|-----------------|  
|Табуляция (t)|Столбцы разделяются символом табуляции (t).|  
|Запятая (,)|Столбцы разделяются символом запятой (,).|  
|Точка с запятой (;)|Столбцы разделяются символом точки с запятой (;).|  
|Пробел ( )|Столбцы разделяются пробелом ( ).|  
|Двоеточие (:)|Столбцы разделяются символом двоеточия (:).|  
|Вертикальная черта (&#124;)|Столбцы разделяются символом вертикальной черты (&#124;).|  
  
 **Дополнительно**  
 Укажите параметры кодировки и локали для неструктурированного файла.  
  
 **Использовать первую строку в качестве заголовков столбцов**  
 Укажите, следует ли использовать первую строку данных в качестве заголовков столбцов целевой таблицы.  
  
 **Предварительный просмотр данных**  
 Создать предварительный просмотр данных в выбранном файле и использовать следующие параметры для изменения импорта данных.  
  
> [!NOTE]  
>  В режиме предварительного просмотра отображаются только первые 50 строк файла.  
  
|Параметр|Описание|  
|------------|-----------------|  
|**Флажок в заголовке столбца**|Установите флажок, чтобы включить столбец в импорт данных. Снимите флажок, чтобы не импортировать столбец.|  
|**Кнопка со стрелкой вниз в заголовке столбца**|Сортировка и фильтрация данных в столбце.|  
  
 **Очистить фильтры строк**  
 Удалить все фильтры, примененные к данным в столбцах.  
  
  
