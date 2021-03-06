---
title: Столбец события ObjectType Trace | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Object Type column values
- events [SQL Server], Object Type column values
- event classes [SQL Server], Object Type column values
- Object Type column values [SQL Server]
ms.assetid: 42f85c50-34c9-49ca-955f-af9595e2707f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 31ba88f3bc49d78dc8c68ac77ba6bda90e63aad0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63028381"
---
# <a name="objecttype-trace-event-column"></a>Столбец события ObjectType Trace
  Столбец события трассировки Object Type используется в различных событиях трассировки. В этом подразделе приведены возможные значения этого столбца и связанные с ними определения.  
  
## <a name="object-type-column-values"></a>Значения столбца Object Type  
  
|Значение|Определение|  
|-----------|----------------|  
|8259|Ограничение CHECK|  
|8260|Значение по умолчанию или ограничение DEFAULT|  
|8262|Ограничение внешнего ключа|  
|8272|Хранимая процедура|  
|8274|Правило|  
|8275|Системная таблица|  
|8276|Триггер сервера|  
|8277|(Пользовательская) таблица|  
|8278|Просмотр|  
|8280|Расширенная хранимая процедура|  
|16724|Триггер CLR|  
|16964|База данных|  
|16975|Object|  
|17222|Полнотекстовый каталог|  
|17232|Хранимая процедура CLR|  
|17235|схема|  
|17475|Учетные данные|  
|17491|Событие DDL|  
|17741|Событие управления|  
|17747|Событие безопасности|  
|17749|Пользовательское событие|  
|17985|Агрегатная функция CLR|  
|17993|Встроенная возвращающая табличное значение функция SQL|  
|18000|Функция секционирования|  
|18002|Процедура фильтра репликации|  
|18004|Возвращающая табличное значение функция SQL|  
|18259|Роль сервера|  
|18263|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows|  
|19265|Асимметричный ключ|  
|19277|Главный ключ|  
|19280|Первичный ключ|  
|19283|ObfusKey|  
|19521|Имя входа асимметричного ключа|  
|19523|Имя входа сертификата|  
|19538|Роль|  
|19539|Имя входа SQL|  
|19543|Имя входа Windows|  
|20034|Привязка удаленной службы|  
|20036|Уведомление о событии в базе данных|  
|20037|Уведомление о событии|  
|20038|Скалярная функция SQL|  
|20047|Уведомление о событии объекта|  
|20051|Синоним|  
|20307|Последовательность|  
|20549|Конечная точка|  
|20801|Кэшируемые нерегламентированные запросы|  
|20816|Кэшируемые подготовленные запросы|  
|20819|Очередь обслуживания компонента Service Broker|  
|20821|Ограничение уникальности|  
|21057|Роль приложения|  
|21059|Сертификат|  
|21075|Сервер|  
|21076|Триггер Transact-SQL|  
|21313|Сборка|  
|21318|Скалярная функция CLR|  
|21321|Встроенная скалярная функция CLR|  
|21328|Схема секционирования|  
|21333|Пользовательская|  
|21571|Контракт службы компонента Service Broker|  
|21572|Триггер базы данных|  
|21574|Функция CLR с табличным значением|  
|21577|Внутренняя таблица, например таблица узла XML, таблица очереди|  
|21581|Тип сообщения компонента Service Broker|  
|21586|Маршрут компонента Service Broker|  
|21587|Статистика|  
|21825<br /><br /> 21827<br /><br /> 21831<br /><br /> 21843<br /><br /> 21847|Пользовательская|  
|22099|Служба компонента Service Broker|  
|22601|Индекс|  
|22604|Имя входа сертификата|  
|22611|XML-схема|  
|22868|Тип|  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
