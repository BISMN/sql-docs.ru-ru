---
title: Динамические свойства набора записей в формате XML | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a058a2d0c5a808f29807744c6ba01f658bebc120
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924448"
---
# <a name="recordset-dynamic-properties-in-xml"></a>Динамические свойства набора записей в XML
Следующие свойства от поставщика набор записей (из обработчик курсора клиента), в настоящее время сохраняются в формате XML:  
  
-   Повторная синхронизация обновления  
  
-   уникальная таблица  
  
-   Уникальной схемы  
  
-   Уникальный каталог  
  
-   Команда синхронизации  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   Изменить имя  
  
-   AutoRecalc  
  
 Эти свойства сохраняются в раздел схемы как атрибуты определения элемента, сохранение набора записей. Эти атрибуты определяются в пространстве имен схемы набора строк и должен иметь префикс «rs:».  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
