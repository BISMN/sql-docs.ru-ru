---
title: 'Задача 5: Экспорт результатов в файл Excel очистки | Документация Майкрософт'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3cc3e51ee8b07ad017e6bf33150ec83e30ec4ff8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155535"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a>Задача 5. Экспорт результатов очистки в файл Excel.
  В этой задаче вы экспортируете результаты операции очистки в файл Excel. См. в разделе [этап экспорта](http://msdn.microsoft.com/library/hh213061.aspx#Export) Дополнительные сведения.  
  
1.  В области справа выберите **Excel** для **конечный тип**.  
  
2.  Нажмите кнопку **Обзор**, укажите имя выходного файла как **Cleansed Supplier List.xls**, а затем нажмите кнопку **откройте**.  
  
3.  Выберите **только данные** для **вывода** формат, чтобы экспортировать только очищенные данные. Во втором случае **данным и очистке**, позволяет экспортировать сведения об очистке вместе с очищенными данными. **Стандартный формат** позволяет применить все форматы вывода, заданные в домене, к значениям этого домена. В этом учебнике формат вывода не был задан ни для одного домена.  
  
     ![Страница очистки экспорта результатов](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "очистки экспорта страница «результаты»")  
  
4.  Нажмите кнопку **Экспорт** для экспорта данных. Не нажимайте кнопку **Готово** еще.  
  
5.  Нажмите кнопку **закрыть** на **Экспорт** диалоговое окно.  
  
6.  Нажмите кнопку **Готово** , чтобы завершить работу. Если вы забыли экспортировать результаты перед нажатием кнопки **Готово**, нажмите кнопку **открыть проект качества данных** в главной странице **клиента DQS**выберите **поставщика очистки Список** из списка проектов, и нажмите кнопку **Далее** в нижней части экрана, чтобы перейти к **Экспорт** этапа процесса очистки. Вы также можете **управление и просмотр результатов** , щелкнув **обратно** кнопки.  
  
7.  Откройте **Cleansed Supplier List.xls** и выполните следующие действия:  
  
    1.  Убедитесь, что адреса электронной почты, заканчивающиеся на adventure-work.com (без символа «s»), отсутствуют, выполнив поиск «adventure-work.com» на листе.  
  
    2.  Убедитесь, что не **США** значение в **страны** столбца.  
  
    3.  Поиск **Лос-Анджелес** и увидеть, что **состояние** присваивается **ЦС**.  
  
    4.  Убедитесь, что условия не **Co.**, **Corp.**, и **Inc.**.  
  
    5.  Удалить **проверка адреса** столбца из электронной таблицы и сохраните файл excel. Этот дополнительный столбец соответствует составному домену проверки адреса.  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 6. Импорт значений из проекта очистки списка поставщиков](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  