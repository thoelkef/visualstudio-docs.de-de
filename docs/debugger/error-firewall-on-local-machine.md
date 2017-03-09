---
title: "Fehler: Firewall auf lokalem Computer | Microsoft Docs"
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
  - "vs.debug.error.firewall.localmachine"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Firewall auf lokalem Computer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Internetverbindungsfirewall auf dem lokalen Computer, auf dem Sie Visual Studio ausführen, ist nicht für Remotedebuggen eingerichtet.  Für das Remotedebuggen von verwaltetem oder systemeigenem Code mit dem Standardtransport muss der TCP\-Anschluss 135 für den DCOM\-Datentransfer geöffnet werden.  Datei\- und Druckerfreigabe müssen geöffnet werden, und devenv.exe muss der Ausnahmenliste hinzugefügt werden.  Es kann möglicherweise auch erforderlich sein, einige IPSEC\-Anschlüsse zu öffnen.  
  
 Weitere Informationen finden Sie unter [Einrichten der Remotetools auf dem Gerät](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).