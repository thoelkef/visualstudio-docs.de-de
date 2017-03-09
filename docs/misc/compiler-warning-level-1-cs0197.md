---
title: "Compilerwarnung (Stufe 1) CS0197 | Microsoft Docs"
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
  - "CS0197"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0197"
ms.assetid: 2b5b1b8d-ce13-4bd7-b80a-abb80e9f79ad
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS0197
Das Übergeben von 'Argument' als Verweis oder Ausgabe oder das Übernehmen der Adresse kann zu einer Laufzeitausnahme führen, da es sich hierbei um ein Feld einer Marshal\-by\-reference\-Klasse handelt.  
  
 Jede Klasse, die direkt oder indirekt von <xref:System.MarshalByRefObject> abgeleitet wird, ist eine Marshal\-by\-reference\-Klasse. Eine solche Klasse kann über Prozess\- und Computergrenzen hinweg als Verweis gemarshallt werden. Folglich können Instanzen dieser Klasse Proxys für Remoteobjekte sein. Sie können ein Feld eines Proxyobjekts nicht als [ref](/dotnet/csharp/language-reference/keywords/ref) oder [out](/dotnet/csharp/language-reference/keywords/out) übergeben. Daher können Felder einer solchen Klasse nicht als `ref` oder `out` übergeben werden, es sei denn, die Instanz ist [this](/dotnet/csharp/language-reference/keywords/this), die kein Proxyobjekt sein kann.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0197 generiert.  
  
```  
// CS0197.cs // compile with: /W:1 class X : System.MarshalByRefObject { public int i; } class M { public int i; static void AddSeventeen(ref int i) { i += 17; } static void Main() { X x = new X(); x.i = 12; AddSeventeen(ref x.i);   // CS0197 // OK M m = new M(); m.i = 12; AddSeventeen(ref m.i); } }  
```