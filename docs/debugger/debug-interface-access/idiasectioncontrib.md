---
title: IDiaSectionContrib | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib interface
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c1fe16951bee79dbda033101043406491d4a56f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991969"
---
# <a name="idiasectioncontrib"></a>IDiaSectionContrib
Abgerufen, die einen Beitrag Abschnitt beschreiben, ein zusammenhängender Speicherblock, also auf das Abbild von einem Kompiliereinheit beigetragenen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaSectionContrib`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaSectionContrib::get_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Ruft einen Verweis auf die Compiland-Symbol, das in diesem Abschnitt beigetragen hat.|  
|[IDiaSectionContrib::get_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Ruft den Teil "Abschnitt" Beteiligung der Adresse ab.|  
|[IDiaSectionContrib::get_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Ruft den Zeitzonenoffset-Teil der Beteiligung der Adresse ab.|  
|[IDiaSectionContrib::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-relativevirtualaddress.md)|Ruft das Bild relative virtuelle Adresse (RVA) des Beitrags ab.|  
|[IDiaSectionContrib::get_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Ruft die virtuelle Adresse (VA) des Beitrags ab.|  
|[IDiaSectionContrib::get_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Ruft die Anzahl der Bytes in einem Abschnitt ab.|  
|[IDiaSectionContrib::get_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|Ruft ein Flag, das angibt, ob der Abschnitt nicht genügend Arbeitsspeicher ausgelagert werden kann.|  
|[IDiaSectionContrib::get_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Ruft ein Flag, der angibt, ob der Abschnitt nicht soll, können Sie auf die nächsten Begrenzung des Arbeitsspeichers aufgefüllt werden ab.|  
|[IDiaSectionContrib::get_code](../../debugger/debug-interface-access/idiasectioncontrib-get-code.md)|Ruft ein Flag, das angibt, ob der Abschnitt ausführbaren Code enthält.|  
|[IDiaSectionContrib::get_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Ruft ein Flag, das angibt, ob der Abschnitt 16-Bit-Code enthält.|  
|[IDiaSectionContrib::get_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|Ruft ein Flag, das angibt, ob der Abschnitt initialisierte Daten enthält.|  
|[IDiaSectionContrib::get_uninitializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata.md)|Ruft ein Flag, das angibt, ob der Abschnitt nicht initialisierte Daten enthält.|  
|[IDiaSectionContrib::get_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Ruft ein Flag, der angibt, ob einen Abschnitt, Kommentare oder ähnliche Informationen enthält ab.|  
|[IDiaSectionContrib::get_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Ruft ein Flag, das angibt, ob der Abschnitt entfernt wird, bevor es Teil des in-Memory-Abbilds durchgeführt wird.|  
|[IDiaSectionContrib::get_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|Ruft ein Flag, das angibt, ob der Bereich einen COMDAT-Datensatz ist.|  
|[IDiaSectionContrib::get_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|Ruft ein Flag, das angibt, ob der Abschnitt nicht verworfen werden kann.|  
|[IDiaSectionContrib::get_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|Ruft ein Flag, das angibt, ob der Abschnitt nicht zwischengespeichert werden kann.|  
|[IDiaSectionContrib::get_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|Ruft ein Flag, das angibt, ob der Abschnitt im Arbeitsspeicher freigegeben werden kann.|  
|[IDiaSectionContrib::get_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|Ruft ein Flag, das angibt, ob der Abschnitt ausführbaren Code ist.|  
|[IDiaSectionContrib::get_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|Ruft ein Flag, das angibt, ob der Abschnitt gelesen werden kann.|  
|[IDiaSectionContrib::get_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|Ruft ein Flag, das angibt, ob der Abschnitt geschrieben werden kann.|  
|[IDiaSectionContrib::get_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|Ruft die zyklische redundanzprüfung (CRC) der Daten in den Abschnitt ab.|  
|[IDiaSectionContrib::get_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Ruft die CRC-Wert für die Umsetzungsinformationen für den Abschnitt ab.|  
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Ruft den Compiland-Bezeichner für den Abschnitt ab.|  
  
## <a name="remarks"></a>Anmerkungen  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird abrufen durch Aufrufen der [idiaenumsectioncontribs:: Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) und [idiaenumsectioncontribs:: Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md) Methoden. Finden Sie unter den [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) Schnittstelle für ein Beispiel zum Abrufen von der `IDiaSectionContrib` Schnittstelle.  
  
## <a name="example"></a>Beispiel  
 Diese Funktion wird die Adresse jedes Abschnitts zusammen mit zugehörigen Symbole angezeigt. Finden Sie unter den [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) Schnittstelle finden Sie unter wie die `IDiaSectionContrib` Schnittstelle abgerufen wird.  
  
```C++  
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)  
{  
    if (pSecContrib != NULL && pSession != NULL)  
    {  
        DWORD rva;  
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )  
        {  
            printf( "\taddr: 0x%.8X", rva );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                        name != NULL ? name : L"",  
                        szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
        else  
        {  
            DWORD isect;  
            DWORD offset;  
            pSecContrib->get_addressSection( &isect );  
            pSecContrib->get_addressOffset( &offset );  
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( SUCCEEDED( psession->findSymbolByAddr(  
                                              isect,  
                                              offset,  
                                              SymTagNull,  
                                              &pSym )  
                          )  
               )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                    name != NULL ? name : L"",  
                    szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)