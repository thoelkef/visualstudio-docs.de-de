---
title: "Dialogfeld &quot;Firewall f&#252;r Remotedebuggen konfigurieren&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.firewallconfiguration"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "Firewall für Remotedebuggen konfigurieren (Dialogfeld)"
  - "Remotedebuggen, Konfigurieren von Firewalls"
  - "Firewalls, Konfigurieren für Remotedebuggen"
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Dialogfeld &quot;Firewall f&#252;r Remotedebuggen konfigurieren&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Dialogfeld wird angezeigt, wenn von der Windows\-Firewall Daten blockiert werden, die der Debugger über das Netzwerk empfangen soll. Um das Remotedebuggen fortzusetzen, müssen Sie der Firewall Ausnahmen hinzufügen und Ports öffnen, damit der Debugger Informationen empfangen kann.  
  
> [!CAUTION]
>  Wenn Sie Ports in der Firewall öffnen, ist der Computer unter Umständen Sicherheitsrisiken ausgesetzt, die sonst von der Firewall blockiert werden. Durch das Öffnen einer Lücke für das Remotedebuggen wird die Blockierung der Ports 4020 und 4021 in Visual Studio 2015 aufgehoben. In anderen Versionen von Visual Studio werden andere Portnummern verwendet. Weitere Informationen finden Sie unter [Remotedebugger \- Portzuweisungen](../debugger/remote-debugger-port-assignments.md). Zusätzlich wird dem Debugger ermöglicht, weitere Ports zu öffnen. Weitere Informationen finden Sie unter [Konfigurieren der Windows\-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## UIElement-Liste  
 **Remotedebugging abbrechen**  
 Mit dieser Option wird der Remotedebugversuch abgebrochen. Die Sicherheitseinstellungen des Computers bleiben bestehen.  
  
 **Blockierung für Remotedebugging auf Computern im lokalen Netzwerk \(Subnetz\) aufheben**  
 Mit dieser Option wird das Remotedebuggen der Computer im lokalen Subnetz aktiviert. Dadurch können Sicherheitslücken in den Computern des Subnetzes entstehen, die Firewall wird jedoch weiterhin Informationen von außerhalb des Subnetzes blockieren.  
  
 **Blockierung für Remotedebugging von beliebigem Computer aufheben**  
 Mit dieser Option wird das Remotedebuggen von jedem möglichen Computer aus dem Netzwerk aktiviert. Diese Einstellung ist am unsichersten.  
  
## Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Einrichten der Remotetools auf dem Gerät](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [Referenz zur Debugger\-Benutzeroberfläche](../debugger/debugging-user-interface-reference.md)