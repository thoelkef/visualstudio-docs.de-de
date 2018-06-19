---
title: IRemoteDebugApplicationEx-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3360cea0d1649348a795356ad827b32b6f8ebc19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729400"
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx-Schnittstelle
Stellt eine ausgeführte Anwendung dar. Es muss nicht zu einem Betriebssystem-Prozess entsprechen. Das Ziel in der Regel ein Debugger eine Anwendung für das Debuggen ist. Der Debug-Prozess-Manager implementiert in der Regel das Anwendungsobjekt.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IRemoteDebugApplicationEx` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Gibt die Prozess-ID für die hostanwendung zurück.|  
|GetHostMachineName|Gibt den Namen des Computers, der die hostanwendung ausgeführt wird.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Hiermit wird die Sprache für die Lokalisierung Debugger.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Erzwingt, dass den Debugger in einschrittigen Modus.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Widerruft einen Break-Befehl.|  
|SetProxyBlanketAndAddRef|COM-Sicherheitsinformationen für einen Proxy für ein Objekt der Debugger zur Sicherstellung der Kompatibilität mit dem Remotedebuggen von Windows 95-basierten Betriebssystemen wird aktualisiert.|  
|ReleaseFromSetProxyBlanket|Versionen AddRef aus SetProxyBlanketAndAddRef.|