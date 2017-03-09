---
title: "Fehler: Die Verbindung mit dem Computer &lt;Name&gt; konnte nicht hergestellt werden. Der Computer kann im Netzwerk nicht gefunden werden. | Microsoft Docs"
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
  - "vs.debug.remote.dcom_disabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DCOM, Verbindung kann nicht hergestellt werden (Fehler)"
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Die Verbindung mit dem Computer &lt;Name&gt; konnte nicht hergestellt werden. Der Computer kann im Netzwerk nicht gefunden werden.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Verhalten tritt auf, wenn eine der folgenden Bedingungen erfüllt ist:  
  
-   Die Verbindung zum Remotecomputer ist unterbrochen.  
  
-   Das Benutzerkonto auf dem Remotecomputer ist deaktiviert.  
  
-   Das Kennwort auf dem Remotecomputer ist abgelaufen.  
  
### So beheben Sie dieses Verhalten  
  
-   Stellen Sie sicher, dass der lokale Computer und der Remotecomputer im gleichen Netzwerk sind.  Tun Sie dies, indem Sie mit dem Microsoft Windows Explorer \(oder File Explorer\) versuchen, auf den Remotecomputer zuzugreifen.  
  
     – und –  
  
-   Stellen Sie sicher, dass das Benutzerkonto, das Sie verwenden, um eine Verbindung mit dem Remotecomputer herzustellen, aktiviert ist.  
  
     – und –  
  
-   Stellen Sie sicher, dass das Kennwort, das Sie verwenden, um eine Verbindung mit dem Remotecomputer herzustellen, gültig und nicht abgelaufen ist.  
  
## Siehe auch  
 [Einrichten der Remotetools auf dem Gerät](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)