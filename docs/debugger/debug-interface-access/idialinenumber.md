---
title: "IDiaLineNumber | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaLineNumber-Schnittstelle"
ms.assetid: 1071f7d0-1f8c-4384-933f-c49c7eb930bd
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaLineNumber
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Greift auf Informationen, die den Prozess der Zuordnung einer Byteblock Bild von Text in einer Quelldatei Zeilennummer für beschreibt.  
  
## Syntax  
  
```  
IDiaLineNumber : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaLineNumber`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaLineNumber::get\_compiland](../../debugger/debug-interface-access/idialinenumber-get-compiland.md)|Ruft einen Verweis auf das Symbol für die Kompiliereinheit ab, die die Bytes Bild von Text beitrug.|  
|[IDiaLineNumber::get\_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)|Ruft einen Verweis auf die Quelldatei Objekt ab.|  
|[IDiaLineNumber::get\_lineNumber](../../debugger/debug-interface-access/idialinenumber-get-linenumber.md)|Ruft die Zeilennummer in der Quelldatei ab.|  
|[IDiaLineNumber::get\_lineNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-linenumberend.md)|Die 1\-basierte Quellzeilen Zahl in der die Anweisungen oder enden Ausdrucks abruft.|  
|[IDiaLineNumber::get\_columnNumber](../../debugger/debug-interface-access/idialinenumber-get-columnnumber.md)|Ruft die Spaltennummer ab, in der der Ausdruck oder die Anweisung begonnen wird.|  
|[IDiaLineNumber::get\_columnNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-columnnumberend.md)|Die Spaltennummer in der die Ausdrucks\- oder Anweisung beendet wird.|  
|[IDiaLineNumber::get\_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)|Ruft den Teil der Speicheradresse Abschnitts ab, in der ein Block beginnt.|  
|[IDiaLineNumber::get\_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)|Ruft den Offset Teil der Speicheradresse ab, in der ein Block beginnt.|  
|[IDiaLineNumber::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idialinenumber-get-relativevirtualaddress.md)|Ruft die relative virtuelle Adresse des Bildes \(RVA\) eines Blocks ab.|  
|[IDiaLineNumber::get\_virtualAddress](../../debugger/debug-interface-access/idialinenumber-get-virtualaddress.md)|Ruft die virtuelle Adresse \(VA\) eines Blocks ab.|  
|[IDiaLineNumber::get\_length](../../debugger/debug-interface-access/idialinenumber-get-length.md)|Ruft die Anzahl der Bytes in einem Block ab.|  
|[IDiaLineNumber::get\_sourceFileId](../../debugger/debug-interface-access/idialinenumber-get-sourcefileid.md)|Ruft einen eindeutigen Bezeichner für eine Quelldatei für die Quelldatei ab, die diese Zeile beitrug.|  
|[IDiaLineNumber::get\_statement](../../debugger/debug-interface-access/idialinenumber-get-statement.md)|Ruft ein Flag ab, das angibt, dass die Zeileninformationen den Anfang einer Anweisung in der Quelle des Programms beschrieben.|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Ruft den eindeutigen Bezeichner der Kompiliereinheit ab, die diese Zeile beitrug.|  
  
## Hinweise  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie die [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md) oder [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)\-Methoden aufgerufen werden.  
  
## Beispiel  
 Die folgende Funktion werden die Zeilennummern an, die in einer Funktion verwendet werden \(dargestellt durch `pSymbol`\).  
  
```cpp#  
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )  
{  
    ULONGLONG length = 0;  
    DWORD     isect  = 0;  
    DWORD     offset = 0;  
  
    pSymbol->get_addressSection( &isect );  
    pSymbol->get_addressOffset( &offset );  
    pSymbol->get_length( &length );  
    if ( isect != 0 && length > 0 )  
    {  
        CComPtr< IDiaEnumLineNumbers > pLines;  
        if ( SUCCEEDED( pSession->findLinesByAddr(  
                                      isect,  
                                      offset,  
                                      static_cast<DWORD>( length ),  
                                      &pLines)  
                      )  
           )  
        {  
            CComPtr< IDiaLineNumber > pLine;  
            DWORD celt      = 0;  
            bool  firstLine = true;  
  
            while ( SUCCEEDED( pLines->Next( 1, &pLine, &celt ) ) &&  
                    celt == 1 )  
            {  
                DWORD offset;  
                DWORD seg;  
                DWORD linenum;  
                CComPtr< IDiaSymbol >     pComp;  
                CComPtr< IDiaSourceFile > pSrc;  
  
                pLine->get_compiland( &pComp );  
                pLine->get_sourceFile( &pSrc );  
                pLine->get_addressSection( &seg );  
                pLine->get_addressOffset( &offset );  
                pLine->get_lineNumber( &linenum );  
                printf( "\tline %d at 0x%x:0x%x\n", linenum, seg, offset );  
                pLine = NULL;  
                if ( firstLine )  
                {  
                    // sanity check  
                    CComPtr< IDiaEnumLineNumbers > pLinesByLineNum;  
                    if ( SUCCEEDED( pSession->findLinesByLinenum(  
                                                  pComp,  
                                                  pSrc,  
                                                  linenum,  
                                                  0,  
                                                  &pLinesByLineNum)  
                                  )  
                       )  
                    {  
                        CComPtr< IDiaLineNumber > pLine;  
                        DWORD celt;  
                        while ( SUCCEEDED( pLinesByLineNum->Next( 1, &pLine, &celt ) ) &&  
                                celt == 1 )  
                        {  
                            DWORD offset;  
                            DWORD seg;  
                            DWORD linenum;  
  
                            pLine->get_addressSection( &seg );  
                            pLine->get_addressOffset( &offset );  
                            pLine->get_lineNumber( &linenum );  
                            printf( "\t\tfound line %d at 0x%x:0x%x\n", linenum, seg, offset );  
                            pLine = NULL;  
                       }  
                    }  
                    firstLine = false;  
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
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)   
 [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)