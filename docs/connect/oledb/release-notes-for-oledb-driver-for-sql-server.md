---
title: Заметки о выпуске (Драйвер OLE DB для SQL Server) | Документация Майкрософт
ms.date: 10/11/2019
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 350856cc27bdec601e0db2998f9ff9953cdf6ec7
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381730"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Заметки о выпуске Microsoft OLE DB Driver for SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

Эта страница описывает, что было добавлено в каждой версии драйвера Microsoft OLE DB для SQL Server.

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1830"></a>18.3.0

Октябрь 2019 г.

### <a name="features-added"></a>Добавлены возможности

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка проверки подлинности Azure Active Directory (`ActiveDirectoryInteractive`, `ActiveDirectoryMSI`). | [Использование Azure Active Directory](features/using-azure-active-directory.md) |
| Поддержка встроенных Библиотека проверки подлинности Active Directory (ADAL). | Для использования определенных методов проверки подлинности не требуется отдельная установка ADAL. |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Исправлены ошибки

| Исправление ошибки | Сведения |
| :-------- | :------ |
| Исправлена логика удаления индекса в [IIndexDefinition::D ропиндекс](https://go.microsoft.com/fwlink/?linkid=2106448). | Предыдущие версии драйвера OLE DB не могут удалить индекс первичного ключа, если идентификатор схемы и идентификатор пользователя владельца индекса не равны. |
| &nbsp; | &nbsp; |

## <a name="1823"></a>18.2.3

Июнь 2019 г.

### <a name="features-added"></a>Добавлены возможности

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка обновления драйверов с SQL Server съемного носителя. | Это улучшение позволяет обновлять драйверы непосредственно с SQL Server съемного носителя. |
| &nbsp; | &nbsp; |

## <a name="1822"></a>18.2.2

Май 2019 г.

### <a name="bugs-fixed"></a>Исправлены ошибки

| Исправление ошибки | Сведения |
| :-------- | :------ |
| Исправлена неинтерактивная проверка подлинности Azure Active Directory в многопотоковом подразделении (MTA). | Драйвер OLE DB 18.2.1 некорректно пытается изменить модель параллелизма COM в подразделении, ранее инициализированном как многопотоковое (MTA). В результате, если приложение впоследствии совершает несколько вызовов [CoInitialize](https://go.microsoft.com/fwlink/?linkid=2092520) или [CoInitializeEx](https://go.microsoft.com/fwlink/?linkid=2092521) до вызова интерфейса [IDBInitialize::Initialize](https://go.microsoft.com/fwlink/?linkid=2092522), драйверу не удается подключиться с использованием какой-либо модели проверки подлинности Azure Active Directory. |
| &nbsp; | &nbsp; |

## <a name="1821"></a>18.2.1

Февраль 2019 г.

### <a name="features-added"></a>Добавлены возможности

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка кодировки UTF-8 на сервере. | [Поддержка UTF-8 в OLE DB Driver for SQL Server](features/utf-8-support-in-oledb-driver-for-sql-server.md). |
| Поддержка проверки подлинности Azure Active Directory. | [Использование Azure Active Directory](features/using-azure-active-directory.md) |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

Июль 2018  г.

### <a name="features-added"></a>Добавлены возможности

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка ключевого слова `UseFMTONLY` для строки подключения, а также свойства инициализации `SSPROP_INIT_USEFMTONLY`. | `UseFMTONLY` определяет способ получения метаданных при подключении к [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более новым версиям.<br/><br/>Дополнительные сведения см. в разделе [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Исправлены ошибки

| Исправление ошибки | Сведения |
| :-------- | :------ |
| Исправлена неверная версия файла форматирования BCP. | Драйвер OLE DB 18.0 некорректно задает версию файла форматирования BCP как 18.0 вместо 11.0.<br/>Файлы форматирования, создаваемые драйвером OLE DB 18.0, не могут быть прочитаны драйвером OLE DB 18.1.<br/>Если файлы форматирования, созданные в предыдущей версии драйвера, требуется использовать в новом драйвере, вы можете отредактировать файлы и изменить версию на 11.0 вручную. |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

### <a name="features-added"></a>Добавлены возможности

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка ключевого слова `MultiSubnetFailover` для строки подключения, а также свойства инициализации `SSPROP_INIT_MULTISUBNETFAILOVER`. | Дополнительные сведения см. в разделе:<br/>&bull; &nbsp; [Поддержка высокого уровня доступности и аварийного восстановления в драйвере OLE DB для SQL Server](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).<br/>&bull; &nbsp; [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>См. также раздел

[Драйвер Microsoft OLE DB для SQL Server](oledb-driver-for-sql-server.md)
