---
title: "IDiaSymbol::findSymbolsForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: fb66852c-c5f7-4140-b9fe-20cb4e51a9fe
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::findSymbolsForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt die Anzahl der Zugriffstastenzeigertags in der AMP\-Stubfunktion einer C\+\+\-Datei zurück.  
  
## Syntax  
  
```cpp  
HRESULT findSymbolsForAccleratorPointerTag (   
   DWORD             tagValue,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### Parameter  
 `tagValue`  
 \[\] werden in der Zeigertagwert, für den das pointee Symbol aufzeichnet, gefunden.  
  
 `ppResult`  
 \[out\] Ein Zeiger auf einen `IDiaEnumSymbols`\-Schnittstellenzeiger, der mit dem Ergebnis initialisiert wird.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)