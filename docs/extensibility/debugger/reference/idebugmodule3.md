---
title: IDebugModule3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1db551b9f62fbf85cd996e5f14bdb95c5aaca1f2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule3"></a>IDebugModule3
Diese Schnittstelle stellt ein Modul, alternative Speicherorte der Symbole und JustMyCode-Status unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle, um alternative Speicherorte der Symbole zu unterstützen, auch zum Arbeiten mit JustMyCode-Status (finden Sie unter der [Visual Studio-Debugger-Glossar](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) eine Definition der "JustMyCode").  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) gibt diese Schnittstelle. Sendet die DE der [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) Schnittstelle zu der Sitzung Debug-Manager (SDM) mithilfe der [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Methode. Darüber hinaus einen Aufruf von [QueryInterface](/cpp/atl/queryinterface) auf eine [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) Schnittstelle gibt diese Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) diese Schnittstelle implementiert, die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Gibt eine Liste von Pfaden für Symbole und die Ergebnisse der Suche jeder Pfad durchsucht.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Lädt und initialisiert Symbole für das aktuelle Modul.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Gibt Kennzeichen, das angibt, ob das Modul Benutzercode darstellt.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Gibt an, ob das Modul Benutzercode oder nicht berücksichtigt werden soll.|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio ist die typische Consumer dieser Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)