---
title: Настройка и использование Always Encrypted с безопасными анклавами | Документация Майкрософт
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: bda4d41d4f2a9c92dca2d41b959ad4c4b32a1c79
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73594478"
---
# <a name="configure-and-use-always-encrypted-with-secure-enclaves"></a>Настройка и использование Always Encrypted с безопасными анклавами 

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md) расширяет существующую функцию [Always Encrypted](always-encrypted-database-engine.md), чтобы обеспечить расширенные функции защиты конфиденциальных данных. В этой статье перечислены распространенные задачи по настройке и использованию этой функции.

См. руководство о том, как приступить к работе с Always Encrypted с безопасными анклавами, см. [Руководство: Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).

## <a name="set-up-your-environment-to-support-enclaves-and-attestation"></a>Настройка среды для поддержки анклавов и аттестации
Подробности см. в следующих статьях:
- [Настройка службы защиты узла для Always Encrypted в SQL Server](https://docs.microsoft.com/windows-server/security/set-up-hgs-for-always-encrypted-in-sql-server).

## <a name="manage-keys-for-always-encrypted-with-secure-enclaves"></a>Управление ключами для Always Encrypted с безопасными анклавами
Подробные сведения см. в следующих разделах:
- [Управление ключами для Always Encrypted с безопасными анклавами — обзор](always-encrypted-enclaves-manage-keys.md)
- [Подготовка ключей с поддержкой анклава](always-encrypted-enclaves-provision-keys.md)
- [Смена ключей с поддержкой анклава](always-encrypted-enclaves-rotate-keys.md)

## <a name="configure-columns-with-always-encrypted-with-secure-enclaves"></a>Настройка столбцов с помощью Always Encrypted с безопасными анклавами
Подробные сведения см. в следующих разделах:
- [Настройка шифрования столбцов на месте с помощью Always Encrypted с безопасными анклавами — обзор](always-encrypted-enclaves-configure-encryption.md)
- [Настройка шифрования столбцов на месте с помощью Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md)
- [Включение Always Encrypted с безопасными анклавами для существующих зашифрованных столбцов](always-encrypted-enclaves-enable-for-encrypted-columns.md)

> [!NOTE]
> Пошаговое руководство о том, как настроить тестовую среду и протестировать функциональные возможности Always Encrypted с безопасными анклавами в SSMS, см. в статье [Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).

## <a name="query-columns-using-always-encrypted-with-secure-enclaves"></a>Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами
Подробные сведения см. в следующих разделах:
- [Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами — обзор](always-encrypted-enclaves-query-columns.md)
- [Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами с использованием SSMS](always-encrypted-enclaves-query-columns-ssms.md)

## <a name="create-and-use-indexes-on-enclave-enabled-columns"></a>Создание и использование индексов в столбцах с поддержкой анклава
Подробные сведения см. в следующих разделах:
- [Создание и использование индексов в столбцах с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-create-use-indexes.md)

## <a name="develop-applications-using-always-encrypted-with-secure-enclaves"></a>Разработка приложений с помощью Always Encrypted с безопасными анклавами
Подробные сведения см. в следующих разделах:
- [Разработка приложений с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-client-development.md)
