---
title: "Compilerwarnung (Stufe 1) CS0612 | Microsoft Docs"
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
  - "CS0612"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0612"
ms.assetid: 7695f3b7-ffef-43f7-83db-fc1a9e361f1a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS0612
"member" ist veraltet  
  
 Der Klassen\-Designer hat einen Member mit dem [Obsolete](http://msdn.microsoft.com/de-de/05e99cd0-bda6-4f79-a890-1ca093b4b488)\-Attribut gekennzeichnet. Dies bedeutet, dass der Member möglicherweise in einer zukünftigen Version der Klasse unterstützt wird.  
  
 Das folgende Beispiel zeigt, wie der Zugriff auf einen veralteten Member CS0612 generiert:  
  
```  
// CS0612.cs // compile with: /W:1 using System; class MyClass { [Obsolete] public static void ObsoleteMethod() { } [Obsolete] public static int ObsoleteField; } class MainClass { static public void Main() { MyClass.ObsoleteMethod();    // CS0612 here: method is deprecated MyClass.ObsoleteField = 0;   // CS0612 here: field is deprecated } }  
```