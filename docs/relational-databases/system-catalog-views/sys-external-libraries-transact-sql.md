---
title: sys. external_libraries (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_libraries catalog view
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ac6ad0872e813d36d9884a00f979b2a5284cd4a3
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73536161"
---
# <a name="sysexternal_libraries-transact-sql"></a>sys. external_libraries (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Поддерживает управление библиотеками пакетов, связанными с внешними средами выполнения, такими как R, Python и Java.

> [!NOTE]
> В SQL Server 2017 поддерживаются язык R и платформа Windows. R, Python и Java на платформах Windows и Linux поддерживаются в SQL Server 2019 и более поздних версиях.

## <a name="sysexternal_libraries"></a>sys.external_libraries

Представление каталога sys. external_libraries содержит строку для каждой внешней библиотеки, которая была передана в базу данных.

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_library_id |int | Идентификатор объекта внешней библиотеки. |
|имя |sysname |Имя внешней библиотеки. Уникален в пределах базы данных на владельца.|
|principal_id |int |Идентификатор участника, владеющего этой внешней библиотекой. |
|language | sysname | Имя языка или среды выполнения, поддерживающей внешнюю библиотеку. Допустимые значения: "R", "Python" и "Java". В будущем могут быть добавлены дополнительные среды выполнения.|
|область |int |0 для общедоступной области; 1 для закрытой области |  
|scope_desc |varchar (7) |Указывает, является ли пакет открытым или закрытым|

## <a name="see-also"></a>См. также:  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [СОЗДАТЬ ВНЕШНЮЮ БИБЛИОТЕКУ](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [Установка новых пакетов R в SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
+ [Установка новых пакетов Python в SQL Server](../../advanced-analytics/python/install-additional-python-packages-on-sql-server.md)  