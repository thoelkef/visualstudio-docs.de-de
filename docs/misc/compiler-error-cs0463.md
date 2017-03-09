---
title: "Compilerfehler CS0463 | Microsoft Docs"
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
  - "CS0463"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0463"
ms.assetid: 0cb4be4e-86ea-4ade-8817-b17d4cacd4d5
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0463
Fehler bei der Auswertung des Dezimalkonstantenausdrucks: "Fehler"  
  
 Dieser Fehler tritt auf, wenn beim Kompilieren eines konstanten Ausdrucks \(Dezimal\) ein Überlauf erfolgt.  
  
 In der Regel treten Überlauffehler zur Laufzeit auf. In diesem Fall wurde der konstante Ausdruck so definiert, dass der Compiler das Ergebnis auswerten konnte und festgestellt hat, dass ein Überlauf auftreten würde.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS0463 ausgelöst.  
  
```  
// CS0463.cs using System; class MyClass { public static void Main() { const decimal myDec = 79000000000000000000000000000.0m + 79000000000000000000000000000.0m; // CS0463 Console.WriteLine(myDec.ToString()); } }  
```