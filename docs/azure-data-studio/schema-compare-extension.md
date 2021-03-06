---
title: Расширение сравнения схем
titleSuffix: Azure Data Studio
description: Установка и использование расширения Schema Compare в Azure Data Studio
ms.custom: seodec18
ms.date: 11/04/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: f93711983eb32a979e47941883e968b52e03459c
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532536"
---
# <a name="schema-compare-extension"></a>Расширение сравнения схем
Расширение сравнения схем предоставляет удобный интерфейс для сравнения определений двух баз данных, а также применения различий из источника к целевому объекту.


## <a name="features"></a>Компоненты

* Сравнение схем двух файлов или баз данных DACPAC
* Просмотр результатов в виде набора действий, которые необходимо применить к целевому объекту, чтобы согласовать его с источником
* Выборочное исключение действий, представленных в результатах
* Установка параметров, определяющих область сравнения
* Применение изменений к целевому объекту или создание скрипта, выполняющего аналогичные действия
* Сохранение результатов сравнения

![Сравнение схем: пример сравнения](media/extensions/schema-compare-extension/schema-compare.png)


## <a name="why-would-i-use-the-schema-compare-extension"></a>Для чего можно использовать расширение сравнения схем?

Ручная синхронизация различных версий базы данных может быть слишком трудоемкой задачей. Расширение сравнения схем позволяет упростить процесс сравнения баз данных и обеспечить полноценное управление их синхронизацией &mdash; вы можете выборочно отфильтровывать отдельные различия или категории различий, прежде чем применять изменения. Расширение сравнения схем — это надежный инструмент, с помощью которого вы сможете сэкономить немало времени и уменьшить объем создаваемого кода.

![Сравнение схем: диалоговое окно параметров](media/extensions/schema-compare-extension/schema-compare-options.png)


## <a name="install-the-extension"></a>Установка расширения

1. Щелкните значок расширений, чтобы просмотреть доступные расширения.

    ![Значок "Диспетчер расширений"](media/extensions/extension-manager-icon.png)

2. Найдите и выберите расширение **Сравнение схем**, чтобы просмотреть сведения о нем. Щелкните **Установить**, чтобы добавить расширение.

3. После установки выберите **Перезагрузить**, чтобы включить расширение в Azure Data Studio (требуется только при первой установке расширения).


## <a name="launch-a-schema-compare"></a>Запуск сравнения схем

1. Чтобы открыть диалоговое окно "Сравнение схем", **щелкните правой кнопкой мыши** базу данных в обозревателе объектов и выберите пункт **Сравнение схем**. Выбранная база данных будет установлена в качестве источника для сравнения.

    ![Меню для запуска сравнения схем](media/extensions/schema-compare-extension/schema-compare-launch.png)


2. С помощью кнопок с многоточием (...) измените источник и целевой объект для сравнения схем, после чего нажмите кнопку "ОК".

    ![Выбор источника и целевого объекта для сравнения схем](media/extensions/schema-compare-extension/schema-compare-select-source-target.png)

3. Чтобы задать настройки сравнения, воспользуйтесь кнопкой **Параметры** на панели инструментов.

4. Нажмите кнопку **Сравнить**, чтобы просмотреть результаты сравнения.


## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о сравнении схем см. в [нашей документации](https://docs.microsoft.com/sql/ssdt/how-to-use-schema-compare-to-compare-different-database-definitions).
Сообщить о проблемах и запросить функции можно [здесь](https://github.com/microsoft/azuredatastudio/issues).