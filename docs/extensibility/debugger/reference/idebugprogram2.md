---
title: "IDebugProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2"
helpviewer_keywords: 
  - "IDebugProgram2-Schnittstelle"
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Programm dar, das in einem Prozess ausgeführt wird.  
  
## Syntax  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) und ein benutzerdefiniertes Anschlusslieferanten diese Schnittstelle implementieren, um ein Programm in einem Prozess darstellt.  Der Debuginformationen Manager der Sitzung \(SDM\) implementiert auch diese Schnittstelle, um Informationen zu [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)bereitzustellen.  
  
## Hinweise für Aufrufer  
 Das [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)\-Ereignis gibt diese Schnittstelle für ein neues Programm zurück.  Diese Schnittstelle wird auch als Parameter für viele Methoden für mehrere Schnittstellen verwendet.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugProgram2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Listet die Threads auf, die in diesem Programm aus.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Ruft den Namen des Programms ab.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Ruft den Prozess ab, die in diesem Programm ausgeführt wird.|  
|[Beenden](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Beendet das Programm.|  
|[Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Fügt diesem Programm an.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Bestimmt, ob eine Debug\- Modul \(DE\) vom Programm getrennt werden kann.|  
|[Trennen](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Ordnet den Debugger von diesem Programm ab.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Ruft einen GUID \(Globally Unique Identifier\) für dieses Programm ab.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Ruft Programm von Eigenschaften ab.|  
|[Ausführen](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Setzt die Ausführung des Programms aus einem Beendet fort.  Jeder vorherige Ausführungsstatus wird gelöscht.|  
|[Weiter](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Setzt die Ausführung des Programms aus einem Beendet fort.  Jeder vorherige Ausführungsstatus wird beibehalten.|  
|[Schritt](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Führt einen Schritt aus.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Fordert an, dass beim nächsten Ausführen dieses Programms anhalten, einer seiner Threads führt Code aus.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Ruft den Namen und den Bezeichner des Debugmoduls \(DE Ausführen dieses Programms\) ab oder legt diese fest.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Listet die Code für kontexte einer angegebenen Position in einer Quelldatei aufgelistet.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Ruft die Bytes Speicherplatz für dieses Programm ab.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Ruft den Disassemblys datenstrom für dieses Programm oder einen Teil des Programms ab.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Listet die Module, die dieses Programm geladen wurde und ausgeführt wird.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Ruft den Bearbeitungsvorgang ab und setzt Update \(Anlage\) für dieses Programm fortgesetzt.<br /><br /> Debuggen eines benutzerdefinierten Moduls diese Methode nicht implementiert \(es soll `E_NOTIMPL`immer zurückgegeben\).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Listet die Codepfade dieses Programms auf.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Schreibt einen Dump in einer Datei.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Hinweise  
 Ein Programm kann ein Thread ausgeführten Container in einer bestimmten Laufzeit als Architektur der Prozess eine oder mehrere Programme besteht.  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)