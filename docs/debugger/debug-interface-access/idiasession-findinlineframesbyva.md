---
title: "IDiaSession::findInlineFramesByVA | Microsoft Docs"
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
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineFramesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Enumeration ab, die einem Client ermöglicht, um alle inline Frames auf einer angegebenen virtuellen Adresse \(VA\) zu durchlaufen.  
  
## Syntax  
  
```cpp#  
HRESULT findInlineFramesByVA (   
   IDiaSymbol*       parent,  
   ULONGLONG         va,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parameter  
 `parent`  
 \[in \]Ein `IDiaSymbol`\-Objekt, das das übergeordnete Objekt darstellt.  
  
 `va`  
 \[in\] Gibt die Adresse als VA an.  
  
 `ppResult`  
 \[out\] `IDiaEnumSymbols` enthält ein Objekt, das die Liste von Rahmen enthält, die abgerufen werden.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)