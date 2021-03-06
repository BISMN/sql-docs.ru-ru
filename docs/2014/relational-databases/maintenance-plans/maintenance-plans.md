---
title: Планы обслуживания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- SQL12.AG.MAINTPLAN.LEGACY.F1
helpviewer_keywords:
- maintenance plans [SQL Server], about database maintenance plans
- maintenance plans [SQL Server], database compatibility level displayed in designer
- maintenance plans [SQL Server]
ms.assetid: 5982ca65-74fe-44e3-aef9-00a65a0db169
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0643c6fbf8e9a6aa649d4d335117bcb4f5b35208
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206850"
---
# <a name="maintenance-plans"></a>Планы обслуживания
  Планы обслуживания используются для создания рабочего процесса из задач, необходимых для гарантии оптимальной производительности базы данных, ее регулярного резервного копирования и отсутствия в ней несогласованностей. Для создания основных планов обслуживания также можно использовать мастер планов обслуживания, однако создание планов вручную более эффективно.  
  
## <a name="benefits-of-maintenance-plans"></a>Преимущества планов обслуживания  
 В компоненте [!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)]планы обслуживания создают пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , выполняемый заданием агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Планы обслуживания можно запускать вручную или автоматически через заданные интервалы.  
  
 Планы обслуживания [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] обеспечивают следующие функциональные возможности.  
  
-   Создание рабочего процесса различных типовых задач обслуживания. Можно создавать и пользовательские скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
-   Концептуальные иерархии. Каждый план позволяет создавать и редактировать рабочий процесс. Задачи в каждом плане можно сгруппировать во вложенные планы, которым можно назначить запуск на разные моменты времени.  
  
-   Поддержка многосерверных планов может использоваться в среде главного или целевого сервера.  
  
-   Поддержка ведения журналов планов на удаленных серверах.  
  
-   Поддержка проверки подлинности Windows и проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="maintenace-plan-functionality"></a>Функции плана обслуживания  
 Планы обслуживания могут создаваться для выполнения следующих задач:  
  
-   Реорганизация данных на страницах данных и индексов путем перестроения индексов с новым коэффициентом заполнения. Перестроение индексов с новым коэффициентом заполнения обеспечивает одинаковое распределение объема данных и свободного пространства на страницах базы данных. Кроме того, при этом обеспечивается более быстрое увеличение размера в будущем. Дополнительные сведения см. в статье [Указание коэффициента заполнения для индекса](../indexes/specify-fill-factor-for-an-index.md).  
  
-   Сжатие файлов данных путем удаления пустых страниц базы данных.  
  
-   Обновление статистики индекса, обеспечивающее оптимизатору запросов новейшие сведения о распределении значений данных в таблицах. Это позволяет оптимизатору запросов делать более качественные суждения по поводу выбора наилучшего способа доступа к данным, так как ему предоставляется больше информации о данных, хранящихся в базе данных. Хотя статистика индекса обновляется компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически и периодически, этот параметр может привести к немедленному обновлению статистики.  
  
-   Проверка данных и страниц данных внутри базы данных на внутреннюю согласованность, позволяющая определить целостность данных после сбоя системы или программного обеспечения.  
  
-   Создание резервных копий файлов базы данных и журналов транзакций. Резервные копии базы данных и журнала могут храниться в течение заданного времени. Это позволяет создавать историю резервных копий, которые могут быть использованы, если нужно восстановить базу данных на момент, предшествующий моменту создания последней резервной копии базы данных. Также можно создавать разностные резервные копии.  
  
-   Выполнение заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Может использоваться для создания заданий, которые выполняют разнообразные действия, а также планов обслуживания для выполнения этих заданий.  
  
 Результаты, полученные в задачах обслуживания, можно записывать в виде отчета в текстовый файл или в таблицы плана обслуживания (`sysmaintplan_log` и `sysmaintplan_logdetail`) в `msdb`. Для просмотра результатов в средстве просмотра журнала щелкните правой кнопкой мыши пункт **Планы обслуживания** и выберите пункт **Просмотр журнала**.  
  
## <a name="related-tasks"></a>Связанные задачи  
 Используйте следующие разделы для начала работы с планами обслуживания.  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Описывает создание плана обслуживания с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].|[Создание плана обслуживания](create-a-maintenance-plan.md)|  
|Описывает создание плана обслуживания с помощью области конструктора плана обслуживания.|[Создание плана обслуживания (область конструктора планов обслуживания)](create-a-maintenance-plan-maintenance-plan-design-surface.md)|  
|Содержит сведения о функциональных возможностях планов обслуживания, доступных в обозревателе объектов.|[Узел "Планы обслуживания" (обозреватель объектов)](../../ssms/object/object-explorer.md)|  
  
  
