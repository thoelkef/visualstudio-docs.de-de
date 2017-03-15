---
title: "Die &quot;&lt;Methodenname&gt;&quot;-Methode enth&#228;lt einen Linkaufruf, &#252;berschreibt bzw. implementiert aber die folgenden Methoden, die keinen Linkaufruf enthalten. M&#246;glicherweise besteht eine Sicherheitsl&#252;cke: | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42200"
  - "vbc42200"
helpviewer_keywords: 
  - "BC42200"
ms.assetid: c79d672e-638c-4d87-9b93-edf12ce84a52
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die &quot;&lt;Methodenname&gt;&quot;-Methode enth&#228;lt einen Linkaufruf, &#252;berschreibt bzw. implementiert aber die folgenden Methoden, die keinen Linkaufruf enthalten. M&#246;glicherweise besteht eine Sicherheitsl&#252;cke:
Der Methode wurde eine Sicherheitsaktion für einen Linkaufruf hinzugefügt. Die Methode überschreibt bzw. implementiert jedoch Methoden, die keine Linkaufrufe enthalten. Daher können die überschriebenen oder implementierten Methoden mit unzureichenden Berechtigungen aufgerufen werden, was möglicherweise zu Sicherheitsproblemen führen kann.  
  
 Standardmäßig ist diese Meldung eine Warnung. Weitere Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42200  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie den überschriebenen und\/oder implementierten Methoden Linkaufrufe hinzu.  
  
## Siehe auch  
 [Link Demands](../Topic/Link%20Demands.md)   
 ["Demand" im Vergleich zu "LinkDemand"](http://msdn.microsoft.com/de-de/1ab877f2-70f4-4e0d-8116-943999dfe8f5)   
 [Sicherheitsoptimierungen](http://msdn.microsoft.com/de-de/cf255069-d85d-4de3-914a-e4625215a7c0)