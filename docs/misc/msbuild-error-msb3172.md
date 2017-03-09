---
title: "MSBuild Error MSB3172 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ReadInputManifestFailed"
helpviewer_keywords: 
  - "MSB3172"
ms.assetid: aa7291db-1f36-41e7-a510-90cd4daaa89d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3172
**MSB3172: Das Manifest \<Datei\> kann nicht gelesen werden. '  \<Fehler\>'**  
  
 Dieser Fehler wird generiert, wenn beim Buildprozess ein unspezifisches Problem beim Lesen einer Manifestdatei auftritt.  Die nachfolgende Fehlermeldung enthält den Dateinamen, gefolgt von ausführlicheren Informationen über das aufgetretene Problem.  
  
 Möglicherweise haben Sie eine Assembly\- oder Manifestdatei als Inhaltsdatei hinzugefügt.  Anstelle des Befehls **Datei hinzufügen** sollten Sie den Befehl **Verweis hinzufügen** verwenden, um sicherzustellen, dass das Projektsystem auf die abhängige Assembly verweist.  Anspruchsvollere Projekte markieren häufig das EXE\-Manifest im Ordner bin als Projektdatei. Dies sollte jedoch nach Möglichkeit vermieden werden.  Die verborgene app.manifest\-Datei wird zur .exe.manifest\-Datei und kann für erweiterte Szenarien manuell bearbeitet werden.  
  
## Siehe auch  
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)