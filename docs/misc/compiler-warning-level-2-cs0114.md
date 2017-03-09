---
title: "Compilerwarnung (Stufe 2) CS0114 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0114"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0114"
ms.assetid: 9647772b-d581-4620-981e-f9c607d4a1af
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0114
"Funktion1" blendet vererbten Member "Funktion2" aus. Wenn diese Implementierung von der aktuellen Methode überschrieben werden soll, fügen Sie das override\-Schlüsselwort hinzu. Fügen Sie andernfalls das new\-Schlüsselwort hinzu.  
  
 Eine Deklaration in einer Klasse steht in Konflikt mit einer Deklaration in einer Basisklasse, sodass der Basisklassenmember ausgeblendet wird.  
  
 Weitere Informationen finden Sie unter [base](/dotnet/csharp/language-reference/keywords/base).  
  
 Im folgenden Beispiel wird CS0114 generiert:  
  
```  
// CS0114.cs // compile with: /W:2 /warnaserror abstract public class clx { public abstract void f(); } public class cly : clx { public void f() // CS0114, hides base class member // try the following line instead // override public void f() { } public static void Main() { } }  
```