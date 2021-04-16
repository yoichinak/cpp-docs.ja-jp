---
description: '詳細情報: CDBException クラス'
title: CDBException クラス
ms.date: 11/04/2016
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
ms.openlocfilehash: 437e59058226f274962dedcda52b973eee4ea1ba
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577275"
---
# <a name="cdbexception-class"></a>CDBException クラス

データベース クラスから発生する例外状態を表現します。

## <a name="syntax"></a>構文

```
class CDBException : public CException
```

## <a name="members"></a>メンバー

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDBException:: m_nRetCode](#m_nretcode)|RETCODE 型の Open Database Connectivity (ODBC) リターンコードを格納します。|
|[CDBException:: m_strError](#m_strerror)|エラーを表す英数字の文字列が含まれています。|
|[CDBException:: m_strStateNativeOrigin](#m_strstatenativeorigin)|ODBC によって返されるエラーコードに関してエラーを説明する文字列を格納します。|

## <a name="remarks"></a>解説

クラスには、例外の原因を特定したり、例外を説明するテキストメッセージを表示したりするために使用できる2つのパブリックデータメンバーが含まれています。 `CDBException` オブジェクトは、データベースクラスのメンバー関数によって構築およびスローされます。

> [!NOTE]
> このクラスは、MFC の Open Database Connectivity (ODBC) クラスの1つです。 代わりに、新しいデータアクセスオブジェクト (DAO) クラスを使用する場合は、代わりに [CDaoException](../../mfc/reference/cdaoexception-class.md) を使用してください。 すべての DAO クラス名は、プレフィックスとして "CDao" を持ちます。 詳細については、記事「 [概要: データベースプログラミング](../../data/data-access-programming-mfc-atl.md)」を参照してください。

例外は、データソースやネットワーク i/o エラーなど、プログラムの制御外の条件に関連する異常な実行のケースです。 通常、プログラムを実行したときに発生する可能性があるエラーは、例外とは見なされません。

これらのオブジェクトには、 **CATCH** 式のスコープ内でアクセスできます。 グローバル関数を使用して、独自のコードからオブジェクトをスローすることもでき `CDBException` `AfxThrowDBException` ます。

一般的な例外処理、またはオブジェクトの詳細については、 `CDBException` 「 [例外処理 (MFC)](../../mfc/exception-handling-in-mfc.md) 」および「 [例外: データベース例外](../../mfc/exceptions-database-exceptions.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>要件

**ヘッダー:** afxdb.h

## <a name="cdbexceptionm_nretcode"></a><a name="m_nretcode"></a> CDBException:: m_nRetCode

ODBC のアプリケーションプログラミングインターフェイス (API) 関数によって返される RETCODE 型の ODBC エラーコードを格納します。

### <a name="remarks"></a>解説

この型には、ODBC で定義されている SQL プレフィックスのコードと、データベースクラスで定義された AFX_SQL プレフィックスが付いたコードが含まれます。 の場合 `CDBException` 、このメンバーには次の値のいずれかが含まれます。

- またはの呼び出しのドライバー AFX_SQL_ERROR_API_CONFORMANCE、 `CDatabase::OpenEx` `CDatabase::Open` 必要な ODBC API の準拠レベル 1 (SQL_OAC_LEVEL1) に準拠していません。

- データソースへの AFX_SQL_ERROR_CONNECT_FAIL 接続に失敗しました。 `CDatabase`レコードセットコンストラクターに NULL ポインターを渡し、その後、失敗したに基づいて接続を作成しようとし `GetDefaultConnect` ました。

- のストレージを提供した数よりも多くのデータを要求した AFX_SQL_ERROR_DATA_TRUNCATED。 またはデータ型に対して提供されるデータストレージを増やす方法の詳細につい `CString` ては、 `CByteArray` `nMaxLength` 「マクロとグローバル」の [RFX_Text](record-field-exchange-functions.md#rfx_text) と [RFX_Binary](record-field-exchange-functions.md#rfx_binary) の引数を参照してください。

- ダイナセットの要求に対する呼び出しが `CRecordset::Open` 失敗した AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED ます。 このドライバーでは、ダイナセットはサポートされていません。

- テーブルを開こうとした AFX_SQL_ERROR_EMPTY_COLUMN_LIST (または、指定した内容をプロシージャ呼び出しまたは **SELECT** ステートメントとして識別できませんでした)、レコードフィールドエクスチェンジ (RFX) 関数呼び出しで、オーバーライド内の列が識別されませんでした `DoFieldExchange` 。

- オーバーライド内の RFX 関数の型が、 `DoFieldExchange` レコードセットの列のデータ型と互換性がありません AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH。

- `CRecordset::Update`以前に `CRecordset::AddNew` またはを呼び出さずにを呼び出した AFX_SQL_ERROR_ILLEGAL_MODE `CRecordset::Edit` 。

- ODBC ドライバーでロックがサポートされていないため、更新用のレコードのロック要求を処理できませんでした AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED。

- `CRecordset::Update` `Delete` 一意のキーを持たないテーブルに対してまたはを呼び出した AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED、複数のレコードが変更されました。

- 以前に削除されたレコードを編集または削除しようとした AFX_SQL_ERROR_NO_CURRENT_RECORD。 削除後に、新しい現在のレコードまでスクロールする必要があります。

- ODBC ドライバーで位置指定更新がサポートされていないため、ダイナセットの要求を処理できませんでした。 AFX_SQL_ERROR_NO_POSITIONED_UPDATES

- `CRecordset::Update`またはを呼び出した AFX_SQL_ERROR_NO_ROWS_AFFECTED `Delete` 、操作が開始された時点でレコードが見つからなくなりました。

- AFX_SQL_ERROR_ODBC_LOAD_FAILED ODBC.DLL の読み込みに失敗しました。この DLL が見つからないか、読み込めませんでした。 このエラーは致命的なエラーです。

- レベル2に準拠した ODBC ドライバーが必要であるため、ダイナセットに対する要求を満たす AFX_SQL_ERROR_ODBC_V2_REQUIRED できませんでした。

- データソースで後方スクロールがサポートされていないため、スクロールしようとしても失敗し AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY。

- スナップショットの要求に対する呼び出しが `CRecordset::Open` 失敗した AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED ます。 スナップショットはドライバーでサポートされていません。 (これは、ODBC カーソルライブラリ ODBCCURS.DLL が存在しない場合にのみ発生します)。

- またはの呼び出しのドライバー AFX_SQL_ERROR_SQL_CONFORMANCE、 `CDatabase::OpenEx` `CDatabase::Open` 必要な ODBC SQL 準拠レベル "Minimum" (SQL_OSC_MINIMUM) に準拠していません。

- AFX_SQL_ERROR_SQL_NO_TOTAL ODBC ドライバーがデータ値の合計サイズを指定できませんでした `CLongBinary` 。 グローバルメモリブロックを事前に割り当てられなかったため、操作に失敗した可能性があります。

- 読み取り専用のレコードセットを更新しようとした AFX_SQL_ERROR_RECORDSET_READONLY、またはデータソースが読み取り専用です。 レコードセットまたは関連付けられているオブジェクトでは、更新操作を実行できません `CDatabase` 。

- 関数を SQL_ERROR できませんでした。 ODBC 関数によって返されるエラーメッセージ `SQLError` は、データメンバーに格納され `m_strError` ます。

- 無効な環境ハンドル、接続ハンドル、またはステートメントハンドルが原因で SQL_INVALID_HANDLE 関数が失敗しました。 これは、プログラミングエラーを示します。 ODBC 関数からは、追加情報を利用できません `SQLError` 。

SQL プレフィックスの付いたコードは、ODBC で定義されています。 AFX プレフィックスが付けられたコードは、AFXDB.H で定義されています。H で見つかりました。

## <a name="cdbexceptionm_strerror"></a><a name="m_strerror"></a> CDBException:: m_strError

例外の原因となったエラーを説明する文字列を格納します。

### <a name="remarks"></a>解説

文字列は、数字の語句でエラーを記述します。 詳細と例については、「」を参照してください `m_strStateNativeOrigin` 。

## <a name="cdbexceptionm_strstatenativeorigin"></a><a name="m_strstatenativeorigin"></a> CDBException:: m_strStateNativeOrigin

例外の原因となったエラーを説明する文字列を格納します。

### <a name="remarks"></a>解説

文字列の形式は "状態:% s、ネイティブ:% ld、オリジン:% s" です。ここで、書式コードは順に、次に示す値に置き換えられます。

- SQLSTATE。 ODBC 関数の *Szsqlstate* パラメーターで返される5文字のエラーコードを含む、null で終わる文字列 `SQLError` です。 SQLSTATE 値については、 *Odbc プログラマーリファレンス* の付録 a 「 [odbc エラーコード](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes)」を参照してください。 例: "S0022"。

- 関数の *Pfのエラー* パラメーターに返される、データソースに固有のネイティブエラーコード `SQLError` 。 例: 207。

- 関数の *Szerrormsg* パラメーターで返されるエラーメッセージのテキスト `SQLError` 。 このメッセージは、複数のかっこで囲まれた名前で構成されます。 ソースからユーザーにエラーが渡されると、各 ODBC コンポーネント (data source、driver、Driver Manager) に独自の名前が付加されます。 この情報は、エラーの発生元を特定するのに役立ちます。 例: [Microsoft] [ODBC SQL Server Driver] [SQL Server]

フレームワークはエラー文字列を解釈し、そのコンポーネントをに格納します。に複数 `m_strStateNativeOrigin` `m_strStateNativeOrigin` のエラーの情報が含まれている場合、エラーは改行で区切られます。 このフレームワークにより、英数字のエラーテキストがに格納され `m_strError` ます。

この文字列を構成するために使用されるコードの詳細については、 *ODBC プログラマーリファレンス* の「 [SQLError](/sql/odbc/reference/syntax/sqlerror-function)関数」を参照してください。

### <a name="example"></a>例

ODBC: "State: S0022, Native: 207, Origin: \[ Microsoft] \[ ODBC SQL Server Driver] \[ SQL Server] 無効な列名 ' ColName '"

`m_strStateNativeOrigin`: "State: S0022, Native: 207, Origin: \[ Microsoft] \[ ODBC SQL Server Driver] \[ SQL Server]"

`m_strError`: "無効な列名 ' ColName '"

## <a name="see-also"></a>関連項目

[CException クラス](../../mfc/reference/cexception-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDatabase クラス](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange クラス](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset:: Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::D e)](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException クラス](../../mfc/reference/cexception-class.md)
