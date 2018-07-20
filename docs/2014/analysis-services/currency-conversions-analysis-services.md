---
title: Конвертация валюты (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple currency conversions
- monetary data [SQL Server]
- currency [Analysis Services]
- converting currency
- one-to-many currency conversions
- many-to-many currency conversions [Analysis Services]
- many-to-one currency conversions [Analysis Services]
ms.assetid: e03f491c-7df8-46a0-ade9-f2e55b68db85
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d2a439a5ef4d422b69b95d1c76dbeefa39b658a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289830"
---
# <a name="currency-conversions-analysis-services"></a>Преобразования валюты (службы Analysis Services)
  **[!INCLUDE[applies](../includes/applies-md.md)]**  Только многомерные  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] используют сочетания функций под управлением сценариев многомерных выражений для обеспечения поддержки преобразований валюты в кубах, поддерживающих несколько валют.  
  
## <a name="currency-conversion-terminology"></a>Терминология конвертации валют  
 В службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] используется следующая терминология для описания функционала конвертации валют.  
  
 Основная валюта  
 Валюта, по отношению к которой обменные курсы вводятся в группу меры курсов.  
  
 Местная валюта  
 Валюта, используемая для хранения транзакций, на которых основаны меры, подлежащие конвертации.  
  
 Местная валюта может быть идентифицирована следующим способом.  
  
-   Идентификатором валюты в таблице фактов, хранимым вместе с транзакцией, как это обычно бывает в банковских приложениях, в которых сама транзакция идентифицирует используемую для нее валюту.  
  
-   Идентификатором валюты, связанным с атрибутом в таблице измерения, который затем связывается с транзакцией в таблице фактов, как это обычно бывает в финансовых приложениях, где местоположение или другой идентификатор, например дочерняя компания, идентифицирует валюту, используемую для соответствующей транзакции.  
  
 Валюта отчета  
 Валюта, в которую транзакции конвертируются из основной валюты.  
  
> [!NOTE]  
>  Для конвертаций валют «многие к одному» основная валюта и валюта отчета одинаковы.  
  
 Измерение валюты  
 Измерение базы данных, определенное следующими настройками.  
  
-   `Type` Свойство измерения присвоено значение Currency.  
  
-   Свойству `Type` одного из атрибутов измерения присвоено значение CurrencyName.  
  
    > [!IMPORTANT]  
    >  Значения этого атрибута должны использоваться во всех столбцах, которые должны содержать идентификатор валюты.  
  
 Группа мер курсов  
 Группа мер в кубе, определенная следующими настройками.  
  
-   Существует связь обычного измерения между измерением валют и группой мер курсов.  
  
-   Существует связь обычного измерения между измерением времени и группой мер курсов.  
  
-   Дополнительно свойство `Type` установлено равным ExchangeRate. В то время как мастер бизнес-аналитики использует связи с измерениями валют и времени для идентификации вероятных групп мер курсов, установка `Type` свойство равным ExchangeRate позволяет клиентским приложениям легче идентифицировать меру курса группы.  
  
-   Одна или несколько мер, представляющих обменные курсы, содержащиеся в группе мер курсов.  
  
 Измерение валют отчета  
 Измерение, определенное мастером бизнес-аналитики после определения конвертации валюты, содержащее валюты отчета для этой конвертации валюты. Измерение валют отчета основано на именованном запросе, определенном в представлении источника данных, на котором основано измерение валют, связанное с группой мер курсов, из главной таблицы измерения валют. Это измерение определено со следующими настройками.  
  
-   `Type` Свойство измерения присвоено значение Currency.  
  
-   `Type` Свойство ключевого атрибута измерения присвоено значение CurrencyName.  
  
-   `Type` Свойство одного из атрибутов измерения присвоено значение CurrencyDestination, и столбец, связанный с атрибутом, содержит идентификаторы валют, представляющие валюты отчета для конвертации валют.  
  
## <a name="defining-currency-conversions"></a>Определение конвертаций валют  
 Можно использовать мастер бизнес-аналитики, чтобы определить функционал конвертации валют для куба, также можно вручную определить конвертации валют, используя скрипты многомерных выражений.  
  
### <a name="prerequisites"></a>предварительные требования  
 Перед тем как определять конвертацию валюты в кубе, используя мастер бизнес-аналитики, вначале необходимо определить хотя бы одно измерение валют, одно измерение времени и одну группу мер курсов. Из этих объектов мастер бизнес-аналитики может получать данные и метаданные, используемые для построения измерения валют отчета и скрипта многомерных выражений, необходимых для обеспечения функционала конвертации валют.  
  
### <a name="decisions"></a>Решения  
 Необходимо принять следующие решения перед тем, как мастер бизнес-аналитики сможет построить измерение валют отчета и скрипт многомерных выражений, необходимые для обеспечения функционала конвертации валют.  
  
-   Направление обменного курса  
  
-   Конвертируемые элементы  
  
-   Тип конвертации  
  
-   Местные валюты  
  
-   Валюты отчета.  
  
### <a name="exchange-rate-directions"></a>Направления обменных курсов  
 Группа мер курсов содержит меры, представляющие обменные курсы между местными валютами и основной валютой (обычно называемой корпоративной валютой). Сочетание направления обменного курса и типа конвертации определяет операцию, выполняемую по отношению к мерам, подлежащим конвертации скриптом многомерных выражений, сформированным с использованием мастера бизнес-аналитики. В следующей таблице содержатся описания операций, выполняемых в зависимости от направления обменного курса и типа конвертации, на основе параметров направления обменного курса и направлений конвертации, доступных в мастере бизнес-аналитики.  
  
|||||  
|-|-|-|-|  
|Направление обменного курса|**«многие к одному»**|**«Один ко многим»**|**«Многие ко многим»**|  
|**n в основной валюте к 1 в валюте образца**|Умножьте показатель, подлежащий конвертации, на показатель обменного курса для местной валюты, чтобы сконвертировать эту меру в основную валюту.|Разделите меру, подлежащую конвертации, на меру обменного курса для валюты отчета, чтобы сконвертировать эту меру в основную валюту.|Умножьте меру, подлежащую конвертации, на меру обменного курса для местной валюты, чтобы сконвертировать эту меру в основную валюту, затем разделите сконвертированную меру на меру обменного курса для валюты отчета, чтобы сконвертировать эту меру в валюту отчета.|  
|**n в валюте образца к 1 в основной валюте**|Разделите меру, подлежащую конвертации, на меру обменного курса для местной валюты, чтобы сконвертировать эту меру в основную валюту.|Умножьте меру, подлежащую конвертации, на меру обменного курса для валюты отчета, чтобы сконвертировать эту меру в основную валюту.|Разделите меру, подлежащую конвертации, на меру обменного курса для местной валюты, чтобы сконвертировать эту меру в основную валюту, затем умножьте сконвертированную меру на меру обменного курса для валюты отчета, чтобы сконвертировать эту меру в валюту отчета.|  
  
 Направление обменного курса выбирается на странице **Установка параметров конвертации валют** мастера бизнес-аналитики. Дополнительные сведения о настройке направлений конвертации валют см. в разделе [Установка параметров конвертации валюты (мастер бизнес-аналитики)](set-currency-conversion-options-business-intelligence-wizard.md).  
  
### <a name="converted-members"></a>Конвертируемые элементы  
 Можно использовать мастер бизнес-аналитики, чтобы указать, какие меры из группы мер курсов используются для конвертации значений для:  
  
-   Меры в других группах мер;  
  
-   элементов в иерархии атрибутов для атрибута счета в измерении базы данных;  
  
-   типов счетов, используемых элементами иерархии атрибутов для атрибута счета в измерении базы данных.  
  
 Мастер бизнес-аналитики использует эти данные в скрипте многомерных выражений, сформированном мастером, чтобы определить область вычислений конвертации валют. Дополнительные сведения об указании элементов для конвертации валют см. в разделе [Выбор элементов (мастер бизнес-аналитики)](select-members-business-intelligence-wizard.md).  
  
### <a name="conversion-types"></a>Типы конвертации  
 Мастер бизнес-аналитики поддерживает три различных типа конвертации валют.  
  
-   **«Один ко многим»**  
  
     Транзакции хранятся в таблице фактов в основной валюте, а затем конвертируются в одну или несколько валют отчета.  
  
     Например, в качестве основной валюты может быть установлен доллар США (USD), и в таблице фактов хранятся транзакции в долларах США. Этот тип конвертации конвертирует эти транзакции из основной валюты в указанные валюты отчета. В результате эти транзакции можно хранить в указанной основной валюте и просматривать либо в указанной основной валюте, либо в одной из валют отчета, указанных в измерении валют отчета, определенном для конвертации валют.  
  
-   **«многие к одному»**  
  
     Транзакции хранятся в таблице фактов в местных валютах, а затем конвертируются в основную валюту. Основная валюта служит в качестве единственной указанной валюты отчета в измерении валют отчета.  
  
     Например, в качестве основной валюты может быть установлен доллар США (USD), а в таблице фактов хранятся транзакции в евро (EUR), австралийских долларах (AUD) и мексиканских песо (MXN). Этот тип конвертации конвертирует эти транзакции из их указанных местных валют в основную валюту. В результате эти транзакции можно хранить в указанных местных валютах и просматривать в основной валюте, которая указана в измерении валют отчета, определенном для конвертации валют.  
  
-   **«Многие ко многим»**  
  
     Транзакции хранятся в таблице фактов в местных валютах. Функционал конвертации валют конвертирует подобные транзакции в основную валюту, а затем в одну или несколько валют отчета.  
  
     Например, в качестве основной валюты может быть установлен доллар США (USD), а в таблице фактов хранятся транзакции в евро (EUR), австралийских долларах (AUD) и мексиканских песо (MXN). Этот тип конвертации конвертирует эти транзакции из их указанных местных валют в основную валюту, а затем сконвертированные транзакции конвертируются вновь из основной валюты в указанные валюты отчета. В результате эти транзакции можно хранить в указанных местных валютах и просматривать либо в указанной основной валюте, либо в любой из валют отчета, указанных в измерении валют отчета, определенном для конвертации валют.  
  
 Указание типа конвертации позволяет мастеру бизнес-аналитики определить именованный запрос и структуру измерения валют отчета, а также структуру скрипта многомерных выражений, определенного для конвертации валют.  
  
### <a name="local-currencies"></a>Местные валюты  
 При выборе типа конвертации «многие ко многим» или «многие к одному» для конвертации валют необходимо указать способ идентификации местных валют, на основе которых скрипт многомерных выражений, сформированный мастером бизнес-аналитики, выполняет вычисления конвертации валют. Местная валюта для транзакции в таблице фактов может быть идентифицирована одним из двух способов.  
  
-   Группа мер содержит связь обычного измерения с измерением валют. Например, в образце [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] базы данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] группа мер «Интернет-продажи» имеет связь обычного измерения с измерением «Валюта». Таблица фактов для группы мер содержит внешний ключевой столбец, который связывает идентификаторы валют в таблице измерений и это измерение. В этом случае можно выбрать атрибут из измерения валют, на который ссылается группа мер, чтобы идентифицировать местную валюту для транзакций в таблице фактов для этой группы мер. Эта ситуация наиболее часто возникает в банковских приложениях, где сама транзакция определяет используемую в ней валюту.  
  
-   Группа мер содержит ссылочную связь измерений с измерением валют через другое измерение, которое непосредственно ссылается на измерение валют. Например, в образце [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] базы данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] группа мер «Финансовая отчетность» имеет связь обычного измерения с измерением «Валюта» через измерение «Организация». Таблица фактов для этой группы мер содержит внешний ключевой столбец, который ссылается на элементы в таблице измерения «Организация». Таблица измерения «Организация», в свою очередь, содержит внешний ключевой столбец, который ссылается на идентификаторы валют в таблице измерения «Валюта». Эта ситуация наиболее часто возникает в приложениях для финансовой отчетности, где местоположение дочерней компании, участвующей в транзакции, определяет валюту для этой транзакции. В этом случае можно выбрать атрибут, который ссылается на измерение валют из измерения для бизнес-сущности.  
  
### <a name="reporting-currencies"></a>Валюты отчета.  
 При выборе типа конвертации «многие ко многим» или «один ко многим» для конвертации валют необходимо указать валюты отчета, на основе которых скрипт многомерных выражений, сформированный мастером бизнес-аналитики, выполняет вычисления конвертации валют. Можно либо указать все элементы измерения валют, связанные с группой мер курсов, либо выбрать отдельные элементы из измерения.  
  
 Мастер бизнес-аналитики создает измерение валют отчета на основе именованного запроса, построенного из таблицы измерения валют с использованием выбранных валют отчета.  
  
> [!NOTE]  
>  При выборе типа конвертации «один ко многим» также создается измерение валют отчета. Это измерение содержит только один элемент, представляющий основную валюту, поскольку она также используется в качестве валюты отчета для конвертации «один ко многим».  
  
 Для каждой конвертации валют, определенной в кубе, определяется отдельное измерение валют отчета. Можно изменить имена измерений валют отчета после их создания, но при этом необходимо также обновить скрипт многомерных выражений, сформированный для этой конвертации валют, чтобы гарантировать использование правильного имени командой скрипта при ссылке на измерение валют отчета.  
  
## <a name="defining-multiple-currency-conversions"></a>Определение нескольких конвертаций валют  
 Используя мастер бизнес-аналитики, можно определить столько конвертаций валют, сколько необходимо для решения бизнес-аналитики. Можно либо перезаписывать существующую конвертацию валют, либо добавлять новую конвертацию валют в скрипт многомерных выражений для куба. Несколько конвертаций валют, определенных в одном кубе, обеспечивают гибкость в приложениях бизнес-аналитики, имеющих сложные требования к отчетности, например в приложениях для финансовой отчетности, поддерживающих несколько различных требований конвертации для международной отчетности.  
  
### <a name="identifying-currency-conversions"></a>Идентификация конвертаций валют  
 Мастер бизнес-аналитики идентифицирует каждую конвертацию валют по разбиению команд скрипта для конвертации валют следующими комментариями:  
  
 `//<Currency conversion>`  
  
 `...`  
  
 `[MDX statements for the currency conversion]`  
  
 `...`  
  
 `//</Currency conversion>`  
  
 При изменении или удалении этих комментариев мастер бизнес-аналитики не способен обнаружить конвертацию валют, поэтому эти комментарии изменять не следует.  
  
 Мастер также хранит метаданные в комментариях внутри этих комментариев, включая дату и время создания, пользователя и тип конвертации. Эти комментарии также не следует изменять, поскольку мастер бизнес-аналитики использует эти метаданные при отображении существующих конвертаций валют.  
  
 При необходимости можно изменять команды скрипта, содержащиеся в конвертации валют. Однако при перезаписи конвертации валют эти изменения будут утеряны.  
  
## <a name="see-also"></a>См. также  
 [Сценарии глобализации для многомерных служб Analysis Services](globalization-scenarios-for-analysis-services-multiidimensional.md)  
  
  