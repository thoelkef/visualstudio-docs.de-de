---
title: "The custom tool &#39;custom tool&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.generator_fail_errorinfo"
ms.assetid: e846b946-a123-49fe-b4bc-a7bbda501417
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The custom tool &#39;custom tool&#39; failed. &lt;reason&gt;
Das benutzerdefinierte Tool wurde nicht erfolgreich ausgeführt.  
  
 Wenn ein MSDataSetGenerator\-Fehler beim Aktualisieren von Projekten auftritt, die Datasets auf N\-Ebene enthalten, müssen Sie das benutzerdefinierte Tool erneut ausführen, nachdem alle Projekte aktualisiert wurden.  
  
 Fehler beim Ausführen des benutzerdefinierten Tools "MSDataSetGenerator".  Das im DataSetProject\-Attribut in \<Datasetname\> angegebene Projekt muss auf eine Version von .NET Framework abzielen, die dem aktuellen Projekt entspricht oder aktueller ist.  
  
### So korrigieren Sie MSDataSetGenerator\-Fehler in Datasets auf N\-Ebene  
  
-   Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf die XSD\-Datei, und klicken Sie dann auf **Benutzerdefiniertes Tool ausführen**.