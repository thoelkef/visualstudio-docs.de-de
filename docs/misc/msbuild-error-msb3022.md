---
title: "MSBuild Error MSB3022 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Copy.ExactlyOneTypeOfDestination"
helpviewer_keywords: 
  - "MSB3022"
ms.assetid: 74ebcced-8a56-4502-8fef-43d36c79a640
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3022
**Sowohl \<Attribut\> als auch \<Attribut\> waren als Eingabeparameter in der Projektdatei angegeben.  Wählen Sie nur einen der Parameter aus.**  
  
 Für die `Copy`\-Aufgabe müssen Sie `DestinationFiles` oder `DestinationDirectory` angeben, aber nicht beide Aufgabenattribute.  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie `DestinationFiles` oder `DestinationDirectory` für die `Copy`\-Aufgabe in der Projektdatei an.  
  
## Siehe auch  
 [Copy Task](../msbuild/copy-task.md)   
 [Tasks](../msbuild/msbuild-tasks.md)