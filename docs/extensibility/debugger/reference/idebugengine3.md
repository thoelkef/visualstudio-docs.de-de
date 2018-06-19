---
title: IDebugEngine3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 291f5ca6f945abe9e0322839eb80c38b60674ce4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114416"
---
# <a name="idebugengine3"></a>IDebugEngine3
Stellt eine einzelne Debugging-Modul (DE), die das Debuggen von einem oder mehreren Modulen steuert.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird durch eine benutzerdefinierte Deutschland (sofern es sich um Symbole unterstützt) um den JustMyCode-Status aktivieren implementiert. Diese Schnittstelle muss von der DE implementiert werden, wenn es sich um Symbole und JustMyCode unterstützt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird von der Sitzung Debug-Manager (SDM) für die Übergabe über Optionen für Speicherorte, von denen So laden Sie Symbole aufgerufen. Es wird auch aufgerufen, um die GUID des Moduls festzulegen, wenn er instanziiert wird (diese GUID wird von der Testmetrik, ab dem Zeitpunkt der Registrierung von Modul basierend). Die SDM ruft auch diese Schnittstelle zum Festlegen des JustMyCode-Status und alle Ausnahmen, die durch den Debugger an einen bestimmten Status bekannt festzulegen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), `IDebugEngine3` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Legt den Pfad oder die Pfade, die die DE bei der Suche nach Debugsymbole verwendet wird.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Lädt die Symbole für alle Module, die noch nicht über die Symbole geladen wurde.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Weist die DE zu den JustMyCode-Informationen an.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Legt die DE GUID aus der Metriken fest.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Alle Ausnahmen, die auf einem angegebenen Zustand derzeit ausstehenden festgelegt.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)