---
title: Настройки электронной почты — диспетчер конфигурации (собственный режим служб SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 808ad67429ee49d6b04533863112b4cbb3af2514
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108878"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a>Параметры электронной почты — диспетчер конфигурации (службы Reporting Services в собственном режиме)
  Эта страница позволяет задать параметры протокола SMTP, предназначенные для доставки отчетов по электронной почте с сервера отчетов. Модуль доставки электронной почты позволяет распространять отчеты и уведомления об их обработке через электронные подписки. Для модуля доставки электронной почты сервера отчетов требуется SMTP-сервер и адрес электронной почты для использования в поле «От».  
  
 Дополнительные параметры могут использоваться для дальнейшей настройки подписок, доставляемых электронной почтой, включая параметры, ограничивающие узлы почтового сервера и доступность модулей подготовки отчетов. Эти параметры нельзя задать в диспетчере конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Чтобы настроить дополнительные параметры, необходимо вручную изменить файл RSReportServer.config. Дополнительные сведения см. в разделе [Настройка сервера отчетов для доставки электронной почты &#40;диспетчер конфигурации служб SSRS&#41; ](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) и [файлы конфигурации служб Reporting Services](../report-server/reporting-services-configuration-files.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] книг Онлайн.  
  
 Чтобы открыть эту страницу, запустите диспетчер конфигурации служб Reporting Services и нажмите кнопку **параметры электронной почты** в области навигации. Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме.  
  
## <a name="options"></a>Параметры  
 **Адрес отправителя**  
 Указывает адрес электронной почты для поля «От» создаваемого сообщения. Необходимо указать учетную запись, имеющую разрешение на передачу почтовых сообщений из SMTP-сервера.  
  
 **Текущий метод доставки SMTP**  
 Указывает, что электронная почта сервера отчетов направляется через SMTP-сервер. Это единственный метод доставки, который можно указать в диспетчере конфигурации служб Reporting Services.  
  
 Альтернативным методом доставки является использование локального каталога считывания службы SMTP. Можно использовать этот метод доставки, если сетевая служба SMTP недоступна. Чтобы указать локальный каталог считывания службы SMTP, необходимо отредактировать файл конфигурации RSReportServer.config. При редактировании файла конфигурации для использования локального каталога считывания службы SMTP, диспетчер конфигурации служб Reporting Services задает **способ доставки** равным *пользовательских* указывает, что доставка метод указывается в файле конфигурации.  
  
 В файле конфигурации метод доставки задается параметром `SendUsing`. Дополнительные сведения об указании `SendUsing` настройки, см. в разделе [Настройка сервера отчетов для доставки электронной почты &#40;диспетчер конфигурации служб SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 **SMTP-сервера**  
 Укажите используемый SMTP-сервер или шлюз. Можно использовать локальный сервер или SMTP-сервер.  
  
## <a name="see-also"></a>См. также  
 [Настройка сервера отчетов для доставки электронной почты &#40;диспетчер конфигурации служб SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Разделы справки F1 диспетчера конфигурации служб Reporting Services &#40;собственный режим служб SSRS&#41;](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
