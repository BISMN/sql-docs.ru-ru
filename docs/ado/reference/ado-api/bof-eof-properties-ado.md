---
title: BOF, EOF свойства (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::BOF
- Recordset15::EOF
helpviewer_keywords:
- EOF property [ADO]
- BOF property [ADO]
ms.assetid: 36c31ab2-f3b6-4281-89b6-db7e04e38fd2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4932d3349c2d4e2948ddd28d9df3a30424064dcb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920387"
---
# <a name="bof-eof-properties-ado"></a>Свойства BOF и EOF (ADO)
-   **BOF** указывает, что текущая запись позиция находится перед первой записи в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
-   **EOF** указывает, что текущая запись позиция находится после последней записи в **записей** объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **BOF** и **EOF** свойства возвращают **логическое** значения.  
  
## <a name="remarks"></a>Примечания  
 Используйте **BOF** и **EOF** свойства, чтобы определить ли **записей** объект содержит записи или вы вышли за рамки возможностей **набора записей**  объекта при переходе от записи к записи.  
  
 **BOF** возвращает **True** (-1), если текущая позиция записей находится перед первой записью и **False** (0), если положение текущей записи в течение или после первого запись.  
  
 **EOF** возвращает **True** Если текущая позиция записей находится после последней записи и **False** если положения текущей записи не позднее последнюю запись.  
  
 Если параметр **BOF** или **EOF** свойство **True**, нет текущей записи.  
  
 При открытии **записей** нет записей, содержащий **BOF** и **EOF** свойствам присваивается **True** (см. в разделе [ RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) получения дополнительных сведений о состоянии этой **записей**). При открытии **записей** объект, который содержит по крайней мере одну запись, первая запись становится текущей записью и **BOF** и **EOF** свойства являются **False** .  
  
 При удалении последней записи оставшиеся **записей** объекта, **BOF** и **EOF** свойства могут оставаться **False** пока не будут Попытка изменить положение текущей записи.  
  
 В этой таблице показано, какие **переместить** методы разрешены с различными комбинациями **BOF** и **EOF** свойства.  
  
||Примеры MoveFirst,<br /><br /> MoveLast|MovePrevious,<br /><br /> Переместить < 0|Переместить 0|MoveNext,<br /><br /> Переместить > 0|  
|------|-----------------------------|---------------------------------|------------|-----------------------------|  
|**BOF**=**True**, **EOF**=**False**|Allowed|Ошибка|Ошибка|Allowed|  
|**BOF**=**False**, **EOF**=**True**|Allowed|Allowed|Ошибка|Ошибка|  
|Оба **True**|Ошибка|Ошибка|Ошибка|Ошибка|  
|Оба **False**|Allowed|Allowed|Allowed|Allowed|  
  
 Позволяя **переместить** не гарантирует, что метод будет успешно находить запись; это только означает, что вызов указанного **переместить** метод не приведет к ошибке.  
  
 В следующей таблице показано, что происходит с **BOF** и **EOF** параметры свойств при вызове различных **переместить** методы но не удается успешно найти запись.  
  
||BOF|EOF|  
|------|---------|---------|  
|**MoveFirst**, **MoveLast**|Значение **True**|Значение **True**|  
|**Переместить** 0|Без изменений|Без изменений|  
|**MovePrevious**, **переместить** < 0|Значение **True**|Без изменений|  
|**MoveNext**, **переместить** > 0|Без изменений|Значение **True**|  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [BOF, EOF и Bookmark Example свойства (Visual Basic)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF, EOF и Bookmark Example свойства (Visual C++)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
