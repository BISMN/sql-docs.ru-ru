---
title: rsServerConfigurationError — ошибка служб Reporting Services | Документы Майкрософт
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4291245b101799238412115ced8b114de5a551be
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65572133"
---
# <a name="rsserverconfigurationerror---reporting-services-error"></a>rsServerConfigurationError - Ошибка службы Reporting Services
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|rsServerConfiguration|  
|Источник события|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Компонент|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Текст сообщения|Сервер отчетов обнаружил ошибку конфигурации.|  
  
## <a name="explanation"></a>Объяснение  
 Это общая ошибка, возникающая в том случае, когда сервер отчетов или средство разработки отчетов имеет недопустимые параметры конфигурации. Эта ошибка обычно сопровождается вторым сообщением, в котором содержится действительная причина первой ошибки.  
  
 В следующем списке приведены основные возможные причины.  
  
-   Не удалось найти или считать файл RSReportServer.config или RSReportDesigner.config.  
  
-   XML-элементы в одном из файлов конфигурации отсутствуют или являются недопустимыми.  
  
-   Значения одного или нескольких XML-элементов отсутствуют или являются недопустимыми.  
  
-   Параметры реестра являются недопустимыми.  
  
## <a name="user-action"></a>Действие пользователя  
 Если эта ошибка возникла после того, как файл конфигурации был изменен вручную, удалите внесенные изменения, вернув прежние значения, либо, при наличии резервной копии, восстановите предыдущую версию файла.  
  
 Дополнительные сведения об ошибке, связанные с ошибкой **rsServerConfiguration**, см. в файлах журналов трассировки сервера отчетов, которые находятся в папке \Microsoft SQL Server\MSRS12.\<имя_экземпляра>\Reporting Services\LogFiles. Дополнительные сведения см. в разделе [Файлы и источники журналов служб Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
## <a name="internal-only"></a>Только для внутреннего использования  
  
## <a name="see-also"></a>См. также:  
 [Файлы конфигурации служб Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
