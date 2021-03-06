---
title: Написание безопасного динамического кода SQL в SQL Server
description: Описывает методы написания безопасного динамического SQL с помощью хранимых процедур.
ms.date: 09/26/2019
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: dd7b76e3333d51a94d6f215a6608511629f35fbe
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451859"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Написание безопасного динамического кода SQL в SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Внедрение кода SQL — это процесс, с помощью которого злонамеренный пользователь вводит инструкции Transact-SQL вместо допустимых входных данных. Если входные данные передаются непосредственно на сервер без проверки, и если приложение случайно выполняет введенный код, атака может повредить или уничтожить данные.  
  
Любая процедура, создающая инструкции SQL, должна рассматриваться на предмет уязвимости к внедрению кода, так как SQL Server выполняет все получаемые синтаксически правильные запросы. Даже параметризованные данные могут стать предметом манипуляций опытного злоумышленника. Если используется динамический SQL, не забудьте параметризовать команды и никогда не включайте значения параметров непосредственно в строку запроса.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Анатомия атаки путем внедрения кода SQL  
Атака осуществляется посредством преждевременного завершения текстовой строки и присоединения к ней новой команды. Поскольку к вставленной команде перед выполнением могут быть добавлены дополнительные строки, злоумышленник заканчивает внедряемую строку меткой комментария «--». Весь последующий текст во время выполнения не учитывается. Можно вставить несколько команд с помощью точки с запятой (;) разделитель.  
  
Если вставленный код SQL синтаксически верен, искаженные данные нельзя выявить программно. Поэтому необходимо проверять правильность всех вводимых пользователями данных, а также внимательно просматривать код, выполняющий созданные с помощью SQL команды на сервере. Никогда не объединяйте введенные пользователем данные без проверки. Объединение строк является основной точкой входа для внедрения скрипта.  
  
Ниже приведены некоторые полезные рекомендации.  
  
- Никогда не создавайте инструкции Transact-SQL непосредственно из вводимых пользователем данных; Используйте хранимые процедуры для проверки вводимых пользователем данных.  
  
- Контролируйте все данные, вводимые пользователем, проверяя тип, длину, формат и диапазон данных. Используйте функцию языка Transact-SQL QUOTENAME () для экранирования системных имен или функции Replace () для экранирования любого символа в строке.  
  
- Реализуйте несколько уровней проверки на каждом уровне приложения.  
  
- Проверьте размер и тип вводимых данных и установите соответствующие ограничения. Это поможет предотвратить преднамеренное переполнение буфера.  
  
- Проверяйте содержимое строковых переменных и допускайте только ожидаемые значения. Отклоняйте записи, содержащие двоичные данные, управляющие последовательности и символы комментария.  
  
- При работе с XML-документами проверяйте все вводимые данные на соответствие схеме.  
  
- В многоуровневых средах перед передачей в доверенную зону должны проверяться все данные.  
  
- Не допускайте использование в полях следующих строк, из которых можно создать имена файлов: AUX, CLOCK$, COM1–COM8, CON, CONFIG$, LPT1–LPT8, NUL и PRN.  
  
- Используйте <xref:Microsoft.Data.SqlClient.SqlParameter> объекты с хранимыми процедурами и командами, чтобы обеспечить проверку типов и длину.  
  
- Используйте выражения <xref:System.Text.RegularExpressions.Regex> в клиентском коде для фильтрации недопустимых символов.  
  
## <a name="dynamic-sql-strategies"></a>Динамические стратегии SQL  
Выполнение динамически создаваемых инструкций SQL в процедурном коде приводит к разрыву цепочки владения, в результате SQL Server проверяет разрешения вызывающего объекта на доступ к объектам, к которым обращается динамический SQL.  
  
В SQL Server есть методы предоставления пользователям доступа к данным с помощью хранимых процедур и определяемых пользователем функций, в которых выполняется динамический код SQL.  
  
- Использование олицетворения с помощью предложения EXECUTE AS языка Transact-SQL.  
  
- Подписывание хранимых процедур с помощью сертификатов.  
  
### <a name="execute-as"></a>EXECUTE AS  
Предложение EXECUTE AS заменяет разрешения вызывающего объекта на пользователя, указанного в предложении EXECUTE AS. Вложенные хранимые процедуры или триггеры выполняются в контексте безопасности пользователя прокси-сервера. Это может привести к нарушению работы приложений, зависящих от безопасности на уровне строк или требующих аудита. Некоторые функции, возвращающие удостоверение пользователя, возвращают пользователя, указанного в предложении EXECUTE AS, а не в исходном вызывающем объекте. Контекст выполнения возвращается к исходному вызывающему объекту только после выполнения процедуры или при выдаче инструкции REVERT.  
  
### <a name="certificate-signing"></a>Подписание сертификата  
При выполнении хранимой процедуры, подписанной с помощью сертификата, разрешения, предоставленные пользователю сертификата, объединяются с теми, которые выполняет вызывающий объект. Контекст выполнения остается неизменным. Пользователь сертификата не олицетворяет вызывающего. Для подписывания хранимых процедур требуется выполнить несколько действий. При каждом изменении процедура должна быть подписана повторно.  
  
### <a name="cross-database-access"></a>Межбазовые доступ к базам данных  
Межбазовые цепочки владения не работают в случаях, когда выполняются динамически создаваемые инструкции SQL. Это можно обойти в SQL Server, создав хранимую процедуру для доступа к данным другой базы данных и подписав эту процедуру сертификатом, существующим в обеих базах данных. Это дает пользователям доступ к ресурсам базы данных, используемым процедурой, без предоставления им доступа к базе данных или разрешений.  
  
## <a name="external-resources"></a>Внешние ресурсы  
Для получения дополнительных сведений см. следующие ресурсы.  
  
|Ресурс|Описание|  
|--------------|-----------------|  
|[Хранимые процедуры](../../../relational-databases/stored-procedures/stored-procedures-database-engine.md) и [Атака путем внедрения кода SQL](../../../relational-databases/security/sql-injection.md) в электронной документации на SQL Server|Разделы описывают, как создавать хранимые процедуры и как работает внедрение кода SQL.|  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Сценарии безопасности приложений в SQL Server](application-security-scenarios-sql-server.md)
