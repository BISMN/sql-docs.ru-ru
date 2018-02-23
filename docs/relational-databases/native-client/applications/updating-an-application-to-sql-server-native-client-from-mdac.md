---
title: "Обновление приложения для собственного клиента SQL Server с компонентами MDAC | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|applications
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- SQLNCLI, vs. MDAC
- SQL Server Native Client, vs. MDAC
- data access [SQL Server Native Client], vs. MDAC
- SQL Server Native Client, updating applications
ms.assetid: 2860efdd-c59a-4deb-8a0e-5124a8f4e6dd
caps.latest.revision: "81"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72bd7a56555da46acacf9431fc82fe006f55cbb6
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="updating-an-application-to-sql-server-native-client-from-mdac"></a>Обновление приложения с переходом от компонентов MDAC к собственному клиенту SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Между собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и компонентами доступа к данным MDAC существует несколько различий; начиная с Windows Vista, компоненты доступа к данным стали называться компонентами доступа к данным Windows, или Windows DAC. Хотя обе программы реализуют собственный доступ к базам данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует новые функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] особым образом, обеспечивая в то же время обратную совместимость с ранними версиями.  
  
 Приведенные в этом разделе сведения помогут вам обновить приложения компонентов MDAC (или выделенное административное соединение Windows) до текущей версии собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], который входит в состав [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Сведения об обновлении приложений до текущей версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, который входит в состав [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], в разделе [обновление приложения от собственного клиента SQL Server 2005](../../../relational-databases/native-client/applications/updating-an-application-from-sql-server-2005-native-client.md).  
  
 Кроме того, в компоненты MDAC входят компоненты для использования OLE DB, ODBC и объектов ADO, а собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] реализует только интерфейсы OLE DB и ODBC (хотя объекты ADO могут использовать функции собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и компоненты MDAC различаются также в следующих областях.  
  
-   Пользователи, использующие объекты ADO для доступа к поставщику собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], могут иметь в своем распоряжении меньше функций фильтрации, чем при доступе к поставщику SQL OLE DB.  
  
-   Если в приложении ADO используется собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и предпринимается попытка обновить вычисляемый столбец, то появляется сообщение об ошибке. При использовании компонентов MDAC обновление было бы принято, но пропущено.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] является одним автономным файлом DLL. Количество интерфейсов с открытым доступом сведено к минимуму, чтобы упростить распространение, а также повысить уровень безопасности.  
  
-   Поддерживаются только интерфейсы OLE DB и ODBC.  
  
-   Поставщик OLE DB и драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имеют имена, отличные от тех, которые используются в компонентах MDAC.  
  
-   Доступные для пользователя функции, предоставляемые компонентами MDAC, можно использовать при работе с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. К ним помимо прочего относится создание пулов соединений, поддержка ADO и поддержка клиентских курсоров. При использовании любой из этих функций собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] обеспечивает только связь с базой данных. Компоненты MDAC предоставляют такие функции, как трассировка, элементы управления в интерфейсе управления и счетчики производительности.  
  
-   Приложения могут использовать основные службы OLE DB в сочетании с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], однако при использовании ядра курсора OLE DB в них должен быть установлен параметр совместимости типов данных во избежание потенциальных проблем, которые могут возникнуть в связи с тем, что в ядре курсора отсутствуют сведения о новых типах данных [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает доступ к базам данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предыдущих версий.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не содержит средств интеграции с XML. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client поддерживает SELECT... БОЛЕЕ XML, но не поддерживает другие функциональные возможности XML. Тем не менее [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client поддерживает **xml** появился тип данных в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает настройку сетевых библиотек на стороне клиента с использованием только атрибутов строки соединения. Если требуется провести более сложную настройку сетевых библиотек, необходимо использовать диспетчер конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] несовместим с odbcbcp.dll. Приложения, которые используют и ODBC и **bcp** API-интерфейсы необходимо перестроить, чтобы связать с файлом sqlncli11.lib, чтобы использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не поддерживается из поставщика Microsoft OLE DB для ODBC (MSDASQL). При использовании драйвера MDAC SQLODBC вместе с MSDASQL или драйвера MDAC SQLODBC вместе с ADO используйте OLE DB в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Подключения MDAC поддерживает логическое значение (**true**) для **Trusted_Connection** ключевое слово. Объект [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственным клиентом строка подключения должна содержать **Да** или **не**.  
  
-   Незначительные изменения внесены в предупреждения и ошибки. Теперь в передаваемых собственному клиенту [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предупреждениях и ошибках, которые возвращаются сервером, сохраняется такая же степень серьезности. Следует тщательно протестировать приложение, если его работа зависит от перехвата определенных предупреждений и ошибок.  
  
-   Проверка ошибок в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] строже, чем в компонентах MDAC, а это означает, что некоторые приложения, которые не полностью соответствуют спецификациям ODBC и OLE DB, могут работать по-разному. Например, в поставщике SQLOLEDB не предусмотрено принудительное применение правила, согласно которому имена результирующих параметров должны начинаться с символа @, а в поставщике OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] такое правило соблюдается.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и компоненты MDAC по-разному реагируют на разрыв соединения. Например, компоненты MDAC возвращают кэшированные значения свойств разорванного соединения, тогда как собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сообщает вызывающему приложению об ошибке.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не формирует события Visual Studio Analyzer, вместо них он формирует события трассировки Windows.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] невозможно использовать с системным монитором. Системный монитор — это средство Windows, которое можно использовать только для файлов DSN, которые используют драйвер MDAC SQLODBC, входящий в Windows.  
  
-   Если собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] подключен к [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий, то возврат ошибки сервера 16947 осуществляется в виде SQL_ERROR. Эта ошибка возникает, если при выполнении позиционированного обновления или удаления не удается обновить или удалить строку. При использовании компонентов MDAC для соединения с любой версией [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ошибка сервера 16947 возвращается в виде предупреждения (SQL_SUCCESS_WITH_INFO).  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Реализует собственный клиент **IDBDataSourceAdmin** интерфейс, который имеет необязательный интерфейс OLE DB, который не был ранее реализованных, но только **CreateDataSource** метод этом необязательных интерфейс реализуется. [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
-   Поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращает синонимы в наборах строк схемы TABLES и TABLE_INFO, при этом параметру TABLE_TYPE присваивается значение SYNONYM.  
  
-   Возвращаемые значения типа данных **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **xml**, **определяемого пользователем типа**, или других типов больших объектов не могут быть возвращены клиенту с версиями более ранней, чем [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Если эти типы должны служить в качестве возвращаемых значений, необходимо использовать собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Компоненты MDAC позволяют выполнять следующие инструкции при запуске ручных или неявных транзакций, а собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] — нет. Они должны выполняться в режиме автоматической фиксации.  
  
    -   Все полнотекстовые операции (операции DDL с индексом и каталогом)  
  
    -   Все операции с базой данных (создание базы данных, изменение базы данных, удаление базы данных)  
  
    -   Повторная настройка  
  
    -   Shutdown  
  
    -   Удаление  
  
    -   Резервное копирование  
  
-   При подключении приложений MDAC к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типы данных, представленные в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], будут отображаться как типы данных, совместимые с [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], как показано в следующей таблице.  
  
    |Тип SQL Server 2005|Тип SQL Server 2000|  
    |--------------------------|--------------------------|  
    |**varchar(max)**|**text**|  
    |**nvarchar(max)**|**ntext**|  
    |**varbinary(max)**|**image**|  
    |**определяемый пользователем тип**|**varbinary**|  
    |**xml**|**ntext**|  
  
     Это сопоставление типов затрагивает значения, возвращаемые для метаданных столбцов. Например **текст** столбец имеет максимальный размер 2 147 483 647, но [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC для собственного клиента сообщает максимальный размер **varchar(max)** столбцы как SQL_SS_LENGTH_UNLIMITED и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]OLE DB для собственного клиента сообщает максимальный размер **varchar(max)** столбцы как 2 147 483 647 или -1, в зависимости от платформы.  
  
-   В собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в целях обеспечения обратной совместимости допускается неоднозначность в строках соединений (например, некоторые ключевые слова могут быть указаны несколько раз, а также может допускаться использование конфликтующих ключевых слов; при этом разрешение конфликтов происходит с учетом позиции или приоритета). В следующих версиях собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] неоднозначность в строках соединения может стать недопустимой. При изменении приложения для работы с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо предусмотреть устранение любых зависимостей от неоднозначности строки соединения.  
  
-   При запуске транзакций с помощью вызова ODBC или OLE DB собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и компоненты MDAC ведут себя по-разному; при работе с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] транзакции запускаются немедленно, а при использовании компонентов MDAC запуск транзакций происходит только после первого доступа к базе данных. Это может повлиять на поведение хранимых процедур и пакетов, так как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] требует@TRANCOUNT должны совпадать после пакета или хранимой процедуры завершения выполнения, в котором он был при запуске пакета или хранимой процедуры.  
  
-   С [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ITransactionLocal::BeginTransaction вызывает немедленный запуск транзакции. При использовании компонентов MDAC запуск транзакции задерживается до выполнения приложением инструкции, которой требуется транзакция в неявном режиме. Дополнительные сведения см. в разделе [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41; ](../../../t-sql/statements/set-implicit-transactions-transact-sql.md).  
  
-   Ошибки могут возникнуть при использовании [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента с System.Data.Odbc для доступа к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на сервере, в котором используются новые, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-определенные типы данных или функций. System.Data.Odbc предоставляет обычную реализацию ODBC и впоследствии не предоставляет особые функциональные возможности поставщика и расширения. (Драйвер собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] обновлен для обеспечения поддержки новейших функций [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].) Чтобы обойти эту проблему, можно либо вернуться к компонентам MDAC, либо перенести System.Data.SqlClient.  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и MDAC поддерживают уровень изоляции транзакций read committed при использовании управления версиями строк, однако изоляцию транзакций моментальных снимков поддерживает только собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. (С точки зрения программирования уровень изоляции транзакций READ COMMITTED с управлением версиями строк представляет собой то же, что и транзакция READ COMMITTED.)  
  
## <a name="see-also"></a>См. также  
 [Построение приложений с использованием собственного клиента SQL Server](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  