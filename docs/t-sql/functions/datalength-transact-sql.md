---
title: DATALENGTH (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/20/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATALENGTH_TSQL
- DATALENGTH
dev_langs:
- TSQL
helpviewer_keywords:
- number of bytes representing expression
- data types [SQL Server], length
- DATALENGTH function
- expressions [SQL Server], length
- lengths [SQL Server], data
ms.assetid: 00f377f1-cc3e-4eac-be47-b3e3f80267c9
author: pmasl
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0ed31eae6817216a694337ed5bc606dcba52fb89
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844510"
---
# <a name="datalength-transact-sql"></a>DATALENGTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Эта функция возвращает число байтов, использованных для представления выражения.

> [!NOTE]
> Чтобы получить количество символов в строковом выражении, используйте функцию [LEN](../../t-sql/functions/len-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```
DATALENGTH ( expression )   
```  
  
## <a name="arguments"></a>Аргументы  
*expression*  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа данных.
  
## <a name="return-types"></a>Типы возвращаемых данных
**bigint**, если *expression* имеет тип данных **nvarchar(max)** , **varbinary(max)** или **varchar(max)** ; в противном случае **int**.
  
## <a name="remarks"></a>Remarks  
Функция `DATALENGTH` особенно полезна при использовании с типами данных переменной длины, как показано ниже.
- **image**
- **ntext**
- **nvarchar**
- **text**
- **varbinary**
- **varchar**
  
Для значения NULL функция `DATALENGTH` возвращает NULL.
  
> [!NOTE]  
> Уровни совместимости могут повлиять на возвращаемые значения. Дополнительные сведения об уровнях совместимости см. в статье [Уровень совместимости ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  

> [!NOTE]
> Функция [LEN](../../t-sql/functions/len-transact-sql.md) возвращает количество символов, закодированных в определенное строковое выражение, а функция [DATALENGTH](../../t-sql/functions/datalength-transact-sql.md) — размер данных в байтах для определенного строкового выражения. Эти выходные данные могут быть разными в зависимости от типа данных и типа кодировки, используемой в столбце. Дополнительные сведения об отличиях типов кодировок, используемых для хранения данных, см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md) (Поддержка параметров сортировки и Юникода).

## <a name="examples"></a>Примеры  
В следующем примере находится длина столбца `Name` в таблице `Product`:
  
```sql
USE AdventureWorks2016  
GO
SELECT length = DATALENGTH(EnglishProductName), EnglishProductName  
FROM dbo.DimProduct  
ORDER BY EnglishProductName;  
GO  
```  
  
## <a name="see-also"></a>См. также раздел
[LEN (Transact-SQL)](../../t-sql/functions/len-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-category-transact-sql.md)
