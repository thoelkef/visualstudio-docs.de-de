---
title: IDiaEnumSymbolsByAddr | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsbyAddr interface
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d8cddaa39635be534e2247b48a370ed88b29ab4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743816"
---
# <a name="idiaenumsymbolsbyaddr"></a>IDiaEnumSymbolsByAddr
Listet die verschiedenen in der Datenquelle enthaltenen Symbole auf.

## <a name="syntax"></a>Syntax

```
IDiaEnumSymbolsByAddr : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
In der folgenden Tabelle sind die Methoden von `IDiaEnumSymbolsByAddr` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|Positioniert den Enumerator, indem eine Suche nach Abschnitt und Offset durchgeführt wird.|
|[IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)|Positioniert den Enumerator, indem eine Suche durch eine relative virtuelle Adresse (RVA) durchgeführt wird.|
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|Positioniert den Enumerator, indem eine Suche nach einer virtuellen Adresse (VA) durchgeführt wird.|
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|Ruft die nächsten Symbole in der Order by-Adresse ab. Aktualisiert die enumeratorposition nach der Anzahl der abgerufenen Elemente.|
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|Ruft die vorherigen Symbole in der Order by-Adresse ab. Aktualisiert die enumeratorposition nach der Anzahl der abgerufenen Elemente.|
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|Erstellt eine Kopie eines Objekts.|

## <a name="remarks"></a>Hinweise
Diese Schnittstelle stellt Symbole gruppiert nach Adresse bereit. Zum Arbeiten mit Symbolen, die nach Typ gruppiert sind (z. b. `SymTagUDT` (benutzerdefinierter Typ) oder `SymTagBaseClass`, verwenden Sie die [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) -Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Rufen Sie diese Schnittstelle durch Aufrufen der [IDiaSession:: getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md) -Methode ab.

## <a name="example"></a>Beispiel
Diese Funktion zeigt den Namen und die Adresse aller von der relativen virtuellen Adresse bestellten Symbole an.

```C++
void ShowSymbolsByAddress(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSymbolsByAddr> pEnumByAddr;
    if ( FAILED( psession->getSymbolsByAddr( &pEnumByAddr ) ) )
    {
        Fatal( "getSymbolsByAddr" );
    }
    CComPtr<IDiaSymbol> pSym;
    if ( FAILED( pEnumByAddr->symbolByAddr( 1, 0, &pSym ) ) )
    {
        Fatal( "symbolByAddr" );
    }
    DWORD rvaLast = 0;
    if ( pSym->get_relativeVirtualAddress( &rvaLast ) == S_OK )
    {
        pSym = 0;
        if ( FAILED( pEnumByAddr->symbolByRVA( rvaLast, &pSym ) ) )
        {
            Fatal( "symbolByAddr" );
        }
        printf( "Symbols in order\n" );
        do
        {
            CDiaBSTR name;
            if ( pSym->get_name( &name ) != S_OK )
            {
                printf( "\t0x%08X (%ws) <no name>\n", rvaLast );
            }
            else
            {
                printf( "\t0x%08X %ws\n", rvaLast, name );
            }
            pSym = 0;
            celt = 0;
            if ( FAILED( hr = pEnumByAddr->Next( 1, &pSym, &celt ) ) )
            {
                break;
            }
        } while ( celt == 1 );
    }
}
```

## <a name="requirements"></a>Anforderungen
Header: Dia2.h

Bibliothek: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
