---
title: Задача 16. Проверка с помощью диспетчера основных данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 35dd2da7f6cf6598918cd9d109b97f3d314556d1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65484690"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Задача 16. Проверка с помощью диспетчера основных данных
  В этой задаче вы проверите состояние пакетного задания, отправленного пакетом служб SSIS, и убедитесь, что данные были переданы на сервер MDS с помощью диспетчера основных данных.  
  
1.  Запустите **диспетчера основных данных** ([http://localhost/MDS](http://localhost/MDS)). Если он уже открыт, нажмите кнопку **Microsoft SQL Server Master Data Services** вверху, чтобы переключиться в режим **Домашняя страница**.  
  
2.  Нажмите кнопку **управление интеграцией**.  
  
3.  Обратите внимание, что имеется пакет с **EIMBatch** , отправленное в списке. Нажмите кнопку **импорта данных** в строке меню, если вы не видите следующий экран.  
  
     ![Пакет EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "пакет EIM")  
  
4.  Переключитесь обратно на домашнюю страницу, щелкните **SQL Server 2012 Master Data Services** вверху.  
  
5.  Убедитесь, что **поставщики** выбрана модель **модели** и **VERSION_1** выбран для **версии**и нажмите кнопку  **Обозреватель**.  
  
6.  Вы можете просмотреть данные, импортированные пакетом служб SSIS в MDS. Данные должны быть очищены и не должны содержать повторяющихся **кода** значения (Примечание: **SupplierID** столбец в Excel соответствует **кода** атрибут сущности Supplier в MDS).  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 17. Обзор DQS очистки проекта, созданного пакетом служб SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
