---
title: IClientVirtualDevice::GetCommand
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IClientVirtualDevice::GetCommand.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a861377924b4bb3cc1c1d2a4b83eba660fbf99e0
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847595"
---
# <a name="iclientvirtualdevicegetcommand-vdi"></a>IClientVirtualDevice::GetCommand (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Функция **GetCommand** используется для получения следующей команды в очереди на устройстве. При запросе эта функция ожидает следующую команду.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IClientVirtualDevice::GetCommand (
   DWORD               dwTimeOut,
   VDC_Command**      const ppCmd
);
```

## <a name="parameters"></a>Параметры

*ppCmd* — при успешном возвращении команды параметр возвращает адрес выполняемой команды. Возвращенная память доступна только для чтения. После выполнения команды этот указатель передается в подпрограмму CompleteCommand. Дополнительные сведения о каждой команде см. в разделе "Команды".

*dwTimeOut* — время ожидания (в миллисекундах). Используйте INFINTE для бесконечного ожидания. Используйте 0, чтобы запросить команду. Если команда в данный момент недоступна, возвращается VD_E_TIMEOUT. Если наступает время ожидания, клиент принимает решение о следующем действии.

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Команда получена. |
| VD_E_CLOSE | Устройство было закрыто сервером. |
| VD_E_TIMEOUT | Доступных команд не было. Время ожидания истекло. |
| VD_E_ABORT | Клиент или сервер использовал SignalAbort для принудительного завершения работы. |

## <a name="remarks"></a>Remarks

Если возвращается значение VD_E_CLOSE, значит, SQL Server закрыл устройство. Это часть нормального завершения работы. После закрытия всех устройств клиент вызывает функцию IClientVirtualDeviceSet2::Close, чтобы закрыть набор виртуальных устройств.

Если эта подпрограмма должна блокироваться для ожидания команды, поток остается в состоянии ожидания оповещения.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).