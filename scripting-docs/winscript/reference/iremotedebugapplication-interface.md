---
title: IRemoteDebugApplication-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a231818def210f7c88ab031059f8561c67b33d1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159152"
---
# <a name="iremotedebugapplication-interface"></a>IRemoteDebugApplication-Schnittstelle
Stellt eine ausgeführte Anwendung dar. Es muss nicht zu einem Betriebssystem-Prozess zu entsprechen. Ein Debugger ist in der Regel eine Anwendung für das Debuggen. Den prozessbasierten Debugmanager implementiert in der Regel der Application-Objekt.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IRemoteDebugApplication` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Wird eine Anwendung, die derzeit an einem Haltepunkt wird fortgesetzt.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Bewirkt, dass die Anwendung im Debugger bei nächstmöglicher Gelegenheit unterbrochen.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Verbindet einen Debugger an diese Anwendung an.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Wird den aktuellen Debugger von der Anwendung getrennt.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Gibt zurück, der aktuelle Debugger an die Anwendung verbunden.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Stellt einen Mechanismus für den Debugger-IDE ausführen Out-of-Process an die Anwendung, zum Erstellen von Objekten im Anwendungsprozess.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Gibt an, wenn die Anwendung reaktionsfähig ist.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Listet alle Threads bekannt, dass der Anwendung zugeordnet sind.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Der Name dieses Knotens für die Anwendung zurückgegeben.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Gibt den Knoten der Anwendung unter dem alle Knoten, die der Anwendung zugeordneten hinzugefügt wurden.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Listet die globale ausdruckskontexten für alle Sprachen, die in dieser Anwendung ausführen.|