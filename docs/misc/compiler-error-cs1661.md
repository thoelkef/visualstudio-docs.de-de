---
title: "Compilerfehler CS1661 | Microsoft Docs"
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
  - "CS1661"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1661"
ms.assetid: 162d5736-ca3c-4a09-a5d9-a19da3d5bf24
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1661
Der anonyme Methodenblock kann nicht in den Delegattyp "Delegattyp" konvertiert werden, da die Parametertypen des angegebenen Blocks nicht mit den Parametertypen des Delegaten übereinstimmen.  
  
 Dieser Fehler tritt auf, wenn in der Definition einer anonymen Methode die Parametertypen der anonymen Methode nicht mit den Parametertypen des Delegaten übereinstimmen. Überprüfen Sie die Anzahl von Parametern, die Parametertypen sowie die ref\- oder out\-Parameter, und prüfen Sie auf eine genaue Übereinstimmung.  
  
 Im folgenden Beispiel wird CS1661 generiert:  
  
```  
// CS1661.cs delegate void MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(string s) { };  // CS1661 } }  
```