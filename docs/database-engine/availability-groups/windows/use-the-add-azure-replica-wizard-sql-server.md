---
title: Использование мастера добавления реплики Azure (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.addreplicawizard.azurereplica.f1
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed09ad0f6325ab2ed8ee1d89d7c36f19584a3475
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176202"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a>Использование мастера добавления реплики Azure (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Мастер добавления реплики Azure упрощает создание виртуальной машины Azure в гибридной среде и ее настройку в качестве вторичной реплики для новой или существующей группы доступности AlwaysOn.  
  

##  <a name="BeforeYouBegin"></a> Перед началом  
 Если вам еще не приходилось добавлять реплики доступности в группу доступности, см. подразделы "Экземпляры сервера" и "Группы доступности и реплики" в разделе [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
##  <a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо подключиться к экземпляру сервера, на котором размещена текущая первичная реплика.  
  
-   Необходима гибридная среда, где в локальной подсети установлено VPN-подключение типа "сеть — сеть" к Azure. Дополнительные сведения см. в разделе [Настройка виртуальной частной сети между площадками через портал управления](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create).  
  
-   Группа доступности должна содержать реплики доступности локально.  
  
-   Клиенты прослушивателя группы доступности должны быть подключены к Интернету, если им нужно поддерживать соединение с прослушивателем при выполнении отработки отказа группы доступности в реплику Azure.  
  
-   **Предварительные условия для использования полной начальной синхронизации данных** Необходимо указать сетевой ресурс, чтобы мастер мог создавать и получать доступ к резервным копиям. Для каждой первичной реплики учетная запись, используемая для запуска [!INCLUDE[ssDE](../../../includes/ssde-md.md)] , должна иметь разрешения в файловой системе на чтение и запись в общей сетевой папке. Для вторичных реплик учетная запись должна иметь разрешение на чтение в сетевой папке.  
  
     Если нет возможности воспользоваться мастером для выполнения полной первоначальной синхронизации данных, то базы данных-получатели нужно подготовить вручную. Это можно сделать до или после запуска мастера. Дополнительные сведения см. в статье [Ручная подготовка базы данных-получателя для присоединения к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
##  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
 Кроме того, требуется разрешение CONTROL ON ENDPOINT, если мастер добавления реплики в группу доступности должен иметь возможность управлять конечной точкой зеркального отображения базы данных.  
  
##  <a name="SSMSProcedure"></a> Работа с мастером добавления реплики Azure (SQL Server Management Studio)  
 Мастер добавления реплики Azure можно запустить на странице [Выбор реплик](../../../database-engine/availability-groups/windows/specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md). На эту страницу можно перейти двумя способами.  
  
-   [Использование мастера групп доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование мастера добавления реплики в группу доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 После того как был запущен мастер добавления реплики Azure, выполните следующие шаги.  
  
1.  Сначала загрузите сертификат управления для подписки Azure. Нажмите кнопку **Загрузить** , чтобы открыть страницу входа.  
  
2.  Войдите в Microsoft Azure, используя учетную запись Майкрософт или учетную запись вашей организации. Учетная запись Майкрософт или организации имеет формат адреса электронной почты, например "mailto:patc@contoso.com" patc@contoso.com. Дополнительные сведения об учетных данных Azure см. в разделах [Часто задаваемые вопросы об учетной записи Майкрософт для организаций](https://technet.microsoft.com/jj592903) и [Устранение проблем с входом при использовании учетной записи организации](https://support.microsoft.com/kb/2756852).  
  
3.  Затем подключитесь к подписке, нажав кнопку **Подключиться**. После подключения раскрывающиеся списки заполняются параметрами Azure, такими как **Виртуальная сеть** и **Подсеть виртуальной сети**.  
  
4.  Укажите параметры для виртуальной машины Azure, на которой будет размещаться новая вторичная реплика.  
  
     image  
     Имя образа SQL Server, которое будет использоваться для виртуальной машины Azure  
  
     Размер виртуальной машины  
     Размер виртуальной машины Azure  
  
     Имя виртуальной машины  
     DNS-имя виртуальной машины Azure  
  
     Имя пользователя виртуальной машины  
     Имя пользователя-администратора системы по умолчанию для виртуальной машины Azure  
  
     Пароль администратора виртуальной машины (и подтверждение пароля)  
     Пароль администратора системы по умолчанию для виртуальной машины Azure  
  
     Виртуальная сеть  
     Виртуальная сеть, в которой будет размещена виртуальная машина Azure  
  
     Подсеть виртуальной сети  
     Подсеть виртуальной сети, в которой будет размещена виртуальная машина Azure  
  
     Домен  
     Домен Active Directory (AD), к которому будет присоединена виртуальная машина Azure  
  
     Имя пользователя домена  
     Имя пользователя AD, используемое для присоединения виртуальной машины Azure к домену  
  
     Пароль  
     Пароль, используемый для присоединения виртуальной машины Azure к домену  
  
5.  Нажмите кнопку **ОК** , чтобы зафиксировать ваши параметры, и выйдите из мастера добавления реплики Azure.  
  
6.  Продолжайте выполнять остальные шаги конфигурации на странице [Выбор реплик](../../../database-engine/availability-groups/windows/specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) так же, как и для любых новых реплик.  
  
     По завершении работы с мастером группы доступности или с мастером добавления реплики в группу доступности процесс конфигурации выполняет все операции в Azure, необходимые для создания виртуальной машины, присоединения ее к домену AD, добавления в кластер Windows, включения высокого уровня доступности AlwaysOn и добавления новой реплики в группу доступности.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Добавление вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)   
 [Добавление вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
