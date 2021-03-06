---
title: Использование Записных книжек SQL в Azure Data Studio
titleSuffix: Azure Data Studio
description: Узнайте, как использовать Записные книжки SQL в Azure Data Studio.
ms.custom: seodec18
ms.date: 06/28/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: achatter; alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 9af2e04a3973eddfcd714c7968c35e544302aba9
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959266"
---
# <a name="how-to-use-notebooks-in-azure-data-studio"></a>Использование записных книжек в Azure Data Studio

В этой статье содержатся сведения о запуске записных книжек в Azure Data Studio и создании собственных записных книжек. Здесь также приводятся инструкции по созданию записных книжек с помощью разных ядер.


## <a name="connect-to-sql-server"></a>Подключение к SQL Server

В Azure Data Studio в поле "Тип подключения" выберите "Microsoft SQL Server".
Кроме того, можно нажать клавишу F1, выбрать **Создать подключение**  и подключиться к SQL Server.

![image1](media/sql-notebooks/connection-info.png)

## <a name="launch-notebooks"></a>Запуск записных книжек

Запустить новую записную книжку можно разными способами.

1. В Azure Data Studio откройте меню **Файл** и щелкните **Создать записную книжку**.

    ![image3](media/sql-notebooks/file-new-notebook.png)

3. Щелкните правой кнопкой мыши подключение **SQL Server**, а затем выберите **Создать записную книжку**. 
    ![image3](media/sql-notebooks/server-new-notebook.png)

4. Откройте палитру команд (**CTRL+SHIFT+P**) и введите **Новая записная книжка**. Откроется новый файл с именем `Notebook-1.ipynb`.

## <a name="supported-kernels-and-attach-to-context"></a>Поддерживаемые ядра и подключение к контексту

При установке записной книжки в Azure Data Studio изначально поддерживается ядро SQL. Разработчики SQL, создающие записные книжки, будут использовать именно его. 

Ядро SQL также можно применять для подключения к экземплярам сервера PostgreSQL. Разработчики PostgreSQL, которым требуется подключиться к серверу PostgreSQL, должны скачать [**расширение PostgreSQL**](postgres-extension.md) в магазине расширений Azure Data Studio.

![image7](media/sql-notebooks/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>Ядро SQL

В ячейках кода в записной книжке (так же как и в редакторе запросов) поддерживаются современные возможности написания кода SQL, которые упрощают выполнение повседневных задач за счет встроенных функций, таких как расширенный редактор SQL, технология IntelliSense и встроенные фрагменты кода. Фрагменты кода позволяют формировать правильный синтаксис SQL для создания баз данных, таблиц, представлений, хранимых процедур и т. д., а также для обновления существующих объектов базы данных. С помощью фрагментов кода можно быстро создавать копии базы данных для разработки или тестирования, а также генерировать и выполнять сценарии.

Нажмите кнопку **Выполнить**, чтобы выполнить каждую ячейку.

Ядро SQL для подключения к экземпляру SQL Server

![image7](media/sql-notebooks/intellisense-code-cell.png)

Результаты запроса

![image19](media/sql-notebooks/sql-cell-results.png)

Ядро SQL для подключения к экземпляру сервера PostgreSQL 

![image18](media/sql-notebooks/pgsql-code-cell.png)

Результаты запроса

![image20](media/sql-notebooks/pgsql-cell-results.png)

### <a name="configure-python-for-notebooks"></a>Настройка Python для записных книжек

При выборе в раскрывающемся списке ядра, отличного от ядра SQL, вам будет предложено **настроить Python для записных книжек**. Зависимости записной книжки устанавливаются в заданном расположении, но вы можете принять решение о необходимости указания расположения установки. Установка может занять некоторое время, поэтому не рекомендуется закрывать приложение до ее завершения. После окончания установки можно приступить к написанию кода на поддерживаемом языке.

![image21](media/sql-notebooks/configure-python.png)

После установки в журнале задач появится уведомление, а в терминале выходных данных будут отображены сведения о расположении запущенного внутреннего сервера Jupyter.

![image22](media/sql-notebooks/jupyter-backend.png)

|Ядро|Описание
|:-----|:-----
| Ядро SQL | Написание кода SQL, предназначенного для реляционной базы данных.
|Ядро PySpark3 и PySpark| Написание кода Python с использованием вычислительных ресурсов Spark из кластера.
|Ядро Spark|Написание кода Scala и R с использованием вычислительных ресурсов Spark из кластера.
|Ядро Python|Написание кода Python для локальной разработки.

`Attach to` предоставляет контекст для присоединения ядра. Если вы используете ядро SQL, то можете `Attach to` любой из экземпляров SQL Server.

Если используется ядро Python3, то `Attach to` имеет значение `localhost`. Это ядро можно использовать для локальной разработки на Python.

Если вы подключились к кластеру больших данных SQL Server 2019, значением `Attach to` по умолчанию является эта конечная точка кластера, и вы можете отправлять код Python, Scala и R с помощью вычислительного ресурса Spark кластера.

### <a name="code-cells-and-markdown-cells"></a>Ячейки кода и ячейки с разметкой Markdown

Добавьте новую ячейку кода, щелкнув команду **+Код** на панели инструментов.

Добавьте новую текстовую ячейку, щелкнув команду **+Текст** на панели инструментов.

![image8](media/sql-notebooks/notebook-toolbar.png)

Ячейка перейдет в режим правки, и по мере ввода текста с разметкой Markdown вам будет доступна возможность предпросмотра.

![image9](media/sql-notebooks/notebook-markdown-cell.png)

Щелкните вне текстовой ячейки, чтобы отобразить текст с разметкой Markdown.

![image10](media/sql-notebooks/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>Доверенные и недоверенные

Записные книжки, открытые в Azure Data Studio, являются **доверенными** по умолчанию.

Записная книжка, открываемая из другого источника, откроется в **недоверенном** режиме, после чего ее можно сделать **доверенной**.

### <a name="save"></a>Сохранять 

Записную книжку можно сохранить с помощью сочетания клавиш **CTRL+S** или команд **Файл > Сохранить**, **Файл > Сохранить как...** и **Файл > Сохранить все** в меню "Файл", а также команд **Файл: Сохранить**, вводимых в палитре команд.

### <a name="pyspark3pyspark-kernel"></a>Ядро Pyspark3 и PySpark

Выберите `PySpark Kernel` и введите приведенный ниже код в ячейке.

Нажмите кнопку **Запустить**.

Запустится приложение Spark, которое вернет следующие выходные данные:

![image12](media/sql-notebooks/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Ядро Spark | Язык Scala

Выберите `Spark|Scala Kernel` и введите приведенный ниже код в ячейке.

![image13](media/sql-notebooks/spark-scala.png)

Чтобы просмотреть параметры ячейки, щелкните значок параметров.

![image14](media/sql-notebooks/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Ядро Spark | Язык R

В раскрывающемся списке ядер выберите "Spark | R". Введите или вставьте код в ячейку. Нажмите кнопку **Выполнить**, чтобы получить и просмотреть следующие выходные данные.

![image15](media/sql-notebooks/spark-r.png)

### <a name="local-python-kernel"></a>Локальное ядро Python

Выберите локальное ядро Python и в ячейке введите следующее:

![image16](media/sql-notebooks/local-python.png)

## <a name="manage-packages"></a>Управление пакетами
Локальная разработка на Python была оптимизирована, и теперь вам доступна возможность установки пакетов, которые потребуются клиентам в их сценариях. По умолчанию включены такие распространенные пакеты, как `pandas`, `numpy` и т. д., но если вам нужен пакет, который отсутствует, напишите в ячейке записной книжки следующий код: 

```python
import <package-name>
```

После выполнения этой команды возвращается `Module not found`. Если пакет существует, ошибка не возникнет.

Если возвращается ошибка `Module not Found`, щелкните **Управление пакетами**, чтобы запустить мастер. 

![image17](media/sql-notebooks/manage-packages.png)

В мастере можно просмотреть **установленные** пакеты. Вы можете просмотреть список, чтобы найти соответствующую версию каждого из этих пакетов. Чтобы **удалить** любой из пакетов, щелкните его и выберите команду **Удалить выбранные пакеты**.

Вы также можете щелкнуть **Добавить новые пакеты**, **найти** определенный пакет, выбрать соответствующую версию, а затем нажать **Установить**. По умолчанию выбирается последняя версия искомого пакета. 

После установки пакета вы сможете перейти в ячейку записной книжки и ввести следующую команду:

```python
import <package-name>
```

Чтобы **удалить** любой из этих пакетов, щелкните его и выберите команду **Удалить выбранные пакеты**.

## <a name="next-steps"></a>Следующие шаги

Сведения о работе с существующей записной книжкой см. в статье об [ управлении записными книжками в Azure Data Studio](https://docs.microsoft.com/sql/big-data-cluster/notebooks-how-to-manage?view=sqlallproducts-allversions).