---
title: "MSBuild Error MSB3187 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PlatformMismatch"
helpviewer_keywords: 
  - "MSB3187"
ms.assetid: c5e93c14-b099-4176-bf1b-dbecc47fb3fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3187
**MSB3187: Für die referenzierte '\<assembly\>'\-Assembly ist ein anderer Zielprozessor festgelegt als für die Anwendung.**  
  
 Diese Warnung wird generiert, wenn die Zielplattform \(Prozessorarchitektur\) der Anwendung auf neutral \(MSIL\) festgelegt ist und die Assembly, auf die verwiesen wird, nicht neutral ist, oder wenn die Architektur der Anwendung nicht neutral und die Abhängigkeit neutral ist.  Auch wenn die Plattform in beiden Fällen nicht neutral ist, müssen die Architekturen übereinstimmen.  Außerdem müssen die Architektur der Anwendung und der Einstiegspunktassembly immer übereinstimmen.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die Zielplattform \(Prozessorarchitektur\) der Anwendung mit der Architektur der Assemblys, auf die verwiesen wird, und der Architektur der Einstiegspunktassembly übereinstimmt.  
  
## Siehe auch  
 [Dialogfeld "Erweiterte Compilereinstellungen \(Visual Basic\)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)   
 [Seite "Erstellen", Projekt\-Designer \(C\#\)](../ide/reference/build-page-project-designer-csharp.md)