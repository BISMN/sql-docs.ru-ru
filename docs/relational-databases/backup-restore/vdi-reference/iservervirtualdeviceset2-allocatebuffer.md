---
title: IServerVirtualDeviceSet2::AllocateBuffer
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IServerVirtualDeviceSet2::AllocateBuffer.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8c28009fae8b52264b541ca3eb4281ab9abccf63
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847495"
---
# <a name="iservervirtualdeviceset2allocatebuffer-vdi"></a>IServerVirtualDeviceSet2::AllocateBuffer (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Функция **AllocateBuffer** получает буфер общей памяти из набора виртуальных устройств.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IServerVirtualDeviceSet2::AllocateBuffer (
   LPVOID*      ppBuffer,
   UINT32      dwSize,
   UINT32      dwAlignment
);
```

## <a name="parameters"></a>Параметры

*ppBuffer* — возвращает указатель на начало буфера.

*dwSize* — размер буфера в байтах. Не включает в себя префиксную зону, запрошенную клиентом. Такие зоны скрываются от сервера, и до возвращения адреса буфера будет доступно место.

*dwAlignment* — определяет границу выравнивания для буфера. Например, при значении 4096 буфер будет выровнен по границе в 4096 байт. Это означает, что младшие 12 бит в возвращенном адресе будут установлены в нулевое значение. Значение этого параметра должно быть степенью двойки.

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Буфер возвращается. |
| VD_E_MEMORY | Не хватает памяти. |
| VD_E_INVALID | Был указан недопустимый параметр. |

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).