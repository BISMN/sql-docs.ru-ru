---
title: srv_willconvert (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_willconvert
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_willconvert
ms.assetid: 6f4db5fd-215a-461c-95e4-17697852733e
author: rothja
ms.author: jroth
ms.openlocfilehash: ec59e76cb90612a2a1dd8fd54f2ee71967a09606
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036021"
---
# <a name="srvwillconvert-extended-stored-procedure-api"></a>srv_willconvert (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Определяет, доступно ли конкретное преобразование типов данных в библиотеке ODS.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL srv_willconvert (  
int  
srctype  
,  
int  
desttype   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srctype*  
 Указывает тип преобразуемых данных. Этот параметр может иметь любой из типов данных API-интерфейса расширенных хранимых процедур.  
  
 *desttype*  
 Указывает тип данных, в который преобразуются исходные данные. Этот параметр может иметь любой из типов данных API-интерфейса расширенных хранимых процедур.  
  
## <a name="returns"></a>Возвращает  
 Значение TRUE, если преобразование типов данных поддерживается, значение FALSE, если преобразование типов данных не поддерживается.  
  
## <a name="remarks"></a>Remarks  
 Описание каждого типа данных см. в разделе [Типы данных (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md).  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://www.microsoft.com/en-us/msrc?rtc=1).  
  
## <a name="see-also"></a>См. также:  
 [srv_convert (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-convert-extended-stored-procedure-api.md)  
  
  
