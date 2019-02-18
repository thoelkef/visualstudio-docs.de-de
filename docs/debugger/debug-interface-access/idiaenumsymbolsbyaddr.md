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
ms.openlocfilehash: 7ec61145d51ba383099d9b08fe0a50db10f97022
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2019
ms.locfileid: "56155616"
---
# <a name="idiaenumsymbolsbyaddr"></a>IDiaEnumSymbolsByAddr
Listet die über die Adresse der verschiedenen Symbole in der Datenquelle.

## <a name="syntax"></a>Syntax

```
IDiaEnumSymbolsByAddr : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Die folgende Tabelle zeigt die Methoden der `IDiaEnumSymbolsByAddr`.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|Positioniert den Enumerator durch eine Suche nach Abschnitts- und Offset.|
|[IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)|Positioniert den Enumerator durch eine Suche durch relative virtuelle Adresse (RVA).|
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|Positioniert den Enumerator durch eine Suche über die virtuelle Adresse (VA).|
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|Ruft die nächste Symbole in der Reihenfolge nach Adresse ab. Aktualisiert die Position des Enumerators durch die Anzahl von Elementen abgerufen.|
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|Ruft die vorherige Symbole in der Reihenfolge nach Adresse ab. Aktualisiert die Position des Enumerators durch die Anzahl von Elementen abgerufen.|
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|Erstellt eine Kopie eines Objekts.|

## <a name="remarks"></a>Hinweise
Diese Schnittstelle bietet nach Adresse angeordneten Symbole. Arbeiten mit Symbolen, die nach Typ gruppiert sind, z. B. `SymTagUDT` (UDT) oder `SymTagBaseClass`, verwenden Sie die [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Rufen Sie diese Schnittstelle durch Aufrufen der [idiasession:: Getsymbolsbyaddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md) Methode.

## <a name="example"></a>Beispiel
Diese Funktion zeigt den Namen und Adresse aller Symbole, geordnet nach relative virtuelle Adresse.

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

Bibliothek: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
[Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)  
[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
