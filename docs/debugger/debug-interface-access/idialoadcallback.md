---
title: IDiaLoadCallback | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5cc40b8041ea5427d223a70c7d3d9347c48be286
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Das DIA Symbol Suchen von Prozedur, sodass eine neue Benutzeroberfläche Auskunft über den Fortschritt des Versuchs Speicherort auf Empfangsvorgänge Rückrufe.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaLoadCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgenden Methoden werden von dieser Schnittstelle verfügbar gemacht:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Wird aufgerufen, wenn ein Debugverzeichnis im .exe-Datei gefunden wurde.|  
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Wird aufgerufen, wenn eine Kandidat .dbg-Datei geöffnet wurde.|  
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Wird aufgerufen, wenn eine Kandidat PDB-Datei geöffnet wurde.|  
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Bestimmt, ob die Registrierung Abfragen zum Suchen von Symbolsuchpfaden verwendet werden können.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Bestimmt, ob der Zugriff auf einen anderen Symbolserver zugelassen wird, um Symbole aufzulösen.|  
  
## <a name="remarks"></a>Hinweise  
 Die Clientanwendung diese Schnittstelle implementiert und enthält einen Verweis darauf im Aufruf der [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.  
  
 Zusätzliche Einschränkungen, die in einem Auslastungstest-Prozess festgelegt werden können, finden Sie unter der [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: "MSDIA80.dll"  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)