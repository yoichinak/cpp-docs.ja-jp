---
description: '詳細情報: CAtlFile クラス'
title: CAtlFile クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
ms.openlocfilehash: d38ab3ad894a589fb59fe03691d6c764414cc8b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147395"
---
# <a name="catlfile-class"></a>CAtlFile クラス

このクラスは、Windows ファイル処理 API のシンラッパーを提供します。

> [!IMPORTANT]
> このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```cpp
class CAtlFile : public CHandle
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlFile::CAtlFile](#catlfile)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlFile:: Create](#create)|ファイルを作成または開くには、このメソッドを呼び出します。|
|[CAtlFile:: Flush](#flush)|ファイルのバッファーをクリアし、バッファー内のすべてのデータがファイルに書き込まれるようにするには、このメソッドを呼び出します。|
|[CAtlFile:: GetOverlappedResult](#getoverlappedresult)|このメソッドを呼び出して、ファイルのオーバーラップ操作の結果を取得します。|
|[CAtlFile::GetPosition](#getposition)|ファイルから現在のファイルポインターの位置を取得するには、このメソッドを呼び出します。|
|[CAtlFile:: GetSize](#getsize)|ファイルのサイズ (バイト単位) を取得するには、このメソッドを呼び出します。|
|[CAtlFile::LockRange](#lockrange)|他のプロセスがアクセスできないように、ファイル内の領域をロックするには、このメソッドを呼び出します。|
|[CAtlFile:: Read](#read)|ファイルポインターによって示される位置から開始して、ファイルからデータを読み取るには、このメソッドを呼び出します。|
|[CAtlFile:: Seek](#seek)|ファイルのファイルポインターを移動するには、このメソッドを呼び出します。|
|[CAtlFile:: SetSize](#setsize)|ファイルのサイズを設定するには、このメソッドを呼び出します。|
|[CAtlFile::UnlockRange](#unlockrange)|ファイルの領域をロック解除するには、このメソッドを呼び出します。|
|[CAtlFile:: Write](#write)|ファイルポインターによって示される位置から開始して、ファイルにデータを書き込むには、このメソッドを呼び出します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAtlFile:: m_pTM](#m_ptm)|オブジェクトへのポインター `CAtlTransactionManager`|

## <a name="remarks"></a>解説

このクラスは、ファイル処理のニーズが比較的単純な場合に使用しますが、MFC の依存関係を含めずに、Windows API よりも多くの抽象化が必要です。

## <a name="inheritance-hierarchy"></a>継承階層

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>要件

**ヘッダー:** atlfile .h

## <a name="catlfilecatlfile"></a><a name="catlfile"></a> CAtlFile::CAtlFile

コンストラクターです。

```cpp
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>パラメーター

*file*<br/>
ファイルオブジェクト。

*hFile*<br/>
ファイルハンドル。

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="remarks"></a>解説

コピーコンストラクターは、ファイルハンドルの所有権を元の `CAtlFile` オブジェクトから新しく構築されたオブジェクトに転送します。

## <a name="catlfilecreate"></a><a name="create"></a> CAtlFile:: Create

ファイルを作成または開くには、このメソッドを呼び出します。

```cpp
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*szFilename*<br/>
ファイル名。

*dwDesiredAccess*<br/>
目的のアクセス。 Windows SDK の [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)の *dwDesiredAccess* を参照してください。

*dwShareMode*<br/>
共有モード。 「 *DwShareMode* 」を参照してください `CreateFile` 。

*Dwの廃棄*<br/>
作成の廃棄。 「」の「 *Dwの廃棄* 」を参照してください `CreateFile` 。

*dwFlagsAndAttributes*<br/>
フラグと属性。 「 *DwFlagsAndAttributes* 」を参照してください `CreateFile` 。

*lpsa*<br/>
セキュリティ属性。 「」の「 *Lpsecurityattributes* 」を参照してください `CreateFile` 。

*hTemplateFile*<br/>
テンプレートファイル。 「 *HTemplateFile* 」を参照してください `CreateFile` 。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>解説

[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)を呼び出して、ファイルを作成または開きます。

## <a name="catlfileflush"></a><a name="flush"></a> CAtlFile:: Flush

ファイルのバッファーをクリアし、バッファー内のすべてのデータがファイルに書き込まれるようにするには、このメソッドを呼び出します。

```cpp
HRESULT Flush() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>解説

[Flushfilebuffers](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers)を呼び出してバッファー内のデータをファイルにフラッシュします。

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a> CAtlFile:: GetOverlappedResult

このメソッドを呼び出して、ファイルのオーバーラップ操作の結果を取得します。

```cpp
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>パラメーター

*pOverlapped*<br/>
オーバーラップされた構造体。 Windows SDK の [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult)の *lpOverlapped* を参照してください。

*dwBytesTransferred*<br/>
転送されたバイト数。 「 *LpNumberOfBytesTransferred* 」を参照してください `GetOverlappedResult` 。

*bWait*<br/>
Wait オプション。 *Bwait* の「」を参照してください `GetOverlappedResult` 。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>解説

[GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult)を呼び出して、ファイルのオーバーラップした操作の結果を取得します。

## <a name="catlfilegetposition"></a><a name="getposition"></a> CAtlFile::GetPosition

現在のファイルポインターの位置を取得するには、このメソッドを呼び出します。

```cpp
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
バイト単位の位置。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>解説

[Setfilepointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)を呼び出して、現在のファイルポインターの位置を取得します。

## <a name="catlfilegetsize"></a><a name="getsize"></a> CAtlFile:: GetSize

ファイルのサイズ (バイト単位) を取得するには、このメソッドを呼び出します。

```cpp
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>パラメーター

*nLen*<br/>
ファイル内のバイト数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>解説

ファイルのサイズ (バイト単位) を取得するために [getfilesize](/windows/win32/api/fileapi/nf-fileapi-getfilesize) 呼び出します。

## <a name="catlfilelockrange"></a><a name="lockrange"></a> CAtlFile::LockRange

他のプロセスがアクセスできないように、ファイル内の領域をロックするには、このメソッドを呼び出します。

```cpp
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
ロックを開始するファイル内の位置。

*nCount*<br/>
ロックするバイト範囲の長さ。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>解説

[LockFile](/windows/win32/api/fileapi/nf-fileapi-lockfile)を呼び出して、ファイル内の領域をロックします。 ファイル内のバイトをロックすると、他のプロセスがそれらのバイトにアクセスできなくなります。 ファイルの複数の領域をロックすることはできますが、重複する領域は許可されません。 [CAtlFile:: UnlockRange](#unlockrange)を使用して領域のロックを解除する場合、バイト範囲は、以前にロックされていた領域と正確に対応している必要があります。 `LockRange` 隣接する領域をマージしません。2つのロックされた領域が隣接している場合は、それぞれを個別にロック解除する必要があります。

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a> CAtlFile:: m_pTM

オブジェクトへのポインター `CAtlTransactionManager` 。

```cpp
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>解説

## <a name="catlfileread"></a><a name="read"></a> CAtlFile:: Read

ファイルポインターによって示される位置から開始して、ファイルからデータを読み取るには、このメソッドを呼び出します。

```cpp
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```

### <a name="parameters"></a>パラメーター

*pBuffer*<br/>
ファイルから読み取られたデータを受け取るバッファーへのポインター。

*nBufSize*<br/>
バイト単位のバッファー サイズ。

*nBytesRead*<br/>
読み取るバイト数。

*pOverlapped*<br/>
オーバーラップされた構造体。 Windows SDK の「 *lpOverlapped* in [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile) 」を参照してください。

*Pfn補完ルーチン*<br/>
完了ルーチン。 Windows SDK の「 [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex)の *lp補完ルーチン*」を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>解説

最初の3つのフォームは、 [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile)を呼び出します。これは、ファイルからデータを読み取る最後の [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) です。 ファイルポインターを移動するには、 [CAtlFile:: Seek](#seek) を使用します。

## <a name="catlfileseek"></a><a name="seek"></a> CAtlFile:: Seek

ファイルのファイルポインターを移動するには、このメソッドを呼び出します。

```cpp
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>パラメーター

*nOffset*<br/>
*Dwfrom* によって指定された開始点からのオフセット。

*dwFrom*<br/>
開始点 (FILE_BEGIN、FILE_CURRENT、または FILE_END)。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>解説

[Setfilepointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)を呼び出して、ファイルポインターを移動します。

## <a name="catlfilesetsize"></a><a name="setsize"></a> CAtlFile:: SetSize

ファイルのサイズを設定するには、このメソッドを呼び出します。

```cpp
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>パラメーター

*nNewLen*<br/>
ファイルの新しい長さ (バイト単位)。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>解説

[Setfilepointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)と[setfilepointer](/windows/win32/api/fileapi/nf-fileapi-setendoffile)を呼び出して、ファイルのサイズを設定します。 返されると、ファイルポインターがファイルの末尾に配置されます。

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a> CAtlFile::UnlockRange

ファイルの領域をロック解除するには、このメソッドを呼び出します。

```cpp
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
ロック解除を開始するファイル内の位置。

*nCount*<br/>
ロックを解除するバイト範囲の長さ。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>解説

[UnlockFile](/windows/win32/api/fileapi/nf-fileapi-unlockfile)を呼び出して、ファイルの領域をロック解除します。

## <a name="catlfilewrite"></a><a name="write"></a> CAtlFile:: Write

ファイルポインターによって示される位置から開始して、ファイルにデータを書き込むには、このメソッドを呼び出します。

```cpp
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```

### <a name="parameters"></a>パラメーター

*pBuffer*<br/>
ファイルに書き込まれるデータを格納しているバッファー。

*nBufSize*<br/>
バッファーから転送されるバイト数。

*pOverlapped*<br/>
オーバーラップされた構造体。 Windows SDK の「 *lpOverlapped* in [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) 」を参照してください。

*Pfn補完ルーチン*<br/>
完了ルーチン。 Windows SDK の「[た writefileex](/windows/win32/api/fileapi/nf-fileapi-writefileex)の *lp補完ルーチン*」を参照してください。

*書き込まれた pnbytes*<br/>
書き込まれたバイト数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>解説

最初の3つのフォームでは、 [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile)を呼び出します。最後に [た writefileex](/windows/win32/api/fileapi/nf-fileapi-writefileex) を呼び出して、ファイルにデータを書き込みます。 ファイルポインターを移動するには、 [CAtlFile:: Seek](#seek) を使用します。

## <a name="see-also"></a>関連項目

[Marquee サンプル](../../overview/visual-cpp-samples.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CHandle クラス](../../atl/reference/chandle-class.md)
