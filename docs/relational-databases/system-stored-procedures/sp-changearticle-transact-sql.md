---
title: sp_changearticle (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changearticle
- sp_changearticle_TSQL
helpviewer_keywords:
- sp_changearticle
ms.assetid: 24c33ca5-f03a-4417-a267-131ca5ba6bb5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8fe752b17af683f59078bd7c37eb702a9408a530
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771402"
---
# <a name="sp_changearticle-transact-sql"></a>sp_changearticle (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Изменяет свойства статьи в публикации транзакций или в публикации моментального снимка. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changearticle [ [@publication= ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, содержащей статью. Аргумент *publication* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @article = ] 'article'`Имя статьи, свойство которой необходимо изменить. Аргумент *article* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @property = ] 'property'`Свойство статьи, которое необходимо изменить. *свойство* имеет тип **nvarchar (100)** .  
  
`[ @value = ] 'value'`Новое значение свойства статьи. *значение* равно **nvarchar (255)** .  
  
 Эта таблица описывает свойства статей и значения этих свойств.  
  
|Свойство|Значения|Описание|  
|--------------|------------|-----------------|  
|**creation_script**||Путь и имя скрипта схемы статьи, используемого для создания целевых таблиц. Значение по умолчанию — NULL.|  
|**del_cmd**||Инструкция DELETE к выполнению; иначе формируется из журнала.|  
|**description**||Новая запись описания статьи.|  
|**dest_object**||Предоставляется для обратной совместимости. Используйте **dest_table**.|  
|**dest_table**||Новая целевая таблица.|  
|**destination_owner**||Имя владельца целевого объекта.|  
|**фильтр**||Новая хранимая процедура для фильтрации таблицы (горизонтальная фильтрация). Значение по умолчанию — NULL. Невозможно изменить для публикаций в одноранговой репликации.|  
|**fire_triggers_on_snapshot**|**true**|Реплицированные пользовательские триггеры срабатывают при применении исходного моментального снимка.<br /><br /> Примечание. Для репликации триггеров значение битовой маски *schema_option* должно включать значение **0x100**.|  
||**false**|Реплицированные пользовательские триггеры не срабатывают при применении исходного моментального снимка.|  
|**identity_range**||Управляет размером диапазонов идентификаторов, назначенных на подписчике. В случае одноранговой репликации не поддерживается.|  
|**ins_cmd**||Инструкция INSERT к выполнению; иначе формируется из журнала.|  
|**pre_creation_cmd**||Команда предсоздания, которая перед применением синхронизации может полностью или частично удалить данные из целевой таблицы или выполнить ее усечение.|  
||**None**|Не использует команду.|  
||**тени**|Удаляет целевую таблицу полностью.|  
||**delete**|Удаляет целевую таблицу.|  
||**truncate**|Усекает целевую таблицу.|  
|**pub_identity_range**||Управляет размером диапазонов идентификаторов, назначенных на подписчике. В случае одноранговой репликации не поддерживается.|  
|**schema_option**||Указывает битовую карту параметра формирования схемы для данной статьи. Аргумент *schema_option* имеет **двоичный формат (8)** . Дополнительные сведения см. в подразделе «Примечания» далее в этом разделе.|  
||**0x00**|Отключает выполнение сценариев агентом моментальных снимков.|  
||**0x01**|Формирует создание объекта (CREATE TABLE, CREATE PROCEDURE и т.п.).|  
||**0x02**|Создает хранимые процедуры, которые распространяют изменения в статье, если они заданы.|  
||**0x04**|Столбцы идентификаторов вносятся в сценарий с помощью свойства IDENTITY.|  
||**0x08**|Репликация столбцов **отметок времени** . Если не задано, то столбцы **отметок времени** реплицируются как **двоичные**.|  
||**0x10**|Создает соответствующий кластеризованный индекс.|  
||**0x20**|Преобразует определяемые пользователем типы данных (UDT) в базовые типы данных подписчика. Этот параметр не может использоваться, если на столбец UDT наложено ограничение CHECK или DEFAULT, если столбец UDT является частью первичного ключа или если вычисляемый столбец ссылается на столбец UDT. Не поддерживается для издателей Oracle.|  
||**0x40**|Создает соответствующие некластеризованные индексы.|  
||**0x80**|Включает объявленную ссылочную целостность по первичным ключам.|  
||**0x100**|Реплицирует пользовательские триггеры для статьи таблицы, если заданы.|  
||**0x200**|Реплицирует ограничения FOREIGN KEY. Если таблица, к которой происходит обращение, не является частью публикации, все ограничения FOREIGN KEY в опубликованной таблице не реплицируются.|  
||**0x400**|Реплицирует ограничения CHECK.|  
||**0x800**|Реплицирует значения по умолчанию.|  
||**0x1000**|Реплицирует параметры сортировки на уровне столбцов.|  
||**0x2000**|Реплицирует расширенные свойства, связанные с исходным объектом опубликованной статьи.|  
||**0x4000**|Реплицирует уникальные ключи для статьи таблицы, если они определены.|  
||**0x8000**|Реплицирует первичный ключ и уникальные ключи статьи таблиц в виде ограничений, используя инструкции ALTER TABLE.<br /><br /> Примечание. Этот параметр является устаревшим. Вместо этого используйте **0x80** и **0x4000** .|  
||**0x10000**|Реплицирует ограничения CHECK как NOT FOR REPLICATION, чтобы они не применялись при синхронизации.|  
||**0x20000**|Реплицирует ограничения FOREIGN KEY как NOT FOR REPLICATION, чтобы они не применялись при синхронизации.|  
||**0x40000**|Реплицирует файловые группы, связанные с секционированной таблицей или индексом.|  
||**0x80000**|Реплицирует схему секционирования для секционированной таблицы.|  
||**0x100000**|Реплицирует схему секционирования для секционированного индекса.|  
||**0x200000**|Реплицирует статистику таблицы.|  
||**0x400000**|Привязки по умолчанию|  
||**0x800000**|Привязки правил|  
||**0x1000000**|Полнотекстовый индекс|  
||**0x2000000**|Коллекции XML-схем, привязанные к **XML-** столбцам, не реплицируются.|  
||**0x4000000**|Реплицирует индексы по **XML-** столбцам.|  
||**0x8000000**|Создает все схемы, отсутствующие в настоящий момент на подписчике.|  
||**0x10000000**|Преобразует **XML-** столбцы в **ntext** на подписчике.|  
||**0x20000000**|Преобразует типы данных больших объектов (**nvarchar (max)** , **varchar (max)** и **varbinary (max)** ), введенные в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , в типы данных, поддерживаемые [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]в.|  
||**0x40000000**|Реплицировать разрешения.|  
||**0x80000000**|Попытаться удалить зависимости для всех объектов, не являющихся частью публикации.|  
||**0x100000000**|Используйте этот параметр, чтобы реплицировать атрибут FILESTREAM, если он указан в столбцах типа **varbinary (max)** . Не указывайте этот параметр, если выполняется репликация таблиц на подписчики [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Репликация таблиц, которые имеют столбцы FILESTREAM [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] для подписчиков, не поддерживается независимо от того, как задан этот параметр схемы.<br /><br /> См. соответствующий параметр **0x800000000**.|  
||**0x200000000**|Преобразует типы данных даты и времени (**Date**, **time**, **DateTimeOffset**и **datetime2**), введенные в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] , в типы данных, которые поддерживаются в более ранних версиях. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
||**0x400000000**|Проводит репликацию параметра сжатия для данных и индексов. Дополнительные сведения см. в разделе [Data Compression](../../relational-databases/data-compression/data-compression.md).|  
||**0x800000000**|Задайте этот параметр для сохранения данных атрибута FILESTREAM в его файловой группе на подписчике. Если этот параметр не задан, данные атрибута FILESTREAM сохраняются в файловой группе по умолчанию. Репликация не создает файловые группы, поэтому, если этот параметр задан, необходимо создать файловую группу до применения моментального снимка на подписчике. Дополнительные сведения о создании объектов перед применением моментального снимка см. [в разделе Выполнение скриптов до и после применения моментального](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)снимка.<br /><br /> См. соответствующий параметр **0x100000000**.|  
||**0x1000000000**|Преобразует определяемые пользователем типы данных среды CLR (UDT) размером более 8000 байт в тип **varbinary (max)** , чтобы столбцы типа UDT могли реплицироваться на подписчики, работающие [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]в.|  
||**0x2000000000**|Преобразует тип данных **hierarchyid** в **varbinary (max)** , чтобы столбцы типа **hierarchyid** могли реплицироваться на подписчики, на которых выполняется [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Дополнительные сведения об использовании столбцов **hierarchyid** в реплицированных таблицах см. в разделе [HIERARCHYID &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md).|  
||**0x4000000000**|Проводит репликацию всех фильтруемых индексов для таблицы. Дополнительные сведения об фильтруемых индексах см. в разделе [CREATE Filtered indexes](../../relational-databases/indexes/create-filtered-indexes.md).|  
||**0x8000000000**|Преобразует типы данных **Geography** и **Geometry** в тип **varbinary (max)** , чтобы столбцы этих типов можно было реплицировать на подписчики, на которых выполняется [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||**0x10000000000**|Реплицирует индексы по столбцам типа **Geography** и **Geometry**.|  
||**0x20000000000**|Производит репликацию атрибута SPARSE для столбцов. Дополнительные сведения об этом атрибуте см. в разделе [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md).|  
||**0x40000000000**|Разрешить агенту моментальных снимков использовать скрипты для создания оптимизированной для памяти таблицы на подписчике.|  
||**0x80000000000**|Преобразует кластеризованный индекс в некластеризованный индекс для статей, оптимизированных для памяти.|  
|**status**||Устанавливает новое состояние свойства.|  
||**горизонтальные секции служб DTS**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
||**включить имена столбцов**|Имена столбцов включаются в реплицируемую инструкцию INSERT.|  
||**нет имен столбцов**|Имена столбцов не включаются в реплицируемую инструкцию INSERT.|  
||**нет горизонтальных секций DTS**|Горизонтальная секция статьи не задается трансформируемой подпиской.|  
||**None**|Очищает все параметры состояния в таблице [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md) и помечает статью как неактивную.|  
||**parameters**|Изменения передаются подписчику при помощи параметризированных команд. Это значение по умолчанию для новой статьи.|  
||**строковые литералы**|Изменения передаются подписчику при помощи значений строковых литералов.|  
|**sync_object**||Имя таблицы или представления, которые используются для создания выходного файла синхронизации. Значение по умолчанию — NULL. Не поддерживается для издателей Oracle.|  
|**одинаковые**||Определяет табличное пространство, используемое таблицей, выполняющей протоколирование, для статьи, опубликованной с базы данных Oracle. Дополнительные сведения см. в статье [Управление табличными пространствами Oracle](../../relational-databases/replication/non-sql/manage-oracle-tablespaces.md).|  
|**значениями**||Процентное значение, определяющее, когда агентом распространителя выделяется новый диапазон идентификаторов. В случае одноранговой репликации не поддерживается.|  
|**type**||Не поддерживается для издателей Oracle.|  
||**основан**|Статья на основе журнала.|  
||**logbased manualboth**|Создаваемая на основе журнала статья с фильтрацией вручную и представлением вручную. Для этого параметра необходимо также задать свойства *sync_object* и *Filter* . Не поддерживается для издателей Oracle.|  
||**logbased manualfilter**|Создаваемая на основе журнала статья с фильтрацией вручную. Для этого параметра необходимо также задать свойства *sync_object* и *Filter* . Не поддерживается для издателей Oracle.|  
||**logbased manualview**|Создаваемая на основе журнала статья с представлением вручную. Для этого параметра необходимо также установить свойство *sync_object* . Не поддерживается для издателей Oracle.|  
||**индексированный виевлогбасед**|Статья индексированного представления, создаваемая на основе журнала. Не поддерживается для издателей Oracle. Для этого типа статьи нет необходимости отдельно публиковать базовую таблицу.|  
||**индексированный виевлогбасед manualboth**|Создаваемая на основе журнала статья индексированного представления с фильтрацией вручную и представлением вручную. Для этого параметра необходимо также задать свойства *sync_object* и *Filter* . Для этого типа статьи нет необходимости отдельно публиковать базовую таблицу. Не поддерживается для издателей Oracle.|  
||**индексированный виевлогбасед manualfilter**|Создаваемая на основе журнала статья индексированного представления с фильтрацией вручную. Для этого параметра также должны быть установлены свойства *sync_object* и *Filter* . Для этого типа статьи нет необходимости отдельно публиковать базовую таблицу. Не поддерживается для издателей Oracle.|  
||**индексированный виевлогбасед manualview**|Создаваемая на основе журнала статья индексированного представления с представлением вручную. Для этого параметра необходимо также установить свойство *sync_object* . Для этого типа статьи нет необходимости отдельно публиковать базовую таблицу. Не поддерживается для издателей Oracle.|  
|**upd_cmd**||Инструкция UPDATE к выполнению; иначе формируется из журнала.|  
|NULL|NULL|Возвращает список свойств статьи, которые могут быть изменены.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Подтверждает, что действие, выполняемое этой хранимой процедурой, может сделать существующий моментальный снимок недействительным. параметр *force_invalidate_snapshot* имеет значение **bit**и значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не приводят к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, возникает ошибка и изменения не выполняются.  
  
 значение **1** указывает, что изменения в статье могут привести к недействительности моментального снимка, и если существуют подписки, требующие создания нового моментального снимка, предоставляет разрешение на пометку существующего моментального снимка как устаревшего и создание нового моментального снимка.  
  
 Сведения о свойствах, при изменении которых требуется формирование нового моментального снимка, см. в разделе «Примечания».  
  
`[ @force_reinit_subscription = ]force_reinit_subscription_`Подтверждает, что действие, выполняемое этой хранимой процедурой, может потребовать повторной инициализации существующих подписок. параметр *force_reinit_subscription* имеет **бит** и значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не приводят к повторной инициализации подписки. Если хранимая процедура определяет, что изменения потребуют повторной инициализации подписок, возникает ошибка, и изменения не выполняются.  
  
 **1** указывает, что изменения в статье приводят к повторной инициализации существующих подписок и предоставляют разрешение на повторную инициализацию подписки.  
  
 Свойства, которые при изменении потребуют повторной инициализации всех текущих подписок, см. в разделе «Примечания».  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  при изменении свойств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] статьи издателя не следует использовать издатель.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_changearticle** используется в репликации моментальных снимков и репликации транзакций.  
  
 Если статья принадлежит публикации, поддерживающей одноранговую репликацию транзакций, можно изменить только свойства **Description**, **ins_cmd**, **upd_cmd**и **del_cmd** .  
  
 Чтобы изменить любое из следующих свойств, необходимо создать новый моментальный снимок, а для параметра *force_invalidate_snapshot* необходимо указать значение **1** :  
  
-   **del_cmd**  
  
-   **dest_table**  
  
-   **destination_owner**  
  
-   **ins_cmd**  
  
-   **pre_creation_cmd**  
  
-   **schema_options**  
  
-   **upd_cmd**  
  
 Изменение любого из следующих свойств требует повторной инициализации существующих подписок, и для параметра *force_reinit_subscription* необходимо указать значение **1** .  
  
-   **del_cmd**  
  
-   **dest_table**  
  
-   **destination_owner**  
  
-   **фильтр**  
  
-   **ins_cmd**  
  
-   **status**  
  
-   **upd_cmd**  
  
 В существующей публикации можно использовать **sp_changearticle** для изменения статьи без удаления и повторного создания всей публикации.  
  
> [!NOTE]  
>  При изменении значения параметра *schema_option*система не выполняет побитового обновления. Это означает, что при установке параметра *schema_option* с помощью **sp_changearticle**существующие битовые параметры могут быть отключены. Чтобы хранить существующие параметры, необходимо выполнить [| (Побитовое или)](../../t-sql/language-elements/bitwise-or-transact-sql.md) между заданной назначением и текущим значением параметра *schema_option*, которое можно определить, выполнив [sp_helparticle](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md).  
  
## <a name="valid-schema-options"></a>Допустимые параметры схемы  
 В следующей таблице описаны допустимые значения параметра *schema_option* в зависимости от типа репликации (отображается в верхней части) и типа статьи (отображается в первом столбце).  
  
|Тип статьи|Тип репликации||  
|------------------|----------------------|------|  
||Транзакционная|Моментальный снимок|  
|**основан**|Все параметры|Все параметры, кроме **0x02**|  
|**logbased manualfilter**|Все параметры|Все параметры, кроме **0x02**|  
|**logbased manualview**|Все параметры|Все параметры, кроме **0x02**|  
|**индексное представление, logbased**|Все параметры|Все параметры, кроме **0x02**|  
|**индексированное представление logbased manualfilter**|Все параметры|Все параметры, кроме **0x02**|  
|**индексированное представление logbased manualview**|Все параметры|Все параметры, кроме **0x02**|  
|**индексированное представление логбасе manualboth**|Все параметры|Все параметры, кроме **0x02**|  
|**Процедура Exec**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**и **0x80000000**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**и **0x80000000**|  
|**Сериализованная процедура Exec**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**и **0x80000000**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**и **0x80000000**|  
|**только схема процесса**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**и **0x80000000**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**и **0x80000000**|  
|**просмотреть только схему**|**0x01**, **0x010**, **0x020**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x100000**, **0x200000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x40000000**и **0x80000000**|**0x01**, **0x010**, **0x020**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x100000**, **0x200000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x40000000**и **0x80000000**|  
|**только схема Func**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**и **0x80000000**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**и **0x80000000**|  
|**только схема индексированного представления**|**0x01**, **0x010**, **0x020**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x100000**, **0x200000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x40000000**и **0x80000000**|**0x01**, **0x010**, **0x020**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x100000**, **0x200000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x40000000**и **0x80000000**|  
  
> [!NOTE]
>  Для публикаций, обновляемых посредством очередей, должно быть включено значение *schema_option* , равное **0x80** . Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] публикаций, не являющихся публикациями, поддерживаются следующие значения аргумента *schema_option* : **0x01**, **0x02**, **0x10**, **0x40**, **0x80**, **0x1000** и **0x4000**.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_changetranarticle](../../relational-databases/replication/codesnippet/tsql/sp-changearticle-transac_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_changearticle**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств статьи](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [хранимая процедуры sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlecolumn (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)  
  
  
