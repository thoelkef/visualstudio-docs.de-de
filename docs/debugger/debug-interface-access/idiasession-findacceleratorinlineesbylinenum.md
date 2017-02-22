---
title: "IDiaSession::findAcceleratorInlineesByLinenum | Microsoft Docs"
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
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findAcceleratorInlineesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt eine Enumeration von Symbolen für inline Frames zurück, die dem angegebenen Quellspeicherort entsprechen.  
  
## Syntax  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parameter  
 `parent`  
 \[\] in `IDiaSymbol`, das der Zugriffstastenstubfunktion entspricht, die gesucht werden muss.  
  
 `file`  
 \[\] in `IDiaSourceFile` des Quellspeicherorts.  
  
 `linenum`  
 \[\] in die Zeilennummer des Quellspeicherorts.  
  
 `colnum`  
 \[\] in die Spaltennummer des Quellspeicherorts.  
  
 `ppResult`  
 \[out\] Ein Zeiger auf einen `IDiaEnumLineNumbers`\-Schnittstellenzeiger, der mit dem Ergebnis initialisiert wird.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)