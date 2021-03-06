---
title: Настройка хранилища для таблиц, оптимизированных для памяти | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6e005de0-3a77-4b91-b497-14cc0f9f6605
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 93698be4738ef2a28c79581d0957f695b036c911
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62990640"
---
# <a name="configuring-storage-for-memory-optimized-tables"></a>Настройка хранилища оптимизированных для памяти таблиц
  Необходимо настроить емкость подсистемы хранения и количество операций ввода-вывода в секунду (IOPS).  
  
## <a name="storage-capacity"></a>Емкость хранилища  
 Чтобы оценить объем памяти, который потребуется для размещения надежных, оптимизированных для памяти таблиц баз данных, используйте сведения из раздела [Оценка требований к объему памяти для таблиц, оптимизированных для памяти](memory-optimized-tables.md) . Поскольку индексы не сохраняются в оптимизированных для памяти таблицах, не учитывайте размер индексов. После определения размера необходимо выделить место на диске, которое будет в четыре раза больше размера надежных, оптимизированных для памяти таблиц.  
  
## <a name="storage-performance"></a>Производительность хранилища  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] может значительно повысить количество операций, выполняемых в рамках рабочей нагрузки. Поэтому важно убедиться в том, что подсистема ввода-вывода не станет узким местом.  
  
-   При миграции таблиц, находящихся на диске, в оптимизированные для памяти таблицы убедитесь в том, что журнал транзакций находится на носителе, который способен поддерживать возросшее число операций журнала транзакций. Например, если носитель поддерживает обработку операций журнала транзакций на скорости в 100 МБ/сек, а оптимизированные для памяти таблицы работают в пять раз быстрее, носитель, на котором находится журнал транзакций, также должен позволять увеличить производительность в пять раз, чтобы операции журнала транзакций не стали узким местом в системе.  
  
-   Оптимизированные для памяти таблицы сохраняются в файлы, которые находятся в одном или нескольких контейнерах. Каждый контейнер обычно следует сопоставить с собственным шпинделем. Он служит для увеличения емкости хранилища и повышения производительности. Необходимо убедиться, что последовательные IOPS носителя могут поддерживать 3 раза увеличить пропускную способность журнала транзакций.  
  
     К примеру Если оптимизированные для памяти таблицы выполняют 500 МБ в секунду для действия в журнале транзакций, то хранилище для оптимизированных для памяти таблиц должно поддерживать 1,5 ГБ/с. Необходимость в три раза увеличение пропускной способности журнала транзакций поступает из наблюдения, что пары файлов данных и разностных сначала записываются начальные данные и затем необходимо чтения/повторно-как часть операции слияния.  
  
     Еще одним фактором при оценке пропускной способности для хранилища является время восстановления оптимизированных для памяти таблиц. Данные из надежных таблиц должны быть считаны в память до того, как база данных станет доступна приложениям. Обычно загрузку данных в оптимизированные для памяти таблицы можно выполнять со скоростью IOPS. Поэтому, если общий объем хранилища для надежных, оптимизированных для памяти таблиц составляет 60 ГБ и необходимо обеспечить возможность загружать эти данные за одну минуту, для хранения должно быть задано значение IOPS в 1 ГБ/сек.  
  
-   При наличии четного числа шпинделей необходимо создать в два раза больше контейнеров и сопоставить с каждым шпинделем пару контейнеров. Это необходимо для распределения IOPS в хранилище. Дополнительные сведения см. в разделе [памяти файловую группу с оптимизированной](the-memory-optimized-filegroup.md).  
  
## <a name="see-also"></a>См. также  
 [Создание и управление хранилищем для оптимизированных для памяти объектов](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
