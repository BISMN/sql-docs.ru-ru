---
title: Использование метаданных базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fce2bf9d72136b303ee3bc974f3aede313233a82
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026419"
---
# <a name="using-database-metadata"></a>Использование метаданных базы данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Чтобы запросить в базе данных сведения о поддерживаемых функциях, в [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализован класс [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md). Этот класс содержит многочисленные методы, которые возвращают сведения в виде одного значения или результирующего набора.

Чтобы создать объект SQLServerDatabaseMetaData, вы можете использовать метод [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) для получения сведений о базе данных, к которой установлено подключение.

В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образцом базы данных передается в функцию, метод GetObject класса SQLServerConnection используется для возврата объекта SQLServerDatabaseMetadata, а затем различные методы класса Объект SQLServerDatabaseMetaData используется для вывода сведений о драйвере, версии драйвера, имени базы данных и версии базы данных.

[!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]

## <a name="see-also"></a>См. также раздел

[Обработка метаданных с помощью JDBC Driver](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
