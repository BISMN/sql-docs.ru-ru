---
title: Свойства агента SQL Server (вкладка "Вход в систему") | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 01fc6329-5d6b-4186-9565-395f375477bb
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 7ce0cf176198a0b26c4812583c4ea89411fedab5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68024217"
---
# <a name="sql-server-agent-properties-log-on-tab"></a>Свойства агента SQL Server (вкладка «Вход в систему»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Используйте вкладку **Вход** диалогового окна **Свойства агента SQL Server** , чтобы указать учетную запись, используемую службой « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент», а также выполнить запуск или остановку службы. Изменение пароля учетной записи вступает в силу немедленно, без перезапуска службы.  
  
> [!NOTE]  
>  При изменении имени учетной записи, используемой службой в кластеризованном экземпляре, новая учетная запись должна быть членом группы домена, заданной во время установки изменяемой службы, или же текущий пользователь должен иметь разрешение на добавление членов в эту группу. Если нет разрешения на изменение состава группы, свяжитесь с администратором домена.  
  
## <a name="options"></a>Параметры  
 **Локальная системная учетная запись**  
 Укажите локальную системную учетную запись, для которой не требуется пароль. Однако локальная системная учетная запись может ограничить взаимодействие служб с другими серверами, это зависит от прав доступа, предоставленных этой учетной записи.  
  
 **Эта учетная запись**  
 Укажите локальную или доменную учетную запись, использующую аутентификацию Windows. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует использовать доменную учетную запись пользователя с минимальными правами. Дополнительные сведения о выборе учетной записи см. в разделе «Настройка учетных записей служб Windows» электронной документации.  
  
 **Имя учетной записи**  
 Укажите имя локальной или доменной учетной записи.  
  
 **Пароль**  
 Введите пароль для учетной записи.  
  
 **Подтверждение пароля**  
 Введите пароль для учетной записи еще раз.  
  
 **Запуск**  
 Запускает службу.  
  
 **Остановить**  
 Остановить службу.  
  
 **Приостановить**  
 Приостановить службу.  
  
 **Возобновить**  
 Возобновить приостановленную работу службы.  
  
  
