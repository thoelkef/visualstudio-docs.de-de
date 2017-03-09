---
title: "Es wurden keine abh&#228;ngigen Assemblys f&#252;r die Assembly &quot;Assembly&quot; gefunden. Das Assemblymanifest ist m&#246;glicherweise besch&#228;digt. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotfinddependencies"
ms.assetid: 6d6e6dda-6cec-49d0-9659-63dfdbd7d247
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Es wurden keine abh&#228;ngigen Assemblys f&#252;r die Assembly &quot;Assembly&quot; gefunden. Das Assemblymanifest ist m&#246;glicherweise besch&#228;digt.
Das Projektsystem konnte eine Assembly nicht lesen, auf die im Projekt verwiesen wird. Somit kann das Projektsystem die Abhängigkeiten der Assembly nicht ermitteln. Ein Vorliegen dieses Fehlers verhindert nicht, dass das Projekt erstellt wird. Allerdings kann ein Laufzeitfehler auftreten.  
  
 **So beheben Sie diesen Fehler**  
  
-   Installieren Sie Visual Studio neu \(wenn die Assembly im Lieferumfang von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] enthalten war\).  
  
     \- oder \-  
  
-   Installieren Sie das entsprechende Drittanbieter\-Steuerelement neu.  
  
## Siehe auch  
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/de-de/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)