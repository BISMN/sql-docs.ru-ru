---
title: Добавление функциональных возможностей с помощью расширяемости
titleSuffix: Azure Data Studio
description: Сведения о модели расширяемости и основных областях расширяемости для добавления функциональных возможностей в Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 20158894567c1452a8d605f5cec84354654c5e96
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959591"
---
# <a name="getting-started-with-includename-sosincludesname-sos-shortmd-extensibility"></a>Начало работы с расширяемостью [!INCLUDE[name-sos](../includes/name-sos-short.md)]

В [!INCLUDE[name-sos](../includes/name-sos.md)] есть несколько механизмов расширяемости для настройки пользовательского интерфейса и предоставления доступа к этим настройкам всему сообществу пользователей. Так как базовая платформа [!INCLUDE[name-sos](../includes/name-sos.md)] построена на основе Visual Studio Code, доступны большинство интерфейсов API расширяемости Visual Studio Code. Кроме того, мы предоставляем дополнительные точки расширяемости для действий, связанных с управлением данными.

Вот некоторые из основных точек расширяемости:

- интерфейсы API расширяемости Visual Studio Code;
- средства разработки расширений Azure Data Studio;
- управление вкладом на панели вкладок панели мониторинга;
- аналитика с действиями;
- интерфейсы API расширяемости Azure Data Studio;
- пользовательские интерфейсы API поставщиков данных.

## <a name="visual-studio-code-extensibility-apis"></a>Интерфейсы API расширяемости Visual Studio Code

Так как базовая платформа [!INCLUDE[name-sos](../includes/name-sos.md)] построена на основе Visual Studio Code, сведения об интерфейсах API расширяемости Visual Studio Code можно найти в документации по [разработке расширений](https://code.visualstudio.com/docs/extensions/overview) и [API расширений](https://code.visualstudio.com/docs/extensionAPI/overview) на веб-сайте Visual Studio Code.

## <a name="manage-dashboard-tab-panel-contributions"></a>Управление вкладом на панели вкладок панели мониторинга

Подробные сведения см. в разделах [Точки вклада](#contribution-points) и [Переменные контекста](#context-variables).

## <a name="azure-data-studio-extensibility-apis"></a>Интерфейсы API расширяемости Azure Data Studio

Подробные сведения см. в статье [API расширяемости](extensibility-apis.md).


## <a name="contribution-points"></a>Точки вклада

В этом разделе рассматриваются различные точки вклада, определенные в манифесте расширения package.json.

В azuredatastudio поддерживается технология IntelliSense.

## <a name="contributes-dashboard"></a>Панель мониторинга вклада

Добавляйте на панель мониторинга вкладки, контейнеры и аналитические мини-приложения.

![Панель мониторинга](media/extensibility/dashboard-page.png)

`dashboard.tabs`

Элемент dashboard.tabs создает разделы вкладок на странице панели мониторинга. Он принимает объект или массив объектов.  

```json
"dashboard.tabs": [
{
    "id": "test-tab1",
    "title": "Test 1",
    "description": "The test 1 displays a list of widgets.",
    "when": "connectionProvider == 'MSSQL' && !mssql:iscloud",
    "alwaysShow": true,
    "container": {
        ...
    }
}
]
```

`dashboard.containers`

Вместо указания контейнера панели мониторинга в коде (внутри dashboard.tab) можно регистрировать контейнеры с помощью элемента dashboard.containers. Он принимает объект или массив объектов.

```json
"dashboard.containers": [
{
    "id": "innerTab1",
    "container": {
        ...
    }
},
{
    "id": "innerTab2",
    "container": {
       ...
    }
}
]
```

Обращение к зарегистрированному контейнеру производится по его идентификатору.

```json
"dashboard.tabs": [
{
    ...
    "container": {
        "innerTab1": {             
        }
    }
}
]

```

`dashboard.insights`

Вы можете регистрировать аналитические мини-приложения с помощью элемента dashboard.insights. Это аналогично процедуре, описываемой в статье [Руководство. Создание настраиваемого аналитического мини-приложения](https://docs.microsoft.com/sql/sql-operations-studio/tutorial-build-custom-insight-sql-server).

```json
"dashboard.insights": {
"id": "my-widget"
"type": {
    "count": {
        "dataDirection": "vertical",
        "dataType": "number",
        "legendPosition": "none",
           "labelFirstColumn": false,
        "columnsAsLabels": false
       }
   },
   "queryFile": "{your file folder}/activeSession.sql"
}
```


### <a name="dashboard-container-types"></a>Типы контейнеров панели мониторинга

В настоящее время поддерживаются четыре типа контейнеров:

1. `widgets-container`

    ![Контейнер мини-приложений](media/extensibility/widgets-container.png)

    Список мини-приложений, которые будут отображаться в контейнере. Это потоковый макет. Он принимает список мини-приложений.

    ```json
    "container": {
        "widgets-container": [
        {
            "widget": {
                "query-data-store-db-insight": {
                }
            }
        },
        {
            "widget": {
                "explorer-widget": {
                }
            }
        }
      ]
    }
    ```

2. `webview-container`

    ![Контейнер веб-представления](media/extensibility/webview-container.png)

    Веб-представление будет занимать весь контейнер. Идентификатор веб-представления должен совпадать с идентификатором вкладки.

    ```json
    "container": {
        "webview-container": null
    }
    ```

3. `grid-container`

   ![Контейнер сетки](media/extensibility/grid-container.png)

   Список мини-приложений или веб-представлений, которые будут отображаться в макете сетки.

    ```json
    "container": {
        "grid-container": [
        {
            "name": "widget 1",
            "widget": {
                "explorer-widget": {
                }
            },
            "row":0,
            "col":0
        },
        {
            "name": "widget 2",
            "widget": {
                "tasks-widget": {
                    "backup", 
                    "restore",
                    "configureDashboard",
                    "newQuery"
                }
            },
            "row":0,
            "col":1
        },
        {
            "name": "Webview 1",
            "webview": {
                "id": "google"
            },
            "row":1,
            "col":0,
            "colspan":2
        },
        {
            "name": "widget 3",
            "widget": {
                "explorer-widget": {}
            },
            "row":0,
            "col":3,
            "rowspan":2
        },
    ]
    ```

4.  `nav-section`

    ![Раздел навигации](media/extensibility/nav-section.png)

    Раздел навигации будет отображаться в контейнере.

    ```json
    "container": {
        "nav-section": [
            {
                "id": "innerTab1",
                "title": "inner-tab1",
                "icon": {
                    "light": "./icons/tab1Icon.svg",
                    "dark": "./icons/tab1Icon_dark.svg"
                }
                "container": {
                    ...
                }
            },
            {
                "id": "innerTab2",
                "title": "inner-tab2",
                "icon": {
                    "light": "./icons/tab2Icon.svg",
                    "dark": "./icons/tab2Icon_dark.svg"
                }
                "container": {
                    ...
                }
            }
        ]
    }
    ```



## <a name="context-variables"></a>Переменные контекста

Общие сведения о контексте в Visual Studio Code и, соответственно, в Azure Data Studio см. в статье, посвященной [расширяемости](https://code.visualstudio.com/docs/extensionAPI/extension-points#_example).

В Azure Data Studio для расширений доступен особый контекст, связанный с подключениями к базам данных.

### <a name="dashboard"></a>Панель мониторинга

Для панели мониторинга предоставляются следующие переменные контекста:

|переменная контекста| description|
|:---|:---|
|`connectionProvider` | Строка с идентификатором поставщика текущего подключения. Например: `connectionProvider == 'MSSQL'`.|
|`serverName`|Строка с именем сервера для текущего подключения. Например: `serverName == 'localhost'`.|
|`databaseName` | Строка с именем базы данных для текущего подключения. Например: `databaseName == 'master'`.|
|`connection` | Полный объект профиля подключения для текущего подключения (IConnectionProfile)|
|`dashboardContext` | Строка с контекстом текущей страницы панели мониторинга. Возможное значение — "database" или "server". Например: `dashboardContext == 'database'`|
