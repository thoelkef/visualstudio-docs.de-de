---
title: "Compilerwarnung (Stufe 1) CS1911 | Microsoft Docs"
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
  - "CS1911"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1911"
ms.assetid: 95e8a7a0-1c19-4930-a7e9-3ae4060e97d3
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1911
Der Zugriff auf das Member 'name' aus einer anonymen Methode, einem Lambdaausdruck, einem Abfrageausdruck oder einem Iterator mithilfe des Schlüsselworts 'base' führt zu nicht überprüfbarem Code. Erwägen Sie, den Zugriff in eine Hilfsmethode auf dem enthaltenden Typ auszulagern.  
  
 Das Aufrufen von virtuellen Funktionen mit dem Schlüsselwort `base` innerhalb des Methodenkörpers von Iteratoren oder anonymen Methoden führt zu nicht überprüfbarem Code. Nicht überprüfbarer Code kann in teilweise vertrauenswürdigen Umgebungen nicht ausgeführt werden.  
  
 Eine Lösung für CS1911 besteht darin, den Aufruf der virtuellen Funktion in eine Hilfsfunktion auszulagern.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1911 generiert.  
  
```  
// CS1911.cs // compile with: /W:1 using System; delegate void D(); delegate D RetD(); class B { protected virtual void M() { Console.WriteLine("B.M"); } } class Der : B { protected override void M() { Console.WriteLine("D.M"); } void Test() { base.M(); } D Test2() { return new D(base.M); } public D CallBaseM() { return delegate () { base.M(); };   // CS1911 // try the following line instead // return delegate () { Test(); }; } public RetD DelToBaseM() { return delegate () { return new D(base.M); };   // CS1911 // try the following line instead // return delegate () { return Test2(); }; } } class Program { public static void Main() { Der der = new Der(); D d = der.CallBaseM(); d(); RetD rd = der.DelToBaseM(); rd()(); } }  
```