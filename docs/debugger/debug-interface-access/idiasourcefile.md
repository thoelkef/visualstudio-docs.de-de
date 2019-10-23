---
title: IDiaSourceFile | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile interface
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08334c59ea061cee1618c76aa61ec6aa6fb8d7d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741774"
---
# <a name="idiasourcefile"></a>IDiaSourceFile
Stellt eine Quelldatei dar.

## <a name="syntax"></a>Syntax

```
IDiaSourceFile : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
In der folgenden Tabelle sind die Methoden von `IDiaSourceFile` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaSourceFile::get_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Ruft einen einfachen ganzzahligen Schlüsselwert ab, der für dieses Bild eindeutig ist.|
|[IDiaSourceFile::get_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Ruft den Namen der Quelldatei ab.|
|[IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Ruft den Prüfsummen Datentyp ab.|
|[IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Ruft einen Enumerator der Kompilierungen mit Zeilennummern ab, die auf diese Datei verweisen.|
|[IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Ruft die Prüfsumme Bytes ab.|

## <a name="remarks"></a>Hinweise

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Rufen Sie diese Schnittstelle durch Aufrufen der [IDiaEnumSourceFiles:: Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) -Methode oder der [IDiaEnumSourceFiles:: Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) -Methode ab. Weitere Informationen finden Sie im Beispiel.

## <a name="example"></a>Beispiel
Diese Funktion zeigt die Namen aller Quelldateien an, die zur angegebenen Tabelle beitragen.

```C++
void ShowSourceFiles(IDiaTable *pTable)
{
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;
    if ( SUCCEEDED( pTable->QueryInterface(
                                _uuidof( IDiaEnumSourceFiles ),
                               (void**)&pSourceFiles )
                  )
       )
    {
        CComPtr<IDiaSourceFile> pSourceFile;
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&
                celt == 1 )
        {
            CDiaBSTR fileName;
            if ( pSourceFile->get_fileName( &fileName) == S_OK )
            {
                printf( "file name: %ws\n", fileName );
            }
            pSourceFile = NULL;
        }
    }
}
```

## <a name="requirements"></a>Anforderungen
Header: Dia2.h

Bibliothek: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)
- [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)
- [IDiaLineNumber::get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)
- [IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)
- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
