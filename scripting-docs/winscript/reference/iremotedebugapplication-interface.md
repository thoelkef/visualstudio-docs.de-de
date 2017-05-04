---
title: "IRemoteDebugApplication-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication-Schnittstelle"
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IRemoteDebugApplication-Schnittstelle
Stellt eine laufende Anwendung dar.  Sie muss nicht, um zu einem Betriebssystemprozess zu entsprechen.  In der Regel wird für ein Debugger eine Anwendung für das Debuggen fest.  Der Prozessdebug\-Manager implementiert normalerweise das Anwendungsobjekt.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IRemoteDebugApplication`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Fügt eine Anwendung fort, die derzeit in einem Haltepunkt ist.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Bewirkt, dass die Anwendung im Debugger bei der nächstmöglichen Möglichkeit zu unterbrechen.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Schließt einen Debugger an diese Anwendung an.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Trennt den aktuellen Debugger aus der Anwendung.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Gibt den aktuellen Debugger zurück, der an die Anwendung verbunden ist.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Stellt einen Mechanismus für den Debugger IDE bereit, das Ausführen prozessextern zur Anwendung, Objekte im Anwendungsprozess zu erstellen.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Gibt an, ob die Anwendung reagiert weiterhin ist.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Listet alle Threads, die bekannt sind, mit der Anwendung zugeordnet werden.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Gibt den Namen dieses Anwendungsknotens zurück.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Gibt den Anwendungsknoten zurück, unter dem alle Knoten, die der Anwendung zugeordnet sind, hinzugefügt werden.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Listet die globalen Ausdruckskontexte für alle Sprachen aufgeführt, die in dieser Anwendung ausgeführt werden.|