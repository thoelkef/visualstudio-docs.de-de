---
title: IDiaLoadCallback2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5c1225d75ea857fe34906daeb4792524fde4bc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538810"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Empfängt Rückrufe aus dem Dia-Symbol zum Suchen von Prozeduren und ermöglicht das Erzwingen von Einschränkungen für den suchen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden in der [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) -Schnittstelle macht diese Schnittstelle die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Bestimmt, ob eine PDB-Datei im ursprünglichen Debugverzeichnis gesucht werden soll.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Bestimmt, ob die Suche nach einer PDB-Datei in dem Pfad zulässig ist, in dem sich die exe-Datei befindet.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Bestimmt, ob die Suche nach Debuginformationen aus dbg-Dateien zulässig ist.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Bestimmt, ob die Suche nach PDB-Dateien im Stammverzeichnis des Systems zulässig ist.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die Client Anwendung implementiert diese Schnittstelle und stellt im Aufrufe der [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) -Methode einen Verweis darauf bereit. Denken Sie daran, auch alle Methoden in der [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) -Schnittstelle zu implementieren.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
