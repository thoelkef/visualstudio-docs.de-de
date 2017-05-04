---
title: "IRemoteDebugApplicationEx-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx-Schnittstelle"
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx-Schnittstelle
Stellt eine laufende Anwendung dar.  Sie muss nicht, um zu einem Betriebssystemprozess zu entsprechen.  In der Regel wird für ein Debugger eine Anwendung für das Debuggen fest.  Der Prozessdebug\-Manager implementiert normalerweise das Anwendungsobjekt.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IRemoteDebugApplicationEx`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Gibt die Prozess\-ID für die Hostanwendung zurück.|  
|GetHostMachineName|Gibt den Namen des Computers zurück, dass die Hostanwendung ausgeführt wird.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Legt die Sprache für die Debuggerlokalisierung fest.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Erzwingt den Debugger in einschrittigen Modus.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Widerruft einen Unterbrechungsbefehl.|  
|SetProxyBlanketAndAddRef|Sicherheitsinformationen der Updates COM über einen Proxy, damit ein Debuggerobjekt Kompatibilität mit Remotedebuggen von Windows 95 basierende Betriebssysteme sicherzustellen.|  
|ReleaseFromSetProxyBlanket|AddRef Versionen von SetProxyBlanketAndAddRef.|