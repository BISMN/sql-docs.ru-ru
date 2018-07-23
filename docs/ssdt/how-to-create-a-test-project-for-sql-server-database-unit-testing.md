---
title: Практическое руководство. Создание тестового проекта для модульного тестирования базы данных SQL Server | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b3e7ba8-b565-4689-af1a-34cc255b7c60
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dd81ffb8d1530478147147c7aecddd39a368cd9b
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094644"
---
# <a name="how-to-create-a-test-project-for-sql-server-database-unit-testing"></a>Практическое руководство. Создание проекта тестов для модульного тестирования базы данных SQL Server
Перед тем как приступить к написанию модульных тестов для проверки объектов базы данных, сначала следует создать проект тестов. Этот проект содержит модульные тесты SQL Server, но может содержать и другие типы тестов.  
  
Вы можете разместить в одном тестовом проекте все модульные тесты SQL Server для определенного проекта базы данных. Изучите следующие вопросы и ответьте на них, чтобы понять, нужно ли вам создавать дополнительные проекты тестов.  
  
|||  
|-|-|  
|**Вопрос**|**Решение**|  
|Нужны ли разным модульным тестам SQL Server разные подключения к базам данных для выполнения и проверки теста?|Если да, то вам потребуется несколько проектов тестов. Для выполнения теста можно указать только одно подключение к базе данных. Однако для проверки теста можно указать другое подключение к базе данных.|  
|Нужно ли развертывать разные проекты базы данных для разных модульных тестов?|Если да, то вам потребуется несколько проектов тестов. Проект тестов может развертывать только один проект базы данных.|  
  
Дополнительные сведения о каждом из этих вопросов см. в статье [Практическое руководство. Настройка запуска модульного теста SQL Server](../ssdt/how-to-configure-sql-server-unit-test-execution.md). Чтобы не создавать несколько тестовых проектов, можно создать собственную реализацию [DatabaseTestService](https://msdn.microsoft.com/en-us/library/microsoft.data.schema.unittesting.databasetestservice.aspx) Microsoft.Data.Schema.UnitTesting.DatabaseTestService.  
  
Есть три варианта добавления проекта теста к решению, которое содержит проект базы данных.  
  
-   Добавление проекта тестов в решение. Проект тестов содержит стандартный модульный тест, который можно удалить. Этот проект не содержит класс модульного теста SQL Server. Его необходимо добавить.  
  
-   Добавьте новый модульный тест SQL Server с помощью меню **Тест**. При добавлении модульного теста SQL Server Data Tools может также создать тестовый проект по выбору пользователя. Этот проект содержит класс модульного теста SQL Server. Тестовые классы модульных тестов SQL Server содержат один или несколько модульных тестов.  
  
-   Создайте модульный тест для хранимой процедуры, функции или триггера из проекта, открытого в обозревателе объектов SQL Server. При создании модульного теста SQL Server Data Tools может также создать тестовый проект по выбору пользователя. Этот проект содержит класс модульного теста SQL Server. Тестовые классы SQL Server содержат один или несколько модульных тестов.  
  
Каждый метод описан в последующих процедурах.  
  
### <a name="to-add-a-test-project-to-an-existing-solution"></a>Добавление проекта тестов к существующему решению  
  
1.  В меню **Файл** укажите пункт **Создать**, затем выберите пункт **Проект**.  
  
    Откроется диалоговое окно **Создание проекта** .  
  
2.  В области **Установленные шаблоны** разверните узел **SQL Server** и выберите **Проект базы данных SQL Server**.  
  
3.  В поле **Имя** введите имя проекта.  
  
### <a name="to-create-a-test-project-with-a-sql-server-unit-test-class"></a>Создание тестового проекта с классом модульного теста SQL Server  
  
-   Выполните процедуру, описанную в статье [Практическое руководство. Создание пустого модульного теста SQL Server](../ssdt/how-to-create-an-empty-sql-server-unit-test.md) или [Практическое руководство. Создание модульных тестов SQL Server для функций, триггеров и хранимых процедур](../ssdt/how-to-create-unit-tests-for-functions-triggers-stored-procedures.md).  
  
## <a name="see-also"></a>См. также:  
[Создание и определение модульных тестов SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
  