---
title: Функция SQLBindCol | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBindCol
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBindCol
helpviewer_keywords:
- SQLBindCol function [ODBC]
ms.assetid: 41a37655-84cd-423f-9daa-e0b47b88dc54
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c1c89ff79ee0fcac37f7b6e231e957e051c9db2e
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289286"
---
# <a name="sqlbindcol-function"></a>SQLBindCol, функция
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: ISO 92  
  
 **Сводка**  
 **SQLBindCol** привязывает буферы данных приложения к столбцам результирующего набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLBindCol(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   ColumnNumber,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Аргументы  
 *статеменсандле*  
 Входной Маркер инструкции.  
  
 *ColumnNumber*  
 Входной Номер столбца результирующего набора для привязки. Столбцы нумеруются в возрастающем порядке столбцов, начиная с 0, где столбец 0 является столбцом закладки. Если закладки не используются, т. е. атрибуту инструкции SQL_ATTR_USE_BOOKMARKS присвоено значение SQL_UB_OFF, то номера столбцов начинаются с 1.  
  
 *TargetType*  
 Входной Идентификатор типа данных C \*буфера *таржетвалуептр* . При извлечении данных из источника данных с помощью **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**или **SQLSetPos**драйвер преобразует данные в этот тип. При отправке данных в источник данных с помощью **SQLBulkOperations** или **SQLSetPos**драйвер преобразует данные из этого типа. Список допустимых типов данных C и идентификаторов типов см. в разделе [типы данных c](../../../odbc/reference/appendixes/c-data-types.md) в приложении г: типы данных.  
  
 Если аргумент *TargetType* является типом данных Interval, то значение интервала по умолчанию (2) и значение интервала в секундах (6), заданное в полях SQL_DESC_DATETIME_INTERVAL_PRECISION и SQL_DESC_PRECISION АРД, соответственно, используются для данных. Если аргумент *TargetType* имеет значение SQL_C_NUMERIC, то точность по умолчанию (определяется драйвером) и масштаб по умолчанию (0), как задано в полях SQL_DESC_PRECISION и SQL_DESC_SCALE АРД, используются для данных. Если какая-либо точность или масштаб по умолчанию не подходит, приложение должно явно задать соответствующее поле дескриптора, вызвав метод **SQLSetDescField** или **SQLSetDescRec**.  
  
 Можно также указать расширенный тип данных C. Дополнительные сведения о типах данных см. в разделе [Типы данных C в ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 *таржетвалуептр*  
 [Отложенные входные и выходные данные] Указатель на буфер данных для привязки к столбцу. **SQLFetch** и **SQLFetchScroll** возвращают данные в этом буфере. **SQLBulkOperations** возвращает данные в этом буфере, когда *Операция* выполняется SQL_FETCH_BY_BOOKMARK; он получает данные из этого буфера, когда *Операция* выполняется SQL_ADD или SQL_UPDATE_BY_BOOKMARK. Функция **SQLSetPos** возвращает данные в этом буфере при SQL_REFRESH *операции* ; он получает данные из этого буфера, когда *Операция* выполняется SQL_UPDATE.  
  
 Если *таржетвалуептр* является пустым указателем, драйвер отменяет привязку буфера данных для столбца. Приложение может отменить привязку всех столбцов путем вызова **SQLFreeStmt** с параметром SQL_UNBIND. Приложение может отменить привязку буфера данных для столбца, но по-прежнему имеет привязанный к нему буфер длины или индикатора, если аргумент *таржетвалуептр* в вызове **SQLBindCol** является пустым указателем, но аргумент *StrLen_or_IndPtr* является допустимым значением.  
  
 *BufferLength*  
 Входной Длина \*буфера *таржетвалуептр* в байтах.  
  
 Драйвер использует *BufferLength* , чтобы избежать записи после конца буфера \**таржетвалуептр* , когда он возвращает данные переменной длины, такие как символьные или двоичные данные. Обратите внимание, что драйвер подсчитывает символ завершения null при возврате символьных данных в \**таржетвалуептр*. \**таржетвалуептр* должен содержать пробел для завершающего символа null или драйвер будет усекать данные.  
  
 Когда драйвер возвращает данные фиксированной длины, такие как целое число или структура даты, драйвер игнорирует *BufferLength* и считает, что буфер достаточно велик для хранения данных. Поэтому важно, чтобы приложение выделило большой буфер для данных фиксированной длины, иначе драйвер запишет за пределы буфера.  
  
 **SQLBindCol** ВОЗВРАЩАЕТ значение SQLSTATE HY090 (Недопустимая строка или длина буфера), если *BufferLength* меньше 0, но не если *BufferLength* равно 0. Однако, если в *TargetType* указан символьный тип, приложение не должно устанавливать *BufferLength* в значение 0, так как драйверы, совместимые с CLI ISO, в этом случае возвращают значение SQLSTATE HY090 (Недопустимая строка или длина буфера).  
  
 *StrLen_or_IndPtr*  
 [Отложенные входные и выходные данные] Указатель на буфер длины или индикатора для привязки к столбцу. **SQLFetch** и **SQLFetchScroll** возвращают значение в этом буфере. **SQLBulkOperations** извлекает значение из этого буфера, когда *Операция* выполняется SQL_ADD, SQL_UPDATE_BY_BOOKMARK или SQL_DELETE_BY_BOOKMARK. **SQLBulkOperations** возвращает значение в этом буфере при SQL_FETCH_BY_BOOKMARK *операции* . Функция **SQLSetPos** возвращает значение в этом буфере, когда *Операция* выполняется SQL_REFRESH; он получает значение из этого буфера, когда *Операция* выполняется SQL_UPDATE.  
  
 **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**и **SQLSetPos** могут возвращать следующие значения в буфере длины и индикатора:  
  
-   Длина возвращаемых данных  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 Приложение может разместить следующие значения в буфере длины и индикатора для использования с **SQLBulkOperations** или **SQLSetPos**:  
  
-   Длина отправляемых данных  
  
-   SQL_NTS  
  
-   SQL_NULL_DATA  
  
-   SQL_DATA_AT_EXEC  
  
-   Результат макроса SQL_LEN_DATA_AT_EXEC  
  
-   SQL_COLUMN_IGNORE  
  
 Если буфер индикатора и буфер длины являются отдельными буферами, то буфер индикатора может возвращать только SQL_NULL_DATA, тогда как буфер длины может возвращать все остальные значения.  
  
 Дополнительные сведения см. в разделе [функция SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md), [Функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)и [Использование значений длины и индикатора](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Если *StrLen_or_IndPtr* является пустым указателем, значение длины или индикатора не используется. Это ошибка при выборке данных, и данные имеют значение NULL.  
  
 Если приложение будет работать в 64-разрядной операционной системе, см. [сведения о ODBC 64-bit](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLBindCol** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и *маркером* *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLBindCol** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|07006|Нарушение атрибута ограниченного типа данных|(DM) аргумент *columnNumber* был равен 0, а аргумент *TargetType* не SQL_C_BOOKMARK или SQL_C_VARBOOKMARK.|  
|07009|Недопустимый индекс дескриптора|Значение, указанное для аргумента *columnNumber* , превышает максимальное число столбцов в результирующем наборе.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере *\*MessageText*, описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY003|Недопустимый тип буфера приложения|Аргумент *TargetType* не был ни допустимым типом данных, ни SQL_C_DEFAULT.|  
|HY010|Ошибка последовательности функций|(DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта асинхронная функция все еще выполнялась при вызове **SQLBindCol** .<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *статеменсандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.<br /><br /> (DM) была вызвана асинхронно исполняемая функция для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны для *статеменсандле* и возвращены SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение, указанное для аргумента *BufferLength* , было меньше 0.<br /><br /> (DM) драйвер был ODBC 2. драйвер *x* , аргумент *columnNumber* был установлен в 0, а значение, указанное для аргумента *BufferLength* , не равно 4.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Необязательная функция не реализована|Драйвер или источник данных не поддерживает преобразование, заданное сочетанием аргумента *TargetType* и определяемого драйвером типа данных SQL соответствующего столбца.<br /><br /> Аргумент *columnNumber* был равен 0, а драйвер не поддерживает закладки.<br /><br /> Драйвер поддерживает только ODBC 2. *x* , а аргумент *TargetType* является одним из следующих:<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> и любые типы данных интервала C, перечисленные в разделе [типы данных c](../../../odbc/reference/appendixes/c-data-types.md) в приложении D: типы данных.<br /><br /> Драйвер поддерживает только версии ODBC до 3,50, а аргумент *TargetType* был SQL_C_GUID.|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 **SQLBindCol** используется для связывания или *привязки* столбцов в результирующем наборе с буферами данных и буферов длины или индикатора в приложении. Когда приложение вызывает **SQLFetch**, **SQLFetchScroll**или **SQLSetPos** для выборки данных, драйвер возвращает данные для связанных столбцов в указанных буферах. Дополнительные сведения см. в разделе [функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md). Когда приложение вызывает **SQLBulkOperations** для обновления или вставки строки или инструкции **SQLSetPos** для обновления строки, драйвер получает данные для связанных столбцов из указанных буферов. Дополнительные сведения см. в разделе [функция SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md) или [Функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md). Дополнительные сведения о привязке см. в разделе [Получение результатов (базовый)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 Обратите внимание, что столбцы не обязательно должны быть привязаны для получения данных из них. Приложение также может вызывать **SQLGetData** для получения данных из столбцов. Хотя можно привязать некоторые столбцы в строке и вызвать **SQLGetData** для других, это подчиняется некоторым ограничениям. Дополнительные сведения см. в разделе [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
## <a name="binding-unbinding-and-rebinding-columns"></a>Привязка, отмена привязки и повторная привязка столбцов  
 В любой момент времени столбец может быть привязан, отменен или перепривязан, даже после того, как данные получены из результирующего набора. Новая привязка вступает в силу при следующем вызове функции, использующей привязки. Например, предположим, что приложение привязывает столбцы в результирующем наборе и вызывает **SQLFetch**. Драйвер возвращает данные в привязанных буферах. Теперь предположим, что приложение привязывает столбцы к другому набору буферов. Драйвер не помещает данные для только что полученной строки в вновь привязанные буферы. Вместо этого он ждет повторного вызова **SQLFetch** , а затем помещает данные для следующей строки в вновь привязанных буферах.  
  
> [!NOTE]  
>  Атрибут инструкции SQL_ATTR_USE_BOOKMARKS всегда должен быть задан перед привязкой столбца к столбцу 0. Это не является обязательным, но настоятельно рекомендуется.  
  
## <a name="binding-columns"></a>Привязка столбцов  
 Для привязки столбца приложение вызывает **SQLBindCol** и передает номер столбца, тип, адрес и длину буфера данных, а также адрес буфера длины или индикатора. Сведения о том, как используются эти адреса, см. в подразделе «буферные адреса» ниже. Дополнительные сведения о привязке столбцов см. [в разделе using SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 Использование этих буферов откладывается; Это значит, что приложение привязывает их в **SQLBindCol** , но драйвер обращается к ним из других функций, а именно **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**или **SQLSetPos**. Это обязанность приложения, чтобы убедиться, что указатели, указанные в **SQLBindCol** , остаются допустимыми, пока привязка остается в силе. Если приложение допускает, чтобы эти указатели стали недопустимыми, например, освобождается буфер, а затем вызывается функция, которая ожидает, что они являются допустимыми, последствия не определены. Дополнительные сведения см. в разделе [отложенные буферы](../../../odbc/reference/develop-app/deferred-buffers.md).  
  
 Привязка остается в силе до тех пор, пока она не будет заменена новой привязкой, не привязана к столбцу или освобождена.  
  
## <a name="unbinding-columns"></a>Отмена привязки столбцов  
 Чтобы отменить привязку одного столбца, приложение вызывает **SQLBindCol** с параметром *columnNumber* , равным количеству этого столбца, а *таржетвалуептр* задает нулевой указатель. Если *columnNumber* ссылается на несвязанный столбец, **SQLBindCol** по-прежнему возвращает SQL_SUCCESS.  
  
 Чтобы отменить привязку всех столбцов, приложение вызывает **SQLFreeStmt** с *параметром fOption* , для которого задано значение SQL_UNBIND. Это также можно сделать, задав в поле SQL_DESC_COUNT АРД значение 0.  
  
## <a name="rebinding-columns"></a>Повторная привязка столбцов  
 Приложение может выполнить одну из двух операций для изменения привязки:  
  
-   Вызовите **SQLBindCol** , чтобы указать новую привязку для уже привязанного столбца. Драйвер перезаписывает старую привязку новым.  
  
-   Укажите смещение, которое будет добавлено к буферному адресу, указанному вызовом привязки к **SQLBindCol**. Дополнительные сведения см. в следующем разделе «смещения привязки».  
  
## <a name="binding-offsets"></a>Смещения привязок  
 Смещение привязки — это значение, которое добавляется к адресам данных и буферов длины или индикатора (как указано в аргументе *таржетвалуептр* и *StrLen_or_IndPtr* ), прежде чем они будут разыменованы. При использовании смещений привязки являются шаблоном способа размещения буферов приложения, и приложение может переместить этот шаблон в различные области памяти, изменив смещение. Поскольку одно и то же смещение добавляется к каждому адресу в каждой привязке, относительные смещения между буферами для разных столбцов должны быть одинаковыми в пределах каждого набора буферов. Это всегда справедливо при использовании привязки на уровне строки. приложение должно тщательно разметить его буферы, чтобы это было истинно при использовании привязки на уровне столбца.  
  
 Использование смещения привязки в основном аналогично повторной привязке столбца путем вызова **SQLBindCol**. Разница заключается в том, что новый вызов **SQLBindCol** указывает новые адреса для буфера данных и буфер длины/индикатора, тогда как использование смещения привязки не изменяет адреса, но просто добавляет к ним смещение. Приложение может указать новое смещение всякий раз, когда оно требуется, и это смещение всегда добавляется к изначально привязанным адресам. В частности, если для смещения задано значение 0 или если атрибуту инструкции задан пустой указатель, драйвер использует изначально привязанные адреса.  
  
 Чтобы задать смещение привязки, приложение устанавливает атрибут SQL_ATTR_ROW_BIND_OFFSET_PTR инструкции в адрес буфера SQLINTEGER. Прежде чем приложение вызовет функцию, которая использует привязки, она помещает смещение в байтах в этом буфере. Чтобы определить используемый адрес буфера, драйвер добавляет смещение к адресу в привязке. Сумма адреса и смещения должна быть действительным адресом, но адрес, к которому добавляется смещение, не должен быть допустимым. Дополнительные сведения о том, как используются смещения привязки, см. в подразделе «буферные адреса» ниже.  
  
## <a name="binding-arrays"></a>Привязка массивов  
 Если размер набора строк (значение атрибута оператора SQL_ATTR_ROW_ARRAY_SIZE) больше 1, приложение привязывает массивы буферов вместо одиночных буферов. Дополнительные сведения см. в разделе [блочные курсоры](../../../odbc/reference/develop-app/block-cursors.md).  
  
 Приложение может выполнять привязку массивов двумя способами:  
  
-   Привяжите массив к каждому столбцу. Это называется *привязкой на уровне столбца* , так как каждая структура данных (массив) содержит данные для одного столбца.  
  
-   Определите структуру для хранения данных для целой строки и свяжите массив этих структур. Это называется *привязкой на уровне строк* , так как каждая структура данных содержит данные для одной строки.  
  
 Каждый массив буферов должен содержать по крайней мере столько элементов, сколько имеет размер набора строк.  
  
> [!NOTE]  
>  Приложение должно проверить допустимость выравнивания. Дополнительные сведения о вопросах выравнивания см. в разделе [Выравнивание](../../../odbc/reference/develop-app/alignment.md).  
  
## <a name="column-wise-binding"></a>Привязка на уровне столбца  
 В привязке на уровне столбца приложение привязывает отдельные данные и массивы длины и индикатора к каждому столбцу.  
  
 Чтобы использовать привязку на уровне столбца, приложение сначала устанавливает атрибут SQL_ATTR_ROW_BIND_TYPE инструкции в значение SQL_BIND_BY_COLUMN. (Это значение по умолчанию.) Для каждого столбца, который должен быть привязан, приложение выполняет следующие действия:  
  
1.  Выделяет массив буфера данных.  
  
2.  Выделяет массив буферов длины или индикатора.  
  
    > [!NOTE]  
    >  Если приложение выполняет запись непосредственно в дескрипторы при использовании привязки на уровне столбца, для данных длины и индикатора можно использовать отдельные массивы.  
  
3.  Вызывает **SQLBindCol** со следующими аргументами:  
  
    -   *TargetType* — это тип одного элемента в массиве буфера данных.  
  
    -   *Таржетвалуептр* — это адрес массива буфера данных.  
  
    -   *BufferLength* — это размер одного элемента в массиве буфера данных. Аргумент *BufferLength* игнорируется, если данные являются данными фиксированной длины.  
  
    -   *StrLen_or_IndPtr* — это адрес массива длины или индикатора.  
  
 Дополнительные сведения об использовании этих сведений см. в подразделе «буферные адреса» ниже Дополнительные сведения о привязке на уровне столбца см. в разделе [Привязка на уровне столбцов](../../../odbc/reference/develop-app/column-wise-binding.md).  
  
## <a name="row-wise-binding"></a>Привязка на уровне строки  
 В привязке на уровне строки приложение определяет структуру, содержащую данные, и буферы длины или индикатора для каждого столбца, поддающийся ограничению.  
  
 Чтобы использовать привязку на уровне строки, приложение выполняет следующие действия:  
  
1.  Определяет структуру для хранения одной строки данных (включая данные и буферы длины или индикатора) и выделяет массив этих структур.  
  
    > [!NOTE]  
    >  Если приложение выполняет запись непосредственно в дескрипторы при использовании привязки на уровне строки, для данных длины и индикатора можно использовать отдельные поля.  
  
2.  Задает для атрибута SQL_ATTR_ROW_BIND_TYPE инструкции размер структуры, содержащей одну строку данных, или размер экземпляра буфера, в который будут привязаны столбцы результатов. Длина должна включать пробел для всех привязанных столбцов и любое заполнение структуры или буфера, чтобы гарантировать, что при увеличении адреса привязанного столбца с указанной длиной результат будет указывать на начало того же столбца в следующей строке. При использовании оператора *sizeof* в ANSI C это поведение гарантировано.  
  
3.  Вызывает **SQLBindCol** со следующими аргументами для каждого столбца, который должен быть привязан:  
  
    -   *TargetType* — это тип элемента буфера данных, который должен быть привязан к столбцу.  
  
    -   *Таржетвалуептр* — это адрес элемента буфера данных в первом элементе массива.  
  
    -   *BufferLength* — это размер элемента буфера данных.  
  
    -   *StrLen_or_IndPtr* — это адрес элемента с длиной или индикатором, который должен быть привязан.  
  
 Дополнительные сведения об использовании этих сведений см. в подразделе «буферные адреса» ниже Дополнительные сведения о привязке на уровне столбца см. в разделе [Привязка на уровне строк](../../../odbc/reference/develop-app/row-wise-binding.md).  
  
## <a name="buffer-addresses"></a>Буферные адреса  
 *Адрес буфера* — это фактический адрес данных или буфера длины или индикатора. Драйвер вычисляет адрес буфера непосредственно перед записью в буфер (например, во время выборки). Он вычисляется по следующей формуле, которая использует адреса, указанные в аргументах *таржетвалуептр* и *StrLen_or_IndPtr* , смещение привязки и номер строки:  
  
 *Привязанный адрес* + *смещение привязки* + ((*номер строки* -1) x *размер элемента*)  
  
 где переменные формулы определены, как описано в следующей таблице.  
  
|Переменная|Описание|  
|--------------|-----------------|  
|*Связанный адрес*|Для буферов данных адрес, указанный с помощью аргумента *таржетвалуептр* в **SQLBindCol**.<br /><br /> Для буферов длины и индикатора адрес, указанный с помощью аргумента *StrLen_or_IndPtr* в **SQLBindCol**. Дополнительные сведения см. в разделе "дополнительные комментарии" раздела "дескрипторы и SQLBindCol".<br /><br /> Если привязанный адрес равен 0, значение данных не возвращается, даже если адрес, вычисленный предыдущей формулой, не равен нулю.|  
|*Смещение привязки*|Если используется привязка на уровне строки, значение, хранящееся в адресе, указанном с помощью атрибута инструкции SQL_ATTR_ROW_BIND_OFFSET_PTR.<br /><br /> Если используется привязка на уровне столбца или значение атрибута SQL_ATTR_ROW_BIND_OFFSET_PTR оператора является пустым указателем, то *смещение привязки* равно 0.|  
|*Номер строки*|Номер строки в наборе строк, отсчитываемый от 1. Для однострочных выборок, которые являются значением по умолчанию, это значение равно 1.|  
|*Размер элемента*|Размер элемента в связанном массиве.<br /><br /> Если используется привязка на уровне столбца, это **sizeof (SQLINTEGER)** для буферов длины или индикатора. Для буферов данных это значение аргумента *BufferLength* в **SQLBindCol** , если тип данных имеет переменную длину, и размер типа данных, если тип данных имеет фиксированную длину.<br /><br /> Если используется привязка на уровне строки, это значение атрибута SQL_ATTR_ROW_BIND_TYPE инструкции для буферов данных и длины/индикатора.|  
  
## <a name="descriptors-and-sqlbindcol"></a>Дескрипторы и SQLBindCol  
 В следующих разделах описывается взаимодействие **SQLBindCol** с дескрипторами.  
  
> [!CAUTION]  
>  Вызов **SQLBindCol** для одного оператора может повлиять на другие инструкции. Это происходит, когда АРД, связанный с инструкцией, явным образом выделяется и также связывается с другими инструкциями. Поскольку **SQLBindCol** изменяет дескриптор, изменения применяются ко всем инструкциям, с которыми связан этот дескриптор. Если это не является необходимым поведением, приложение должно отменить связь этого дескриптора с другими инструкциями перед вызовом **SQLBindCol**.  
  
## <a name="argument-mappings"></a>Сопоставления аргументов  
 По сути, **SQLBindCol** выполняет следующие действия последовательно:  
  
1.  Вызывает **SQLGetStmtAttr** для получения маркера АРД.  
  
2.  Вызывает **SQLGetDescField** для получения поля SQL_DESC_COUNT дескриптора, и если значение аргумента *ColumnNumber* превышает значение SQL_DESC_COUNT, вызывает **SQLSetDescField** , чтобы увеличить значение SQL_DESC_COUNT до *columnNumber*.  
  
3.  Вызывает **SQLSetDescField** несколько раз, чтобы присвоить значения следующим полям АРД:  
  
    -   Устанавливает SQL_DESC_TYPE и SQL_DESC_CONCISE_TYPE значение *TargetType*, за исключением того, что если *TargetType* является одним из кратких идентификаторов типа DateTime или interval, он устанавливает SQL_DESC_TYPE SQL_DATETIME или SQL_INTERVAL соответственно. Задает SQL_DESC_CONCISE_TYPE для краткого идентификатора; и присваивает SQL_DESC_DATETIME_INTERVAL_CODE соответствующему подкоду DateTime или Interval.  
  
    -   Задает один или несколько SQL_DESC_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE и SQL_DESC_DATETIME_INTERVAL_PRECISION в соответствии с соответствующими для *TargetType*.  
  
    -   Устанавливает поле SQL_DESC_OCTET_LENGTH в значение *BufferLength*.  
  
    -   Устанавливает поле SQL_DESC_DATA_PTR в значение *таржетвалуе*.  
  
    -   Задает для поля SQL_DESC_INDICATOR_PTR значение *StrLen_Or_Ind*. (См. следующий абзац.)  
  
    -   Задает для поля SQL_DESC_OCTET_LENGTH_PTR значение *StrLen_Or_Ind*. (См. следующий абзац.)  
  
 Переменная, на которую ссылается аргумент *StrLen_Or_Ind* , используется для сведений о индикаторе и длине. Если выборка обнаруживает значение NULL для столбца, то в этой переменной сохраняется SQL_NULL_DATA. в противном случае она сохраняет длину данных в этой переменной. Передача пустого указателя в качестве *StrLen_Or_Ind* позволяет операции выборки возвращать длину данных, но делает выборку ошибкой, если она встречает значение NULL и не имеет способа возвращать SQL_NULL_DATA.  
  
 Если вызов **SQLBindCol** завершается ошибкой, содержимое полей дескриптора, которое было бы задано в АРД, не определено и значение поля SQL_DESC_COUNT в АРД не изменяется.  
  
## <a name="implicit-resetting-of-count-field"></a>Неявный сброс поля СЧЕТЧИКа  
 **SQLBindCol** задает SQL_DESC_COUNT значение аргумента *columnNumber* только в том случае, если это увеличит значение SQL_DESC_COUNT. Если значение аргумента *таржетвалуептр* является пустым указателем, а значение в аргументе *columnNumber* равно SQL_DESC_COUNT (то есть при отмене привязки к столбцу с наибольшим связыванием), то SQL_DESC_COUNT задается на число наибольших оставшихся связанных столбцов.  
  
## <a name="cautions-regarding-sql_default"></a>Предостережения относительно SQL_DEFAULT  
 Для успешного извлечения данных столбца приложение должно правильно определить длину и начальную точку данных в буфере приложения. Если в приложении указан явный *TargetType*, легко обнаруживаются неконцепции приложений. Однако, если приложение указывает *TargetType* SQL_DEFAULT, **SQLBindCol** можно применить к столбцу другого типа данных из того, который предназначен для приложения, либо из изменений метаданных, либо путем применения кода к другому столбцу. В этом случае приложение может не всегда определять начало или длину данных извлекаемого столбца. Это может привести к неотчетным ошибкам данных или нарушениям памяти.  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере приложение выполняет инструкцию **SELECT** в таблице Customers для возврата результирующего набора идентификаторов клиентов, имен и номеров телефонов, отсортированных по имени. Затем он вызывает **SQLBindCol** для привязки столбцов данных к локальным буферам. Наконец, приложение извлекает каждую строку данных с помощью **SQLFetch** и выводит имя, идентификатор и номер телефона каждого клиента.  
  
 Дополнительные примеры кода см. в разделе [функция SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [функция SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md), функция [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)и [Функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```cpp  
// SQLBindCol_ref.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <stdio.h>  
  
#define UNICODE  
#include <sqlext.h>  
  
#define NAME_LEN 50  
#define PHONE_LEN 20  
  
void show_error() {  
   printf("error\n");  
}  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
   SQLWCHAR szName[NAME_LEN], szPhone[PHONE_LEN], sCustID[NAME_LEN];  
   SQLLEN cbName = 0, cbCustID = 0, cbPhone = 0;  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            // Connect to data source  
            retcode = SQLConnect(hdbc, (SQLWCHAR*) L"NorthWind", SQL_NTS, (SQLWCHAR*) NULL, 0, NULL, 0);  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {   
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               retcode = SQLExecDirect(hstmt, (SQLWCHAR *) L"SELECT CustomerID, ContactName, Phone FROM CUSTOMERS ORDER BY 2, 1, 3", SQL_NTS);  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
                  // Bind columns 1, 2, and 3  
                  retcode = SQLBindCol(hstmt, 1, SQL_C_CHAR, &sCustID, 100, &cbCustID);  
                  retcode = SQLBindCol(hstmt, 2, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
                  retcode = SQLBindCol(hstmt, 3, SQL_C_CHAR, szPhone, PHONE_LEN, &cbPhone);   
  
                  // Fetch and print each row of data. On an error, display a message and exit.  
                  for (i ; ; i++) {  
                     retcode = SQLFetch(hstmt);  
                     if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
                        show_error();  
                     if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
                        wprintf(L"%d: %S %S %S\n", i + 1, sCustID, szName, szPhone);  
                     else  
                        break;  
                  }  
               }  
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLCancel(hstmt);  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
 См. также [Пример программы ODBC](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Возврат сведений о столбце в результирующем наборе|[Функция SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Выборка блока данных или прокрутка результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Выборка нескольких строк данных|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Освобождение буферов столбцов в инструкции|[Функция SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Выборка части или всего столбца данных|[Функция SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Возвращение количества столбцов результирующего набора|[Функция SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
  
## <a name="see-also"></a>См. также статью  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
