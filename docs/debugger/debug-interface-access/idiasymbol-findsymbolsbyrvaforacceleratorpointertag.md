---
title: "IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Erstellen eines entsprechenden Tagwert angegeben, gibt diese Methode eine Enumeration von Symbolen zurück, die in dieser Stubfunktion an einer angegebenen relativen virtuellen Adresse enthalten sind.  
  
## Syntax  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### Parameter  
 `tagValue`  
 \[\] werden in der Zeigertagwert, für den das pointee Symbol aufzeichnet, gefunden.  
  
 `rva`  
 \[\] in das rva, das verwendet wird, um die Symbole zu filtern, die zur pointee Variable mit dem angegebenen Tagwert entsprechen.  
  
 `ppResult`  
 \[out\] Ein Zeiger auf einen `IDiaEnumSymbols`\-Schnittstellenzeiger, der mit dem Ergebnis initialisiert wird.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Rufen Sie diese Methode nur für eine `IDiaSymbol`\-Schnittstelle an, die einer Zugriffstastenstubfunktion entspricht.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)