---
title: Динамические курсоры | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86e51b7880004117e8efc96bd310c6de705d43a6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925509"
---
# <a name="dynamic-cursors"></a>Динамические курсоры
Динамические курсоры обнаруживают все изменения, сделанные в строках в результирующем наборе, независимо от того происходят изменения из внутри курсора или другими пользователями вне курсора. Все инструкции insert, update и инструкций delete, выполняемые пользователями, видимы посредством курсора. Динамический курсор может обнаружить любые изменения, внесенные в строки, порядок и значения в результирующем наборе после открытия курсора. Обновления, сделанные вне курсора, не будут видны, до момента фиксации (если уровень изоляции транзакций курсора не задано значение «незафиксированных»).  
  
 Например предположим, динамический курсор извлекает две строки и другое приложение и обновляет один из этих строк и удаляет другой. Если после этого динамический курсор снова извлекает эти две строки, он не найдет удаленную строку, а для обновленной строки отобразит новые значения.  
  
 Динамический курсор является хорошим выбором, если приложение должно определять все параллельные обновления, сделанные другими пользователями. Используйте **adOpenDynamic CursorTypeEnum** для указания, что вы хотите использовать динамический курсор в ADO.  
  
## <a name="see-also"></a>См. также  
 [Однопроходные курсоры](../../../ado/guide/data/forward-only-cursors.md)   
 [Статические курсоры](../../../ado/guide/data/static-cursors.md)   
 [Курсоры ключевого набора](../../../ado/guide/data/keyset-cursors.md)
