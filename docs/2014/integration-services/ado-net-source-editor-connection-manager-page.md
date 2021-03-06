---
title: Редактор источника «ado.net» (страница «Диспетчер соединений») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.connection.f1
ms.assetid: 7de3f438-bdd6-49b5-937a-47369e754943
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f3d9d2270603c3f38189478ccaaf48510085907f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66061690"
---
# <a name="ado-net-source-editor-connection-manager-page"></a>Редактор источника данных «ADO.NET» (страница «Диспетчер соединений»)
  Используйте страницу **Диспетчер соединений** диалогового окна **Редактор назначения «ADO.NET»** для выбора соединения [!INCLUDE[vstecado](../includes/vstecado-md.md)] применительно к источнику. На этой странице также можно выбрать таблицу или представление базы данных.  
  
 Дополнительные сведения об источниках данных «ADO.NET» см. в разделе [ADO NET Source](data-flow/ado-net-source.md).  
  
 **Открытие страницы «Диспетчер соединений»**  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий источник данных «ADO.NET».  
  
2.  На вкладке **Поток данных** дважды щелкните источник данных "ADO.NET".  
  
3.  В окне **Редактор источника «ADO.NET»** нажмите кнопку **Диспетчер соединений**.  
  
## <a name="static-options"></a>Статические параметры  
 **Диспетчер соединений ADO.NET**  
 Выберите из списка существующий диспетчер соединений или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Создайте новый диспетчер соединений с помощью диалогового окна **Настройка диспетчера соединений ADO.NET** .  
  
 **Режим доступа к данным**  
 Укажите метод выбора данных из источника.  
  
|Параметр|Описание|  
|------------|-----------------|  
|Таблица или представление|Выборка данных из таблицы или представления в источнике данных [!INCLUDE[vstecado](../includes/vstecado-md.md)] .|  
|Команда SQL|Выборка данных из источника данных [!INCLUDE[vstecado](../includes/vstecado-md.md)] с использованием SQL-запроса.|  
  
 **Предварительный просмотр**  
 Осуществляйте предварительный просмотр результатов в диалоговом окне **Просмотр данных** . В окне**Предварительный просмотр** может отображаться до 200 строк.  
  
> [!NOTE]  
>  При предварительном просмотре столбцы с определяемым пользователем типом данных CLR не содержат данных. Вместо этого отображается текст \<значение слишком велико для отображения> или System.Byte[]. Первый вариант отображается во время доступа к источнику данных с помощью поставщика [!INCLUDE[vstecado](../includes/vstecado-md.md)] , а последний — при использовании поставщика данных для собственного клиента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="data-access-mode-dynamic-options"></a>Динамические параметры режима доступа к данным  
  
### <a name="data-access-mode--table-or-view"></a>Режим доступа к данным = Таблица или представление  
 **Имя таблицы или представления**  
 Выберите имя таблицы или представления из списка доступных в источнике данных.  
  
### <a name="data-access-mode--sql-command"></a>Режим доступа к данным — команда SQL  
 **Текст команды SQL**  
 Введите текст SQL-запроса, постройте запрос, нажав кнопку **Создать запрос**, или выберите файл, содержащий текст запроса, нажав кнопку **Обзор**.  
  
 **Создать запрос**  
 Воспользуйтесь диалоговым окном **Построитель запросов** для визуального конструирования SQL-запроса.  
  
 **Обзор**  
 Воспользуйтесь диалоговым окном **Открыть** для выбора файла, содержащего текст SQL-запроса.  
  
## <a name="see-also"></a>См. также  
 [Редактор источника "ADO.NET" (страница "Столбцы")](../../2014/integration-services/ado-net-source-editor-columns-page.md)   
 [Редактор источника данных "ADO.NET" (страница "Вывод ошибок")](../../2014/integration-services/ado-net-source-editor-error-output-page.md)   
 [Диспетчер соединений ADO.NET](connection-manager/ado-net-connection-manager.md)  
  
  
