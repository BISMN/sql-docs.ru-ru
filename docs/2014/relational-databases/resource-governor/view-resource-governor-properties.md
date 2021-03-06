---
title: Просмотр свойств регулятора ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties.f1
helpviewer_keywords:
- Resource Governor, properties
ms.assetid: de3510df-f792-4a9d-80fa-f198fd36cdc8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 35d4720a8fe8b8c1b404a97e27b36896f36dd5f7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63209685"
---
# <a name="view-resource-governor-properties"></a>Просмотр свойств регулятора ресурсов
  На странице свойств регулятора ресурсов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]предусмотрена возможность создания и настройки сущности регуляторов ресурсов — пулов ресурсов и групп рабочей нагрузки.  
  
1.  **Перед началом:**  [Разрешения](#Permissions)  
  
2.  **Просмотр свойств регулятора ресурсов, с помощью:**  [Страницы свойств регулятора ресурсов](#ViewRGProp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 Кроме просмотра свойств сущностей регулятора ресурсов, на странице **Свойства регулятора ресурсов** можно выполнить некоторые задачи настройки. Дополнительные сведения см. в разделах:  
  
-   [Активация регулятора ресурсов](enable-resource-governor.md)  
  
-   [Отключение регулятора ресурсов](disable-resource-governor.md)  
  
-   [Создание пула ресурсов](create-a-resource-pool.md)  
  
-   [Создание группы рабочей нагрузки](create-a-workload-group.md)  
  
-   [Изменение параметров пула ресурсов](change-resource-pool-settings.md)  
  
-   [Изменение параметров группы рабочей нагрузки](change-workload-group-settings.md)  
  
-   [Перемещение группы рабочей нагрузки](move-a-workload-group.md)  
  
 При нажатии кнопки **ОК** после добавления, удаления или перемещения группы рабочей нагрузки или пула ресурсов выполняется инструкция ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
 Если операция создания или изменения конфигурации пула ресурсов или группы рабочей нагрузки завершилась неуспешно, под заголовком страницы свойств будет отображено сводное сообщение об ошибке. Чтобы просмотреть подробное сообщение об ошибке, щелкните стрелку вниз рядом с ним.  
  
 Чтобы выяснить, находится ли конфигурация в состоянии ожидания, выполните запрос к динамическому административному представлению [sys.dm_resource_governor_configuration](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) , получив текущее состояние is_configuration_pending.  
  
###  <a name="Permissions"></a> Permissions  
 Для просмотра свойств регулятора ресурсов требуется разрешение VIEW SERVER STATER. Для задач настройки конфигурации регулятора ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="ViewRGProp"></a> Просмотр страницы свойств регулятора ресурсов  
 **Просмотр свойств регулятора ресурсов на странице "Свойства регулятора ресурсов" в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните правой кнопкой мыши **Регулятор ресурсов** и выберите пункт **Свойства**, после чего откроется страница **Свойства регулятора ресурсов** .  
  
3.  Описания полей этой страницы см. в разделе [Свойства регулятора ресурсов](#RGProp).  
  
4.  Чтобы сохранить изменения, нажмите кнопку **ОК**.  
  
##  <a name="RGProp"></a> Свойства регулятора ресурсов  
 **Имя функции-классификатора**  
 Укажите функцию-классификатор, выбрав ее из списка.  
  
 **Активация регулятора ресурсов**  
 Включите или отключите регулятор ресурсов путем установки или снятия флажка.  
  
 **Пулы ресурсов**  
 Создайте или измените конфигурацию пула ресурсов в этой сетке. Сетка заполнена сведениями о стандартных внутренних пулах и пулах по умолчанию. Выберите пул для работы, щелкнув первый столбец строки, содержащей имя пула. Чтобы создать пул ресурсов, щелкните строку, отмеченную символом "звездочка" ( **&#42;** ).  
  
 **Name**  
 Укажите имя пула ресурсов.  
  
 **Минимальная пропускная способность ЦП, %**  
 Укажите гарантированную среднюю пропускную способность ЦП для всех запросов в пуле ресурсов при возникновении состязания использования ЦП. Диапазон от 0 до 100.  
  
 **Максимальная пропускная способность ЦП, %**  
 Укажите максимальную среднюю пропускную способность ЦП для всех запросов в пуле ресурсов при возникновении состязания использования ЦП. Диапазон от 0 до 100. Значение по умолчанию — 100.  
  
 **Минимальный объем памяти, %**  
 Укажите минимальный объем памяти, резервируемый для данного пула ресурсов, который не подлежит использованию совместно с другими пулами ресурсов. Диапазон от 0 до 100.  
  
 **Максимальный объем памяти, %**  
 Укажите общий объем памяти сервера, который может использоваться для запросов в данном пуле ресурсов. Диапазон от 0 до 100. Значение по умолчанию — 100.  
  
 Дополнительные сведения см. в разделе [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql).  
  
 **Группы рабочей нагрузки для пула ресурсов**  
 Создайте или измените конфигурацию группы рабочей нагрузки в этой сетке. Сетка заполнена сведениями о стандартных внутренних группах и группах по умолчанию. Выберите группу для работы, щелкнув первый столбец строки, содержащей имя пула. Чтобы создать группу рабочей нагрузки, щелкните строку, отмеченную символом "звездочка" ( **&#42;** ).  
  
 **Name**  
 Укажите имя группы рабочей нагрузки.  
  
 **Важность**  
 Укажите относительную важность запроса в группе рабочей нагрузки. Доступны следующие значения: «Низкая», «Средняя» и «Высокая».  
  
 **Максимальное число запросов**  
 Укажите максимальное число запросов, одновременное выполнение которых разрешено в группе рабочей нагрузки. Должно быть 0 или положительным целым числом.  
  
 **Время ЦП (с)**  
 Укажите максимальное время ЦП, которое может быть использовано запросом. Должно быть 0 или положительным целым числом. Если задано значение 0, то время не ограничено.  
  
 **Предоставление памяти, %**  
 Укажите максимальный объем памяти, который может использоваться одним запросом из пула. Диапазон от 0 до 100.  
  
 **Время ожидания предоставления (секунды)**  
 Укажите максимальное количество времени, в течение которого запрос может ожидать освобождения ресурса, прежде чем завершится ошибкой. Должно быть 0 или положительным целым числом.  
  
 **Степень параллелизма**  
 Укажите максимальную степень параллелизма (DOP) для параллельных запросов. Диапазон от 0 до 64.  
  
 Дополнительные сведения см. в разделе [CREATE WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/create-workload-group-transact-sql).  
  
## <a name="view-resource-governor-properties-by-using-transact-sql"></a>Просмотр свойств регулятора ресурсов с помощью Transact-SQL  
 **Просмотр свойств регулятора ресурсов с помощью Transact-SQL**  
  
1.  Для просмотра определений сущностей регулятора ресурсов используются [представления каталога регулятора ресурсов (Transact-SQL)](/sql/relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql).  
  
2.  Для просмотра текущей конфигурации сущностей регулятора ресурсов используются [динамические административные представления регулятора ресурсов (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [регулятор ресурсов](resource-governor.md)   
 [Активация регулятора ресурсов](enable-resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](resource-governor-resource-pool.md)   
 [Группа рабочей нагрузки регулятора ресурсов](resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](resource-governor-classifier-function.md)  
  
  
