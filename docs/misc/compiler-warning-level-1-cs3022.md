---
title: "Compilerwarnung (Stufe 1) CS3022 | Microsoft Docs"
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
  - "CS3022"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3022"
ms.assetid: 9340645c-10c3-4e21-a825-3f05fae02ff7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3022
CLSCompliant\-Attribut hat bei der Anwendung auf Parameter keine Bedeutung. Versuchen Sie, es stattdessen auf die Methode anzuwenden.  
  
 Methodenparameter werden nicht auf CLS\-Kompatibilität überprüft, weil die CLS\-Kompatibilitätsregeln für Methoden und Typendeklarationen gelten.  
  
## Beispiel  
 Im folgenden Beispiel wird CS3022 generiert:  
  
```  
// CS3022.cs // compile with: /W:1 using System; [assembly: CLSCompliant(true)] [CLSCompliant(true)] public class C { public void F([CLSCompliant(true)] int i) { } public static void Main() { } }  
```