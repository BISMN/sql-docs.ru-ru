---
title: Отключение нескольких целевых серверов от главного | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0123027ac9aa87d616b52ac5cc26f36a20f7e1e3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62524018"
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a>Defect Multiple Target Servers from a Master Server
  В этом разделе описывается, как исключить несколько целевых серверов из конфигурации администрирования нескольких серверов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Запустите эту процедуру с главного сервера.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a>Отключение нескольких целевых серверов от главного  
  
1.  В **Обозревателе объектов**разверните главный сервер.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите пункт **Администрирование нескольких серверов**, а затем выберите пункт **Управление целевыми серверами**.  
  
3.  Щелкните **Отправить инструкции**и в списке **Тип инструкции** выберите **Отключить**.  
  
4.  В пункте **Адресаты**выполните одно из следующих действий:  
  
    -   щелкните **Все целевые серверы** , чтобы отключить от главного сервера все целевые (этот параметр используется в случае, когда нужно полностью удалить установленную текущую конфигурацию администрирования нескольких серверов);  
  
    -   щелкните **Эти целевые серверы**, а затем соответствующий пункт **Выбрать** , чтобы отключить от главного сервера некоторые, но не все целевые серверы.  
  
## <a name="see-also"></a>См. также  
 [Создание многосерверной среды](create-a-multiserver-environment.md)   
 [Автоматизация администрирования в масштабах предприятия](automated-administration-across-an-enterprise.md)   
 [Отключение целевого сервера от главного сервера](defect-a-target-server-from-a-master-server.md)  
  
  
