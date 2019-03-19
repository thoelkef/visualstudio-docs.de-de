---
title: IRemoteDebugApplicationEx-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9e25a28ade1ac73b9e4837dae61e2d91f24c45
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144406"
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx-Schnittstelle
Stellt eine ausgeführte Anwendung dar. Es muss nicht zu einem Betriebssystem-Prozess zu entsprechen. Ein Debugger ist in der Regel eine Anwendung für das Debuggen. Den prozessbasierten Debugmanager implementiert in der Regel der Application-Objekt.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IRemoteDebugApplicationEx` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Gibt die Prozess-ID für die hostanwendung zurück.|  
|GetHostMachineName|Gibt den Namen des Computers, der die hostanwendung ausgeführt wird.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Legt die Sprache für die Lokalisierung Debugger fest.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Erzwingt, dass den Debugger in einschrittigen Modus.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Widerruft einen Break-Befehl.|  
|SetProxyBlanketAndAddRef|Informationen zum COM-Sicherheit für einen Proxy für ein Objekt der Debugger zur Sicherstellung der Kompatibilität mit dem Remotedebuggen von Windows 95-basierten Betriebssystemen wird aktualisiert.|  
|ReleaseFromSetProxyBlanket|Releases von SetProxyBlanketAndAddRef "AddRef".|