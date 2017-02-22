---
title: "IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Erstellen eines entsprechenden Tagwert angegeben, gibt diese Methode eine Enumeration von Symbolen zurück, die in einer angegebenen Elementen Zugriffstastenstubfunktion an einer angegebenen relativen virtuellen Adresse enthalten sind.  
  
## Syntax  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Parameter  
 `parent`  
 \[\] in `IDiaSymbol`, das der zu durchsuchenden Zugriffstastenstubentspricht Funktion.  
  
 `tagValue`  
 \[\] in der Zeigertagwert.  
  
 `rva`  
 \[\] in die relative virtuelle Adresse.  
  
 `ppResult`  
 \[out\] Ein Zeiger auf einen `IDiaEnumSymbols`\-Schnittstellenzeiger, der mit dem Ergebnis initialisiert wird.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Rufen Sie diese Methode nur für eine `IDiaSymbol`\-Schnittstelle an, die einer Zugriffstastenstubfunktion entspricht.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)