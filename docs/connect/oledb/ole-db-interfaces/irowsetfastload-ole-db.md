---
title: IRowsetFastLoad (OLE DB) | Документация Майкрософт
description: Метод IRowsetFastLoad (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IRowsetFastLoad interface
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 2d21e270eb7e2d387201d66df0bb566c3924d53c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994395"
---
# <a name="irowsetfastload-ole-db"></a>Метод IRowsetFastLoad (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Интерфейс **IRowsetFastLoad** обеспечивает поддержку операций массового копирования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в памяти. Драйвер OLE DB для SQL Server потребители используют интерфейс для быстрого добавления данных в существующую [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицу.  
  
 Если присвоить SSPROP_ENABLEFASTLOAD значение VARIANT_TRUE для сеанса, то будет невозможно считывать данные из наборов строк, возвращаемых впоследствии в этом сеансе. Если присвоить SSPROP_ENABLEFASTLOAD значение VARIANT_TRUE, то все наборы строк, созданные для сеанса, будут иметь тип IRowsetFastLoad. Наборы строк IRowsetFastLoad не поддерживают функциональные возможности получения данных из набора строк, поэтому чтение данных из наборов строк невозможно.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Метод|Описание|  
|------------|-----------------|  
|[IRowsetFastLoad:: Commit &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md)|Обозначает конец пакета вставляемых строк и записывает эти строки в таблицу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|[IRowsetFastLoad:: InsertRow &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)|Добавляет строку в набор строк для массового копирования.|  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)   
 [Выполнение массового копирования данных с использованием интерфейса IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Отправка данных BLOB-объектов в SQL Server с помощью интерфейсов IROWSETFASTLOAD и ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
