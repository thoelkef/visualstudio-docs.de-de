---
title: BP_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 481dd21287ba3ca68c2abc61412785fc0151788d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="bpflags"></a>BP_FLAGS
Bietet optionale Kennzeichen, die verwendet werden können, um zusätzliche Informationen angeben, wenn Sie einen Haltepunkt festlegen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```csharp  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## <a name="members"></a>Member  
 BP_FLAG_NONE  
 Gibt kein Haltepunkt-Flag an.  
  
 BP_FLAG_MAP_DOCPOSITION  
 Gibt an, dass den Haltepunkt mithilfe der Dokumentposition Debugging-Modul (DE) zugeordnet werden sollen. Dies gilt nur für Haltepunkte in Skripts orientierten Quelldateien z. B. Active Server Pages (ASP).  
  
 BP_FLAG_DONT_STOP  
 Gibt an, dass der Haltepunkt von Debugging-Modul verarbeitet werden sollen, aber das Debugmodul letztendlich nicht es beendet werden soll (d. h. eine [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) Ereignisobjekt nicht gesendet werden soll). Dieses Flag dient in erster Linie mit Ablaufverfolgungspunkten verwendet werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet für die `dwFlags` Mitglied der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen.  
  
 Diese Werte können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)