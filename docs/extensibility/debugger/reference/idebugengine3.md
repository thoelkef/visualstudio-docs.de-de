---
title: IDebugEngine3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f89452582677334f75c330ff00af58b95e928c2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992346"
---
# <a name="idebugengine3"></a>IDebugEngine3
Stellt eine einzelne Debug-Engine (DE), die steuert, das Debuggen von ein oder mehrere Module dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird durch eine benutzerdefinierte DE implementiert (wenn es sich um Symbole unterstützt) um den JustMyCode-Status aktivieren. Diese Schnittstelle muss von der DE implementiert werden, wenn sie Symbole und JustMyCode unterstützt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird von der Sitzungs-Manager (SDM) für die Übergabe über Optionen für die Speicherorte der Symbole laden aufgerufen. Es wird auch aufgerufen, um die GUID der Engine festgelegt, wenn er instanziiert wird (diese GUID basiert auf die Metriken ab dem Zeitpunkt der Engine-Registrierung). Das SDM ruft auch dieser Schnittstelle, um den JustMyCode-Status festlegen, und legen Sie alle Ausnahmen, die durch den Debugger an einen bestimmten Status bekannt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), `IDebugEngine3` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Legt fest, den Pfad oder die Pfade, die die DE verwenden, suchen Sie für die Debugsymbole.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Lädt die Symbole für alle Module, die noch nicht über die Symbole geladen wurden.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Teilt die DE zu den JustMyCode-Informationen.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Legt die DE-GUID aus der Metriken fest.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Legen Sie alle Ausnahmen, die derzeit ausstehenden, auf einem angegebenen Zustand.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)