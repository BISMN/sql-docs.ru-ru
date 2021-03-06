---
title: Изменение сопоставления типов (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7078b4ed-c779-4bf3-8db8-f9dcb3edd50f
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: b3857d2acda8f5c8b16f416987651db2b6b991b7
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264235"
---
# <a name="edit-type-mapping-oracletosql"></a>Изменение сопоставления типов (OracleToSQL)
**Изменение сопоставления типа** диалоговое окно позволяет указать, как типы сопоставляются между объектами базы данных источника и назначения.  
  
Это диалоговое окно, в нескольких местах, можно открыть:  
  
-   При выборе базы данных-источника или объекта базы данных, **сопоставления типов** появится вкладка справа от элемента в обозревателе метаданных. Нажмите кнопку **добавить** нужно добавить новое сопоставление типа, или щелкните **изменить** Чтобы изменить существующее сопоставление типа.  
  
-   На **средства** меню, выберите **параметры проекта** или **параметры проекта по умолчанию**. В появившемся диалоговом окне выберите **сопоставления типов**. Нажмите кнопку **добавить** нужно добавить новое сопоставление типа, или щелкните **изменить** Чтобы изменить существующее сопоставление типа.  
  
Сопоставления типов, связанные с таблицами базы данных и проект сопоставления типов. Сопоставления конкретной базы данных переопределяют сопоставления проекта.  
  
## <a name="options"></a>Параметры  
**Тип источника**  
Выберите тип источника данных для сопоставления с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.  
  
Если тип данных имеет переменную длину, следующие поля будут отображаться на вкладке **типа источника**:  
  
**From**  
Укажите минимальную длину для данного сопоставления. Например, для **nchar** тип данных, можно ввести 10, чтобы указать, что это сопоставление для диапазона, начиная с **nchar(10) в формате**.  
  
**Задача**  
Укажите максимальную длину для данного сопоставления. Например, для **nchar** тип данных, можно ввести 20, чтобы указать, что это сопоставление для диапазона, заканчивая **nchar(20)** .  
  
**Тип целевого объекта**  
Выберите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных, с которым сопоставляется тип источника данных. Когда SSMA создает таблицу или хранимую процедуру в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], исходный тип данных изменится на этот тип данных.  
  
Если тип данных имеет переменную длину, поле будет отображаться на вкладке **целевой тип**:  
  
**Replace with**  
Укажите длину целевой объект для данного сопоставления. Например, для **nvarchar** тип данных, можно ввести 20, чтобы указать, что тип данных указанного источника должен быть сопоставлен **nvarchar(20)** .  
  
