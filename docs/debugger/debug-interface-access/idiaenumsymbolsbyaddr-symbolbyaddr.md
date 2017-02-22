---
title: "IDiaEnumSymbolsByAddr::symbolByAddr | Microsoft Docs"
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
helpviewer_keywords: 
  - "IDiaEnumSymbolsByAddr::symbolByAddr-Methode"
ms.assetid: 0b6f5a68-8402-4f29-8219-20576fda8166
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbolsByAddr::symbolByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Positioniert den Enumerator durch das Ausführen einer Suche in Bildausschnitt Zahl und dem angegebenen Offset begonnen wird.  
  
## Syntax  
  
```cpp#  
HRESULT symbolByAddr (   
   DWORD**      isect,  
   DWORD**      offsect,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### Parameter  
 isect  
 \[in\]  Bildausschnitt Zahl.  
  
 offsect  
 \[in\]  Offset im Abschnitt.  
  
 ppsymbol  
 \[out\]  Gibt ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt zurück, das das gefundene Symbol darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn das Symbol nicht gefunden werden konnte.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)