---
title: "IDiaSession::findAcceleratorInlineesByName | Microsoft Docs"
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
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt eine Enumeration von Symbolen für inline Frames gemäß dem angegebenen Inlinefunktionsnamen zurück.  
  
## Syntax  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Parameter  
 `name`  
 \[\] in der zu durchsuchenden Inlinee Funktionsname.  
  
 `option`  
 \[\] in die Namesuchoptionen beim Suchen verwendet werden für inline Frame, der zu `name` entsprechen.  Weitere Informationen finden Sie unter [NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 \[out\] Ein Zeiger auf einen `IDiaEnumSymbols`\-Schnittstellenzeiger, der mit dem Ergebnis initialisiert wird.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Suchen dieser Funktion für inlinees nur innerhalb des Zugriffstastenstubs funktioniert.  Die systemeigene C\+\+\-Prozedurdatensätze ignoriert.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)