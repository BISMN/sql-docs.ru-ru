---
title: Обзор решения базы данных службы "Экспериментирование" Assistant для SQL Server обновляет
description: Обзор помощника по базе данных службы "Экспериментирование"
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: 1c2a28a5dc83d22a327bf797358d5edae69eb82b
ms.sourcegitcommit: 9ea11d738503223b46d2be5db6fed6af6265aecc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2019
ms.locfileid: "56987830"
---
# <a name="overview-of-database-experimentation-assistant"></a>Обзор помощника по базе данных службы "Экспериментирование"

Помощник по базе данных службы "Экспериментирование" (веб) — это решение службы "Экспериментирование" для обновления до SQL Server. Инициатив помогут вам оценить целевая версия SQL Server для конкретной рабочей нагрузки. Клиенты, которые при обновлении с более ранних версий SQL Server (начиная с 2005 г.) до более новой версии SQL Server можно использовать средство предоставляет важные показатели analysis. 

Анализ метрик Инициатив включают:
- Запросы, содержащие ошибки совместимости
- Снижение запросы и планы запросов
- Другие данные сравнения рабочей нагрузки

Сравнение данных может привести к большей уверенностью и успешно вопросы обновления.

19-минутный введение Инициатив и демонстрацию в следующем видео:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]

## <a name="get-dea"></a>Получить Инициатив

Чтобы установить Инициатив, [загрузить](https://www.microsoft.com/download/details.aspx?id=54090) последнюю версию средства. Затем запустите **DatabaseExperimentationAssistant.exe** файла.

## <a name="solution-architecture-for-comparing-workloads"></a>Архитектура решения для сравнения рабочих нагрузок

Следующей схеме показана архитектура решения для сравнения рабочей нагрузки. Сравнение рабочей нагрузки использует Инициатив и распределенного воспроизведения, во время обновления с SQL Server 2008 до SQL Server 2016.

![Архитектура решения сравнения рабочей нагрузки](./media/database-experimentation-assistant-overview/dea-overview-compare-solution-architecture.png)

## <a name="dea-prerequisites"></a>Предварительные требования для Инициатив

Ниже приведены некоторые предварительные требования для запуска Инициатив.
- Минимальные требования к оборудованию: Одноядерной машине с 3,5 ГБ ОЗУ.
- Требование идеальный оборудования. 8 ядерный Процессор (3,5 ГБ ОЗУ или больше). Процессоры, которые имеют более чем восьми ядер не улучшают Инициатив сред выполнения.
- Дополнительные 33% размер трассировки производительности требуется хранилище A, B и баз данных анализа отчетов.

## <a name="configure-dea"></a>Настройка Инициатив

В архитектуре готовности среды, мы рекомендуем установить Инициатив *на том же компьютере, что и контроллер распределенного воспроизведения*. Такой подход позволяет избежать вызовы между компьютерами и упрощает настройку.

### <a name="required-configuration-for-workload-comparison-by-using-dea"></a>Необходимые настройки для сравнения рабочей нагрузки с помощью Инициатив

Инициатив подключается к серверам баз данных с использованием проверки подлинности Windows. Убедитесь, что пользователь, запускающий Инициатив может подключиться к серверам баз данных (источник, цель и анализа) с использованием проверки подлинности Windows.

**Узнайте требования конфигурации**:

*   Пользователь, запускающий веб можно подключиться к исходному серверу базы данных с использованием проверки подлинности Windows.
*   Пользователь, запускающий Инициатив прав системного администратора на исходном сервере базы данных.
*   Учетная запись службы, под управлением исходном сервере базы данных имеет доступ на запись к пути папки трассировки.

Дополнительные сведения см. в разделе [записи часто задаваемые вопросы](database-experimentation-assistant-capture-trace.md#frequently-asked-questions-about-trace-capture)

**Требования к конфигурации воспроизведению**: 

*   Пользователь, запускающий Инициатив можно подключиться к целевому серверу базы данных с использованием проверки подлинности Windows.
*   Пользователь, запускающий Инициатив имеет права системного администратора на целевом сервере базы данных.
*   Учетная запись службы, под управлением целевых серверов базы данных имеет доступ на запись к пути папки трассировки.
*   Учетная запись службы которых выполняются клиенты распределенного воспроизведения можно подключиться к целевому серверу базы данных с использованием проверки подлинности Windows.
*   Инициатив взаимодействует с контроллером распределенного воспроизведения с помощью COM-интерфейсов. Убедитесь, что TCP-порты открыты для входящих запросов на контроллере распределенного воспроизведения.

Дополнительные сведения см. в разделе [воспроизведения часто задаваемые вопросы](database-experimentation-assistant-replay-trace.md#frequently-asked-questions-about-trace-replay)

**Требования к конфигурации Analysis**: 

*   Пользователь, запускающий Инициатив можно подключиться к серверу базы данных служб analysis с помощью проверки подлинности Windows.
*   Пользователь, запускающий Инициатив прав системного администратора на исходном сервере базы данных.

Дополнительные сведения см. в разделе [анализ часто задаваемые вопросы](database-experimentation-assistant-create-report.md#frequently-asked-questions-about-analysis-reports)

## <a name="set-up-telemetry"></a>Настройка телеметрии

Инициатив есть Интернет-функция, которая может отправлять данные телеметрии в корпорацию Майкрософт. Корпорация Майкрософт собирает данные телеметрии для улучшения качества продукта. Данные телеметрии является необязательным. Собираемая информация также сохраняется на компьютере для локального аудита. Всегда можно увидеть, что именно должна собирать. Все файлы журнала из Инициатив сохраняются в папке % temp %\\папку Инициатив.

Можно решить, какие события собираются. Также принято ли собранные события отправляются в корпорацию Майкрософт. Существует четыре типа событий:

*   **Объект TraceEvent**: События использования для приложения (например, «захват активированные stop»).
*   **Исключение**: Исключение, возникающее во время использования приложения.
*   **DiagnosticEvent**: Журнал событий, способствующую при возникновении проблем (*не* отправляются в корпорацию Майкрософт).
*   **FeedbackEvent**: Отзывы пользователей, передаваемых через приложение.

Ниже показано, как выбрать, какие события собираются и ли события отправляются в корпорацию Майкрософт:

1.  Перейдите к расположению, где установлен Инициатив (например, C:\\Program Files (x86)\\Корпорация Майкрософт\\помощник базы данных службы "Экспериментирование").
2.  Откройте два файла .config: DEA.exe.config (для приложения) и DEACmd.exe.config (для интерфейса командной строки).
3.  Чтобы остановить сбор тип события, установите для параметра *событий* (например, **TraceEvent**) для **false**. Чтобы начать сбор событий снова, задайте значение **true**.
4.  Чтобы остановить сохранять локальные копии событий, установите для параметра **TraceLoggerEnabled** для **false**. Чтобы начать попытку сохранения локальных копий, задайте значение **true**.
5.  Чтобы остановить отправку событий в корпорацию Майкрософт, установите для параметра **AppInsightsLoggerEnabled** для **false**. Чтобы начать попытку отправки событий в корпорацию Майкрософт, задайте значение **true**.

Инициатив регулируется [заявление о конфиденциальности Microsoft](https://aka.ms/dea-privacy).

## <a name="next-steps"></a>Следующие шаги

[Начало работы](database-experimentation-assistant-get-started.md) поможет выполнить шаги, необходимые для записи, воспроизведения и анализ трассировки.