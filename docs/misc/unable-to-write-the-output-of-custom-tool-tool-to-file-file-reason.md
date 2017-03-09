---
title: "Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_write_gen_output"
ms.assetid: eafcee9e-186b-4019-9042-8d8f9fc0925a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt;
Das Projektsystem konnte die Ausgabe des benutzerdefinierten Tools nicht in die angegebene Datei schreiben.  
  
 Wenn sich der Dateiname einer Eingabe des benutzerdefinierten Tools nicht ändert, wird die Ausgabe von einem benutzerdefinierten Tool in dieselbe Datei geschrieben.  Dieser Fehler kann auftreten, wenn die generierte Ausgabe auf der Festplatte gesperrt ist.  
  
 **So beheben Sie diesen Fehler**  
  
-   Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu, und führen Sie das benutzerdefinierte Tool erneut aus, indem Sie mit der rechten Maustaste auf die betroffene Datei klicken und im Kontextmenü die Option **Benutzerdefiniertes Tool ausführen** auswählen.  
  
     Die generierte Datei ist wahrscheinlich veraltet, da das Projektsystem sie nicht aktualisieren konnte.