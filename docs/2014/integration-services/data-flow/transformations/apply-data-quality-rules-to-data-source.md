---
title: Применение правил качества данных к источнику данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c420a52528662cecec1bae8e0e1718152279bc0e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62770460"
---
# <a name="apply-data-quality-rules-to-data-source"></a>Применение правил качества данных к источнику данных
  Можно использовать службы Data Quality Services (DQS) для корректировки данных в потоке данных пакета, подключив преобразование DQS Cleansing к источнику данных. Дополнительные сведения о языке DQS см. в разделе [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md). Дополнительные сведения об этом преобразовании см. в разделе [DQS Cleansing Transformation](dqs-cleansing-transformation.md).  
  
 При обработке данных с помощью преобразования DQS Cleansing, создается проект служб DQS на сервере служб DQS. Для управления проектом используется клиент DQS. Дополнительные сведения см. в статье [Управление проектом служб DQS (открытие, разблокировка, переименование и удаление)](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md).  
  
### <a name="to-correct-data-in-the-data-flow"></a>Исправление данных в потоке данных  
  
1.  Создайте пакет.  
  
2.  Добавьте и настройте преобразование «Очистка DQS». Дополнительные сведения см. в разделе [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Соедините преобразование «Очистка DQS» с источником данных.  
  
  
