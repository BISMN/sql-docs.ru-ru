---
title: Вопросы безопасности XML | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML security in ADO
ms.assetid: fadbd38e-6e7b-4b81-96ea-85169c664374
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fa0e9e2df1e8ba3f44b10e662d25e536ac7962f8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923358"
---
# <a name="xml-security-considerations"></a>Вопросы безопасности при работе с XML
Сохраните ADO и открытые методы в объекте набора записей не считаются безопасные операции для запуска в Internet Explorer. Таким образом Если эти методы используются в коде скрипта, который выполняется в приложение или элемент управления, который размещается в браузере, параметры безопасности браузера повлияет на его поведение.  
  
 Internet Explorer 5 обеспечивает ограничения безопасности для таких операций, по умолчанию в зоне Интернета. В этой конфигурации не может упростить любой доступ к локальной файловой системы на клиентском компьютере или получить доступ к источникам данных за пределами домена сервера, из которого было загружено страницы набора записей. В частности при выполнении в рамках узла обозревателя, набор записей можно сохранить обратно в файл только в том случае, если он находится на том же сервере, из которого было загружено страницы. Аналогичным образом можно открыть набор записей, загрузив его из файла только в том случае, если этот файл находится на том же сервере, из которого было загружено страницы.  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
