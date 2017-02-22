---
title: "IDiaSegment | Microsoft Docs"
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
  - "IDiaSegment-Schnittstelle"
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSegment
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wird von Daten aus der Nummer des Abschnitts in Segmenten des Adressbereichs.  
  
## Syntax  
  
```  
IDiaSegment : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaSegment`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaSegment::get\_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Ruft die Segmentnummer ab.|  
|[IDiaSegment::get\_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Ruft den Offset in Segmenten ab, in dem der Bereich beginnt.|  
|[IDiaSegment::get\_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Ruft die Anzahl von Bytes im Segment ab.|  
|[IDiaSegment::get\_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|Ruft ein Flag ab, das angibt, ob das Segment gelesen werden kann.|  
|[IDiaSegment::get\_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|Ruft ein Flag ab, das angibt, ob das Segment geändert werden kann.|  
|[IDiaSegment::get\_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|Ruft ein Flag ab, das angibt, ob das Segment ausführbar ist.|  
|[IDiaSegment::get\_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Ruft die Nummer des Abschnitts ab, die diesem Segment zuordnet.|  
|[IDiaSegment::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Ruft die relative virtuelle Adresse \(RVA\) vom Anfang des Abschnitts ab.|  
|[IDiaSegment::get\_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Ruft die virtuelle Adresse \(VA\) vom Anfang des Abschnitts ab.|  
  
## Hinweise  
 Da das DIA SDK bereits ausgeführt wird, Übersetzungen im Abschnitt zu den relativen virtuellen Adressen, die meisten Anwendungen verwenden nicht die Informationen in der Segment aus zugeordnet.  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie die [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md) oder [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)\-Methoden aufgerufen werden.  Weitere Informationen finden Sie im Beispiel für Details.  
  
## Beispiel  
 Diese Funktion wird die Adresse aller Segmente in einer Tabelle und im nächsten Symbol an.  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSegments ),  
                               (void**)&pSegments )  
                  )  
       )  
    {  
        CComPtr<IDiaSegment> pSegment;  
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&  
                celt == 1 )  
        {  
            DWORD rva;  
            DWORD seg;  
  
            pSegment->get_addressSection( &seg );  
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )  
            {  
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );  
                pSegment = NULL;  
  
                CComPtr<IDiaSymbol> pSym;  
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
                {  
                    CDiaBSTR name;  
                    DWORD    tag;  
  
                    pSym->get_symTag( &tag );  
                    pSym->get_name( &name );  
                    printf( "\tClosest symbol: %ws (%ws)\n",  
                            name != NULL ? name : L"",  
                            szTags[ tag ] );  
                }  
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
 [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)   
 [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)