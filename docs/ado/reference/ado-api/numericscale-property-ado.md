---
title: Свойство NumericScale (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 38d283e8fedb90ed5a99143090bc6a077efa8512
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932106"
---
# <a name="numericscale-property-ado"></a>Свойство NumericScale (ADO)
Указывает масштаб числовых значений в [параметр](../../../ado/reference/ado-api/parameter-object.md) или [поле](../../../ado/reference/ado-api/field-object.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **байтов** значение, указывающее число десятичных разрядов для числового значения, которые будут разрешены.  
  
## <a name="remarks"></a>Примечания  
 Используйте **NumericScale** свойства, чтобы определить, сколько разрядов справа от десятичного разделителя будет использоваться для представления значений для числового **параметр** или **поле** объекта.  
  
 Для **параметр** объектов, **NumericScale** свойство доступно для чтения/записи.  
  
 Для **поле**объекта, **NumericScale** обычно предназначены только для чтения. Тем не менее, для новых **поле** объекты, добавленные [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md), **NumericScale** доступно для чтения и записи только после того, как [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство для **поле** была определена и успешно добавил новый поставщик данных **поле** путем вызова [ Обновление](../../../ado/reference/ado-api/update-method.md) метод [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Field](../../../ado/reference/ado-api/field-object.md)|  
  
## <a name="see-also"></a>См. также  
 [Свойств NumericScale и Precision (Visual Basic)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [Свойств NumericScale и Precision (Visual C++)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Свойство Precision (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)
