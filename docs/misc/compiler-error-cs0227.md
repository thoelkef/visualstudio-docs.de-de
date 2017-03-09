---
title: "Compilerfehler CS0227 | Microsoft Docs"
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
  - "CS0227"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0227"
ms.assetid: b595a1c9-8204-4ff7-a1d0-258b0b1d6ff7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0227
Unsicherer Code wird nur angezeigt, wenn mit \/unsafe kompiliert wird.  
  
 Wenn Quellcode das [unsafe](/dotnet/csharp/language-reference/keywords/unsafe)\-Schlüsselwort enthält, muss die [\/unsafe](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option)\-Compileroption ebenfalls verwendet werden. Weitere Informationen finden Sie unter [Unsicherer Code und Zeiger](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 Klicken Sie zum Festlegen der unsafe\-Option in [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] im Hauptmenü auf **Projekt**, wählen Sie den Bereich **Erstellen** aus, und aktivieren Sie das Kontrollkästchen „Unsicheren Code zulassen“.  
  
 Im folgenden Beispiel wird bei der Kompilierung ohne **\/unsafe** der Fehler CS0227 generiert:  
  
```  
// CS0227.cs public class MyClass { unsafe public static void Main()   // CS0227 { } }  
```  
  
## Siehe auch  
 [C\# Compiler Errors](/dotnet/csharp/language-reference/compiler-messages/index)