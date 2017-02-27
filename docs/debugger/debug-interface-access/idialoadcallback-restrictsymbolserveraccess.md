---
title: "IDiaLoadCallback::RestrictSymbolServerAccess | Microsoft Docs"
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
  - "IDiaLoadCallback::RestrictSymbolServerAccess-Methode"
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::RestrictSymbolServerAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob der Zugriff auf einem Symbolserver auf die Symbole aufgelöst werden darf.  
  
## Syntax  
  
```cpp#  
HRESULT RestrictSymbolServerAccess();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jeder andere als Rückgabecode `S_OK` verhindert Verwendung eines Symbols servers Symbole aufzulösen.  
  
## Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)