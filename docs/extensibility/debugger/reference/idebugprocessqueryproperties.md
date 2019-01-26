---
title: IDebugProcessQueryProperties | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5bfdca9a60061e2e519f0e98db9864ecae06b7c0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021766"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Diese Schnittstelle ist eine Erweiterungsschnittstelle implementiert [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) Implementierungen. Dadurch kann die Implementierung zum Abrufen von Informationen in der Debugumgebung-Prozess.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Implementieren Sie diese Schnittstelle zum Abrufen von Informationen zu die ausführungsumgebung der einen Debugprozess.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProcessQueryProperties`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Abfragen für einen Eigenschaftswert.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Abfragen für Eigenschaftswerte.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird nur selten implementiert.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)