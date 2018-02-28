---
title: IRemoteDebugApplication-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea91afdc44b70a91846d7b1a3dc4c017c0c4c80e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication-interface"></a>IRemoteDebugApplication-Schnittstelle
Stellt eine ausgeführte Anwendung dar. Es muss nicht zu einem Betriebssystem-Prozess entsprechen. Das Ziel in der Regel ein Debugger eine Anwendung für das Debuggen ist. Der Debug-Prozess-Manager implementiert in der Regel das Anwendungsobjekt.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IRemoteDebugApplication` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Wird eine Anwendung, die derzeit eines Haltepunkts wird fortgesetzt.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Bewirkt, dass die Anwendung der Debugger bei nächstmöglicher Gelegenheit zu unterbrechen.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Verbindet einen Debugger an dieser Anwendung an.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Trennt den aktuellen Debugger aus der Anwendung an.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Gibt der aktuellen Debugger an die Anwendung verbunden.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Bietet einen Mechanismus für den Debugger ausführen Out-of-Process an die Anwendung, zum Erstellen von Objekten im Anwendungsprozess-IDE.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Gibt an, ob die Anwendung reagiert.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Listet alle Threads bekannt, dass der Anwendung zugeordnet werden.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Der Name dieses Knotens Anwendung zurückgegeben.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Gibt den Anwendungsknoten, unter dem alle Knoten, die der Anwendung zugeordneten hinzugefügt wurden.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Listet die globalen ausdruckskontexten für alle Sprachen, die in dieser Anwendung ausgeführt wird.|