---
title: IDebugProgram2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2
helpviewer_keywords: IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7f02d099fe680006966219bb626e17bc7a7114b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2"></a>IDebugProgram2
Diese Schnittstelle stellt ein Programm, das in einem Prozess ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (Deutschland) und einen benutzerdefinierten Port Lieferanten implementieren diese Schnittstelle, um ein Programm in einem Prozess darstellen. Die Sitzungs-Debug-Manager (SDM) auch implementiert diese Schnittstelle, um Informationen zum Bereitstellen [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Ereignis wird diese Schnittstelle für ein neues Programm zurückgegeben. Diese Schnittstelle wird auch als Parameter für zahlreiche Methoden für auf mehrere Schnittstellen verwendet.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProgram2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Listet die Threads, die an diesem Programm ausgeführt werden.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Ruft den Namen des Programms.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Ruft den Prozess ab, dem dieses Programm ausgeführt wird.|  
|[Beenden](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Dieses Programm wird beendet.|  
|[Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Dieses Programm wird angefügt.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Bestimmt, ob das Programm einen Debugging-Modul (DE) trennen kann.|  
|[Trennen](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Trennt den Debugger aus dem Programm.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Ruft einen global eindeutigen Bezeichner für dieses Programm an.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Ruft die Programmeigenschaften an.|  
|[Führen Sie](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Wird fortgesetzt, Status "beendet" dieses Programm ausführen. Alle vorherigen Ausführungsstatus ist deaktiviert.|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Wird fortgesetzt, Status "beendet" dieses Programm ausführen. Alle vorherigen Ausführungsstatus wird beibehalten.|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Führt einen Schritt aus.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Fordert an, dass dieses Programm, die Ausführung der nächsten beenden Zeitpunkt eins des zugehörigen Codes des Threads ausgeführt wird.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Ruft den Namen und die Bezeichner von die Debugging-Modul (DE), die dieses Programm ausführen.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Listet die Kontexte Code für eine bestimmte Position in einer Quelldatei.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Ruft die Speicherbytes für dieses Programm an.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Ruft den Disassembly-Datenstrom für dieses Programm oder einen Teil dieses Programm an.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Listet die Module, die dieses Programm wurde geladen und ausgeführt wird.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Ruft das Update bearbeiten und Fortfahren (ENC) für dieses Programm an.<br /><br /> Einen benutzerdefinierten Debugmodul implementiert diese Methode nicht (es sollten stets `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Listet die Codepfade Vertrieb dieses Programms.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Schreibt einen Dump in eine Datei.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Hinweise  
 Ein Programm ist eine Thread-Container in einer bestimmten Architektur zur Laufzeit ausgeführt wird, während ein Prozesses aus einem oder mehreren Programmen besteht.  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)