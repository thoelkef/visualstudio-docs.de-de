---
title: IDebugProcessSecurity | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e78baf34a3ecb6d5b40162b424c11a104617669
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` wird implementiert, ein Lieferant Port, dem Benutzer gewarnt, dass das Anhängen an den Prozess nicht sicher ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProcessSecurity`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Ruft den Benutzernamen des Lieferanten Port ab.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Eine Warnung ausgegeben, dass das Anfügen an den Debugprozess unsicher ist.|  
  
## <a name="remarks"></a>Hinweise  
 Implementieren Sie diese Schnittstelle, um eine Warnmeldung angezeigt und ermöglicht dem Benutzer das Abbrechen, wenn der Prozess, den Sie angefügt werden, als unsicher angesehen werden kann.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Ports](../../../extensibility/debugger/ports.md)   
 [Port-Lieferanten](../../../extensibility/debugger/port-suppliers.md)   
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)