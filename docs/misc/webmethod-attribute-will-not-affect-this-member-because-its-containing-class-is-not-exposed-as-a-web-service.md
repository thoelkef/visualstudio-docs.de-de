---
title: "Das WebMethod-Attribut hat auf diesen Member keine Auswirkungen, da die enthaltende Klasse nicht als Webdienst verf&#252;gbar gemacht wurde. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30771"
  - "bc30771"
helpviewer_keywords: 
  - "BC30771"
ms.assetid: 20b09f6a-b61a-4d89-9ca5-4632b5e68e65
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das WebMethod-Attribut hat auf diesen Member keine Auswirkungen, da die enthaltende Klasse nicht als Webdienst verf&#252;gbar gemacht wurde.
Das <xref:System.Web.Services.WebMethodAttribute>\-Attribut ermöglicht den Aufruf einer Methode von Remotewebclients aus, jedoch nur, wenn die Klasse der Methode von <xref:System.Web.Services.WebService> abgeleitet ist.  
  
 **Fehler\-ID:** BC30771  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Klasse so, dass sie aus <xref:System.Web.Services.WebService> abgeleitet wird.  
  
     – oder –  
  
-   Entfernen Sie das <xref:System.Web.Services.WebMethodAttribute>\-Attribut aus der Methode.  
  
## Siehe auch  
 [NIB: Exemplarische Vorgehensweise: Erstellen eines Webdiensts mithilfe von Visual Basic oder Visual C\#](http://msdn.microsoft.com/de-de/295f4c3f-9540-4bd1-b1cc-3e9cb9675cc7)