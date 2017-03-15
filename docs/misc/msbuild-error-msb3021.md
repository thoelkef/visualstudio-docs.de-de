---
title: "MSBuild Error MSB3021 | Microsoft Docs"
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
  - "MSBuild.Copy.Error"
helpviewer_keywords: 
  - "MSB3021"
ms.assetid: 8cb3a860-6916-4406-b5c7-b1106b44b92a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3021
**Datei \<Datei\> kann nicht in \<Datei\> kopiert werden. '  \<Fehler\>'**  
  
 Die `Copy`\-Aufgabe kann die angegebene Datei nicht kopieren.  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie, ob die Zieldatei durch eine andere Anwendung gesperrt \(in Gebrauch\) ist.  Stellen Sie sicher, dass Sie die Berechtigung haben, die Quelldatei zu lesen und die Zieldatei in den Zielordner zu schreiben.  Wenn der Zieldateipfad sehr lang ist, müssen Sie möglicherweise an einen anderen Speicherort kopieren.  
  
## Siehe auch  
 [Copy Task](../msbuild/copy-task.md)   
 [Tasks](../msbuild/msbuild-tasks.md)