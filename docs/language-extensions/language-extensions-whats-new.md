---
title: Новые возможности расширений языка SQL Server
titleSuffix: ''
description: Узнайте о новых возможностях расширений языка SQL Server.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3bcf60c390b06695c4913bd1347045b807c1ae9d
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73658803"
---
# <a name="whats-new-in-sql-server-language-extensions"></a>Новые возможности расширений языка SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Возможности [расширений языка](language-extensions-overview.md) добавляются в SQL Server в каждом выпуске, так как мы продолжаем расширять и углублять интеграцию между внешними языками и платформой данных. 

## <a name="new-in-sql-server-2019"></a>Новые возможности в SQL Server 2019 

В этом выпуске добавлена поддержка расширений языка в SQL Server. Дополнительные сведения обо всех возможностях этого выпуска см. в статьях [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md) и [Заметки о выпуске SQL Server 2019](../sql-server/sql-server-ver15-release-notes.md).

- Средой выполнения Java по умолчанию в Windows и Linux является Open Zulu JRE и входит в состав [установки расширений языка SQL Server для Windows ](install/install-sql-server-language-extensions-on-windows.md) и [установки расширений языка SQL Server для Linux](../linux/sql-server-linux-setup-language-extensions.md).
- Поддержка [типов данных Java](how-to/java-to-sql-data-types.md).
- Инструкция [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md) для регистрации внешнего языка (например, Java) в SQL Server.
- [Пакет Microsoft Extensibility SDK для Java](how-to/extensibility-sdk-java-sql-server.md).
- В Windows и Linux доступ к коду Java можно получить во внешней библиотеке с помощью инструкции [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md). Дополнительные сведения: [Вызов кода Java из SQL Server](how-to/call-java-from-sql.md).
- [Расширение языка Java](language-extensions-overview.md) в Windows и Linux. Можно сделать скомпилированный код Java доступным в SQL Server путем назначения разрешений и установки пути. Клиентские приложения с доступом SQL Server могут использовать данные и выполнять код, вызывая [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) — ту же самую процедуру, которая используется для интеграции языков R и Python в службы машинного обучения SQL Server.

## <a name="next-steps"></a>Дальнейшие действия

+ Установка [Расширений языка для SQL Server в Windows](install/install-sql-server-language-extensions-on-windows.md) или [в Linux](../linux/sql-server-linux-setup-language-extensions.md)
