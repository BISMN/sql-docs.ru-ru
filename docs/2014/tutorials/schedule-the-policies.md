---
title: Планирование политик | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8becd7ad30acf1ea2a63feae4760091aede70c06
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63033506"
---
# <a name="schedule-the-policies"></a>Планирование политик
  В этой задаче будет осуществлено планирование рекомендованных политик, импортированных в предыдущей задаче.  
  
### <a name="to-schedule-the-best-practices-policies"></a>Планирование рекомендованных политик  
  
1.  В обозревателе объектов разверните **управления**, разверните **Управление политикой**, разверните **политики**, щелкните правой кнопкой мыши рекомендованную политику и нажмите кнопку  **Свойства**.  
  
    > [!NOTE]  
    >  Кроме того, чтобы легко увидеть, какие политики связаны с рекомендациями и сортировать по рекомендованным категориям, разверните **управления**, разверните **Управление политикой**и нажмите кнопку **Политики**. В меню **Вид** выберите **Сведения об обозревателе объектов**. В **Подробности обозревателя объектов** панели щелкните **категории** заголовок, чтобы отсортировать политики по категориям. Рекомендованные политики имеют префикс **рекомендации корпорации Майкрософт**. Щелкните правой кнопкой мыши политику, который требуется настроить, а затем нажмите кнопку **свойства**.  
  
2.  На **Общие** странице **Открытие политики** отображаемое в диалоговом окне **режим оценки** выберите **по расписанию**.  
  
3.  Рядом с полем **расписание** выберите **выбрать** указать существующее расписание, или нажмите кнопку **New** для создания нового расписания.  
  
4.  После настройки расписания можно выбрать **включено** флажок в верхней части страницы, чтобы включить запланированную политику.  
  
5.  Повторяйте шаги от 1 до 4 для каждой политики, которую необходимо запланировать.  
  
    > [!NOTE]  
    >  Чтобы просмотреть результаты вычисления после запуска запланированной политики, откройте журнал политик на целевом экземпляре. Открыть журнал, щелкните правой кнопкой мыши **Управление политикой**, а затем нажмите кнопку **Просмотр журнала**.  
  
## <a name="summary"></a>Сводка  
 Тем самым была выполнена настройка запланированных политик на выполнение в единственном экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Если необходимо развернуть запланированные политики на нескольких экземплярах, перейдите к следующей задаче в этом учебнике.  
  
## <a name="next-steps"></a>Следующие шаги  
 [Развертывание запланированных политик на нескольких экземплярах](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  
