---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 372ec1bbee84b90a9a30ec768fd7a35e3f6112d5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67995784"
---
# <a name="localdberrorinsufficientbuffer"></a>LOCALDB_ERROR_INSUFFICIENT_BUFFER
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|276|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Буфер, переданный методу API экземпляра локальной базы данных, имеет недостаточный размер.|  
  
## <a name="explanation"></a>Объяснение  
 Размер входного буфера является недостаточным, а усечение не было запрошено.  
  
## <a name="user-action"></a>Действие пользователя  
 Предоставьте буфер указанного размера.  
  
  
