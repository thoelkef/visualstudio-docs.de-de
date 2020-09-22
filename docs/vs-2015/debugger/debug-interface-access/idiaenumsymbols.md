---
title: IDiaEnumSymbols | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols interface
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fae39270cfbbbb93b106de65b3b01210ffc61d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840941"
---
# <a name="idiaenumsymbols"></a>IDiaEnumSymbols
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Listet die verschiedenen Symbole auf, die in der Datenquelle enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaEnumSymbols : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDiaEnumSymbols` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[IDiaEnumSymbols::get__NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Ruft die `IEnumVARIANT Interface` Version dieses Enumerators ab.|  
|[IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Ruft die Anzahl der Symbole ab.|  
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Ruft ein Symbol mithilfe eines Indexes ab.|  
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Ruft eine angegebene Anzahl von Symbolen in der enumerationssequenz ab.|  
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Überspringt eine angegebene Anzahl von Symbolen in einer enumerationssequenz.|  
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle stellt Symbole bereit, die nach einem bestimmten Symboltyp gruppiert sind, z `SymTagUDT` . b. (benutzerdefinierte Typen) oder `SymTagBaseClass` . Verwenden Sie die [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) -Schnittstelle zum Arbeiten mit Symbolen, die nach Adressen gruppiert sind.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle durch Aufrufen der folgenden Methoden ab:  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie Sie die `IDiaEnumSymbols` -Schnittstelle abrufen und diese Enumeration dann zum Auflisten von benutzerdefinierten Typen (User-Defined Types, UDTs) verwenden.  
  
> [!NOTE]
> `CDiaBSTR` ist eine Klasse, die einen umschließt `BSTR` und automatisch die Freigabe der Zeichenfolge behandelt, wenn die Instanziierung den Gültigkeitsbereich verlässt.  
  
```cpp#  
void ShowUDTs(IDiaSymbol *pGlobals)  
{  
    CComPtr<IDiaEnumSymbols> pEnum;  
    CComPtr<IDiaSymbol> pSymbol;  
    HRESULT hr;  
  
    hr = pGlobals->findChildren(SymTagUDT,  
                                NULL,  
                                nsfCaseInsensitive | nsfUndecoratedName,  
                                &pEnum);  
    if (hr == S_OK)  
    {  
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR name;  
            if ( pSymbol->get_name( &name ) != S_OK )  
                Fatal( "get_name" );  
            printf( "Found UDT: %ws\n", name );  
            pSymbol = 0;  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSourceFile:: get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
