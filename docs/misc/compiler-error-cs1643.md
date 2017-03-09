---
title: "Compilerfehler CS1643 | Microsoft Docs"
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
  - "CS1643"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1643"
ms.assetid: 521f352b-00fb-4d62-89be-44251db3cc5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1643
Nicht alle Codepfade geben in "Methode" einen Wert vom Typ "Typ" zurück.  
  
 Dieser Fehler tritt auf, wenn ein Delegatkörper keine return\-Anweisung oder eine return\-Anweisung hat, die der Compiler nicht überprüfen kann. Im folgenden Beispiel versucht der Compiler nicht, das Ergebnis der Verzweigungsbedingung vorherzusagen, um sicherzustellen, dass der anonyme Methodenblock immer einen Wert zurückgibt.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1643 generiert:  
  
```  
// CS1643.cs delegate int MyDelegate(); class C { static void Main() { MyDelegate d = delegate {                 // CS1643 int i = 0; if (i == 0) return 1; }; } }  
```