---
title: Метод DeleteRecord (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_DeleteRecord
- _Record::DeleteRecord
helpviewer_keywords:
- DeleteRecord method [ADO]
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 409c4e21395b7b903cf4ff03726fbd37a2a218d1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67919086"
---
# <a name="deleterecord-method-ado"></a>Метод DeleteRecord (ADO)
Удаляет сущности, представленной [записи](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательный параметр. Объект **строка** значение, содержащее URL-адрес идентифицирует сущность (например, файл или каталог) для удаления. Если *источника* опущен или указывает пустую строку, сущности, представленной текущим [записи](../../../ado/reference/ado-api/record-object-ado.md) удаляется. Если запись является записью коллекции ([RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md) из **adCollectionRecord**, например в каталоге) также будут удалены все дочерние элементы (например, вложенные папки).  
  
 *Async*  
 Необязательный параметр. Объект **логическое** значением, которое при **True**, указывает, что асинхронная операция удаления.  
  
## <a name="remarks"></a>Примечания  
 Операции для объекта, представленного данным **записи** может завершиться ошибкой после завершения этого метода. После вызова метода **DeleteRecord**, **записи** должен быть закрыт, поскольку поведение **записи** может стать непредсказуемым зависимости при обновлении поставщика **Записи** с источником данных.  
  
 Если этот **записи** были получены из [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md), а затем результаты этой операции не будут отражены немедленно, в **набор записей**. Обновить **записей** , закройте и повторно откройте его, или выполнив **записей** [Requery](../../../ado/reference/ado-api/requery-method.md) метод, [обновления](../../../ado/reference/ado-api/update-method.md) метод, или [Resync](../../../ado/reference/ado-api/resync-method.md) метод.  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Delete (коллекция Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Удаление метода (коллекция Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Метод Delete (объект Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
