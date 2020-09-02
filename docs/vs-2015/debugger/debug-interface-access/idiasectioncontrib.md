---
title: IDiaSectionContrib | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib interface
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc263d7238166f4f381bac35f0482ca2433f7b33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150478"
---
# <a name="idiasectioncontrib"></a>IDiaSectionContrib
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft Daten ab, die einen Abschnitts Beitrag beschreiben, d. h. ein zusammenhängender Speicherblock, der durch eine kompisierung zum Image beigetragen hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDiaSectionContrib` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaSectionContrib::get_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Ruft einen Verweis auf das compilersymbol ab, das diesen Abschnitt beigetragen hat.|  
|[IDiaSectionContrib::get_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Ruft den Abschnitts Teil der Adresse des Beitrags ab.|  
|[IDiaSectionContrib::get_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Ruft den Offset Teil der Adresse des Beitrags ab.|  
|[IDiaSectionContrib::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-relativevirtualaddress.md)|Ruft die Bild relative virtuelle Adresse (RVA) des Beitrags ab.|  
|[IDiaSectionContrib::get_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Ruft die virtuelle Adresse (VA) des Beitrags ab.|  
|[IDiaSectionContrib::get_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Ruft die Anzahl der Bytes in einem Abschnitt ab.|  
|[IDiaSectionContrib::get_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|Ruft ein Flag ab, das angibt, ob für den Abschnitt nicht genügend Arbeitsspeicher verfügbar ist.|  
|[IDiaSectionContrib::get_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt nicht an der nächsten Speichergrenze aufgefüllt werden soll.|  
|[IDiaSectionContrib::get_code](../../debugger/debug-interface-access/idiasectioncontrib-get-code.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt ausführbaren Code enthält.|  
|[IDiaSectionContrib::get_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt 16-Bit-Code enthält.|  
|[IDiaSectionContrib::get_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt initialisierte Daten enthält.|  
|[IDiaSectionContrib::get_uninitializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt nicht initialisierte Daten enthält.|  
|[IDiaSectionContrib::get_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Ruft ein Flag ab, das angibt, ob ein Abschnitt Kommentare oder ähnliche Informationen enthält.|  
|[IDiaSectionContrib::get_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt entfernt wird, bevor er Teil des in-Memory-Bilds wird.|  
|[IDiaSectionContrib::get_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt ein COMDAT-Datensatz ist.|  
|[IDiaSectionContrib::get_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt verworfen werden kann.|  
|[IDiaSectionContrib::get_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt nicht zwischengespeichert werden kann.|  
|[IDiaSectionContrib::get_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt im Arbeitsspeicher freigegeben werden kann.|  
|[IDiaSectionContrib::get_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt ausführbare Dateien als Code ist.|  
|[IDiaSectionContrib::get_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt gelesen werden kann.|  
|[IDiaSectionContrib::get_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt geschrieben werden kann.|  
|[IDiaSectionContrib::get_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|Ruft die zyklische Redundanz Überprüfung (CRC) der Daten im-Abschnitt ab.|  
|[IDiaSectionContrib::get_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Ruft den CRC der Verschiebungs Informationen für den Abschnitt ab.|  
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Ruft den Compilerbezeichner für den Abschnitt ab.|  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird durch Aufrufen der [idiaenumsectioncontrisb:: Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) -Methode und der [idiaenumsectioncontrisb:: Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md) -Methode abgerufen. Ein Beispiel für das Abrufen der-Schnittstelle finden Sie in der [idiaenumsectioncontrisb](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) -Schnittstelle `IDiaSectionContrib` .  
  
## <a name="example"></a>Beispiel  
 Diese Funktion zeigt die Adresse jedes Abschnitts sowie alle zugehörigen Symbole an. Informationen dazu, wie die Schnittstelle abgerufen wird, finden Sie unter [idiaenumsectioncontrisb](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) -Schnittstelle `IDiaSectionContrib` .  
  
```cpp#  
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
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [Idiaenumsectioncontrisb:: Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)
