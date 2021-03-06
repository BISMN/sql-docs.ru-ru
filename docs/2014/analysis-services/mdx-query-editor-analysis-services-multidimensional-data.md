---
title: Редактор запросов многомерных Выражений (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.startpage.mdx.f1
helpviewer_keywords:
- Query Editor [MDX]
- MDX Query Editor
ms.assetid: 777f2c23-1c1c-4b72-9d19-48a4866551f8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 579af162998ffaa7c9483a6e6d29a87f98e96fac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66077881"
---
# <a name="mdx-query-editor-analysis-services---multidimensional-data"></a>Редактор запросов многомерных выражений (службы Analysis Services — многомерные данные)
  Редактор запросов многомерных выражений служит для создания и выполнения инструкций и сценариев, написанных на языке многомерных выражений (XMLA).  
  
## <a name="features"></a>Компоненты  
  
-   Введите скрипты на панели редактора запросов многомерных выражений.  
  
-   Чтобы выполнить сценарии, нажмите клавишу **F5**или кнопку **Выполнить** на панели инструментов, либо в меню **Запрос** выберите команду **Выполнить**. При выборе части кода выполнена будет только выбранная часть. Если ни одна часть кода не была выбрана, содержимое редактора запросов многомерных выражений выполняется целиком.  
  
-   Просмотрите метаданные для кубов и других объектов, содержащихся в базе данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] на панели метаданных.  
  
-   Чтобы получить справку по синтаксису многомерных выражений, выберите ключевое слово в редакторе запросов многомерных выражений, а затем нажмите клавишу **F1**.  
  
-   Чтобы получить динамическую справку по синтаксису многомерных выражений, в меню **Справка** выберите пункт **Динамическая справка**, чтобы открыть компонент динамической справки. При вводе ключевых слов в редакторе запросов разделы справки отображаются в окне **Динамическая справка** .  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>Панель инструментов редакторов служб SQL Server Analysis Services  
 Если открыт редактор запросов многомерных выражений, панель инструментов редакторов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] отображается с кнопками, перечисленными в следующей таблице.  
  
|Термин|Определение|  
|----------|----------------|  
|**Подключить**|Открывает диалоговое окно **Соединиться с сервером** для установки соединения с экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Отключить**|Отключает редактор запросов многомерных выражений от экземпляра служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Изменить соединение**|Открывает диалоговое окно **Соединение с сервером** для установки соединения с другим экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Создать запрос в текущем соединении**|Открывает новое окно редактора запросов многомерных выражений, используя сведения о соединении из текущего окна редактора запросов многомерных выражений.|  
|**Доступные базы данных**|Переключает соединение на другую базу данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в том же экземпляре.|  
|**Выполнение**|Выполняет выбранный код или, если код не выбран, выполняет весь код в редакторе запросов многомерных выражений.|  
|**Синтаксический анализ**|Проверяет синтаксис выбранного кода. Если код не выбран, осуществляет проверку синтаксиса всего содержимого окна редактора запросов многомерных выражений.|  
|**Отменить выполнение запроса**|Отправляет на сервер запрос отмены. Выполнение некоторых запросов не может быть отменено незамедлительно, для этого необходимо дождаться условий отмены. После отмены запросов откат транзакций может происходить с задержками.|  
  
## <a name="mdx-query-editor-window"></a>Окно редактора запросов многомерных выражений  
 Параметры, перечисленные в следующей таблице, доступны в редакторе запросов многомерных выражений.  
  
|Термин|Определение|  
|----------|----------------|  
|**Окно редактора запросов**|Введите инструкции и скрипты многомерных выражений, которые должны быть выполнены редактором запросов многомерных выражений.<br /><br /> Контекстное меню редактора запросов содержит следующие пункты.<br /><br /> **Вырезать**. Копирует текущее выделение в буфер обмена и удаляет выделение из окна редактора запросов.<br /><br /> **Копировать**. Копирует текущее выделение в буфер обмена.<br /><br /> **Вставить**. Вставляет содержимое буфера обмена в текущее выделение.<br /><br /> **Соединить**. Открывает диалоговое окно **Соединиться с сервером** для установки соединения с экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .<br /><br /> **Отключить**. Отключает текущий редактор запросов от экземпляра служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .<br /><br /> **Отключить все запросы**. Отключает все открытые редакторы запросов.<br /><br /> **Изменить соединение**. Открывает диалоговое окно **Соединение с сервером** для установки соединения с другим экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .<br /><br /> **Открыть сервер в обозревателе объектов**. Открывает диалоговое окно [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , с которым соединен текущий редактор запросов, в **обозревателе объектов**.<br /><br /> **Выполнить**. Выполняет выбранный код или, если код не выбран, выполняет весь код в текущем редакторе запросов.<br /><br /> **Окно "Свойства"** . Отображает окно **Свойства** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] для текущего окна запроса.<br /><br /> **Параметры запроса**. Отображает диалоговое окно **Параметры запроса** .|  
|**Окно метаданных**|Отображает метаданные для базы данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , подключенной в настоящий момент.|  
|**Cube**|Выберите куб в подключенной на текущий момент базе данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , чтобы отобразить метаданные, связанные с кубом, на вкладке **Метаданные** .|  
|**Метаданные**|Отображает метаданные для куба, выбранного на вкладке **Куб**, включая группы мер и меры, ключевые показатели эффективности, измерения, иерархии, уровни, элементы и свойства элементов. Чтобы получить полный ключ объекта, выполните одно из следующих действий.<br /><br /> Перетащите объект из вкладки **Метаданные** на панель запроса.<br /><br /> Щелкните правой кнопкой мыши объект и выберите команду **Копировать**, затем щелкните правой кнопкой мыши на панели запроса и выберите команду **Вставить**.|  
|**Функции**|Отображает метаданные для функций многомерных выражений, доступных для базы данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , в том виде, в каком они получены из набора строк схемы MDSCHEMA_FUNCTIONS. Чтобы получить синтаксис функции, выполните одно из следующих действий.<br /><br /> Перетащите объект из вкладки **Функции** на панель запроса.<br /><br /> Щелкните правой кнопкой мыши функцию и выберите команду **Копировать**, затем щелкните правой кнопкой мыши на панели запроса и выберите команду **Вставить**.|  
|**Окно "Результаты"**|Отображает результаты инструкции или скрипта многомерных выражений в сетке.|  
|**Окно «сообщения»**|Отображает информацию о выполнении инструкции или скрипта многомерных выражений. Например, это окно отображает любые ошибки, обнаруженные в процессе выполнения, или число ячеек, полученных после выполнения.|  
  
  
