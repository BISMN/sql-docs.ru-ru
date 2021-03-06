---
title: Свойство Status (объект Recordset ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetStatus
- Recordset15::Status
helpviewer_keywords:
- Status property [ADO Recordset]
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1d91c3e92be7679ad6fbbb4a4ee7bd1bb6a48422
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916838"
---
# <a name="status-property-ado-recordset"></a>Свойство Status (объект Recordset ADO)
Указывает состояние текущей записи в отношении обновлений для пакетной службы или других массовых операций.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает сумму одного или нескольких [RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md) значения.  
  
## <a name="remarks"></a>Примечания  
 Используйте **состояние** свойство, чтобы увидеть, какие изменения, ожидающих выполнения для записей, изменена во время обновления пакета. Можно также использовать **состояние** свойство, чтобы просмотреть состояние записи с ошибкой во время массовых операций, например при вызове [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) методы [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, или задать [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство **набор записей** в массив закладок. Это свойство можно определить как не удалось определенной записи и разрешите его соответствующим образом.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Status (объект Recordset) (Visual Basic)](../../../ado/reference/ado-api/status-property-example-recordset-vb.md)   
 [Пример свойства Status (Visual C++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
