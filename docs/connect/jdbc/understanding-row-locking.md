---
title: Основные сведения о блокировке строк | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bcd18baf401378605abf0d53e203d0a3745ee887
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027330"
---
# <a name="understanding-row-locking"></a>Основные сведения о блокировке строк

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] использует блокировки строк [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С помощью таких блокировок реализуется управление параллелизмом между несколькими пользователями, одновременно вносящими изменения в базу данных. По умолчанию управление транзакциями и блокировками ведется в рамках соединения. Например, если приложение открывает два соединения JDBC, то блокировки, установленные одним соединением, не могут совмещаться с другим соединением. Ни одно из соединений не может устанавливать блокировки, которые вызывают конфликт с блокировкам, удерживаемыми другим соединением.

> [!NOTE]  
> Если используется блокировка строк, то блокируются все строки в буфере выборки, поэтому задание очень большого размера выборки может отрицательно сказаться на параллелизме.

Блокировка обеспечивает целостность транзакций и согласованность базы данных. Блокировка не позволяет пользователям считывать данные, которые изменяются другими пользователями, а также исключает одновременное изменение одних и тех же данных несколькими пользователями. Если блокировка не применяется, то данные в базе данных могут утратить логическую верность, и запросы к этим данным могут давать непредвиденные результаты.

> [!NOTE]  
> Дополнительные сведения о блокировке строк в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе "Блокировки в компоненте [!INCLUDE[ssDE](../../includes/ssde_md.md)]" электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="see-also"></a>См. также раздел

[Управление результирующими наборами с помощью JDBC Driver](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)
