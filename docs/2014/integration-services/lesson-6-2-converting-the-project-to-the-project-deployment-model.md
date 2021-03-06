---
title: Шаг 2. Преобразование проекта в модель развертывания проекта | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1ba6dcb7052fed3d209dd87f55789a99df24116c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62767356"
---
# <a name="step-2-converting-the-project-to-the-project-deployment-model"></a>Шаг 2. Преобразование проекта в модель развертывания проекта
  В этой задаче будет использоваться мастер преобразования проекта служб Integration Services для преобразования проекта в модель развертывания проекта.  
  
### <a name="converting-the-project-to-the-project-deployment-model"></a>Преобразование проекта в модель развертывания проекта  
  
1.  В меню Проект выберите пункт Преобразовать в модель развертывания пакета.  
  
2.  На странице "Общие сведения мастера преобразования проекта служб Integration Services" просмотрите действия, а затем нажмите кнопку "Далее".  
  
3.  На странице "Выбор пакетов" в списке пакетов снимите все флажки за исключением Lesson 6.dtsx, затем нажмите кнопку "Далее".  
  
4.  На странице "Задание свойств проекта" нажмите кнопку "Далее".  
  
5.  На странице "Задача обновления выполнения пакета" нажмите кнопку "Далее".  
  
6.  На странице "Выбор конфигураций" убедитесь, что в списке конфигураций выбран пакет Lesson 6.dtsx, а затем нажмите кнопку "Далее".  
  
7.  На странице "Параметры создания" убедитесь, что выбран пакет Lesson 6.dtsx, и область имеет значение "Пакет" в списке свойств конфигурации, а затем нажмите кнопку "Далее".  
  
8.  На странице "Параметры настройки" убедитесь, что значения для имени и значения те же имя и значение, указанные на занятии 5 для переменной и значения конфигурации, а затем нажмите кнопку "Далее".  
  
9. На странице "Просмотр" панели "Сводка" обратите внимание, что мастер использовал сведения из файла конфигурации для задания свойств для преобразования.  
  
10. Щелкните Преобразовать.  
  
     После завершения преобразования отображается сообщение, предупреждающее, что изменения не сохраняются до сохранения проекта в Visual Studio. В диалоговом окне предупреждения нажмите кнопку ОК.  
  
11. В мастере преобразования проекта служб Integration Services нажмите кнопку "Закрыть".  
  
12. В SQL Server Data Tools щелкните меню "Файл", а затем нажмите кнопку "Сохранить", чтобы сохранить преобразованный пакет.  
  
13. Перейдите на вкладку "Параметры" и убедитесь, что пакет теперь содержит параметр для VarFolderName и, что значение является тем же путем, который был определен для папки New Sample Data из файла конфигурации занятия 5.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Шаг 3. Тестирование пакета занятия 6](lesson-6-3-testing-the-lesson-6-package.md)  
  
  
