---
title: 'Idiasession:: Findlinesbylinenum | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByLinenum method
ms.assetid: 76d5622d-9a91-4c2a-a98f-263af5d1daef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d5999febf6e926ef8e9beb365728a3b150e1a38
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56647058"
---
# <a name="idiasessionfindlinesbylinenum"></a>IDiaSession::findLinesByLinenum
Bestimmt die Zeilennummern der Kompiliereinheit, der die Anzahl der angegebenen Zeile in einer Quelldatei in oder in der Nähe liegt.

## <a name="syntax"></a>Syntax

```C++
HRESULT findLinesByLinenum ( 
    IDiaSymbol*           compiland,
    IDiaSourceFile*       file,
    DWORD                 linenum,
    DWORD                 column,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parameter
`compiland`

[in] Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das der Kompiliereinheit in die Suche nach den Zeilennummern darstellt. Dieser Parameter darf nicht sein `NULL`.

`file`

[in] Ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) -Objekt, suchen Sie in die Quelldatei darstellt. Dieser Parameter darf nicht sein `NULL`.

`linenum`

[in] Gibt eine 1-basierte Zeilennummer an.

> [!NOTE]
> Sie darf nicht 0 (null) verwenden, um alle Zeilen angeben (verwenden Sie die [idiasession:: Findlines](../../debugger/debug-interface-access/idiasession-findlines.md) Methode, um alle Zeilen zu ermitteln).

`column`

[in] Gibt die Nummer der Spalte an. Verwenden Sie 0 (null), um alle Spalten anzugeben. Eine Spalte ist ein Byteoffset in einer Zeile.

`ppResult`

[out] Gibt eine [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) Objta, die eine Liste mit den Zeilennummern enthält abgerufen.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie eine Quelldatei öffnen, die von dieser Datei beigetragenen Compilands aufzählen und suchen die Zeilennummern in der Quelldatei, in dem jede Kompiliereinheit beginnt.

```C++
void ShowLinesInCompilands(IDiaSession *pSession, LPCOLESTR filename)
{
    IDiaEnumSourceFiles* pEnum;
    IDiaSourceFile*      pFile;
    DWORD                celt;

    pSession->findFile ( NULL, filename, nsFNameExt, &pEnum );
    while ( pEnum->Next ( 1, &pFile, &celt ) == S_OK ) // for each file
    {
        IDiaEnumSymbols* pEnumCompilands;
        IDiaSymbol* pCompiland;

        pFile->get_compilands ( &pEnumCompilands );
        // for each compiland
        while ( pEnumCompilands->Next ( 1, &pCompiland, &celt ) == S_OK )
        {
            IDiaEnumLineNumbers* pEnum;
            // Find first compiland closest to line 1 of the file.
            if (pSession->findLinesByLinenum( pCompiland, pFile, 1, 0, &pEnum ) == S_OK)
            {
                IDiaLineNumber *pLineNumber;
                DWORD lineCount;
                while ( pEnum->Next(1,&pLineNumber,&lineCount) == S_OK)
                {
                    DWORD lineNum;
                    if (pLineNumber->get_line(&lineNum) == S_OK)
                    {
                        printf("compiland starts in source at line number = %lu\n",lineNum);
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Siehe auch
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
