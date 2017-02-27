---
title: "IDiaLoadCallback | Microsoft Docs"
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
  - "IDiaLoadCallback-Schnittstelle"
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Empfängt Rückrufe vom Durchmesser\-Symbol, das Verfahren heraussucht und ermöglicht so eine Benutzeroberfläche zum Speicherort des versuchs über den Fortschritt zu melden.  
  
## Syntax  
  
```  
IDiaLoadCallback : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 Die folgenden Methoden werden von dieser Schnittstelle verfügbar gemacht:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Wird aufgerufen, wenn ein Verzeichnis Debug in der EXE\-Datei gefunden wurde.|  
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Wird aufgerufen, wenn eine mögliche dbg\-datei geöffnet wurde.|  
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Wird aufgerufen, wenn eine mögliche pdb\-datei geöffnet wurde.|  
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Bestimmt, ob Abfragen Registrierungsdaten verwendet werden können, um Symbol Suchpfade zu suchen.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Bestimmt, ob der Zugriff auf einem Symbolserver auf die Symbole aufgelöst werden darf.|  
  
## Hinweise  
 Die Clientanwendung implementiert diese Schnittstelle und macht einen Verweis auf sie im Aufruf der [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)\-Methode bereit.  
  
 Zusätzliche Einschränkungen, die einen Ladevorgang auferlegt werden können, finden Sie in der [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)\-Schnittstelle.  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)