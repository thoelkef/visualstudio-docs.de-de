---
title: "Fehler: Der Remotecomputer konnte die DCOM-Kommunikation nicht initiieren | Microsoft Docs"
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
  - "vs.debug.error.unmarshal_callback_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Der Remotecomputer konnte die DCOM-Kommunikation nicht initiieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bei einem Versuch des Remotecomputers, mit dem lokalen Computer zu kommunizieren, ist ein DCOM\-Fehler aufgetreten.  Der lokale Computer ist der Computer, auf dem  
  
 Visual Studio ausgeführt wird.  Dieser Fehler kann mehrere Ursachen haben:  
  
-   Auf dem lokalen Computer ist eine Firewall aktiviert.  
  
-   Die Windows\-Authentifizierung vom Remotecomputer zum lokalen Computer funktioniert nicht.  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn auf dem lokalen Computer die Windows\-Firewall aktiviert ist, finden Sie unter [Einrichten der Remotetools auf dem Gerät](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md) Anweisungen zum Konfigurieren der Firewall zum lokalen Debugging.  
  
2.  Testen Sie die Windows\-Authentifizierung, indem Sie versuchen, vom Remoteserver auf dem lokalen Computer eine Dateifreigabe zu öffnen.  
  
3.  Versuchen Sie zum Wiederherstellen der Windows\-Authentifizierung, beide Computer neu zu starten.  Überprüfen Sie die Ereignisprotokolle auf dem lokalen Computer und dem Remotecomputer auf Kerberos\-Fehler, und klären Sie mit den Domänenadministratoren ab, ob bekannte Probleme vorliegen.  
  
## Siehe auch  
 [Einrichten der Remotetools auf dem Gerät](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)