---
title: "IDiaStackWalker::getEnumFrames | Microsoft Docs"
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
  - "IDiaStackWalker2::getEnumFrames-Methode"
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalker::getEnumFrames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft einen Stapelrahmenenumerator für x86\-Plattformen ab.  
  
## Syntax  
  
```cpp#  
HRESULT getEnumFrames(   
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### Parameter  
 `pHelper`  
 \[in\]  Das Hilfe [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)\-Objekt.  
  
 `ppEnum`  
 \[out\]  Gibt ein [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)\-Objekt zurück, das eine Liste von [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)\-Objekten enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Um eine Liste Stapelrahmen auf einer beliebigen anderen Plattform abzurufen, rufen Sie die [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)\-Methode auf.  
  
## Siehe auch  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)