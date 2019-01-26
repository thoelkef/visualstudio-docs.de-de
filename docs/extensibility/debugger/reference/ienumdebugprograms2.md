---
title: IEnumDebugPrograms2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0cadbfee175f26e13b38775442430676edba254
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931218"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Diese Schnittstelle Listet die in der aktuellen Debuggingsitzung ausgeführten Programme.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um eine Liste von durch die DE gedebuggten Programme bereitstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Visual Studio-Aufrufe [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) dieser Schnittstelle abgerufen. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) wird von Visual Studio nicht verwendet.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugPrograms2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Ruft eine angegebene Anzahl von Programmen in einer Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Überspringt eine angegebene Anzahl von Programmen in einer Enumerationsfolge.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Ruft die Anzahl der Programme in einen Enumerator ab.|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio verwendet diese Schnittstelle:  
  
-   Füllen Sie die **Module** Fenster (durch Aufrufen von [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) und dem anschließenden Aufrufen [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) für jedes Programm).  
  
-   Füllen Sie die **an den Prozess anhängen** Liste (durch Aufrufen von `IDebugProcess2::EnumPrograms` und dem anschließenden Aufrufen [QueryInterface](/cpp/atl/queryinterface) auf jedem [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle zum Abrufen einer [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) Schnittstelle).  
  
-   Generiert eine Liste mit DEs, den jedes Programm in den Prozess zu debuggen, können (mit [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Anwenden von Updates für bearbeiten und Fortfahren "(ENC) für jedes Programm (durch Aufrufen von IDebugProcess2::EnumPrograms und dem anschließenden Aufrufen [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)