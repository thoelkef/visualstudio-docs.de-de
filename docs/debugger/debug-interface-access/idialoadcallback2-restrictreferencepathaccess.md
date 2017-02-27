---
title: "IDiaLoadCallback2::RestrictReferencePathAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictReferencePathAccess-Methode"
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaLoadCallback2::RestrictReferencePathAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob die Suche nach einer PDB\-Datei im Pfad ermöglicht wird, in dem die EXE\-Datei befindet.  
  
## Syntax  
  
```cpp#  
HRESULT RestrictReferencePathAccess();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Alle anderen als Rückgabecode `S_OK` um nach einer PDB\-Datei im Pfad gesucht werden soll, in der die EXE\-Datei befindet.  
  
## Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)