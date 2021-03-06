---
title: Создание данных в примерах SQL WideWorldImporters
ms.date: 04/04/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 0f880ea881b53c2600fb1fffdf7da5d16ab8d423
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056286"
---
# <a name="wideworldimporters-data-generation"></a>Создание данных WideWorldImporters
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Выпущенные версии баз данных WideWorldImporters и WideWorldImportersDW содержат данные с 1 января 2013 до дня создания баз данных.

При использовании этих образцов баз данных может потребоваться включить более свежие образцы данных.

## <a name="data-generation-in-wideworldimporters"></a>Создание данных в WideWorldImporters

Создание образца данных до текущей даты:

1. Если это еще не сделано, установите чистую версию базы данных WideWorldImporters. Инструкции по установке см. в разделе [Установка и настройка](wide-world-importers-oltp-install-configure.md).
2. Выполните следующую инструкцию в базе данных:

    ```
        EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
            @AverageNumberOfCustomerOrdersPerDay = 60,
            @SaturdayPercentageOfNormalWorkDay = 50,
            @SundayPercentageOfNormalWorkDay = 0,
            @IsSilentMode = 1,
            @AreDatesPrinted = 1;
    ```

    Эта инструкция добавляет пример данных о продажах и покупках в базу данных вплоть до текущей даты. В нем отображается ход создания данных по дням. Создание данных может занять около 10 минут каждый год, требующий данных. Из-за случайного коэффициента в создании данных существуют некоторые различия в данных, создаваемых между запусками.

    Чтобы увеличить или уменьшить объем данных, создаваемых для заказов в день, измените значение параметра `@AverageNumberOfCustomerOrdersPerDay`. Используйте параметры `@SaturdayPercentageOfNormalWorkDay` и `@SundayPercentageOfNormalWorkDay`, чтобы определить объем заказа для выходных дней.

## <a name="import-generated-data-in-wideworldimportersdw"></a>Импорт созданных данных в WideWorldImportersDW

Чтобы импортировать образец данных вплоть до текущей даты в базе данных WideWorldImportersDW OLAP, выполните следующие действия.

1. Выполните логику создания данных в базе данных OLTP WideWorldImporters, выполнив действия, описанные в предыдущем разделе.
2. Если вы еще не сделали этого, установите чистую версию базы данных WideWorldImportersDW. Инструкции по установке см. в разделе [Установка и настройка](wide-world-importers-oltp-install-configure.md).
3. Выполните повторное заполнение базы данных OLAP, выполнив следующую инструкцию в базе данных:

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. Запустите пакет SQL Server Integration Services *ежедневного ETL. ISPAC* , чтобы импортировать данные в базу данных OLAP. Чтобы узнать, как запустить задание ETL, см. раздел [WIDEWORLDIMPORTERS ETL Workflow](wide-world-importers-perform-etl.md).

## <a name="generate-data-in-wideworldimportersdw-for-performance-testing"></a>Создание данных в WideWorldImportersDW для тестирования производительности

WideWorldImportersDW может произвольно увеличить размер данных для тестирования производительности. Например, он может увеличить размер данных для использования с кластеризованным индексированием columnstore.

Одна из проблем заключается в том, чтобы размер загружаемого файла был достаточно мал для легкого скачивания, но достаточно велик, чтобы продемонстрировать SQL Server функции производительности. Например, значительные преимущества для индексов columnstore достигаются только при работе с большим количеством строк. 

Для увеличения количества строк в `Fact.Sale` таблице можно использовать процедуру `Application.Configuration_PopulateLargeSaleTable`. Строки вставляются в 2012 календарного года, чтобы избежать конфликта с существующими данными в мире импорта, которые начинаются с 1 января 2013.

### <a name="procedure-details"></a>Сведения о процедуре

#### <a name="name"></a>Name

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>Параметры

  `@EstimatedRowsFor2012` **bigint** (значение по умолчанию — 12000000)

#### <a name="result"></a>Результат

Приблизительно требуемое число строк вставляется в таблицу `Fact.Sale` 2012 года. Процедура искусственно ограничивает число строк до 50 000 в день. Это ограничение можно изменить, но ограничение помогает избежать случайного перероста таблицы.

Процедура также применяет кластеризованное индексирование columnstore, если оно еще не применено.
