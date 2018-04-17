---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1e95996a0548dcf81957dad60c3e6f73b3424c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Diese Schnittstelle Listet die in der aktuellen Debugsitzung ausgeführten Programme.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle, um eine Liste mit durch DE gedebuggten Programme bereitstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Visual Studio-Aufrufe [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) beim Abrufen dieser Schnittstelle. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) wird von Visual Studio nicht verwendet.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugPrograms2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Ruft eine angegebene Anzahl von Programmen in einer Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Überspringt eine angegebene Anzahl der Programme in einem Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Setzt ein Enumerationsfolge auf den Anfang zurück.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumeration Status als der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Ruft die Anzahl der Programme in einen Enumerator ab.|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio verwendet diese Schnittstelle:  
  
-   Auffüllen der **Module** Fenster (durch Aufrufen von [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) und dem anschließenden Aufrufen [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) für jedes Programm).  
  
-   Auffüllen der **an den Prozess anhängen** Liste (durch Aufrufen von `IDebugProcess2::EnumPrograms` und dem anschließenden Aufrufen [QueryInterface](/cpp/atl/queryinterface) auf jedem [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle zum Abrufen einer [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) Schnittstelle).  
  
-   Generieren Sie eine Liste der DEs, die jedes Programm in den Prozess zu debuggen (mit [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Anwenden von Updates von bearbeiten und Fortfahren (ENC) für jedes Programm (durch Aufrufen von IDebugProcess2::EnumPrograms und dem anschließenden Aufrufen [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)