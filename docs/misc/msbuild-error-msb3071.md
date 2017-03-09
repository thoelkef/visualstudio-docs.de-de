---
title: "MSBuild Error MSB3071 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Exec.AllDriveLettersMappedError"
helpviewer_keywords: 
  - "MSB3071"
ms.assetid: 8afbc6ec-e399-4f06-a30b-f33c87642ef7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3071
**Alle Laufwerkbuchstaben von A: bis Z: sind derzeit in Gebrauch.  Da das Arbeitsverzeichnis \<Pfad\> ein UNC\-Pfad ist, benötigt die Exec\-Aufgabe einen freien Laufwerkbuchstaben, dem sie den UNC\-Pfad zuordnen kann  Entfernen Sie eine oder mehrere freigegebene Ressourcen, sodass wieder Laufwerkbuchstaben zur Verfügung stehen, oder geben Sie ein lokales Arbeitsverzeichnis an, bevor Sie diesen Befehl erneut ausführen.**  
  
 Alle Laufwerkbuchstaben von A: bis Z: sind derzeit in Gebrauch.  Da das angegebene Arbeitsverzeichnis ein UNC\-Pfad ist, benötigt die `Exec`\-Aufgabe einen freien Laufwerkbuchstaben, dem sie den UNC\-Pfad zuordnen kann.  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie eine oder mehrere freigegebene Ressourcen, sodass wieder Laufwerkbuchstaben zur Verfügung stehen, oder  
  
-   geben Sie ein lokales Arbeitsverzeichnis an, bevor Sie diesen Befehl erneut ausführen.  
  
## Siehe auch  
 [Exec Task](../msbuild/exec-task.md)