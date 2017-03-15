---
title: "IDiaEnumSymbols | Microsoft Docs"
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
  - "IDiaEnumSymbols-Schnittstelle"
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaEnumSymbols
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Listet die verschiedenen Symbole auf, die in der Datenquelle enthalten sind.  
  
## Syntax  
  
```  
IDiaEnumSymbols : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaEnumSymbols`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaEnumSymbols::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Ruft die `IEnumVARIANT Interface`\-Version dieses Enumerators ab.|  
|[IDiaEnumSymbols::get\_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Ruft die Anzahl der Symbole ab.|  
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Ruft ein Symbol mithilfe eines Indexes ab.|  
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Ruft eine angegebene Anzahl von Symbolen in der Enumerationsfolge ab.|  
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Überspringt eine angegebene Anzahl von Symbolen in der Enumerationsfolge.|  
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
  
## Hinweise  
 Diese Schnittstelle stellt die Symbole, die von einem bestimmten Symboltyp, z. B. gruppiert werden, `SymTagUDT` \) oder benutzerdefinierte Typen \( `SymTagBaseClass`.  Um mit den Symbolen, die durch Adresse gruppiert werden, verwenden Sie die [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)\-Schnittstelle.  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie die folgenden Methoden aufgerufen:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
-   [IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die `IDiaEnumSymbols`\-Schnittstelle abruft und dann diese Enumeration verwendet, um benutzerdefinierte Typen \(UDT\) aufzulisten.  
  
> [!NOTE]
>  `CDiaBSTR` ist eine Klasse, die `BSTR` behandelt und automatisch durchgeführt wird, die die Zeichenfolge freigeben, wenn die Instanziierung den Gültigkeitsbereich verlässt.  
  
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
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)