---
title: "IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictOriginalPathAccess-Methode"
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob dieses passend ist, nach einer PDB\-Datei im ursprünglichen Verzeichnis Debug zu suchen.  
  
## Syntax  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jeder andere als Rückgabecode `S_OK` verhindert Sucht nach einer PDB\-Datei im ursprünglichen Verzeichnis Debug.  Das ursprüngliche Debuginformationen Verzeichnis ist der Pfad zur Symboldatei, die in die ausführbare Datei kompiliert wird, wenn das Debuggen aktiviert ist.  Dieser Pfad ist nicht unbedingt derselbe wie der Pfad, in dem die ausführbare Datei vorhanden ist.  
  
## Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)