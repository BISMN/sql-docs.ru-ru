---
title: catalog.execution_data_statistics | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 6f51407e-0e4e-4b44-af33-db14c9d40ded
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 97d78f4a96a87b6ffe373335167b796ea5a2de3d
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71296590"
---
# <a name="catalogexecution_data_statistics"></a>catalog.execution_data_statistics 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Это представление отображает строку каждый раз, когда компонент потока данных передает данные в компонент, находящийся ниже в иерархии, для выполнения данного пакета. Данные в этом представлении могут быть использованы для расчета пропускной способности данных для компонента.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|data_stats_id|**bigint**|Уникальный идентификатор данных.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра исполнения.|  
|package_name|**nvarchar(260)**|Имя первого пакета, запущенного во время выполнения.|  
|task_name|**nvarchar(4000)**|Имя задачи потока данных.|  
|dataflow_path_id_string|**nvarchar(4000)**|Строка идентификации пути потока данных.|  
|dataflow_path_name|**nvarchar(4000)**|Имя пути потока данных.|  
|source_component_name|**nvarchar(4000)**|Имя компонента потока данных, который отправил данные.|  
|destination_component_name|**nvarchar(4000)**|Имя компонента потока данных, который получил данные.|  
|rows_sent|**bigint**|Число строк, отправленных из компонента источника.|  
|created_time|**datatimeoffset(7)**|Время, когда были получены значения.|  
|execution_path|**nvarchar(max)**|Путь выполнения компонента.|  
  
## <a name="remarks"></a>Remarks  
  
-   Если существует несколько выходов из компонента, добавляется строка для каждого выхода.  
  
-   По умолчанию, когда начинается выполнение, сведения о количестве переданных строк не регистрируются.  
  
-   Для просмотра этих данных для указанного выполнения пакета установите уровень ведения журнала **Подробно**. Дополнительные сведения см. в разделе [Включение ведения журналов при выполнении пакета на сервере служб SSIS](../../integration-services/performance/integration-services-ssis-logging.md#server_logging).  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
