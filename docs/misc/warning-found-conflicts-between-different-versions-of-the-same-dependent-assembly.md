---
title: "Warning: Found conflicts between different versions of the same dependent assembly | Microsoft Docs"
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
  - "ResolveAssemblyReference.SuggestedRedirects"
ms.assetid: fd14a789-bbdf-46c7-bcd3-9d3165adf96d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Warning: Found conflicts between different versions of the same dependent assembly
Diese Warnung wird angezeigt, wenn das Abhängigkeitsdiagramm des Projekts Verweise auf verschiedene Versionen derselben Assembly enthält.  
  
 Wenn Sie über eine app.config\-Datei verfügen, ermöglicht Ihnen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], eine bindende Umleitung hinzuzufügen.  Eine bindende Umleitung erzwingt, dass alle Assemblyverweise zu der Version der Assembly mit der höchsten Nummer umgeleitet werden. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] speichert die Umleitungsinformationen in app.config.  Wenn Sie eine bindende Umleitung verwenden, wird diese Warnung nicht mehr angezeigt.  
  
 Wenn Sie keine bindende Umleitung hinzufügen möchten, verweist das Projekt weiterhin auf die gleiche Version der Assembly.  Diese Warnung wird jedoch weiterhin angezeigt.  
  
### So beheben Sie diesen Fehler  
  
-   Doppelklicken Sie auf die Warnung, und wählen Sie bei der Aufforderung "Möchten Sie diese Konflikte durch Hinzufügen bindender Umleitungsdatensätze in der Datei "app.config" beheben?" die Option "Ja".