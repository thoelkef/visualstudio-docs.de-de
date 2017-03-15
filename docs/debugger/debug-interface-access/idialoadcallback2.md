---
title: "IDiaLoadCallback2 | Microsoft Docs"
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
  - "IDiaLoadCallback2-Schnittstelle"
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaLoadCallback2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Empfängt Rückrufe vom Durchmesser\-Symbol, der die Prozedur heraussucht und lässt die dem suchenden Prozesses erzwingt Einschränkungen werden soll.  
  
## Syntax  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden in der [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)\-Schnittstelle macht diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Bestimmt, ob bei einer PDB\-Datei im ursprünglichen Suche Verzeichnis Debug.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Bestimmt, ob die Suche nach einer PDB\-Datei im Pfad ermöglicht wird, in dem die EXE\-Datei befindet.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Bestimmt die beim Suchen nach Debuginformationen aus .dbg\-Dateien zugelassen wird.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Bestimmt, ob die Suche nach PDB\-Dateien Stammverzeichnis im System zulässig ist.|  
  
## Hinweise  
 Die Clientanwendung implementiert diese Schnittstelle und macht einen Verweis auf sie im Aufruf der [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)\-Methode bereit.  Denken Sie daran, [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) alle Methoden in der Schnittstelle zu implementieren.  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)