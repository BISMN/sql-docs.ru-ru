---
title: Свойство LineSeparator (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0343954f549f2cba4b535b8ab4ebafec5a842015
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918287"
---
# <a name="lineseparator-property-ado"></a>Свойство LineSeparator (ADO)
Указывает двоичный символ для использования в качестве разделителя строки в тексте [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объектов.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md) значение, указывающее знак разделителя строки, используемые в **Stream**. Значение по умолчанию — **adCRLF**.  
  
## <a name="remarks"></a>Примечания  
 **LineSeparator** используется для интерпретации строк при чтении содержимого текстового **Stream**. Строки могут быть пропущены с [SkipLine](../../../ado/reference/ado-api/skipline-method.md) метод.  
  
 **LineSeparator** используется только с текстом **Stream** объектов ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**). Это свойство учитывается, если **тип** — **adTypeBinary**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
