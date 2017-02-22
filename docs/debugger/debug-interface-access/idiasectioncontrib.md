---
title: "IDiaSectionContrib | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSectionContrib-Schnittstelle"
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Daten ab, die über den beitrag Abschnitts beschrieben. h. einen zusammenhängenden Speicherblock, der dem Bild von einer Kompiliereinheit bereitgestellt wird.  
  
## Syntax  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaSectionContrib`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaSectionContrib::get\_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Ruft einen Verweis auf das Symbol Kompiliereinheits ab, das diesen Abschnitt beitrug.|  
|[IDiaSectionContrib::get\_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Ruft den Teil der Adresse des Abschnitts Nachbedingung ab.|  
|[IDiaSectionContrib::get\_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Ruft den Offset Teil der Adresse des Nachbedingung ab.|  
|[IDiaSectionContrib::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-relativevirtualaddress.md)|Ruft die relative virtuelle Adresse \(RVA\) des Bilds in der Nachbedingung ab.|  
|[IDiaSectionContrib::get\_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Ruft die virtuelle Adresse \(VA\) des Nachbedingung ab.|  
|[IDiaSectionContrib::get\_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Ruft die Anzahl der Bytes in einem Abschnitt ab.|  
|[IDiaSectionContrib::get\_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt nicht geblättertes aufgrund von ungenügendem Arbeitsspeicher erfolgen kann.|  
|[IDiaSectionContrib::get\_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Ruft ein Flag ab, das angibt, ob der Grenze Speicherplatz zur nächsten Abschnitt nicht aufgefüllt werden soll.|  
|[IDiaSectionContrib::get\_code](../../debugger/debug-interface-access/idiasectioncontrib-get-code.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt ausführbaren Code enthält.|  
|[IDiaSectionContrib::get\_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt 16\-Bit\-Code enthält.|  
|[IDiaSectionContrib::get\_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt enthält initialisierte Daten.|  
|[IDiaSectionContrib::get\_uninitializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt nicht initialisierte Daten enthält.|  
|[IDiaSectionContrib::get\_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Ruft ein Flag ab, das angibt, ob ein Abschnitt Kommentare oder ähnliche Informationen enthält.|  
|[IDiaSectionContrib::get\_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Ruft ein Flag ab, das angibt, ob der Bereich entfernt wird, bevor er Teil des Bildes im Arbeitsspeicher ausgeführt wird.|  
|[IDiaSectionContrib::get\_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|Ruft ein Flag ab, das angibt, ob es sich bei dem Abschnitt ein COMDAT\-Datensatz ist.|  
|[IDiaSectionContrib::get\_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt verworfen werden kann.|  
|[IDiaSectionContrib::get\_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt nicht zwischengespeichert werden kann.|  
|[IDiaSectionContrib::get\_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|Ruft ein Flag ab, das angibt, ob der Bereich im Arbeitsspeicher freigegeben werden kann.|  
|[IDiaSectionContrib::get\_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|Ruft ein Flag ab, das angibt, ob der Bereich als Code ausgeführt werden kann.|  
|[IDiaSectionContrib::get\_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|Ruft ein Flag ab, das angibt, ob der Abschnitt gelesen werden kann.|  
|[IDiaSectionContrib::get\_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|Ruft ein Flag ab, das angibt, ob der Bereich geschrieben werden kann.|  
|[IDiaSectionContrib::get\_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|Ruft die zyklische Blockprüfung \(CRC\) der Daten im Abschnitt ab.|  
|[IDiaSectionContrib::get\_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Ruft das Verschieben der CRC für den Abschnitt ab.|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Ruft den Bezeichner für den Kompiliereinheits Abschnitt ab.|  
  
## Hinweise  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird abgerufen, indem die [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) und [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)\-Methoden aufgerufen werden.  Zeigen Sie die [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)\-Schnittstelle als Beispiel für die `IDiaSectionContrib`\-Schnittstelle abzurufen.  
  
## Beispiel  
 Diese Funktion wird die Adresse eines Abschnitts zusammen mit allen zugeordneten Symbolen angezeigt.  Zeigen Sie die [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)\-Schnittstelle, um zu sehen, wie die `IDiaSectionContrib`\-Schnittstelle ermittelt wird.  
  
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
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)