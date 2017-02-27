---
title: "IDiaLoadCallback::RestrictRegistryAccess | Microsoft Docs"
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
  - "IDiaLoadCallback::RestrictRegistryAccess-Methode"
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::RestrictRegistryAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob Abfragen Registrierungsdaten verwendet werden können, um Symbol Suchpfade zu suchen.  
  
## Syntax  
  
```cpp#  
HRESULT RestrictRegistryAccess();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jeder andere als Rückgabecode `S_OK` verhindert, dass Abfragen der Registrierung für Symbol Suchpfade.  
  
## Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)