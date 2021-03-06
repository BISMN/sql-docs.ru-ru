---
title: Уменьшение уровня шума в политиках загрузки ЦП (служебная программа SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.SWB.UE.ReduceNoise.F1
ms.assetid: 94bf4d93-c0ff-4869-bde7-80c24866092e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ce41c287105f97ce4a9cc0ce92facf9919f7ad33
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63035800"
---
# <a name="reduce-noise-in-cpu-utilization-policies-sql-server-utility"></a>Уменьшение уровня шума в политиках загрузки ЦП (служебная программа SQL Server)
  Чтобы сократить число неважных записей в отчетах и нежелательных нарушений в политиках использования ресурсов программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , применяются следующие стратегии.  
  
## <a name="how-frequently-should-processor-utilization-be-in-violation-before-it-is-reported-as-overutilized"></a>Как часто параметр загрузки процессора должен превышать пороговое значение, чтобы программа сообщила о его перегрузке?  
 Оценочный период и допуск на процент нарушений настраиваются с помощью параметров вкладки **Политика** на узле **Администрирование программ** в обозревателе программ. Для изменения политик воспользуйтесь соответствующим ползунком справа от описания политики, затем нажмите кнопку **Применить**. Можно также восстановить значения по умолчанию или отменить изменения с помощью кнопок в нижней части экрана.  
  
-   Интервал сбора данных составляет 15 минут. Это значение изменить нельзя.  
  
-   Верхний порог политики загрузки процессора по умолчанию составляет 70 %. Диапазон значений параметра — от 0 до 100 %.  
  
-   Период оценки перегрузки процессора по умолчанию — 1 час. Диапазон значений параметра — от 1 дня до 1 недели.  
  
-   Процент точек данных, указывающих на нарушение, по умолчанию, при котором сообщается о перегрузке процессора, — 20 %. Диапазон значений параметра — от 0 до 100 %.  
  
 Например, исходя из значений по умолчанию каждый час собирается четыре точки данных, а пороговое значение политики — 20 %. Отсюда по умолчанию каждое нарушение за часовой период сбора составит 25 % от 4 точек данных. При значениях по умолчанию сообщается о любом нарушении порога политики перегрузки ЦП.  
  
 Чтобы сократить количество сообщений, вызванных одиночным нарушением, возможны следующие варианты.  
  
-   Увеличение периода оценки до 6 часов по часу за раз. Одно нарушение за 6 часов составит в этом случае одну точку данных в выборке размером в 24 точки. При этом политика не сработает при 4 нарушениях порога политики (16,7 % точек данных) за 6 часов и будет сообщать о перегрузке при пяти или более нарушениях (>20 % точек данных) за 6-часовой период сбора.  
  
-   Увеличьте допуск на процент нарушений до 30 %, по одному проценту за раз. Одно нарушение за один час составит в этом случае одну точку данных в выборке из четырех точек. При этом политика не сработает при одном нарушении в час, но будет сообщать о перегрузке при двух или более нарушениях (>30 % точек данных) за часовой период сбора.  
  
-   Увеличьте пороговые значения политики загрузки процессора управляемого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и приложения уровня данных. Дополнительные сведения об изменении глобальных политик загрузки ЦП в управляемых экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или приложениях уровня данных см. в разделе [Администрирование программ (служебная программа SQL Server)](../../database-engine/utility-administration-sql-server-utility.md). Дополнительные сведения об изменении политик загрузки ЦП в отдельных экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Подробные сведения об управляемом экземпляре (служебная программа SQL Server)](../../database-engine/managed-instance-details-sql-server-utility.md). Дополнительные сведения об изменении политик загрузки ЦП для отдельных приложений уровня данных см. в разделе [Подробные сведения о развернутом приложении уровня данных (служебная программа SQL Server)](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md).  
  
## <a name="how-frequently-should-processor-utilization-be-in-violation-before-it-is-reported-as-underutilized"></a>Как часто параметр загрузки процессора должен быть ниже порогового значения, чтобы программа сообщила о его недостаточной загрузке?  
 Оценочный период и допуск на процент нарушений настраиваются с помощью параметров вкладки **Политика** на узле **Администрирование программ** в обозревателе программ. Для изменения политик воспользуйтесь соответствующим ползунком справа от описания политики, затем нажмите кнопку **Применить**. Можно также восстановить значения по умолчанию или отменить изменения с помощью кнопок в нижней части экрана.  
  
-   Интервал сбора данных составляет 15 минут. Это значение изменить нельзя.  
  
-   Нижний порог политики загрузки процессора по умолчанию составляет 0 %. Диапазон значений параметра — от 0 до 100 %.  
  
-   Период оценки недостаточной загрузки процессора по умолчанию — 1 час. Диапазон значений параметра — от 1 дня до 1 месяца.  
  
-   Процент точек данных, указывающих на нарушение, по умолчанию, при котором сообщается о недостаточной загрузке процессора, — 90 %. Диапазон значений параметра — от 0 до 100 %.  
  
 Согласно значениям по умолчанию, еженедельно собирается 672 точки данных, а порог политики составляет 0 %. Поэтому по умолчанию эта политика не выдает сообщений о недостаточной загрузке процессора. Дополнительные сведения об изменении глобальных политик загрузки ЦП в управляемых экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или приложениях уровня данных см. в разделе [Администрирование программ (служебная программа SQL Server)](../../database-engine/utility-administration-sql-server-utility.md). Дополнительные сведения об изменении политик загрузки ЦП в отдельных экземплярах SQL Server см. в разделе [Подробные сведения об управляемом экземпляре (служебная программа SQL Server)](../../database-engine/managed-instance-details-sql-server-utility.md). Дополнительные сведения об изменении политик загрузки ЦП для отдельных приложений уровня данных см. в разделе [Подробные сведения о развернутом приложении уровня данных (служебная программа SQL Server)](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md).  
  
## <a name="see-also"></a>См. также  
 [Администрирование программ (служебная программа SQL Server)](../../database-engine/utility-administration-sql-server-utility.md)   
 [Наблюдение за экземплярами SQL Server в служебной программе SQL Server](monitor-instances-of-sql-server-in-the-sql-server-utility.md)   
 [Изменение определения политики исправности ресурсов (служебная программа SQL Server)](modify-a-resource-health-policy-definition-sql-server-utility.md)   
 [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md)  
  
  
