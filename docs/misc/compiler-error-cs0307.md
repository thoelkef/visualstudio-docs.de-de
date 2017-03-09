---
title: "Compilerfehler CS0307 | Microsoft Docs"
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
  - "CS0307"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0307"
ms.assetid: 202a9985-ed7a-4e0a-9573-5624e066d314
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0307
'konstrukt' 'bezeichner' ist keine generische Methode. Wenn Sie eine Ausdrucksliste erstellen wollten, setzen Sie den \<\-Ausdruck in runde Klammern.  
  
 Das genannte Konstrukt war kein Typ und keine Methode, die einzigen Konstrukte, die generische Argumente annehmen können. Entfernen Sie die Typargumente in spitzen Klammern. Wenn ein Generikum erforderlich ist, deklarieren Sie Ihr generisches Konstrukt als generischen Typ oder generische Methode.  
  
 Im folgenden Beispiel wird CS0307 generiert:  
  
```  
// CS0307.cs class C { public int P { get { return 1; } } public static void Main() { C c = new C(); int p = c.P<int>();  // CS0307 – C.P is a property // Try this instead // int p = c.P; } }  
```