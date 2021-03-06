---
title: Экземпляр CDC Oracle | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ed71e8c4-e013-4bf2-8b6c-1e833ff2a41d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0152594c213196860e80ff5d5267356977404b7d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62771195"
---
# <a name="the-oracle-cdc-instance"></a>Экземпляр CDC Oracle
  Экземпляр Oracle CDC — это процесс, создаваемый службой Oracle CDC Service для обработки изменений, отслеживаемых в одной базе данных-источнике Oracle. Экземпляр Oracle CDC получает свою конфигурацию из таблицы **cdc.xdbcdc_config** и передает данные о своем состоянии в таблицу **cdc.xdbcdc_state** . Эти таблицы являются частью базы данных CDC, которая определяет экземпляр Oracle CDC. Дополнительные сведения о базе данных и таблицах xdbcdc см. в разделе [The CDC Databases](the-oracle-cdc-service.md).  
  
 Далее описываются задачи, выполняемые экземпляром Oracle CDC.  
  
-   **Выполнение проверки при запуске служб**: при запуске экземпляр CDC загружает свою конфигурацию из таблицы **xdbcdc_config** и выполняет ряд проверок состояния. Цель этих проверок — убедиться, что сохраненное состояние экземпляра CDC не содержит ошибок, а экземпляр может начать обработку изменений.  
  
-   **Подготовка к отслеживанию изменений**: Если проверка прошла успешно, экземпляр CDC просматривает все существующие экземпляры отслеживания, подготавливает запросы средства интеллектуального анализа журнала Oracle и другие вспомогательные структуры, необходимые для отслеживания изменений. Кроме того, экземпляр Oracle заново загружает внутреннее состояние отслеживания изменений, сохраненное в последний раз, когда выполнялся этот экземпляр Oracle CDC.  
  
-   **Отслеживание изменений из Oracle**: Экземпляр Oracle CDC Instance группирует изменения, поступающие из Oracle, с помощью средства интеллектуального анализа журнала Oracle, сортирует их по времени фиксации транзакции, а затем изменяет время транзакции и записывает изменения в таблицы изменений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных CDC.  
  
-   **Обработка завершения работы службы**: Жизненным циклом экземпляра Oracle CDC Instance управляет служба Oracle CDC Service. Получив команду завершения работы, экземпляр CDC Oracle выполняет следующие задачи:  
  
    -   прекращает чтение журнала транзакций Oracle;  
  
    -   прекращает запись завершенных транзакций Oracle в базу данных CDC;  
  
    -   ждет до 30 секунд (при необходимости), пока текущая транзакция не закончит запись в базу данных CDC. Если прошло более 30 секунд, операция записи отменяется и транзакция откатывается (при повторном запуске экземпляра CDC она будет выполнена заново);  
  
    -   в отдельном потоке в течение не более 30 секунд записывает как можно больше кэшированных в памяти записей в промежуточную таблицу транзакций (от самой старой до самой новой), затем обновляет таблицу **xdbcdc_state** и выполняет фиксацию всех изменений.  
  
-   **Обработка изменений конфигурации**: экземпляр Oracle CDC получает сообщение об изменениях конфигурации от службы CDC или через обнаружение новой версии в таблице **cdc.xdbcdc_config**. Большинство изменений (например, добавление или удаление экземпляров отслеживания) не требуют перезапуска экземпляра Oracle CDC. Однако при внесении некоторых изменений, например строки подключения Oracle или учетных данных доступа, экземпляр CDC необходимо перезапустить.  
  
-   **Обработка восстановления**: при запуске экземпляра Oracle CDC его внутреннее состояние восстанавливается из таблиц **xdbcdc_state** и **xdbcdc_staged_transactions**. После восстановления состояния экземпляр CDC продолжает работу как обычно.  
  
## <a name="see-also"></a>См. также  
 [Обработка ошибок](error-handling.md)  
  
  
