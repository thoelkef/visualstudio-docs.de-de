---
title: "Compilerfehler CS0277 | Microsoft Docs"
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
  - "CS0277"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0277"
ms.assetid: 8abec3eb-4d4c-4aab-87cc-d0444ab23535
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0277
"Klasse" implementiert den Schnittstellenmember "Accessor" nicht. "Klassenaccessor" ist nicht öffentlich.  
  
 Dieser Fehler tritt auf, wenn Sie versuchen, eine Eigenschaft einer Schnittstelle zu implementieren, die Implementierung des Eigenschaftenaccessors in der Klasse aber nicht öffentlich ist. Der Zugriff auf Methoden, die Schnittstellenmember implementieren, muss öffentlich sein. Um den Fehler zu beheben, entfernen Sie den Zugriffsmodifizierer für den Eigenschaftenaccessor.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0277 generiert:  
  
```  
// CS0277.cs public interface MyInterface { int Property { get; set; } } public class MyClass : MyInterface   // CS0277 { public int Property { get { return 0; } // Try this instead: //set { } protected set { } } }  
```