---
title: Обработка множественных шагов задания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- ordering job steps [SQL Server]
- multiple job steps
- SQL Server Agent jobs, job steps
- control of flow for jobs [SQL Server]
ms.assetid: 7aba19ff-72b3-45f6-8e54-23f4988d63a8
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5ec0a6966a7bb87112329ec20a0c5dd507d791cb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308924"
---
# <a name="handle-multiple-job-steps"></a>Обработка множественных шагов задания
  Если в задании содержится более одного шага, необходимо указать порядок выполнения шагов задания. Это называется *управлением потоком***. Добавить новые шаги задания и реорганизовать поток шагов задания можно в любое время; изменения вступают в силу при следующем выполнении задания. На этой иллюстрации показано управление потоком для задания резервного копирования базы данных.  
  
 ![Управление потоком шагов заданий агента SQL Server](../../database-engine/media/dbflow01.gif "Управление потоком шагов заданий агента SQL Server")  
  
 Первый шаг — это создание резервной копии базы данных. Если этот шаг завершается ошибкой, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщает о сбое оператору, назначенному для получения уведомления. Если шаг создания резервной копии базы данных завершается успешно, выполнение задания переходит к следующему шагу — «очистке» данных заказчика. Если этот шаг завершается ошибкой, агент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] пропускает его и переходит сразу к шагу восстановления базы данных. Если «очистка» данных заказчика завершается успешно, выполнение задания переходит к следующему шагу — обновлению статистики, и так далее, до тех пор, пока в результате выполнения последнего шага не будет выдан отчет об успешном или неудачном завершении.  
  
 Пользователь определяет действие управления потоком на случай успешного или неудачного завершения каждого из шагов задания. Необходимо указать действие, которое предпринимается, когда шаг задания завершается успешно, и действие, предпринимаемое в случае неудачного завершения шага. Можно также задать число повторных попыток для неудачно завершенных шагов задания и интервал между повторными попытками.  
  
> [!NOTE]  
>  Если в графическом пользовательском интерфейсе (GUI) агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удалить один или нескольких шагов из многошагового задания, то GUI удаляет все шаги задания, а затем вновь добавляет остающиеся шаги с исправленными ссылками для успешного и ошибочного завершения. Предположим, что имеется задание из пяти шагов, и первый шаг сконфигурирован так, что в случае его успешного завершения задание переходит на шаг 4. Если удалить шаг 3, GUI удаляет все остальные шаги этого задания и добавляет остающиеся четыре шага (1, 2, 4 и 5) с исправленными ссылками. В этом случае ссылка на шаге 1 будет перенастроена для перехода на шаг 3, если шаг 1 завершается успешно.  
  
 Шаги задания должны быть автономными. Это значит, что задание не может передавать логические значения, данные или числовые значения между шагами задания. Однако можно передавать значения из одного шага задания [!INCLUDE[tsql](../../includes/tsql-md.md)] в другой с помощью постоянных таблиц или глобальных временных таблиц. Можно передавать значения между шагами задания, в которых запускаются исполняемые программы, с помощью файлов. Например, исполняемая программа, выполняемая на одном шаге задания, записывает файл, а программа, выполняемая на последующем шаге, считывает файл.  
  
> [!NOTE]  
>  Если создаются задания с циклическими шагами (за шагом 1 следует шаг 2, затем шаг 2 возвращается к шагу 1), то при создании задания с использованием среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]выдается предупреждающее сообщение.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент записывает сведения о задании и шагах задания в журнал заданий.  
  
## <a name="see-also"></a>См. также  
 [sp_add_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)   
 [dbo.sysjobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql)   
 [dbo.sysjobs &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobs-transact-sql)   
 [dbo.sysjobsteps &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobsteps-transact-sql)   
 [Реализация заданий](implement-jobs.md)   
 [Управление шагами задания](manage-job-steps.md)  
  
  