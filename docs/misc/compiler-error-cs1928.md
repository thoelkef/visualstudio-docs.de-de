---
title: "Compilerfehler CS1928 | Microsoft Docs"
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
  - "CS1928"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1928"
ms.assetid: bcc9dbef-ded5-4ddd-8c03-a9837cb6d165
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1928
'Typ' enthält keine Definition für 'Methode', und die Überladung der optimalen 'Methode'\-Erweiterungsmethode enthält einige ungültige Argumente.  
  
 Dieser Fehler wird ausgelöst, wenn der Compiler keinen Klassenmember mit dem Namen der aufgerufenen Methode findet. Er kann eine Erweiterungsmethode mit diesem Namen finden, aber nicht mit einer Signatur, die mit den Typen übereinstimmt, die Sie mit dem Methodenaufruf übergeben haben.  
  
### So beheben Sie diesen Fehler  
  
1.  Übergeben Sie Typen, die mit einer vorhandenen Erweiterungsmethode oder Klassenmethode übereinstimmen.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS1928 ausgelöst:  
  
```  
// cs1928.cs class Test { static void Main() { Test t = new Test(); t.M("hi"); // CS1928 } } static class Ext { public static void M(this Test t, int i) { } }  
```  
  
 Dieser Fehler geht häufig mit CS1503 einher: Argument 'n': Konvertierung von 'TypA' in 'TypB' nicht möglich.  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)