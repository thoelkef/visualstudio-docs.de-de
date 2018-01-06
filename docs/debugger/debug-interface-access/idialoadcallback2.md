---
title: IDiaLoadCallback2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ee2733643350b2fea9b78a9d876037497d35e41a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
Das DIA-Symbol Suchen von Prozedur, sodass Einschränkungen beim Eintreten, bei der Product-Rückrufe Empfangsvorgänge.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden in der [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) diese Schnittstelle stellt die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Bestimmt, ob eine PDB-Datei im ursprünglichen Debugverzeichnis suchen.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Bestimmt, ob die Suche nach einer PDB-Datei im Pfad zulässig ist, wo sich die .exe-Datei befindet.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Bestimmt, ob die Suche nach Informationen zum Debuggen von .dbg-Dateien zulässig ist.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Bestimmt, ob die Suche nach PDB-Dateien in das Systemstammverzeichnis zulässig ist.|  
  
## <a name="remarks"></a>Hinweise  
 Die Clientanwendung diese Schnittstelle implementiert und enthält einen Verweis darauf im Aufruf der [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode. Denken Sie daran, alle Methoden implementieren die [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) Schnittstelle auch.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: "MSDIA80.dll"  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)