---
title: "Die Abh&#228;ngigkeit &quot;Abh&#228;ngigkeit1&quot; der Abh&#228;ngigkeit &quot;Abh&#228;ngigkeit2&quot; ist keine Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.notcomplusassembly2"
ms.assetid: e3b96601-458e-40de-81ea-ddcae9b42996
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Die Abh&#228;ngigkeit &quot;Abh&#228;ngigkeit1&quot; der Abh&#228;ngigkeit &quot;Abh&#228;ngigkeit2&quot; ist keine Assembly
Das Projektsystem hat bestimmt, dass es sich bei einer bestimmten Abhängigkeit \(Abhängigkeit1\) einer Assembly \(Abhängigkeit2\) nicht um eine .NET\-Assembly handelt.  
  
 **So beheben Sie diesen Fehler**  
  
-   Installieren Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu \(wenn die Assembly im Lieferumfang von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder von .NET Framework enthalten war\).  
  
     \- oder \-  
  
-   Installieren Sie das entsprechende Drittanbieter\-Steuerelement neu.  
  
     Ein Vorliegen dieses Fehlers verhindert nicht, dass das Projekt erstellt wird. Allerdings kann ein Laufzeitfehler auftreten.  
  
## Siehe auch  
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/de-de/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)