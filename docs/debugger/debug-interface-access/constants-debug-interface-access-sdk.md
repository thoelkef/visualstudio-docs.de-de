---
title: "Konstanten (Debug Interface Access SDK) | Microsoft Docs"
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
  - "Konstanten, DIA-SDK"
  - "DIA-SDK, Konstanten"
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Konstanten (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Diese Zeichenfolgenkonstanten können verwendet werden, um unterschiedliche Abschnitte einer Debugkonfiguration Datei der Datenbank des Programms \(PDB\) vom DIA SDK zu identifizieren.  
  
## Konstanten  
 Folgende wird als C\/C\+\+\-Makros deklariert.  
  
|Makro|Wert|  
|-----------|----------|  
|`DiaTable_Symbols`|Symbole“ L "|  
|`DiaTable_Sections`|L " Bereiche“|  
|`DiaTable_SrcFiles`|SourceFiles“ L "|  
|`DiaTable_LineNums`|LineNumbers“ L "|  
|`DiaTable_SegMap`|SegmentMap“ L "|  
|`DiaTable_Dbg`|Dbg“ L "|  
|`DiaTable_InjSrc`|InjectedSource“ L "|  
|`DiaTable_FrameData`|FrameData“ L "|  
  
## Beispiel  
 Im Folgenden ein Beispiel für die Verwendung eines dieser Symbole:  
  
```cpp#  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## Anforderungen  
 Header: dia2.h  
  
## Siehe auch  
 [Verweis](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)