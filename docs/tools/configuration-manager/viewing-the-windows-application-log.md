---
title: Просмотр журнала приложений Windows | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- application logs [SQL Server]
- Windows application logs [SQL Server]
- viewing Windows application logs
- errors [SQL Server], logs
- system logs [SQL Server]
- security logs [SQL Server]
- displaying Windows application logs
- logs [SQL Server], Windows application logs
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 7c6d652545fcdc44ea46fbc417b1f0de7956cd83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106061"
---
# <a name="viewing-the-windows-application-log"></a>Просмотр журнала приложений Windows
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Если настройками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусмотрено использование журнала приложений Microsoft Windows, каждый сеанс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает новые события в этот журнал. В отличие от журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , новый журнал приложений не создается заново каждый раз при запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Просмотр и управление журналом приложений Windows осуществляется с помощью средства просмотра событий Windows или средства просмотра журналов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 С помощью средства просмотра событий можно просмотреть три журнала.  
  
|Тип журнала Windows|Описание|  
|----------------------|-----------------|  
|Системный журнал|Регистрирует события, записанные компонентами операционной системы Windows. Например, отказ загрузки драйвера или другого системного компонента при запуске записывается в системный журнал.|  
|Журнал безопасности|Регистрирует события безопасности, например неудавшиеся попытки входа в систему. Это помогает отследить изменения в системе безопасности и идентифицировать возможные «дыры». Например, попытка войти в систему регистрируется в журнале безопасности в зависимости от параметров аудита в диспетчере пользователей.<br /><br /> Только члены предопределенной роли сервера **sysadmin** могут просматривать журнал безопасности.|  
|Журнал приложений|Регистрирует события, записываемые приложениями. Например, приложение базы данных может записать в журнал приложений ошибку файла.|  
  
 Дополнительные сведения о средстве просмотра событий, управлении журналом приложений и данных, которые он представляет, см. в документации Windows.  
  
 **Просмотр журнала приложений Windows**  
  
 [Просмотр журнала приложений Windows (Windows)](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
  
