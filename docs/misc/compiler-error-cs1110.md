---
title: "Compilerfehler CS1110 | Microsoft Docs"
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
  - "CS1110"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1110"
ms.assetid: 5b571a76-1891-4f33-b23d-7c4cc654a05f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1110
Der 'this'\-Modifizierer kann nicht ohne Verweis auf „System.Core.dll“ im ersten Parameter einer Methodendeklaration verwendet werden. Fügen Sie einen Verweis auf „System.Core.dll“ hinzu, oder entfernen Sie den 'this'\-Modifizierer aus der Methodendeklaration.  
  
 Erweiterungsmethoden werden in Version 3.5 und höher von .NET Framework unterstützt. Erweiterungsmethoden generieren Metadaten, die die Methode mit einem Attribut kennzeichnen. Die Attributklasse befindet sich in „system.core.dll“.  
  
### So beheben Sie diesen Fehler  
  
1.  Wie in der Meldung angegeben – Sie können einen Verweis auf „System.Core.dll“ hinzufügen oder den `this`\-Modifizierer aus der Methodendeklaration entfernen.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1110 generiert, wenn die Datei nicht mit einem Verweis auf „System.Core.dll“ kompiliert wird:  
  
```  
// cs1110.cs // CS1110 // Compile with: /target:library public static class Extensions { public static bool Test(this bool b) { return b; } }  
```  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)