---
title: IDiaLoadCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09e835d8a7bfe0bc5d7ae06f0bac457126d21956
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466782"
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