---
title: Управление Кластерами больших данных SQL Server с помощью записных книжек Azure Data Studio
titleSuffix: Manage SQL Server Big Data Clusters with Azure Data Studio notebooks
description: Используйте записную книжку из Azure Data Studio для управления кластером больших данных и устранения его неполадок.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 09/09/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 860524daa5e6ab2db17fdf95cf5aa785aeb4fdf7
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844288"
---
# <a name="manage-sql-server-big-data-clusters-with-azure-data-studio-notebooks"></a>Управление Кластерами больших данных SQL Server с помощью записных книжек Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] предоставляет расширение для Azure Data Studio, включающее в себя записные книжки. Записная книжка предоставляет документацию и код, которые можно использовать в Azure Data Studio для управления Кластерами больших данных SQL Server 2019.

[Записные книжки](notebooks-guidance.md), которые изначально были реализованы как проект с открытым кодом, теперь включены в [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download). Вы можете использовать разметку Markdown для текста в текстовых ячейках и одно из доступных ядер для написания кода в ячейках кода.

С помощью записных книжках можно развертывать кластеры больших данных для [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Помимо стандартных записных книжек, вы можете просмотреть коллекцию записных книжек, называемых книгами Jupyter. Книга Jupyter содержит оглавление для навигации по коллекции записных книжек, что позволяет легко найти требуемую записную книжку для устранения неполадок SQL Server или просмотра состояния кластера.

## <a name="prerequisites"></a>предварительные требования

Для открытия записной книжки необходимы следующие компоненты:

* последняя [сборка Azure Data Studio для участников программы предварительной оценки](https://aka.ms/azuredatastudio-rc);
* расширение [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], установленное в Azure Data Studio.

Помимо этих компонентов, для развертывания Кластеров больших данных SQL Server 2019 требуется следующее:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="access-troubleshooting-notebooks"></a>Доступ к записным книжкам для устранения неполадок
Получить доступ к записным книжкам для устранения неполадок можно тремя способами.

### <a name="command-palette"></a>Палитра команд
1. Выберите элемент **Вид** > **Палитра команд**.
2. Введите **Книги Jupyter: руководство для SQL Server 2019**.

Откроется мини-приложение "Книги Jupyter" с книгой Jupyter, содержащей записные книжки для устранения неполадок, связанных с Кластерами больших данных SQL Server.

### <a name="sql-master-dashboard"></a>Главная панель мониторинга SQL
1. После установки Azure Data Studio для участников программы предварительной оценки подключитесь к экземпляру Кластеров больших данных SQL Server.
2. Подключившись к экземпляру, щелкните правой кнопкой мыши имя сервера в разделе **Подключения** и выберите пункт **Управление**.
3. На панели мониторинга выберите **Кластер больших данных SQL Server**. Выберите **руководство по SQL Server 2019**, чтобы открыть книгу Jupyter с нужными записными книжками.
    ![Записные книжки Jupyter на панели мониторинга](media/manage-notebooks/jupyter-book-button.png)

1. Выберите записную книжку, соответствующую нужной задаче.

### <a name="controller-dashboard"></a>Информационная панель контроллера
1. В представлении **Подключения** разверните раздел **Кластеры больших данных SQL Server**.
2. Добавьте сведения о конечной точке контроллера.
3. Подключившись к контроллеру, щелкните правой кнопкой мыши конечную точку и выберите пункт **Управление**.
4. После загрузки панели мониторинга выберите **Устранение неполадок**, чтобы открыть руководства по устранению неполадок в книге Jupyter.

## <a name="use-troubleshooting-notebooks"></a>Использование записных книжек для устранения неполадок
1. Найдите нужное руководство по устранению неполадок в оглавлении книги Jupyter.
1. Записные книжки оптимизированы, поэтому нужно просто выбрать **Запустить ячейки**. Это действие будет выполнять каждую ячейку в записной книжке по отдельности, пока записная книжка не завершится.
1. При обнаружении ошибки книга Jupyter предложит записную книжку для ее устранения. Выполните рекомендуемые действия и снова запустите записную книжку.

## <a name="next-steps"></a>Дальнейшие действия
Дополнительные сведения о записных книжках в Azure Data Studio см. в статье [Использование записных книжек в SQL Server](notebooks-guidance.md).
