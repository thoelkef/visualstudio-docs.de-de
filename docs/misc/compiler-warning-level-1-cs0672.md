---
title: "Compilerwarnung (Stufe 1) CS0672 | Microsoft Docs"
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
  - "CS0672"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0672"
ms.assetid: 140a8708-97d0-444b-980b-62e74328cafb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS0672
Member "Member1" überschreibt den veralteten Member "Member2". Fügen Sie "Member1" das Obsolete\-Attribut hinzu.  
  
 Der Compiler hat `override` für eine Methode gefunden, die als `obsolete` markiert ist. Die überschreibende Methode selbst wurde jedoch nicht als "obsolete" markiert. Die überschreibende Methode löst beim Aufrufen immer den Fehler [CS0612](../misc/compiler-warning-level-1-cs0612.md) aus.  
  
 Überprüfen Sie die Methodendeklarationen, und geben Sie explizit an, ob eine Methode \(und alle Überschreibungen\) als `obsolete` markiert werden soll.  
  
 Im folgenden Beispiel wird CS0672 generiert:  
  
```  
// CS0672.cs // compile with: /W:1 class MyClass { [System.Obsolete] public virtual void ObsoleteMethod() { } } class MyClass2 : MyClass { public override void ObsoleteMethod()   // CS0672 { } } class MainClass { static public void Main() { } }  
```