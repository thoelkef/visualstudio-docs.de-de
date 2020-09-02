---
title: IDebugModule2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fc229a353655aeae06460c32b5233888f22dd6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555809"
---
# <a name="idebugmodule2"></a>IDebugModule2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Modul dar, d. –. eine ausführbare Einheit eines Programms – z. b. eine DLL.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (de) implementiert diese Schnittstelle, um ein Modul darzustellen und Zugriff auf Informationen über dieses Modul bereitzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Bei einem [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) -Rückruf wird diese Schnittstelle zurückgegeben. Der de sendet mithilfe der- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Methode die [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) -Schnittstelle an den Sitzungs-Debug-Manager (SDM).  
  
 Diese Schnittstelle kann auch in einer [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Struktur zurückgegeben werden (die durch einen aufzurufenden [enumframeinfo-Befehl](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)zurückgegeben wird).  
  
 [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) gibt auch diese Schnittstelle zurück ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) gibt die [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) -Schnittstelle zurück).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugModule2` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ruft den [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) ab, der dieses Modul beschreibt.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|VERALTET. Verwenden Sie nicht. Lädt die Symbole für dieses Modul erneut.|  
  
## <a name="remarks"></a>Bemerkungen  
 Modul Informationen können im Fenster " **Module** " der IDE angezeigt werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FrameInfo](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
