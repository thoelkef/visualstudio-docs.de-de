---
title: "IDiaSymbol::findInlineFramesByRVA | Microsoft Docs"
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
ms.assetid: e7a6d9cb-2726-4ac7-9f38-415ad215bf9c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::findInlineFramesByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Enumeration ab, die einem Client ermöglicht, um alle inline Frames auf einer angegebenen relativen virtuellen Adresse RVA \(\) zu durchlaufen.  
  
## Syntax  
  
```cpp#  
HRESULT findInlineFramesByRVA (   
   DWORD             rva,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parameter  
 `rva`  
 \[\] in gibt die Adresse als RVA an.  
  
 `ppResult`  
 \[out\] `IDiaEnumSymbols` enthält ein Objekt, das die Liste von Rahmen enthält, die abgerufen werden.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)