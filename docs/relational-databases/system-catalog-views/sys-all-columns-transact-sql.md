---
title: sys. all_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- all_columns_TSQL
- all_columns
- sys.all_columns_TSQL
- sys.all_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.all_columns catalog view
ms.assetid: 40e04fe9-0b64-4799-84c0-57f128b2bdc2
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 712898faaf9ca24cf4b5a01b1b726231f76f0c22
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "73981824"
---
# <a name="sysall_columns-transact-sql"></a>sys.all_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Показывает объединение всех столбцов, принадлежащих к пользовательским и системным объектам.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор объекта, которому принадлежит этот столбец.|  
|name|**sysname**|Имя столбца. Уникален в пределах объекта.|  
|column_id|**int**|Идентификатор столбца. Уникален в пределах объекта.<br /><br /> Идентификаторы столбца могут быть непоследовательными.|  
|system_type_id|**tinyint**|Идентификатор системного типа столбца.|  
|user_type_id|**int**|Идентификатор определенного пользователем типа столбца.<br /><br /> Чтобы вернуть имя типа, присоединитесь к представлению каталога [sys. types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) в этом столбце.|  
|max_length|**smallint**|Максимальная длина столбца (в байтах).<br /><br /> -1 = тип данных столбца — **varchar (max)** , **nvarchar (max)** , **varbinary (max)** или **XML**.<br /><br /> Для **текстовых** столбцов значение max_length будет равно 16, а значение задается sp_tableoption "text in row".|  
|precision|**tinyint**|Точность столбца, если он является числовым; в противном случае — 0.|  
|масштаб|**tinyint**|Масштаб столбца, если он является числовым; в противном случае — 0.|  
|collation_name|**sysname**|Имя параметров сортировки столбца, если он символьный; в противном случае — значение NULL.|  
|is_nullable|**бит**|1 = столбец может принимать значение NULL.|  
|is_ansi_padded|**бит**|1 = столбец использует поведение ANSI_PADDING ON, если имеет тип данных character, binary или variant.<br /><br /> 0 = столбец имеет тип данных, отличный от character, binary или variant.|  
|is_rowguidcol|**бит**|1 = столбец объявлен как ROWGUIDCOL.|  
|is_identity|**бит**|1 = столбец содержит значения идентификаторов.|  
|is_computed|**бит**|1 = столбец является вычисляемым.|  
|is_filestream|**бит**|1 = для столбца используется потоковое хранилище.|  
|is_replicated|**бит**|1 = столбец реплицирован.|  
|is_non_sql_subscribed|**бит**|1 = у столбца есть подписчик, отличный от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|is_merge_published|**бит**|1 = столбец публикуется слиянием.|  
|is_dts_replicated|**бит**|1 = столбец реплицируется с помощью служб [!INCLUDE[ssIS](../../includes/ssis-md.md)].|  
|is_xml_document|**бит**|1 = содержимое является готовым XML-документом.<br /><br /> 0 = содержимое — фрагмент документа, или данные столбца не принадлежат к типу XML.|  
|xml_collection_id|**int**|Ненулевое значение, если тип данных столбца — **XML** , а XML-код типизирован. Значением будет идентификатор коллекции, содержащей пространство имен проверяющей схемы XML столбца.<br /><br /> 0 = нет коллекции схем XML.|  
|default_object_id|**int**|Идентификатор объекта по умолчанию, независимо от того, является ли он автономным представлением [sys. sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)или встроенным ограничением по умолчанию на уровне столбцов. Столбец parent_object_id встроенного объекта «значение по умолчанию» уровня столбца представляет собой ссылку на саму таблицу.<br /><br /> 0 = значение по умолчанию отсутствует.|  
|rule_object_id|**int**|Идентификатор изолированного правила, привязанного к столбцу с помощью процедуры sys.sp_bindrule.<br /><br /> 0 = изолированное правило отсутствует.<br /><br /> Ограничения CHECK на уровне столбцов см. в разделе [sys. &#40;CHECK_CONSTRAINTS Transact-&#41;SQL](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md).|  
|is_sparse|bit|1 = столбец является разреженным. Дополнительные сведения см. в статье [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md).|  
|is_column_set|bit|1 = столбец является набором столбцов. Дополнительные сведения см. в статье [Использование наборов столбцов](../../relational-databases/tables/use-column-sets.md).|  
|generated_always_type|**tinyint**|**Область применения**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и более поздних версий.<br /><br /> Числовое значение, представляющее тип столбца:<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END|  
|generated_always_type_desc|**nvarchar(60)**|**Область применения**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и более поздних версий.<br /><br /> Текстовое описание типа столбца:<br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также статью  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Запросы к системному каталогу SQL Server вопросы и ответы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys. system_columns &#40;  Transact-&#41; SQL](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)  
 [sys. computed_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)  
  
  
