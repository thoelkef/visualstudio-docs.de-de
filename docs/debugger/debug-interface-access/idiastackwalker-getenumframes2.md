---
title: "IDiaStackWalker::getEnumFrames2 | Microsoft Docs"
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
  - "IDiaStackWalker2::getEnumFrames2-Methode"
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft einen Stapelrahmen enumerator für einen bestimmten Plattform des Arrays ab.  
  
## Syntax  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### Parameter  
 `cpuid`  
 \[in\]  Ein Wert aus der Enumeration, [CV\_CPU\_TYPE\_e Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md) den Typ der Plattform angibt.  
  
 `pHelper`  
 \[in\]  Das Hilfe [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)\-Objekt.  
  
 `ppEnum`  
 \[out\]  Gibt ein [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)\-Objekt zurück, das eine Liste von [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)\-Objekten enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Zum Abrufen einer Liste der Stapelrahmen für nur die x86\-Plattform, rufen Sie die [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)\-Methode auf.  
  
## Siehe auch  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [CV\_CPU\_TYPE\_e Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)