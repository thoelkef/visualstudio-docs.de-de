---
title: "IDebugFirewallConfigurationCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFirewallConfigurationCallback2-Schnittstelle"
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Aktiviert eine Debug\- Modul DCOM verwendet wird, um das [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche zu bitten, um sicherzustellen, dass die Firewall das Remotedebuggen nicht blockiert.  
  
## Syntax  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Wird vom Port Objekt des Managers Debuggen der Sitzung.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von `IDebugFirewallConfigurationCallback2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Fordert das remotedebugging der Firewall nicht blockieren.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll