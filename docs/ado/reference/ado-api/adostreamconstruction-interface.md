---
title: Интерфейс ADOStreamConstruction | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction
helpviewer_keywords:
- ADOStreamConstruction interface [ADO]
ms.assetid: 92f5a939-3e1a-4b14-a9dd-90e6ce2dec74
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 70a6dd02722a34159b345a83b32897aa8c38d0ff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920785"
---
# <a name="adostreamconstruction-interface"></a>Интерфейс ADOStreamConstruction
**ADOStreamConstruction** интерфейс используется для создания ADO **Stream** объект из OLE DB **IStream** объекта в приложении C/C++.  
  
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|[Свойство Stream](../../../ado/reference/ado-api/stream-property.md)|Чтение и запись. Получает или задает поставщика OLE DB **Stream** объекта.|  
  
## <a name="methods"></a>Методы  
 Нет.  
  
## <a name="events"></a>События  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 Учитывая OLE DB **IStream** объекта (`pStream`), конструирование объекта ADO **Stream** объекта (`adoStr`) равносильно следующие три основные операции:  
  
1.  Создайте объект ADO **Stream** объекта:  
  
    ```  
    Stream20Ptr adoStr;  
    adoStr.CreateInstance(__uuidof(Stream));  
    ```  
  
2.  Запрос **IADOStreamConstruction** интерфейс **Stream** объекта:  
  
    ```  
    adoStreamConstructionPtr adoStrConstruct=NULL;  
    adoStr->QueryInterface(__uuidof(ADOStreamConstruction),  
                         (void**)&adoStrConstruct);  
    ```  
  
 Вызовите `IADOStreamConstruction::get_Stream` метод свойство для задания OLE DB **IStream** объекта ADO **Stream** объекта:  
  
```  
IUnknown *pUnk=NULL;  
pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
adoStrConstruct->put_Stream(pUnk);  
```  
  
 Полученный `adoStr` теперь представляет объект ADO **Stream** объект, созданный из OLE DB **IStream** объекта.  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2.0 или более поздней версии  
  
 **Библиотека:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)
