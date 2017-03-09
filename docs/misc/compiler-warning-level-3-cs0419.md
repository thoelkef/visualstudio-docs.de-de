---
title: "Compilerwarnung (Stufe 3) CS0419 | Microsoft Docs"
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
  - "CS0419"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0419"
ms.assetid: de439ad5-422f-4ed6-96d6-69dade29c7b2
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 3) CS0419
Mehrdeutige Referenz im cref\-Attribut: 'Methodenname1'  Es wird 'Methodenname2' angenommen, jedoch könnten auch andere Überladungen, einschließlich 'Methodenname3', zugeordnet werden.  
  
 In einem XML\-Dokumentationskommentar im Code konnte ein Verweis nicht aufgelöst werden. Dies kann auftreten, wenn die Methode überladen wird oder wenn zwei verschiedene Bezeichner mit dem gleichen Namen gefunden werden. Um die Warnung aufzulösen, verwenden Sie einen qualifizierten Namen, um den Verweis eindeutig zu machen, oder schließen Sie die bestimmte Überladung in Klammern ein.  
  
 Im folgenden Beispiel wird CS0419 generiert:  
  
```  
// cs0419.cs // compile with: /doc:x.xml /W:3 interface I { /// text for F(void) void F(); /// text for F(int) void F(int i); } /// text for class MyClass public class MyClass { /// <see cref="I.F"/> public static void MyMethod(int i) { } /* Try this instead: /// <see cref="I.F(int)"/> public static void MyMethod(int i) { } */ /// text for Main public static void Main () { } }  
```