---
title: Свойства служб SQL Server Integration Services (вкладка "Служба") | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d4cb1b821604d125bc81148a06fb613c8547a449
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68186705"
---
# <a name="sql-server-integration-services-properties-service-tab"></a>Свойства служб SQL Server Integration Services (вкладка «Служба»)
  Используйте вкладку **Служба**диалогового окна [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Properties** dialog box to view or specify the following options.  
  
## <a name="options"></a>Параметры  
 **Путь к двоичным файлам**  
 Отображает расположение программных файлов, используемых этой службой.  
  
 **Контроль ошибок**  
 1 означает `SERVICE_ERROR_NORMAL`. Если службе не удалось запуститься при запуске компьютера, программа запуска заносит в журнал сообщение об ошибке и выдает всплывающее сообщение об ошибке, но продолжает выполнять операцию запуска. Это значение невозможно изменить.  
  
 **Код завершения**  
 Код ошибки [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows определяет любые проблемы, возникшие при запуске или остановке службы. Этому свойству присваивается значение **ERROR_SERVICE_SPECIFIC_ERROR** (1066), если ошибка является уникальной для службы, представленной этим классом, а сведения об ошибке доступны в свойстве **ServiceSpecificExitCode** . Во время выполнения и после нормального завершения работы служба присваивает этому параметру значение NO_ERROR (0).  
  
 **Host Name**  
 Отображает имя компьютера или кластера, где запущена служба [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **Name**  
 Указывает отображаемое имя службы.  
  
 **Идентификатор процесса**  
 Отображает идентификатор процесса Windows.  
  
 **Тип службы SQL**  
 Отображает тип службы, предоставленной для вызывающих процессов. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливает несколько служб.  
  
 **Режим запуска**  
 Установите для этой службы один из следующих вариантов:  
  
-   Вручную: Эта служба запускается автоматически при запуске компьютера. Необходимо запустить службу при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или другого средства.  
  
-   Автоматически: Эта служба пытается запуститься при запуске этого компьютера.  
  
-   Отключено: Служба не может быть запущена.  
  
 **Состояние**  
 Указывает, была ли служба запущена, остановлена или отключена. **…** указывает, что ожидается изменение состояния.  
  
  
