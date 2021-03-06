---
title: IBCPSession (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 142f6ac339e437877c485588333fabb04e0bd66b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63241352"
---
# <a name="ibcpsession-ole-db"></a>Интерфейс IBCPSession (OLE DB)
  Интерфейс **IBCPSession** предоставляет поддержку операций массового копирования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на основе файлов. Интерфейс **IBCPSession** представлен в поставщике OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под тем же уровнем, что и объекты Session. В поставщике OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекты источника данных являются фабриками объектов Session, и операции массового копирования указываются в свойстве соединения SSPROP_ENABLEBULKCOPY. Кроме того, свойство SSPROP_ENABLEFASTLOAD должно быть установлено в значение TRUE.  
  
 Вызов метода **IDBCreateSession::CreateSession** приведет к созданию объекта **BulkCopySession** . Все методы массового копирования, основанные на файлах, доступные через объект **IBCPSession** , можно вызывать с помощью этих объектов **IBCPSession** интерфейса **IBCPSession** .  
  
> [!NOTE]  
>  Поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает операции массового копирования в памяти через интерфейс [IRowsetFastLoad](irowsetfastload-ole-db.md) .  
  
 Дополнительные сведения об использовании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента для операций массового копирования, см. в разделе [выполнение операций массового копирования](../native-client/features/performing-bulk-copy-operations.md).  
  
 Пример, демонстрирующий использование **IBCPSession** интерфейсом, см. в разделе [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Метод|Описание|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md)|Создает привязку между переменными программы и столбцами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[IBCPSession::BCPColumns &#40;OLE DB&#41;](ibcpsession-bcpcolumns-ole-db.md)|Задает количество полей для привязки к столбцам в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[IBCPSession::BCPControl &#40;OLE DB&#41;](ibcpsession-bcpcontrol-ole-db.md)|Устанавливает параметры для операции массового копирования.|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)|Фиксирует оставшиеся строки для отправки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IBCPSession::BCPExec &#40;OLE DB&#41;](ibcpsession-bcpexec-ole-db.md)|Выполняет операцию массового копирования.|  
|[IBCPSession::BCPInit &#40;OLE DB&#41;](ibcpsession-bcpinit-ole-db.md)|Инициализирует структуру массового копирования, выполняет проверку ошибок, проверяет правильность имен файла данных и файла форматирования, а затем открывает эти файлы.|  
|[IBCPSession::BCPReadFmt &#40;OLE DB&#41;](ibcpsession-bcpreadfmt-ole-db.md)|Считывает сведения о формате для каждого столбца из файла форматирования.|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](ibcpsession-bcpwritefmt-ole-db.md)|Записывает в файл форматирования сведения о формате каждого из столбцов.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
