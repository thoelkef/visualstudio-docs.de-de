---
title: IDebugModule2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4ffa4044e6490f8de8228541787b7bf8ab80285a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule2"></a>IDebugModule2
Diese Schnittstelle stellt ein Modul dar – d. h. eine ausführbare Einheit eines Programms – z. B. eine DLL.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle, um ein Modul darstellen und Zugriff auf Informationen zu diesem Modul bereitzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) gibt diese Schnittstelle. Sendet die DE der [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) Schnittstelle zu der Sitzung Debug-Manager (SDM) mithilfe der [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Methode.  
  
 Diese Schnittstelle kann auch zurückgegeben werden, einem [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Struktur (der zurückgegeben wird, durch den Aufruf von [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Nächste](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) auch gibt diese Schnittstelle ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) gibt die [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) Schnittstelle).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugModule2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ruft die [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) , der dieses Modul beschreibt.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|VERALTET. DARF NICHT VERWENDET WERDEN. Lädt die Symbole für dieses Modul erneut.|  
  
## <a name="remarks"></a>Hinweise  
 Modulinformationen kann angezeigt werden, der **Module** Fenster der IDE.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)