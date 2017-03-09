---
title: "Fehler: Die DCOM-Kommunikation kann nicht initiiert werden | Microsoft Docs"
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
  - "vs.debug.error.unmarshal_server_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Die DCOM-Kommunikation kann nicht initiiert werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bei einem Versuch des lokalen Computers, mit dem Remotecomputer zu kommunizieren, ist ein DCOM\-Fehler aufgetreten.  Dies wird durch eine Firewall auf dem Remoteserver oder durch eine nicht funktionierende Windows\-Authentifizierung auf dem Remotecomputer verursacht.  
  
### So beheben Sie diesen Fehler  
  
-   Wenn auf dem Remotecomputer die Windows\-Firewall aktiviert ist, finden Sie unter [Einrichten der Remotetools auf dem Gerät](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md) Anweisungen zum Konfigurieren der Firewall zum lokalen Debugging.  
  
-   Versuchen Sie zum Wiederherstellen der Windows\-Authentifizierung, beide Computer neu zu starten.  Überprüfen Sie die Ereignisprotokolle auf dem lokalen Computer und dem Remotecomputer auf Kerberos\-Fehler, und klären Sie mit den Domänenadministratoren ab, ob bekannte Probleme vorliegen.  
  
## Siehe auch  
 [Remotedebugging](../debugger/remote-debugging.md)