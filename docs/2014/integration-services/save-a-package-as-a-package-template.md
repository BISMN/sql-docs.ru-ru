---
title: Сохранение пакета в качестве шаблона пакета | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- reusing packages
- templates [Integration Services]
ms.assetid: efe66cec-3933-4f6e-8d35-fe3d300de66c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 76349c0ca91f24a6d8d7942a89eb9683a91b573d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66056342"
---
# <a name="save-a-package-as-a-package-template"></a>Сохранение пакета в качестве шаблона пакета
  В этом разделе описано, как обозначить и использовать пользовательские пакеты в виде шаблонов при создании новых пакетов служб Integration Services в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. По умолчанию в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] используется шаблон пакета, который создает пустой пакет при добавлении нового пакета в проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Этот шаблон по умолчанию заменить нельзя, однако можно добавить новые шаблоны.  
  
 Для использования в роли шаблонов можно назначить несколько пакетов. Прежде чем сделать из пользовательского пакета шаблон, необходимо создать сам пакет.  
  
 При создании пакета с помощью пользовательских пакетов в виде шаблонов новые пакеты имеют те же имя и код GUID, что и шаблон. Чтобы различать пакеты, необходимо обновить значение свойства `Name` и создать новый код GUID для свойства `ID`. Дополнительные сведения см. в разделах [Создание пакетов в SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) и [Установка свойства пакета](set-package-properties.md).  
  
### <a name="to-designate-a-custom-package-as-a-package-template"></a>Обозначение пользовательского пакета как шаблона пакета  
  
1.  Найдите в файловой системе пакет, который нужно использовать в роли шаблона.  
  
2.  Скопируйте пакет в папку DataTransformationItems. По умолчанию эта папка находится в каталоге «C:\Program Files\Microsoft Visual Studio 9,0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject».  
  
3.  Повторите шаги 1 и 2 для каждого пакета, который нужно использовать в качестве шаблона.  
  
### <a name="to-use-a-custom-package-as-a-package-template"></a>Чтобы использовать пользовательский пакет как шаблон пакета  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , в котором необходимо создать пакет.  
  
2.  В обозревателе решений щелкните проект правой кнопкой мыши, укажите **Добавить** и выберите **Новый элемент**.  
  
3.  В диалоговом окне **Добавление нового элемента — \<имя проекта>** щелкните пакет, который нужно использовать в качестве шаблона.  
  
     Список шаблонов включает шаблон пакетов по умолчанию с именем «Новый пакет служб SSIS». Значок пакета определяет шаблоны, которые можно использовать в качестве шаблонов пакетов.  
  
4.  Нажмите кнопку **Добавить**.  
  
## <a name="see-also"></a>См. также  
 [Создание пакетов в SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)   
 [Пакеты служб Integration Services (SSIS)](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
