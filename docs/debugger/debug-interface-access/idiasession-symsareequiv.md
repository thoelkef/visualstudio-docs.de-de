---
title: "IDiaSession::symsAreEquiv | Microsoft Docs"
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
  - "IDiaSession::symsAreEquiv-Methode"
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Überprüft, ob zwei Symbole übereinstimmen.  
  
## Syntax  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### Parameter  
 `symbolA`  
 \[in\]  Das erste [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt verwendet im Vergleich.  
  
 `symbolB`  
 \[in\]  Das zweite `IDiaSymbol`\-Objekt verwendet im Vergleich.  
  
## Rückgabewert  
 Wenn die Symbole übereinstimmen, gibt `S_OK`zurück. Andernfalls gibt `S_FALSE`zurück, die die Symbole sind nicht erforderlich.  Andernfalls geben Sie einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)